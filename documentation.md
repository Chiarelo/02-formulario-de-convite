# Documentação do Código

## Estrutura do Componente Radio Box

### HTML
```html
<div class="radio-box flex-1">
  <label for="type">Tipo</label>
  <div class="radio-wrapper">
    <div class="radio-content">
      <input type="radio" name="type" id="in-person">
      <img src="assets/icons/building-2.svg" alt="">
      <label for="in-person">Presencial</label>
    </div>

    <div class="radio-content">
      <input type="radio" name="type" id="online">
      <img src="assets/icons/video.svg" alt="">
      <label for="online">Online</label>
    </div>
  </div>
</div>
```

### Explicação do HTML
- O elemento `<div class="radio-box flex-1">` agrupa os botões de opção.
- O `<label for="type">` define o título "Tipo" para o grupo de botões.
- A `<div class="radio-wrapper">` contém os botões de opção.
- Cada `<div class="radio-content">` representa uma opção (Presencial ou Online).
- Os botões `input` estão ocultos, permitindo que o clique aconteça em toda a área da opção.

---

### CSS
```css
.radio-wrapper {
  display: flex;
  height: 3rem;
  background-color: var(--input-base);
  border: 2px solid transparent;
  outline: 1px solid var(--input-stroke);
  border-radius: 0.5rem;
  padding: 0.25rem;
  gap: 0.25rem;
}

.radio-content {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: var(--input-base);
  height: 100%;
  padding: 0.25rem;
  gap: 0.5rem;
  border-radius: 0.5rem;
  flex: 1 0 0;
  cursor: pointer;
  position: relative;
  transition: background-color 0.3s ease;
}

.radio-content img {
  width: 1rem;
  height: 1rem;
}

.radio-content label {
  margin: 0;
}

.radio-content:hover,
.radio-content:focus,
.radio-content:has(:checked) {
  background-color: var(--shape-hover);
}

.radio-content:hover label,
.radio-content:focus label,
.radio-content:has(:checked) label {
  color: var(--text-heading);
}

.radio-content input {
  all: unset;
  position: absolute;
  inset: 0;
}
```

### Explicação do CSS
- `.radio-wrapper`:
  - Define o layout flexível para distribuir os botões igualmente.
  - Define altura, espaçamento, bordas e cores.
- `.radio-content`:
  - Utiliza `flexbox` para alinhar os elementos centralmente.
  - Define espaçamento entre os elementos.
  - Aplica `cursor: pointer` para indicar interação.
  - Aplica `position: relative` para manipular a posição do input oculto.
  - Transição suave para mudança de cor ao interagir.
- `.radio-content input`:
  - Esconde o `input` padrão e expande sua área para permitir clique em toda a opção.
- `.radio-content:hover`, `.radio-content:focus`, `.radio-content:has(:checked)`:
  - Muda a cor do fundo ao passar o mouse, focar ou quando estiver selecionado.

---

## Comportamento
- O `.radio-wrapper` distribui os botões igualmente no espaço disponível.
- O `.radio-content` organiza os elementos internos horizontalmente.
- O `input[type="radio"]` fica invisível, mas é clicável em toda a área do `.radio-content`.
- A cor do fundo muda ao passar o mouse, focar ou selecionar a opção.


