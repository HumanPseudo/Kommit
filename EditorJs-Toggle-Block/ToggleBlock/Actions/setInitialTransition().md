  /**

   * Adds the initial status for the icon, and establishes

   * the delay for the transition displayed when the icon

   * is clicked.

   */

  setInitialTransition() {

    const { status } = this.data;

    const icon = this.wrapper.firstChild;

    const svg = icon.firstChild;

    svg.style.transition = '0.1s';

    svg.style.transform = `rotate(${status === 'closed' ? 0 : 90}deg)`;

  }