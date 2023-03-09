## Adding your own themes
If you're asking if GitHub Readme Stats supports custom theming, the short answer is YES! There are two ways you can do this:
1. Using the URL parameters (Highly recommended if you're just using it personally)
2. Adding the theme to the [themes/index.js](./index.js) file

We will breakdown both ways here and, after explaining the URL parameters, adding your theme to the file will be a breeze. So without any further ado, let's get started!

### Guidelines & Licensing
We ask that if you are planning to contribute a theme just because you are using it personally, don't. Please use the URL parameters instead. This documentation will help you do that. When you do contribute, you understand that your submissions will be governed under the same [MIT License](http://choosealicense.com/licenses/mit/) that covers the project. If this is a concern, please contact the maintainers. For any other guidelines, please be sure to review the [Contribution Guidelines](./CONTRIBUTING.md).

### Using the URL parameters
You're going to need the following in your profile's readme:
```
![<yourName>'s GitHub stats](https://github-readme-stats.vercel.app/api?username=<yourName>)
```
This is the root of the stats card. Make sure you replace both `<yourName>` placeholders with your username. 

#### Introduction to custom parameters
The most common parameters you're going to see are `&hide=`, `&count_private=`, `&showicons=`, and `&theme=`. Notice the ampersand `&` at the start of each item? This is required otherwise the link will break. This seperates each parameter and selector. There are over 20 parameters that can added.
```
![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra&theme=dark&border_radius=10&text_bold=false&custom_title=My%20stats)
```
| Default | Customized |
| :--: | :--: |
| ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra) | ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra&theme=dark&border_radius=10&text_bold=false&custom_title=My%20stats) |

In this above example, we are using 4:
- `&theme=dark` selects the dark theme
- `&border_raius=10` changes the rounding of the card's corners (default is `4.5`)
- `&text_bold=false` ensures the text isn't bold as it normally is.
- `&custom_title=My%20stats` changes the title from `Anurag Hazra's GitHub Stats` to `My Stats`. Notice the `%20` in there? Read this warning in footnote [^1]

#### Colorizing your card
Now let's remove the theme and change only the colors on a per-item basis. Colors are in HEX color format. These are the parameters you can choose from and an example:
| Parameter | Default | New | Explanation |
| --- | :--: | :--: | --- |
| `title_color` | `2f80ed` | `de08f2` | Changes the color of `My Stats` |
| `text_color` | `434d58` | `85d434` | Changes the color of other text in the list (e.g.: `Total PRs:`, `Total Issues:`, numbers, etc.) and the grade color |
| `icon_color` | `4c71f2` | `2f17c4` | Changes the color of the icons |
| `border_color` | `e4e2e2` | `2e2e4e` | Changes border color and does not apply if `hide_border` is `true` as there wouldn't be a border to colorize |
| `bg_color` | `fffefe` | `000909` | Changes the card's background color. This supports the alpha (transparency) channel and gradient coloring (by seperating each HEX color value by a comma `,` |
| `ring_color` | `title_color` | `aabbcc` | Changes the color of the ring that surrounds the grade.
<details>
  <summary>Show/hide markdown examples</summary>
  
  ```
      Default: ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra)
          New: ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra&title_color=de08f2&text_color=85d434&icon_color=2f17c4&border_color=2e2e4e&bg_color=00090900)
  Transparent: ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra&title_color=de08f2&text_color=85d434&icon_color=2f17c4&border_color=2e2e4e&ring_color=aabbcc&bg_color=00090900)
     Gradient: ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra&title_color=de08f2&text_color=85d434&icon_color=2f17c4&border_color=2e2e4e&ring_color=aabbcc&bg_color=fffefe,aaabab,444545,000909)
  ```
  
</details>

| Default | New |
| :--: | :--:|
| ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra) | ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra&title_color=de08f2&text_color=85d434&icon_color=2f17c4&border_color=2e2e4e&ring_color=aabbcc&bg_color=000909) |
| **Transparent** | **Gradient** |
|![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra&title_color=de08f2&text_color=85d434&icon_color=2f17c4&border_color=2e2e4e&bg_color=00090900) | ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra&title_color=de08f2&text_color=85d434&icon_color=2f17c4&border_color=2e2e4e&ring_color=aabbcc&bg_color=fffefe,aaabab,444545,000909) |

Notice the transparent example ring color? Because it wasn't specified, it was automatically set to match the `title_color`. Also, you can see the gradient's text is partially readable. This is an example of what **not** to do if you're submitting a theme for the community. Text **must** be readable and will be checked when a pull request is created.

#### Additional universal card options
Got your color scheme figured out? Awesome! Let's move on. You can customize both Stats and Language cards with the following options:
| Parameter | Default | Description |
| --- | :--: | --- |
| `hide` | `[]` | Allows you to hide [specific items](./readme.md#hiding-individual-stats) (stats card) or languages (language card)[^1] from the card. These are comman-seperated values with a default array of `[]` (blank array). |
| `hide_title` | `false` | Hides the card's title. Reminder: If the title is hidden, you cannot color it. |
| `hide_border` | `false` | Hides the card's border. Reminder: If the border is hidden, you cannot color it. |
| `border_radius` | `4.5` | Sets the corner rounding on the card.
| `theme` | `default` | Selects a defined theme from [all available themes](readme.md).
| `cache_seconds` | `14400` | Sets the cache header manually.[^2]<br> Minimum: `14400` seconds (4 hours)<br> Maximum: `86400` seconds (24 hours) |
| `locale` | `en` | Specifies the language of the card (e.g.: en, es, de, cn, etc.) |

<details>
  <summary>Show/hide examples of these parameters</summary>
  
  | `&hide=prs,issues` | `&hide_title=true` | `&hide_border=true` |
  | :--: | :--: | :--: |
  | ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra&hide=prs,issues) | ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra&hide_title=true) | ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra&hide_border=true) |
  | `&border_radius=20` | `&theme=dark` | `&locale=es` (Spanish) |
  | ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra&border_radius=20) | ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra&theme=dark) | ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=anuraghazra&locale=es) |
  
  `cache_seconds` does not have a visual change[^2]. Therefore no example is given. As for the ability to hide languages:
  | Normal Language Card | `&hide=javascript` added |
  | --- | --- |
  | ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api/top-langs/?username=anuraghazra) | ![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api/top-langs/?username=anuraghazra&hide=javascript) |

</details>

#### Card exclusive options
All set with the universal stuff? Good deal. Let's move on to the options that only work with specific card types. If you try these with the wrong card type, your card will fail. They are exclusive for a reason.

**Stats Card Only**
| Parameter | Default | Description
| --- | :--: | --- |
| `hide_rank` | `false` | If you don't want your grade visible, you can hide it by setting this to `true`. This will also automatically resize the card. |
| `show_icons` | `false` | Icons are not shown by default. However, you can add style to your stats by setting this to `true`. |
| `include_all_commits` | `false` | Counts every single commit you have ever made instead of the current year alone. |
| `count_private` | `false` | Includes private commits in the total commit count. |

You would need to edit the [themes/index.js](./index.js) file and add your theme to the end of the file. Then, while you're submitting a *Pull Request*, **don't forget to add a screenshot** of how your theme looks


[^1]: **WARNING:** For links containing spaces or certain special characters, you **must** use the URL-escapes, as specified in [Percent Encoding](https://en.wikipedia.org/wiki/Percent-encoding). For example, if there is a space in the text like in `My spaced text`, you must add the code `%20` instead of the spaces like this: `My%20spaced%20text`. If it's a symbol, such as the plus sign `+` as in `C++`, it must be written as `c%2B%2B` when put in the link. You can use [URL Encoder](https://urlencoder.org/) to help you do this automatically.
[^2]: **WARNING:** We use caching to decrease the load on our servers. Cards are cached for a minimum of 4 hours (`14400` seconds, dafault cache) and a maximum of 24 hours (`86400` seconds). See #1471 (comment) for more information.
