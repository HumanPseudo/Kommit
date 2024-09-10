  /**

   * Validates if a block contains one of the classes to be

   * part of a toggle. If It has it returns 'true' (It's part

   * of a toggle), otherwise returns 'false' (It's another

   * type of block)

   *

   * @param {HTMLDivElement} block - Block to be validated

   * @returns {boolean}

   */

  isPartOfAToggle(block) {

    const classes = Array.from(block.classList);

    const classNamesToCheck = ['toggle-block__item', 'toggle-block__input', 'toggle-block__selector'];

    const isToggleChild = classNamesToCheck.some(

      (className) => block.getElementsByClassName(className).length !== 0,

    );

    const isToggle = classNamesToCheck.some((className) => classes.includes(className));

  

    return isToggle || isToggleChild;

  }