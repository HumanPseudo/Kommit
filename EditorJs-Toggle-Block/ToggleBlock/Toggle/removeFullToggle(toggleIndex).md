  /**

   * Removes a toggle root and its nested blocks.

   *

   * @param {number} toggleIndex - toggle index

   */

  removeFullToggle(toggleIndex) {

    const children = document.querySelectorAll(`div[foreignKey="${this.wrapper.id}"]`);

    const { length } = children;

  

    for (let i = toggleIndex; i < toggleIndex + length; i += 1) {

      setTimeout(() => this.api.blocks.delete(toggleIndex));

    }

  }