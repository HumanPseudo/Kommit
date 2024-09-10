  /**

   * Restores the item attributes to nested blocks.

   *

   * @param {HTMLDivElement} mutation - Html element removed or inserted

   */

  restoreItemAttributes(mutation) {

    if (this.wrapper !== undefined) {

      const index = this.api.blocks.getCurrentBlockIndex();

      const block = this.api.blocks.getBlockByIndex(index);

      const { holder } = block;

      const currentBlockValidation = !this.isPartOfAToggle(holder);

      const { length: toggleItemsCount } = this.itemsId;

      const { length: existingToggleItemsCount } = document.querySelectorAll(`div[foreignKey="${this.data.fk}"]`);

  

      if (this.itemsId.includes(block.id) && currentBlockValidation) {

        this.setAttributesToNewBlock(index);

      } else if (

        mutation.addedNodes[0]

        && mutation?.previousSibling

        && this.isPartOfAToggle(mutation.previousSibling)

        && !this.isPartOfAToggle(mutation.addedNodes[0])

        && toggleItemsCount > existingToggleItemsCount

      ) {

        const { id: addedBlockId } = mutation.addedNodes[0];

        const addedBlock = this.api.blocks.getById(addedBlockId);

        this.setAttributesToNewBlock(null, this.wrapper.id, addedBlock);

        this.itemsId[index] = block.id;

      }

    }

  }