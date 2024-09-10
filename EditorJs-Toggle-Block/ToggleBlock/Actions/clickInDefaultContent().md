  /**

   * Adds the actions to do when the default content is clicked.

   */

  clickInDefaultContent() {

    this.api.blocks.insert();

    this.setAttributesToNewBlock();

    this.setDefaultContent();

  }