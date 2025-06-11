# My Hugo Site

This README provides a quick guide to managing content and running your Hugo site locally.

## Getting Started with Hugo

This site is built using Hugo, a fast and flexible static site generator.

### Prerequisites

Before you begin, ensure you have Hugo installed. You can find installation instructions on the [official Hugo website](https://gohugo.io/getting-started/installing/).

### Running the Site Locally

To see your changes in real-time or to preview your site before deployment:

1.  Open your terminal or command prompt.
2.  Navigate to the root directory of your Hugo site (where `config.toml` is located).
3.  Run the following command:

    ```bash
    hugo server
    ```

    This will start a local server, usually accessible at `http://localhost:1313`. Hugo will automatically rebuild the site whenever you make changes to your content or templates.

## Creating Content

Hugo uses a content management system that relies on Markdown files.

### Creating a New Post

Posts are typically stored in the `content/posts/` directory.

1.  To create a new post, use the Hugo command:

    ```bash
    hugo new posts/my-new-post.md
    ```

    This will create a new Markdown file (`my-new-post.md`) in the `content/posts/` directory with some pre-filled front matter.

2.  Open the newly created file in your text editor.
3.  Edit the front matter (the section enclosed by `---` at the top of the file) to set the title, date, draft status, and any other relevant metadata.
4.  Write your post content below the front matter using Markdown syntax.
5.  If the `draft` status is set to `true`, the post will not be published when you build the site for production. Change it to `false` when you're ready to publish.

### Creating a New Page

Pages are typically stored in the `content/` directory directly or in their own subdirectories (e.g., `content/about/index.md`).

1.  To create a new page, for example, an "About" page:

    ```bash
    hugo new about.md
    ```

    Or, for a more structured page:

    ```bash
    hugo new about/_index.md
    ```

    The `_index.md` file is used for section pages or single pages that serve as the root of a section.

2.  Similar to posts, open the generated Markdown file, edit the front matter, and add your content.

### Other Important Considerations

- **Front Matter:** The YAML (or TOML/JSON) block at the beginning of your content files. This is where you define metadata like `title`, `date`, `tags`, `categories`, `draft`, etc. The theme you are using, PaperMod, often has specific front matter options for customizing the appearance and behavior of your content. Refer to the [PaperMod documentation](https://adityatelange.github.io/hugo-PaperMod/posts/papermod-features/#frontmatter-params) for details.
- **Static Files:** For images, CSS, JavaScript, or other static assets, place them in the `static/` directory. These files will be copied directly to the root of your public site. For example, `static/images/my-image.png` would be accessible at `/images/my-image.png` on your site.
- **Configuration (`config.toml` or `hugo.toml`):** This is the main configuration file for your Hugo site. Here you can set global site parameters, menu items, enable/disable features, and configure your theme. Review this file to customize your site's behavior.

## Credits

This site is powered by [Hugo](https://gohugo.io/).

The theme used is [PaperMod](https://github.com/adityatelange/hugo-PaperMod) by [adityatelange](https://github.com/adityatelange).
