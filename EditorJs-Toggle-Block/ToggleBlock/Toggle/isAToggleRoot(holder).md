  /**

   * Returns true if the div element is a toggle root, otherwise, returns false

   * @param {HTMLDivElement} holder

   * @returns {boolean}

   */

  isAToggleRoot(holder) {

    return holder.classList.contains('toggle-block__selector') || Boolean(holder.querySelector('.toggle-block__selector'));

  }