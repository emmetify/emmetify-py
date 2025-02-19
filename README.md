# Emmetify 🚀

[![pypi](https://img.shields.io/pypi/v/emmetify.svg)](https://pypi.python.org/pypi/emmetify)
[![versions](https://img.shields.io/pypi/pyversions/emmetify.svg)](https://github.com/emmetify/emmetify-py)
[![PyPI Downloads](https://static.pepy.tech/badge/emmetify)](https://pepy.tech/projects/emmetify)
[![codecov](https://codecov.io/gh/emmetify/emmetify-py/graph/badge.svg?token=GY70C7TMD8)](https://codecov.io/gh/emmetify/emmetify-py)
[![license](https://img.shields.io/github/license/emmetify/emmetify-py.svg)](https://github.com/emmetify/emmetify-py/blob/main/LICENSE)
[![Twitter Follow](https://img.shields.io/twitter/follow/maledorak?style=social)](https://x.com/maledorak)


Cut your LLM processing costs by up to 90% by transforming verbose HTML into efficient Emmet notation, without losing structural integrity.

## Why Emmetify? 🤔

- 💰 **Drastically Reduce Costs** - Process HTML with your LLM agents at a fraction of the cost by using our efficient Emmet-based compression
- 🎯 **Maintain Performance** - Your LLM agents can still generate XPath and CSS selectors with the same accuracy using the compressed format
- 🔌 **Seamless Integration** - Emmet syntax is well-understood by all major LLMs thanks to its 10+ years of widespread use in frontend development
- ⚡ **Fast Processing** - Less tokens means faster processing times for your HTML analysis tasks

## How It Works 🛠️

Emmetify converts complex HTML structures into concise Emmet notation. For example:

```html
<div class="container">
    <header class="header">
        <nav class="nav">
            <ul class="nav-list">
                <li class="nav-item"><a href="#">Link</a></li>
            </ul>
        </nav>
    </header>
</div>
```
Becomes:
```
div.container>header.header>nav.nav>ul.nav-list>li.nav-item>a[href=#]{Link}
```

Using the [OpenAI Tokenizer](https://platform.openai.com/tokenizer), we can see this simple transformation reduces token count from:
- HTML: 59 tokens
- Emmet: 22 tokens

That's 63% fewer tokens while preserving all structural information! And this is just with default settings.

You can achieve even higher compression rates (up to 90%, or even more depending on the HTML structure) by using advanced configuration options:
- Removing unnecessary tags
- Simplifying attributes
- Optimizing class names
- Shortening URLs

Check our documentation for detailed optimization strategies and their impact on token reduction.

## Why Not Just Use Markdown? 🤔

While Markdown is great for content representation, it removes HTML structure that's crucial for web automation. When working with tools like Selenium or Playwright, you need the actual DOM structure to click buttons, fill forms, and follow links. Emmetify gives you the best of both worlds:

- Preserves complete HTML structure for accurate element targeting
- Uses fewer tokens than raw HTML (up to 90% reduction)
- Allows LLMs to make informed decisions about page navigation and interaction

Perfect for scenarios where you need both efficiency and structural fidelity!

## The Technology Behind It 🔍

Emmetify leverages [Emmet](https://emmet.io) notation - a powerful and mature syntax that's been a standard in web development for over a decade. While developers typically use Emmet to expand short abbreviations into HTML:

```
div.container>h1{Title}+p{Content}
```
↓ Expands to ↓
```html
<div class="container">
    <h1>Title</h1>
    <p>Content</p>
</div>
```

Emmetify uses this well-established syntax in reverse, converting verbose HTML back into this concise format that LLMs can understand just as well as raw HTML.

## Installation 🔧

```bash
pip install emmetify
```

## Usage 💻

### Basic Usage

```python
from emmetify import Emmetifier
import requests

emmetifier = Emmetifier()
html = requests.get("https://example.com").text
emmet = emmetifier.emmetify(html)
print(emmet)
```

### Advanced HTML Simplification ⚡

Transform verbose HTML into its most essential form while preserving navigational structure. This mode intelligently:
- Skips non-essential HTML tags
- Prioritizes important attributes
- Removes redundant information

For example, this verbose HTML:

```html
<link rel="stylesheet" href="style.css">
<div id="main" class="container" style="color: red;" data-test="ignore">Example</div>
```

Becomes this concise Emmet notation:

```
div#main.container{Example}
```

Much shorter, yet retains all necessary information for LLM navigation and processing!

#### Advanced Usage:

```python
from emmetify import Emmetifier, emmetify_compact_html
import requests


# Fetch and process HTML
html = requests.get("https://example.com").text

# Configure Emmetifier class
emmetifier = Emmetifier(config={
    "html": {
        "skip_tags": True,
        "prioritize_attributes": True
    }
})
emmetified = emmetifier.emmetify(html)
print(emmetified)

# or use the shorthand function, which is a shortcut for emmetifier.emmetify(html)
# with the default configuration for compact HTML
emmetified = emmetify_compact_html(html)
print(emmetified)
```

## Examples

See the [examples](./examples/README.md) directory for more examples of how to use Emmetify.

## Sponsors

<table>
  <tr>
    <td align="center" vertical-align="center">
      <a href="https://www.rumblefish.dev/?utm_source=github_Emmetify&utm_medium=link&utm_campaign=sponsorship" >
        <img src="https://strapi-uploads.rumblefish.dev/rf_circle_colour.png" width="120px;" alt="Rumble Fish Logo" />
      </a>
    </td>
    <td align="center" vertical-align="center">
      <b>Rumble Fish</b>
      <br />
      <a href="https://www.rumblefish.dev/?utm_source=github_Emmetify&utm_medium=link&utm_campaign=sponsorship">https://rumblefish.dev</a>
      <br />
      <p width="100px">
        Rumble Fish a software development house crafting bespoke Web3 and AI-powered solutions
        <br/>
      </p>
    </td>
  </tr>
</table>

## Backlog 📝

- [x] Add support for HTML
- [ ] Add examples

## Supported Formats 📊

- ✅ HTML
- 🚧 XML (Coming Soon)
- 🚧 JSON (Coming Soon)
