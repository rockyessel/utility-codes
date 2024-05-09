# Slug Creation Utility

This utility function creates a slug from the input string for generating SEO-friendly URLs. It replaces non-alphanumeric characters with hyphens, converts the string to lowercase, and trims any leading or trailing spaces.

## Functionality

The `createSlug` function takes an input string as parameter and performs the following operations:

1. Replaces non-alphanumeric characters with hyphens.
2. Replaces consecutive hyphens with a single hyphen.
3. Converts the string to lowercase.
4. Trims leading and trailing spaces.

## Code

```typescript
/**
 * Creates a slug from the input string for SEO-friendly URLs.
 * @param input - The input string to create a slug from.
 * @returns The generated slug.
 */
export const createSlug = (input: string): string => {
  const slug = input
    ?.replaceAll(/[^a-zA-Z0-9-]/g, '-') // Replace non-alphanumeric characters with hyphens
    ?.replaceAll(/-+/g, '-') // Replace consecutive hyphens with a single hyphen
    .toLowerCase() // Convert to lowercase
    .trim(); // Remove leading and trailing spaces
  // console.log(slug);

  return slug;
};
```

## Usage

```typescript
import { createSlug } from './your-utility-file';

const inputString = 'This is a Sample Input String!';
const slug = createSlug(inputString);
console.log(slug); // Output: 'this-is-a-sample-input-string'
```

## Parameters

- `input`: The input string to create a slug from.

## Returns

The generated slug as a string.

## Example

```typescript
const inputString = 'This is a Sample Input String!';
const slug = createSlug(inputString);
console.log(slug); // Output: 'this-is-a-sample-input-string'
```

## Requirements

- JavaScript or TypeScript environment.

## License

This utility function is provided under the MIT License. See the [LICENSE](LICENSE) file for details.
