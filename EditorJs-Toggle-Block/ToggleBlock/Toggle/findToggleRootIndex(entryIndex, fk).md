  /**

  * Returns the toggle's root index, given the index of one of its children

  *

  * @param {number} entryIndex - block index

  * @param {String} fk - The block's foreign key

  * @returns {number} The Toggle's root index

  */

  findToggleRootIndex(entryIndex, fk) {

    const block = this.getBlockByIndex(entryIndex);

    const { holder } = block;

  

    if (this.isAToggleRoot(holder)) {

      const id = holder.querySelector('.toggle-block__selector').getAttribute('id');

      if (fk === id) {

        return entryIndex;

      }

    }

    if (entryIndex - 1 >= 0) {

      return this.findToggleRootIndex(entryIndex - 1, fk);

    }

    return -1;

  }