  /**

   * Sets the default content. If the toggle has no other blocks inside it,

   * so sets the 'block__hidden tag' in the default content,

   * otherwise it removes it.

   */

  setDefaultContent() {

    const children = document.querySelectorAll(`div[foreignKey="${this.wrapper.id}"]`);

    const { firstChild, lastChild } = this.wrapper;

    const { status } = this.data;

    const value = (children.length > 0 || status === 'closed');

  

    lastChild.classList.toggle('toggle-block__hidden', value);

    firstChild.style.color = (children.length === 0) ? 'gray' : 'black';

  }