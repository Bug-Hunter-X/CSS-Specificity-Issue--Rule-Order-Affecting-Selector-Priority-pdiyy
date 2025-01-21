# CSS Specificity Issue: Rule Order Affecting Selector Priority

This repository demonstrates a subtle CSS bug related to the interaction of selector specificity and the order of rules in a stylesheet.  Under certain conditions, a less-specific selector can override a more-specific selector due to the order they're declared in the CSS.

## Bug Description

The unexpected behavior stems from how some browsers handle CSS parsing and cascading. While typically a more specific selector (`div p`) should override a less specific one (`p`), this might not always hold true if the less specific rule is placed after the more specific rule in the CSS file.  This is not standard CSS behavior but can surface as a rendering issue in some environments.

## Reproduction

1.  Examine the `bug.css` file. Note the order of the `div p` and `p` rules.  The `p` selector is intentionally placed after `div p`. 
2.  Open `index.html` (You may need to create an HTML file to test this). This HTML file will include a `<div>` containing a `<p>` tag.
3.  Observe the text color of the paragraph. In most scenarios, it would be blue (because of the `div p` selector). However, due to the bug, it may be red, demonstrating the unexpected override.

## Solution

The solution (`bugSolution.css`) focuses on ensuring consistent specificity resolution by maintaining the order of selectors. Here we moved the more specific selector to the last one to ensure the precedence.  This addresses the potential inconsistency caused by rule order.

## Note

This is a non-standard behavior and likely related to browser-specific nuances in CSS processing.  This bug highlights the importance of carefully considering selector specificity and consistently managing CSS rule order, particularly in complex stylesheets and situations involving dynamically generated content.