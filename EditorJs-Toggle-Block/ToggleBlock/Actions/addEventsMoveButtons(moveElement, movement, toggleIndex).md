  /**

   * Add listener to move button.

   * @param {HTMLDivElement} moveElement

   * @param {number} movement // 0: Move down || 1: Move up

   * @param {number} toggleIndex

   */

  addEventsMoveButtons(moveElement, movement, toggleIndex) {

    if (!moveElement) return;

    moveElement.addEventListener('click', () => {

      this.moveToggle(toggleIndex, movement);

    });

  }