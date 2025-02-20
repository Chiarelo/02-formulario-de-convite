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


# Documentação do Checkbox Toggle Button

Este documento explica a estrutura e os estilos utilizados para criar um botão de alternância (toggle button) estilizado. O objetivo é fornecer uma visão geral de como os elementos estão organizados e quais técnicas foram usadas para obter o efeito visual desejado.

## Estrutura do HTML

O HTML do componente é estruturado da seguinte forma:

```html
<div class="checkbox-wrapper flex-1">
  <label for="toggle">Estilo</label>
  <div class="checkbox-inner">
    <div class="toggle-button">
      <input type="checkbox" id="toggle" />
      <div class="ellipse">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
          <circle cx="12" cy="12" r="12" fill="#363B40" />
        </svg>
      </div>
    </div>
    <label for="toggle" class="toggle-label"></label>
  </div>
</div>
```

### Explicação da Estrutura

1. **`checkbox-wrapper`**: Wrapper principal que engloba o componente.
2. **`checkbox-inner`**: Agrupa os elementos internos do checkbox, garantindo alinhamento.
3. **`toggle-button`**: Contém o input e o elemento visual do botão.
4. **`input[type=checkbox]`**: O próprio controle de checkbox (invisível).
5. **`ellipse`**: O elemento responsável pelo indicador do estado do toggle.
6. **`toggle-label`**: Responsável por exibir dinamicamente os textos "Escuro" e "Claro".

## Estilização no CSS

Abaixo estão os principais estilos usados para o botão:

### 1. Posicionamento e Layout

- O `checkbox-inner` utiliza `display: flex; align-items: center;` para alinhar os elementos lado a lado.
- O `toggle-button` é `position: relative;`, permitindo que o `input` e o `ellipse` sejam posicionados corretamente dentro dele.

### 2. Estilização do Toggle

- O `toggle-button` tem um `background-color` padrão e muda de cor quando ativado.
- O `input` está escondido (`all: unset; opacity: 0;`) e cobre toda a área clicável.
- A `ellipse` usa `transform` para se mover suavemente ao ser ativada.

```css
.toggle-button {
  position: relative;
  width: 4rem;
  height: 2rem;
  background-color: var(--input-base);
  border-radius: 999px;
  outline: 1px solid var(--input-stroke);
  transition: background-color 0.3s ease-in-out;
}
```

### 3. Animações e Mudanças Dinâmicas

- A `ellipse` desliza de um lado para o outro ao marcar o `checkbox`.
- O `toggle-label` muda o texto automaticamente utilizando `::after`.

```css
input:checked + .ellipse {
  transform: translate(2rem, -50%);
}

.toggle-button:has(input:checked) {
  background-color: var(--brand-light);
}

.toggle-label::after {
  content: "Escuro";
}

.checkbox-inner:has(input:checked) .toggle-label::after {
  content: "Claro";
}
```

## Conclusão

Este toggle button utiliza conceitos modernos de CSS, como `::after`, `:has()`, `transform` e `transition`, para criar uma experiência interativa suave. O `input` é mantido funcional enquanto os elementos visuais fornecem um design intuitivo para o usuário.

