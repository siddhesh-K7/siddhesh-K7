from pathlib import Path
import re

source = Path("/mnt/data/single_file_profile/README.md").read_text()
text = source

# Add a neon banner without requiring any local image files.
banner = '''
<a id="top"></a>

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&amp;color=0:0D1117,45:7C3AED,100:00D9FF&amp;height=220&amp;section=header&amp;text=SIDDHESH.exe&amp;fontSize=55&amp;fontColor=FFFFFF&amp;animation=twinkling&amp;fontAli[[1]]gnY=37&amp;desc=SOFTWARE%20%2F%20AI%20%2F%20CURIOSITY&amp;descAlignY=60&amp;descSize=17" width="100%" alt="Siddhesh.exe — neon software and AI banner" />
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/versions/generation-v/black-white/animated/25.gif" width="65" alt="Animated Pikachu pixel mascot" />
  &nbsp; &nbsp; <b>✦ WELCOME TO MY DEV ARCADE ✦</b> &nbsp; &nbsp;
  <img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/versions/generation-v/black-white/animated/133.gif" width="65" alt="Animated Eevee pixel mascot" />
</p>
'''
pos = text.index('<p align="center">')
text = text[:pos] + banner + text[pos:]

old_nav = re.search(r'<p align="center">\n  <a href="#start">.*?</p>', text, re.S)
new_nav = '''<p align="center">
  <a href="#start"><img src="https://img.shields.io/badge/01_PLAYER-7C3AED?style=for-the-badge" alt="Go to about me" /></a>
  <a href="#projects"><img src="https://img.shields.io/badge/02_PROJECTS-0891B2?style=for-the-badge" alt="Go to project ideas" /></a>
  <a href="#paths"><img src="https://img.shields.io/badge/03_SKILL_TREE-059669?style=for-the-badge" alt="Go to learning paths" /></a>
  <a href="#arcade"><img src="https://img.shields.io/badge/04_ARCADE-DB2777?style=for-the-badge" alt="Go to coding challenges" /></a>
  <a href="#connect"><img src="https://img.shields.io/badge/05_CONNECT-D97706?style=for-the-badge" alt="Go to collaboration interests" /></a>
</p>'''
text = text[:old_nav.start()] + new_nav + text[old_nav.end():]

menu = '''
## 🕹️ Choose Your Path

<table>
<tr>
<td align="center" width="33%">
<b>🛠️ THE BUILDER</b><br>
Software · APIs · Applications<br><br>
<a href="#projects">Explore project concepts →</a>
</td>
<td align="center" width="33%">
<b>🤖 THE EXPLORER</b><br>
AI · LLMs · Experiments<br><br>
<a href="#ai-room">Enter the AI room →</a>
</td>
<td align="center" width="33%">
<b>🧩 THE PROBLEM SOLVER</b><br>
Python · Java · DSA<br><br>
<a href="#arcade">Try a challenge →</a>
</td>
</tr>
</table>

<details>
<summary><b>🎁 Open the welcome chest</b></summary>

### You found the starting kit!

- **Curiosity:** Ask how it works.
- **Patience:** Read the error before changing the code.
- **Practice:** Build the smallest useful version.
- **Honesty:** Show what works and what still needs improvement.

**Choose your next move:** [Meet me](#start) · [View ideas](#projects) · [Try the arcade](#arcade)

</details>

'''
text = text.replace('<a id="start"></a>', menu + '<a id="start"></a>', 1)

ai_room = '''
<a id="ai-room"></a>

## 🤖 The AI Exploration Room

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&amp;size=18&amp;duration=2300&amp;pause=800&amp;color=A78BFA&amp;center=true&amp;vCenter=true&amp;width=750&amp;lines=Ask+better+questions.;Build+small+experiments.;Evaluate+the+results.;Document+the+limitations." width="90%" alt="Animated AI learning motto: ask, experiment, evaluate, document." />
</p>

<details>
<summary><b>🚪 Door 1 — Talk to a database</b></summary>

**An idea I'm exploring:** Natural-language database interaction.

Before building, I want to answer:
- What should the assistant be allowed to access?
- How should ambiguous requests be clarified?
- How would I test whether an answer is correct?

[Explore the project concept](#projects)

</details>

<details>
<summary><b>🚪 Door 2 — Build a chat experience</b></summary>

**An idea I'm exploring:** Astra Chat UI with a backend.

A useful interface should make its state understandable:
- Waiting for input.
- Loading a response.
- Displaying a result.
- Explaining a failure.

[Explore Astra](#projects)

</details>

<details>
<summary><b>🚪 Door 3 — The evidence room</b></summary>

A polished demo is a starting point, not proof of reliability.

For an experiment, I want to record:
- What I tested.
- What worked.
- What failed.
- What remains uncertain.

</details>

'''
text = text.replace('<a id="arcade"></a>', ai_room + '<a id="arcade"></a>', 1)

# Decorative separators and easy return links.
for anchor in ["projects", "paths", "arcade", "options", "connect"]:
    text = text.replace(
        f'<a id="{anchor}"></a>',
        '<p align="center">✦ ━━━━━━━━━━━ ◈ ━━━━━━━━━━━ ✦</p>\n\n'
        f'<a id="{anchor}"></a>', 1
    )

text += '''
<p align="center">
  <a href="#top"><img src="https://img.shields.io/badge/↑_BACK_TO_SPAWN-7C3AED?style=for-the-badge" alt="Back to the top of the profile" /></a>
</p>

<details>
<summary><b>🎨 Artwork credits & motion options</b></summary>

- Animated pixel mascots: PokéAPI sprite repository; Pokémon characters belong to their respective owners.
- Decorative snake: Platane/snk demonstration, not my contribution history.
- Animated text: DenverCoder1/readme-typing-svg.
- Banner: kyechan99/capsule-render.
- Navigation badges: Shields.io.
- Images load from external hosts and may become unavailable.
- For less motion, remove the animated image tags; navigation and panels still work.
- All profile markup is in this file; no assets directory or workflow is required.
- Animations are decorative images, not playable games or live progress indicators.

</details>

<img src="https://capsule-render.vercel.app/api?type=waving&amp;color=0:0D1117,45:7C3AED,100:00D9FF&amp;height=110&amp;section=footer" width="100%" alt="Purple and cyan decorative footer" />
'''

# Replace outdated visual-switch text from the previous edition.
text = text.replace("Keep the typing header and decorative snake.",
                    "Keep the neon banner, typing headers, pixel mascots, and snake.")
text = text.replace("Keep the typing header; remove the snake.",
                    "Keep one typing header; remove the mascots and snake.")
text = text.replace("The former custom robot GIFs are not embedded in this edition.",
                    "Pixel mascots replace the earlier locally stored robot GIFs.")

# Keep the new visual features; remove one optional learning group for space.
group = "<details>\n<summary><b>🛠️ Developer Workflow Exploration"
start = text.find(group)
if start >= 0:
    next_section = text.find('<a id="ai-room"></a>', start)
    # The group ends just before the AI room and its surrounding whitespace.
    segment = text[start:next_section]
    end = segment.rfind("</details>") + len("</details>")
    text = text[:start] + text[start+end:]

lines = text.splitlines()

# Compact Markdown paragraph spacing, preserving explicit visual line breaks.
while len(lines) > 1000:
    candidate = next(
        (i for i in range(1, len(lines)-1)
         if not lines[i] and lines[i+1].startswith(
             ("**Try this:**", "**Review:**", "**Focus:**", "**Mode:**"))),
        None
    )
    if candidate is not None:
        lines[candidate-1] = lines[candidate-1].rstrip() + "  "
        lines.pop(candidate)
        continue
    # Blank lines immediately before closing HTML panels are not needed.
    candidate = next(
        (i for i in range(1, len(lines)-1)
         if not lines[i] and lines[i+1] == "</details>"),
        None
    )
    if candidate is None:
        raise RuntimeError("Unable to compact safely to 1,000 lines.")
    lines.pop(candidate)

# If necessary, wrap long prose lines rather than adding empty filler.
while len(lines) < 1000:
    in_code = False
    chosen = None
    for i, line in enumerate(lines):
        if line.startswith("```"):
            in_code = not in_code
            continue
        if (not in_code and len(line) > 85 and
            not line.startswith(("<", "|", "#", "-", "[", " ", "!", ">")) and
            "http" not in line):
            cut = line.rfind(" ", 30, 78)
            if cut > 0:
                chosen = (i, cut)
                break
    if chosen is None:
        raise RuntimeError("No suitable prose line available for wrapping.")
    i, cut = chosen
    lines[i:i+1] = [lines[i][:cut], lines[i][cut+1:]]

result = "\n".join(lines) + "\n"
assert len(result.splitlines()) == 1000
assert result.count("<details") == result.count("</details>")
assert result.count("```") % 2 == 0
assert "./assets/" not in result
assert all(f'id="{a}"' in result for a in
           ["top", "start", "projects", "paths", "arcade", "ai-room", "options", "connect"])

folder = Path("/mnt/data/siddhesh_neon_arcade")
folder.mkdir(exist_ok=True)
file = folder / "README.md"
file.write_text(result, encoding="utf-8")

print("Created: README.md")
print("Exactly 1,000 lines")
print("Single file • No local assets • No workflow files")
print("Added: neon banner, animated mascots, badge navigation, choice panels, and AI exploration rooms")
