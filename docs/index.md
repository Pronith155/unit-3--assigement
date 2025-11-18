/**
 * Calculates the final price of an item after applying a single discount percentage.
 * * @param {number} originalPrice - The initial price of the item. Must be a positive number.
 * @param {number} discountPercent - The discount rate to apply (e.g., 15 for 15%). Must be between 0 and 100.
 * @returns {number} The final price of the item after the discount is applied.
 */
function calculateDiscountedPrice(originalPrice, discountPercent) {
    if (originalPrice <= 0 || discountPercent < 0 || discountPercent > 100) {
        console.error("Invalid price or discount percentage provided.");
        return originalPrice; 
    }
    const discountAmount = originalPrice * (discountPercent / 100);
    return parseFloat((originalPrice - discountAmount).toFixed(2));
}

/**
 * Formats a raw number of cents into a localized currency string.
 * Assumes USD for simplicity in this utility.
 * * @param {number} amountInCents - The monetary amount represented in cents (e.g., 1999 for $19.99).
 * @returns {string} The formatted currency string (e.g., "$19.99").
 */
function formatCurrency(amountInCents) {
    if (typeof amountInCents !== 'number' || amountInCents < 0) {
        return "$0.00";
    }
    const dollars = amountInCents / 100;
    return new Intl.NumberFormat('en-US', {
        style: 'currency',
        currency: 'USD'
    }).format(dollars);
}

// Export functions for use in other modules
export { calculateDiscountedPrice, formatCurrency };
