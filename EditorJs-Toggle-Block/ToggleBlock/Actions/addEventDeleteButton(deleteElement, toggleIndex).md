  /**

   * Add listener to delete button.

   * @param {HTMLDivElement} deleteElement

   * @param {number} toggleIndex

   */

  addEventDeleteButton(deleteElement, toggleIndex) {

    if (!deleteElement) return;

  

    deleteElement.addEventListener('click', () => {

      const classesList = deleteElement.classList;

      const classes = Object.values(classesList);

  

      if (classes.indexOf('clicked-to-destroy-toggle') === -1) {

        deleteElement.classList.add('clicked-to-destroy-toggle');

      } else {

        this.removeFullToggle(toggleIndex);

      }

    });

  }