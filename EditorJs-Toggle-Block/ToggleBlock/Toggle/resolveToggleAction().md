  /**

   * Converts the toggle status to its opposite.

   * If the toggle status is open, then now will be closed and

   * the icon will reset to rotation. Otherwise, will be open

   * and the icon will be rotated 90 degrees to the left.

   *

   * @returns {string} icon - toggle icon

   */

  resolveToggleAction() {

    const icon = this.wrapper.firstChild;

    const svg = icon.firstChild;

  

    if (this.data.status === 'closed') {

      this.data.status = 'open';

      svg.style.transform = 'rotate(90deg)';

    } else {

      this.data.status = 'closed';

      svg.style.transform = 'rotate(0deg)';

    }

  

    const toggleBlock = this.api.blocks.getBlockByIndex(this.api.blocks.getCurrentBlockIndex());

    toggleBlock.holder.setAttribute('status', this.data.status);

  }