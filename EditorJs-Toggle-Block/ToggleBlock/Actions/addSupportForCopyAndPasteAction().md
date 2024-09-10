  /**

   * Adds mutation observer to reset the toggle ids

   * when a toggle is copied and pasted.

   */

  addSupportForCopyAndPasteAction() {

    if (!this.readOnly) {

      const target = document.querySelector('div.codex-editor__redactor');

  

      const observer = new MutationObserver((mutations) => {

        mutations.forEach((mutation) => {

          if (mutation.type === 'childList') {

            setTimeout(this.resetIdToCopiedBlock.bind(this, mutation));

          }

        });

      });

  

      const config = { attributes: true, childList: true, characterData: true };

  

      observer.observe(target, config);

    }

  }