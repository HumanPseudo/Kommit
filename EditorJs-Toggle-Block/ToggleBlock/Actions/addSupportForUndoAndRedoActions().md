  /**

   * Adds mutation observer to restore the item attributes

   * when the undo action is executed and they're lost.

   */

  addSupportForUndoAndRedoActions() {

    if (!this.readOnly) {

      const target = document.querySelector('div.codex-editor__redactor');

  

      const observer = new MutationObserver((mutations) => {

        mutations.forEach((mutation) => {

          if (mutation.type === 'childList') {

            setTimeout(this.restoreItemAttributes.bind(this, mutation));

          }

        });

      });

  

      const config = { attributes: true, childList: true, characterData: true };

  

      observer.observe(target, config);

    }

  }