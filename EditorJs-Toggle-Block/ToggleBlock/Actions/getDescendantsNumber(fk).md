  /**

   * Return the number of blocks inside the root Toggle

   * @param {string} fk - The id of the root Toggle

   */

  getDescendantsNumber(fk) {

    let counter = 0;

    const listChildren = document.querySelectorAll(`div[foreignKey="${fk}"]`);

    listChildren.forEach((child) => {

      // Evaluate if the child is a toggle

      if (child.hasAttribute('status')) {

        const childId = child.querySelector('.toggle-block__selector').getAttribute('id');

        counter += this.getDescendantsNumber(childId);

      }

      counter += 1;

    });

    return counter;

  }