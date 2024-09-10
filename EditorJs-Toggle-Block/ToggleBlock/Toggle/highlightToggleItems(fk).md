  /**

   * Highlight the blocks that belongs to the Toggle

   * @param {string} fk - The id of the root Toggle

   */

  highlightToggleItems(fk) {

    const listChildren = document.querySelectorAll(`div[foreignKey="${fk}"]`);

    listChildren.forEach((child) => {

      child.classList.add('ce-block--selected');

      // Evaluate if the child is a toggle, then highlight also its children

      if (child.hasAttribute('status')) {

        const childId = child.querySelector('.toggle-block__selector').getAttribute('id');

        this.highlightToggleItems(childId);

      }

    });

  }