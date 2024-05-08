# File Mime Type Setter Utility

This utility function sets the mimeType of a file if it is not provided or empty. It ensures that the file object has the correct mimeType assigned for proper handling in applications.

## Functionality

The `fileMimeTypeSetter` function takes a file object as input and checks if its mimeType is empty. If the mimeType is empty, it determines the appropriate mimeType based on the file extension and assigns it to the file object. If the mimeType is already provided or if it doesn't match the allowed mimeTypes, the function returns the file object as-is.

## Code

```typescript
/**
 * Sets the mimeType of a file if it is not provided or empty.
 * @param file - The file object.
 * @returns The updated file object with the mimeType set.
 */
export const fileMimeTypeSetter = (file: File): File => {
  // Check if the file object exists and if its mimeType is empty
  if (file && file.type === '') {
    const extension = file.name.toLowerCase().split('.').pop(); // Get the file extension
    const isMimeTypePresentInArr = mimeTypes?.includes(`${extension}`); // Check if the mimeType is present in the allowed mimeTypes array

    if (isMimeTypePresentInArr) {
      // If the mimeType is present in the allowed mimeTypes array, create a new File object with the updated mimeType
      const updatedFile = new File([file], file.name, {
        type: assignedMimeTypes[`${extension}`], // Assign the appropriate mimeType based on the extension
      });

      return updatedFile;
    }
  }

  return file; // Return the file object as-is if the mimeType is already provided or if it doesn't match the allowed mimeTypes
};
```

The `mimeTypes` and `assignedMimeTypes` are below.

## Usage

```typescript
import { fileMimeTypeSetter } from './fileMimeTypeSetter';

const file = new File(/* file details */);
const updatedFile = fileMimeTypeSetter(file);
console.log(updatedFile);
```

## Parameters

- `file`: The file object to update.

## Returns

The updated file object with the mimeType set.

## Example

```typescript
const file = new File(
  [
    /* file content */
  ],
  'example.txt',
  { type: '' }
);
const updatedFile = fileMimeTypeSetter(file);
console.log(updatedFile); // Output: File { /* updated file details */ }
```

## Requirements

- JavaScript or TypeScript environment.
- Proper handling of the file object.

## License

This utility function is provided under the MIT License. See the [LICENSE](LICENSE) file for details.

## Constant

### `mimeTypes`

```typescript
export const mimeTypes = [
  'deb',
  'rpm',
  'app',
  'ipa',
  'dmg',
  'msi',
  'rs',
  'c',
  'cpp',
  'cs',
  'java',
  'py',
  'js',
  'rb',
  'php',
  'swift',
  'go',
  'rust',
  'ts',
  'html',
  'css',
  'json',
  'xml',
  'sh',
  'pl',
  'kt',
  'lua',
  'objc',
  'ps1',
  'sql',
  'vb',
  'cr',
  'ex',
  'f90',
  'ml',
  'groovy',
  'puppet',
  'matlab',
  'r',
  'scala',
  'haskell',
  'dart',
  'erlang',
  'julia',
  'perl',
  'kotlin',
  'lisp',
  'ada',
  'pro',
  'cob',
  'scm',
  'e',
  'awk',
  'ahk',
  'purs',
  'elm',
  're',
  'crystal',
  'groovy',
  'julia',
  'mips',
  'ps',
  'rkt',
  'lua',
  'vb',
  'rexx',
  'hack',
  'abap',
  'elixir',
  'dylan',
  'factor',
  'forth',
  'io',
  'j',
  'nim',
  'oz',
  'pli',
  'sather',
  'vhdl',
  'x10',
  'bal',
  'bef',
  'chpl',
  'd',
  'hx',
  'ttf',
  'otf',
  'woff',
  'woff2',
  'eot',
  'svg',
  'pfa',
  'pfb',
  'ps',
  'zip',
  'rar',
  '7z',
  'tar',
  'gz',
  'bz2',
  'xz',
  'lz',
  'Z',
  'lha',
  'lzh',
  'cab',
  'iso',
  'gltf',
  'glb',
];
```

### `assignedMimeTypes`

```typescript
export const assignedMimeTypes: { [key: string]: string } = {
  zip: 'application/zip',
  rar: 'application/x-rar-compressed',
  '7z': 'application/x-7z-compressed',
  tar: 'application/x-tar',
  gz: 'application/gzip',
  gltf: 'model/gltf+json',
  glb: 'model/gltf-binary',
  bz2: 'application/x-bzip2',
  xz: 'application/x-xz',
  lz: 'application/x-lzip',
  Z: 'application/x-compress',
  lha: 'application/x-lha',
  lzh: 'application/x-lha',
  cab: 'application/vnd.ms-cab-compressed',
  iso: 'application/x-iso9660-image',
  ttf: 'application/font-sfnt',
  otf: 'application/font-sfnt',
  woff: 'font/woff',
  woff2: 'font/woff2',
  eot: 'application/vnd.ms-fontobject',
  svg: 'font/svg',
  pfa: 'application/x-font-type1',
  pfb: 'application/x-font-type1',
  ps: 'application/postscript',
  deb: 'application/vnd.debian.binary-package',
  rpm: 'application/x-rpm',
  app: 'application/octet-stream',
  ipa: 'application/octet-stream',
  dmg: 'application/x-apple-diskimage',
  msi: 'application/x-msdownload',
  xls: 'application/vnd.ms-excel',
  xlsx: 'application/vnd.openxmlformats-officedocument.spreadsheetml.sheet',
  doc: 'application/msword',
  docx: 'application/vnd.openxmlformats-officedocument.wordprocessingml.document ',
  ppt: 'application/vnd.ms-powerpoint',
  pptx: 'application/vnd.openxmlformats-officedocument.presentationml.presentation',
  pdf: 'application/pdf',
  rs: 'text/x-rustsrc',
  c: 'text/x-csrc',
  cpp: 'text/x-c++src',
  cs: 'text/x-csharp',
  java: 'text/x-java-source',
  py: 'text/x-python',
  js: 'text/javascript',
  rb: 'text/x-ruby',
  php: 'text/x-php',
  swift: 'text/x-swift',
  go: 'text/x-go',
  rust: 'text/x-rustsrc',
  ts: 'text/typescript',
  html: 'text/html',
  css: 'text/css',
  json: 'text/json',
  xml: 'text/xml',
  sh: 'text/x-sh',
  pl: 'text/x-perl',
  kt: 'text/x-kotlin',
  lua: 'text/x-lua',
  objc: 'text/x-objectivec',
  ps1: 'text/x-powershell',
  sql: 'text/sql',
  cr: 'text/x-crystal',
  ex: 'text/x-elixir',
  f90: 'text/x-fortran',
  ml: 'text/x-ocaml',
  groovy: 'text/x-groovy',
  puppet: 'text/x-puppet',
  matlab: 'text/matlab',
  r: 'text/x-rsrc',
  scala: 'text/x-scala',
  haskell: 'text/x-haskell',
  dart: 'text/dart',
  erlang: 'text/x-erlang',
  julia: 'text/julia',
  perl: 'text/perl',
  kotlin: 'text/x-kotlin',
  lisp: 'text/x-lisp',
  ada: 'text/x-ada',
  pro: 'text/x-prolog',
  cob: 'text/x-cobol',
  scm: 'text/x-scheme',
  e: 'text/x-eiffel',
  awk: 'text/x-awk',
  ahk: 'text/x-autohotkey',
  purs: 'text/x-purescript',
  elm: 'text/x-elm',
  re: 'text/x-reasonml',
  crystal: 'text/x-crystal',
  mips: 'text/x-mips',
  rkt: 'text/x-racket',
  vb: 'text/x-vb',
  rexx: 'text/rexx',
  hack: 'text/x-hack',
  abap: 'text/plain',
  elixir: 'text/x-elixir',
  dylan: 'text/x-dylan',
  factor: 'text/x-factor',
  forth: 'text/x-forth',
  io: 'text/x-io',
  j: 'text/plain',
  nim: 'text/x-nim',
  oz: 'text/x-oz',
  pli: 'text/x-pli',
  sather: 'text/plain',
  vhdl: 'text/x-vhdl',
  x10: 'text/x-x10',
  bal: 'text/plain',
  bef: 'text/plain',
  chpl: 'text/x-chapel',
  d: 'text/x-d',
  hx: 'text/plain',
};
```
