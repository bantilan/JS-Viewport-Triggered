# Viewport Triggered Class Change

A JavaScript function that adds or removes a CSS class from an HTML element based on its visibility within the viewport while scrolling. This utility allows you to easily create scroll-triggered animations, effects, or any other dynamic behavior for your web page elements.

## Function Usage

```javascript
/**
 * Checks if an element is within the viewport and adds/removes a CSS class accordingly.
 * @param {HTMLElement} element - The HTML element to observe.
 * @param {number} percentage - The percentage of the element's height that needs to be visible in the viewport.
 * @param {string} activeClass - The CSS class to add when the element is in the viewport.
 */
function toggleClassOnViewport(element, percentage, activeClass) {
    if (percentage < 0 || percentage > 100) {
        throw new Error("Percentage should be between 0 and 100");
    }

    const rect = element.getBoundingClientRect();
    const panelHeight = rect.height;
    const threshold = (percentage / 100) * panelHeight;

    if (rect.top >= -threshold && rect.top <= window.innerHeight - threshold) {
        element.classList.add(activeClass);
    } else {
        element.classList.remove(activeClass);
    }
}

// Example usage:
const panel = document.querySelector(".your-element");
const percentage = 50; // Adjust this value as needed
const activeClass = "your-active-class";

window.addEventListener("scroll", function () {
    toggleClassOnViewport(panel, percentage, activeClass);
});
