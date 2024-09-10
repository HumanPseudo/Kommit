  /**

   * Adds the required listeners to call the toggle shortcuts

   * on the editor.

   */

  addListeners() {

    if (!this.readOnly) {

      const redactor = document.activeElement;

      redactor.addEventListener('keyup', (e) => {

        const blockContainer = document.activeElement;

        const currentBlock = this.getCurrentBlockIndex();

        const { holder: currentBlockContainer } = this.getBlockByIndex(currentBlock);

  

        if (e.code === 'Space') {

          this.createToggleWithShortcut(blockContainer);

        } else if (currentBlock > 0 && !this.isPartOfAToggle(currentBlockContainer) && e.code === 'Tab') {

          this.nestBlock(currentBlockContainer);

        }

      });

    }

  }