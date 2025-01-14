  /**

   * Creates a toggle block view without paragraphs

   * and sets the default content.

   */

  createToggle() {

    this.wrapper = document.createElement('div');

    this.wrapper.classList.add('toggle-block__selector');

    this.wrapper.id = this.data.fk;

  

    const icon = document.createElement('span');

    const input = document.createElement('div');

    const defaultContent = document.createElement('div');

  

    icon.classList.add('toggle-block__icon');

    icon.innerHTML = toggleIcon;

  

    input.classList.add('toggle-block__input');

    input.setAttribute('contentEditable', !this.readOnly);

    input.innerHTML = this.data.text || '';

  

    // Events

    if (!this.readOnly) {

      // Events to create other blocks and destroy the toggle

      input.addEventListener('keyup', this.createParagraphFromToggleRoot.bind(this));

      input.addEventListener('keydown', this.removeToggle.bind(this));

  

      // Sets the focus at the end of the text when a nested block is deleted with the backspace key

      input.addEventListener('focusin', () => this.setFocusToggleRootAtTheEnd());

  

      // Establishes the placeholder for the toggle root when it's empty

      input.addEventListener('keyup', this.setPlaceHolder.bind(this));

      input.setAttribute('placeholder', this.placeholder);

  

      // Calculates the number of toggle items

      input.addEventListener('focus', this.setDefaultContent.bind(this));

      input.addEventListener('focusout', this.setDefaultContent.bind(this));

  

      // Event to add a block when the default content is clicked

      defaultContent.addEventListener('click', this.clickInDefaultContent.bind(this));

  

      input.addEventListener('focus', this.setNestedBlockAttributes.bind(this));

    }

  

    defaultContent.classList.add('toggle-block__content-default', 'toggle-block__hidden');

    defaultContent.innerHTML = this.defaultContent;

  

    this.wrapper.appendChild(icon);

    this.wrapper.appendChild(input);

    this.wrapper.appendChild(defaultContent);

  }