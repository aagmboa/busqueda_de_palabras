# Word Search Game - specification

## Project Overview
- **Type**: Browser-based word search game (single HTML file)
- **Core functionality**: 15x15 letter grid where players find hidden words in all directions
- **Target users**: Casual gamers looking for word puzzles
- **Languages**: Spanish and English with language selector

## UI/UX Specification

### Layout Structure
1. **Language Selector Screen** (initial)
   - Title: "Word Search / Búsqueda de Palabras"
   - Two buttons: "Español" / "English"
   
2. **Game Screen**
   - Header with title, language toggle, word counter, and "New Game" button
   - 15x15 grid centered
   - Word list below grid (shows all words, marks found ones)
   - Footer: "Play Again" button when game complete

### Visual Design
- **Background**: Dark charcoal (#1a1a2e) with subtle grid pattern
- **Primary color**: Electric cyan (#00fff5)
- **Secondary color**: Soft magenta (#ff006e)
- **Accent**: Warm amber (#ffbe0b)
- **Grid background**: Dark navy (#16213e)
- **Letter cells**: Semi-transparent dark (#0f0f23) with cyan border
- **Selected cells**: Magenta highlight (#ff006e)
- **Found word highlight**: Amber (#ffbe0b) with glow
- **Typography**:
  - Title: "Orbitron", 2.5rem
  - Letters: "JetBrains Mono", 1.1rem, bold
  - UI text: "Outfit", 1rem
- **Cell size**: 40px x 40px
- **Spacing**: 2px gap between cells
- **Effects**: 
  - Glow on found words
  - Scale animation on selection
  - Pulse animation when word found

### Responsive
- Desktop: Full 40px cells
- Tablet (< 768px): 32px cells
- Mobile (< 480px): 24px cells

## Functionality Specification

### Word Database
- 200 words in Spanish + 200 English translations
- Mixed topics: animals, food, colors, countries, sports, objects, actions, nature, body, feelings
- Stored as array of objects: { es: "perro", en: "dog" }

### Game Initialization
1. Select 10 random words from database (avoiding last 5 games)
2. Place words in 15x15 grid (all 8 directions)
3. Fill remaining cells with random letters
4. Display all 10 words in the word list (unmarked)

### History System (localStorage)
- Store: { games: [{ words: [...], found: [...], date: timestamp }], last5Words: [...] }
- On new game: check last 5 games' words, exclude them from selection
- Maximum 50 games stored (FIFO)

### Interactions
1. Click first letter to start selection
2. Drag to show selection path
3. Release to check if valid word
4. Valid: highlight in amber, mark in list, decrement counter
5. Invalid: shake animation
6. Game complete: show congratulations, "Play Again" button
7. Language toggle: switch between ES/EN (restart not required)

### Translations (UI)
| Key | Spanish | English |
|-----|---------|---------|
| title | Búsqueda de Palabras | Word Search |
| remaining | Palabras restantes | Words remaining |
| found | Palabras encontradas | Words found |
| newGame | Nuevo Juego | New Game |
| selectLang | Selecciona idioma | Select language |
| congratulations | ¡Felicitaciones! | Congratulations! |
| playAgain | Jugar de nuevo | Play again |

## Acceptance Criteria
- [ ] Language selector appears on load
- [ ] 10 random words selected (no repeat in last 5 games)
- [ ] All 10 words placed in grid and findable
- [ ] Selection works in all 8 directions
- [ ] Found words highlight, mark in list, counter decreases
- [ ] Invalid selection shows shake
- [ ] Game complete shows victory message
- [ ] Language can be switched mid-game
- [ ] History persists across browser sessions
- [ ] Responsive on mobile/tablet/desktop
