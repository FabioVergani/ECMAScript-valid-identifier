# ECMAScript-valid-identifier

Characters outside the BMP (Unicode Basic Multilingual Plane),
e.g. U+1D306 (0x1D306) as tetragram for centre (𝌆),
can only be encoded in UTF-16 using two 16-bit code units: 0xD834 & 0xDF06. (� & �)
This is called a surrogate pair.

The first code unit of a surrogate pair is always in the range from 0xD800 to 0xDBFF,
and is called a high surrogate or a lead surrogate.

(n >=0xD800 && n <=0xDFFF)
(n >= 55296 && n <=56319 )
(n > 55295 && n < 56320 )

The second code unit of a surrogate pair is always in the range from 0xDC00 to 0xDFFF,
and is called a low surrogate or a trail surrogate.

(n >=0xDC00 && n <=0xDFFF)
(n >=56320 && n <=57343)
(n >56319 && n <57344)




Note that a surrogate pair only represents a single character.

	'𝌆' === '\uD834\uDF06'
	'𝌆' === 0x1D306);//119558
	'𝌆'==='\u{1D306}'//CodePoint:119558

Note that a call like:

	document.write('\uD834');
	document.write('\uDF06');

ends up getting rendered as 𝌆 — one glyph.
but '𝌆'.length === 2//true

The hexadecimal part of this kind of character escape is case-insensitive;
in other words, '\u{1d306}' and '\u{1D306}' are equivalent.
