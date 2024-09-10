  /**

   * Creates a toggle through the '>' char and the 'Space' key

   */

  createToggleWithShortcut(blockContainer) {

    const content = blockContainer.textContent;

  

    if ((content[0] === '>') && !this.isPartOfAToggle(blockContainer)) {

      const blockCaller = this.api.blocks.getCurrentBlockIndex();

  

      this.api.blocks.insert('toggle', { text: content.slice(2) }, this.api, blockCaller, true);

      this.api.blocks.delete(blockCaller + 1);

      this.api.caret.setToBlock(blockCaller);

    }

  }