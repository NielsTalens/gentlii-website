# Gentlii Header Navigation Design

## Goal

Add a compact sticky header to the single-page marketing site so visitors can always see the Gentlii brand and jump directly to each suite module.

## Chosen Approach

Use a sticky top header with the existing `logo.png`, the wordmark `Gentlii`, and three in-page links:

- `Foundations`
- `Product Guard`
- `Feature Validator`

This keeps the site as a single document, avoids unnecessary page splitting, and improves navigation on long-scroll sections.

## Layout

- Brand block on the left with logo and name
- Module navigation on the right on larger screens
- Wrapped navigation below the brand on smaller screens

## Behavior

- Header remains visible while scrolling
- Links scroll to the corresponding section anchors
- Visual styling follows the existing dark background and blue accent language

## Files

- Modify `index.html`
- No new runtime dependencies
