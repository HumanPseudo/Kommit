  /**

   * If the toggle root is empty and the key event received is 'backspace'

   * or 'enter', its content is cleared so that the visible placeholder

   * is set through the css.

   *

   * @param {KeyboardEvent} e - key up event

   */

  setPlaceHolder(e) {

    if (e.code === 'Backspace' || e.code === 'Enter') {

      const { children } = this.wrapper;

      const { length } = children[1].textContent;

  

      if (length === 0) children[1].textContent = '';

    }

  }