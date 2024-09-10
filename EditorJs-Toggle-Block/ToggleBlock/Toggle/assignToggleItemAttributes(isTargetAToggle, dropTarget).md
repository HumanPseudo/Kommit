  assignToggleItemAttributes(isTargetAToggle, dropTarget) {

    if (isTargetAToggle) {

      const foreignKey = dropTarget.getAttribute('foreignKey')

        ?? dropTarget.querySelector('.toggle-block__selector').getAttribute('id');

  

      const newToggleIndex = this.getIndex(this.holderDragged);

      this.setAttributesToNewBlock(newToggleIndex, foreignKey);

    }

  }