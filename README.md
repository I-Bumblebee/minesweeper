# Minesweeper AI

This project implements an AI that can play Minesweeper using knowledge-based logical reasoning.

## Solution Approach

The AI employs a propositional logic approach to make deductions about the Minesweeper board:

1. **Knowledge Representation**: 
   - Each piece of knowledge is represented as a sentence in the form `{cells} = count`
   - This means that out of the cells in the set, exactly `count` of them contain mines

2. **Inference Methods**:
   - **Direct Inference**: If count = 0, all cells are safe; if count = number of cells, all cells are mines
   - **Subset-based Inference**: If one sentence is a subset of another, we can deduce new information
     - For sentences S1 = {A,B,C} = 1 and S2 = {A,B,C,D,E} = 2, we can infer {D,E} = 1

3. **Move Selection Strategy**:
   - The AI always chooses a known safe move when available
   - If no safe move is available, it makes a random move among cells not known to be mines

The implementation carefully tracks known mines, known safe cells, and all logical sentences, constantly updating and refining its knowledge base with each move.

## Implementation Notes

- The recursive inference system continues making deductions until no new information can be derived
- Special care is taken to handle edge cases and maintain logical consistency
- The AI effectively emulates how a logical human player would approach the game
