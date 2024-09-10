  /**

   * Sets the focus at the end of the toggle root when

   * a nested block is deleted through the backspace key.

   */

  setFocusToggleRootAtTheEnd() {

    const toggle = document.activeElement;

    const selection = window.getSelection();

    const range = document.createRange();

  

    selection.removeAllRanges();

    range.selectNodeContents(toggle);

    range.collapse(false);

    selection.addRange(range);

    toggle.focus();

  }