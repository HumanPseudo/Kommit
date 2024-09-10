  /**

   * Adds drop listener to move the childs item

   * when the drag and drop action is executed.

   */

  addSupportForDragAndDropActions() {

    if (!this.readOnly) {

      if (this.wrapper === undefined) {

        setTimeout(() => this.addSupportForDragAndDropActions(), 250);

        return;

      }

  

      // Set status in attribute to a proper hide and show

      const toggleBlock = document.querySelector(`#${this.wrapper.id}`).parentNode.parentNode;

      toggleBlock.setAttribute('status', this.data.status);

  

      const settingsButton = document.querySelector('.ce-toolbar__settings-btn');

      settingsButton.setAttribute('draggable', 'true');

      settingsButton.addEventListener('dragstart', () => {

        this.startBlock = this.api.blocks.getCurrentBlockIndex();

        this.nameDragged = this.api.blocks.getBlockByIndex(this.startBlock).name;

        this.holderDragged = this.api.blocks.getBlockByIndex(this.startBlock).holder;

      });

  

      document.addEventListener('drop', (event) => {

        // Get the position when item was dropped

        const { target } = event;

        if (document.contains(target)) {

          const dropTarget = target.classList.contains('ce-block') ? target : target.closest('.ce-block');

          if (dropTarget && dropTarget !== this.holderDragged) {

            let endBlock = this.getIndex(dropTarget);

  

            // Control the toggle's children will be positioned down of the parent

            endBlock = this.startBlock < endBlock ? endBlock + 1 : endBlock;

  

            // Check if the item dropped is another toggle

            const isTargetAToggle = dropTarget.querySelectorAll('.toggle-block__selector').length > 0

              || dropTarget.getAttribute('foreignKey') !== null;

  

            setTimeout(() => {

              // Verify if the item dropped is the toggle

              if (this.nameDragged === 'toggle') {

                // Verify if the toggle dropped is the same of this eventListener

                const currentToggleDropped = this.holderDragged.querySelector(`#${this.wrapper.id}`);

  

                if (currentToggleDropped) {

                  // Check if the toggle dropped was not dropped in its children

                  if (!this.isChild(currentToggleDropped.getAttribute('id'), dropTarget.getAttribute('foreignKey'))) {

                    // If is a toggle we have to add the attributes to make it a part of the toggle

                    this.assignToggleItemAttributes(isTargetAToggle, dropTarget);

                    this.moveChildren(endBlock);

                  } else {

                    // If we are dropping in the toggle children,

                    // we have to move the toggle in the original position

                    if (this.startBlock === endBlock) {

                      this.api.blocks.move(this.startBlock + 1, endBlock);

                    } else {

                      this.api.blocks.move(this.startBlock, endBlock);

                    }

  

                    // And remove the attributes

                    if (!isTargetAToggle) {

                      const newToggleIndex = this.getIndex(this.holderDragged);

                      this.removeAttributesFromNewBlock(newToggleIndex);

                    }

                  }

                }

              } else if (this.nameDragged) {

                // Add the dropped item as an element of the toggle

                this.assignToggleItemAttributes(isTargetAToggle, dropTarget);

              }

  

              // If we are dropping out of a toggle we have to remove the attributes

              if (!isTargetAToggle) {

                const newToggleIndex = this.getIndex(this.holderDragged);

                this.removeAttributesFromNewBlock(newToggleIndex);

              }

            });

          }

        }

      });

    }

  }