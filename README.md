# bridge
Bridge

@Component({
  tag: 'my-list',
  styleUrl: 'my-list.css',
  shadow: true,
})
export class MyList {
  private listItems: HTMLElement[] = [];

  componentDidLoad() {
    this.listItems = Array.from(
      this.el.shadowRoot.querySelectorAll('[role="listitem"]')
    );
  }

  private handleKeydown(event: KeyboardEvent, index: number) {
    if (event.key === 'ArrowDown') {
      event.preventDefault();
      const nextItem = this.listItems[index + 1];
      if (nextItem) nextItem.focus();
    } else if (event.key === 'ArrowUp') {
      event.preventDefault();
      const prevItem = this.listItems[index - 1];
      if (prevItem) prevItem.focus();
    }
  }

  render() {
    return (
      <div role="list">
        <div
          role="listitem"
          tabindex="0"
          onKeyDown={(event) => this.handleKeydown(event, 0)}
        >
          <div>
            <p>Texto descriptivo</p>
            <button>Botón</button>
          </div>
        </div>
        <div
          role="listitem"
          tabindex="0"
          onKeyDown={(event) => this.handleKeydown(event, 1)}
        >
          <div>
            <p>Otro texto descriptivo</p>
            <a href="#">Enlace</a>
          </div>
        </div>
      </div>
    );
  }
}

<div role="list">
  <div role="listitem" tabindex="0">
    <div>
      <!-- Contenido dentro del listitem -->
      <p>Texto descriptivo</p>
      <button>Botón</button>
    </div>
  </div>
  <div role="listitem" tabindex="0">
    <div>
      <!-- Otro contenido -->
      <p>Otro texto descriptivo</p>
      <a href="#">Enlace</a>
    </div>
  </div>
</div>

