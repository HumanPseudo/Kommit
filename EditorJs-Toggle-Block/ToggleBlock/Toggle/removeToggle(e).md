  /**

   * Deletes the toggle structure and converts the main text and the nested blocks

   * in regular blocks.

   *

   * @param {KeyboardEvent} e - key down event

   */

  removeToggle(e) {

    if (e.code === 'Backspace') {

      const { children } = this.wrapper;

      const content = children[1].innerHTML;

  

      const cursorPosition = document.getSelection();

  

      if (cursorPosition.focusOffset === 0) {

        const index = this.api.blocks.getCurrentBlockIndex();

        const breakLine = content.indexOf('<br>');

        const end = breakLine === -1 ? content.length : breakLine;

        const blocks = document.querySelectorAll(`div[foreignKey="${this.wrapper.id}"]`);

  

        for (let i = 1; i < blocks.length + 1; i += 1) {

          this.removeAttributesFromNewBlock(index + i);

        }

  

        this.api.blocks.delete(index);

        this.api.blocks.insert('paragraph', { text: content.slice(0, end) }, {}, index, 1);

        this.api.caret.setToBlock(index);

      }

    }

  }