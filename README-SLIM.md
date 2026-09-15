# lingua-go (slim: English + Swahili)

A data-trimmed fork of [pemistahl/lingua-go](https://github.com/pemistahl/lingua-go)
v1.4.0 (Apache-2.0, LICENSE retained). The code is byte-identical to upstream (module path included); the `language-models/` directory keeps only `en` and `sw`,
dropping ~120MB the upstream `//go:embed language-models` compiles into
every consuming binary.

Behavior is identical for a detector built with
`FromLanguages(lingua.English, lingua.Swahili)` — models load lazily per
requested language, so the removed directories were never read by such a
detector. Building a detector that requests any OTHER language will fail
to find its model.

Upstream test files are removed (they exercise the full language set).
Consume via a `replace` directive:

    replace github.com/pemistahl/lingua-go => github.com/paulmanoni/lingua-go v1.4.2
