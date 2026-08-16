import re

with open('/home/claude/original_readme.md', 'r', encoding='utf-8') as f:
    lines = f.readlines()

VALID_CATEGORIES = [
    "Animals","Anime","Anti-Malware","Art & Design","Authentication & Authorization",
    "Blockchain","Books","Business","Calendar","Cloud Storage & File Sharing",
    "Continuous Integration","Cryptocurrency","Currency Exchange","Data Validation",
    "Development","Dictionaries","Documents & Productivity","Email","Entertainment",
    "Environment","Events","Finance","Food & Drink","Games & Comics","Geocoding",
    "Government","Health","Jobs","Machine Learning","Music","News","Open Data",
    "Open Source Projects","Patent","Personality","Phone","Photography","Programming",
    "Science & Math","Security","Shopping","Social","Sports & Fitness","Test Data",
    "Text Analysis","Tracking","Transportation","URL Shorteners","Vehicle","Video","Weather"
]
VALID_SET = set(VALID_CATEGORIES)

# find start (### Animals)
start_idx = None
for i, l in enumerate(lines):
    if l.strip() == "### Animals":
        start_idx = i
        break
body = lines[start_idx:]

row_re = re.compile(r'^\|\s*\[([^\]]+)\]\(([^)]+)\)\s*\|\s*(.*?)\s*\|\s*(.*?)\s*\|\s*(.*?)\s*\|\s*(.*?)\s*\|\s*$')
cat_re = re.compile(r'^###\s+(.+)$')

sections = {}
order = []
current_cat = None

for line in body:
    line = line.rstrip('\n')
    m = cat_re.match(line)
    if m:
        cat_name = m.group(1).strip()
        if cat_name in VALID_SET:
            current_cat = cat_name
            if current_cat not in sections:
                sections[current_cat] = []
                order.append(current_cat)
        else:
            current_cat = None
        continue
    m2 = row_re.match(line)
    if m2 and current_cat:
        name, url, desc, auth, https, cors = m2.groups()
        auth = auth.replace('`', '')
        if name.strip() == 'API':
            continue
        sections[current_cat].append((name.strip(), url.strip(), desc.strip(), auth.strip(), https.strip(), cors.strip()))

print("Categories found:", len(order))
total = sum(len(v) for v in sections.values())
print("Total entries:", total)
missing = VALID_SET - set(order)
print("Missing categories:", missing)

def anchor_for(cat):
    a = cat.lower()
    a = a.replace('&', '')
    a = re.sub(r'[^a-z0-9\s-]', '', a)
    a = re.sub(r'\s+', '-', a.strip())
    return a

out = []
out.append("# Public APIs Reference\n")
out.append("A curated, categorized list of free and public APIs — adapted from the community-maintained [public-apis](https://github.com/public-apis/public-apis) repository, with a live homepage/docs link for every entry.\n")
out.append("## Index\n")
for cat in VALID_CATEGORIES:
    out.append(f"- [{cat}](#{anchor_for(cat)})")
out.append("- [Example Usage](#example-usage)")
out.append("")

for cat in VALID_CATEGORIES:
    if cat not in sections:
        continue
    out.append(f"\n## {cat}\n")
    out.append("| API | Description | Auth | HTTPS | CORS |")
    out.append("|---|---|---|---|---|")
    for name, url, desc, auth, https, cors in sections[cat]:
        desc_safe = desc.replace('|', '\\|')
        name_safe = name.replace('|', '\\|')
        out.append(f"| [{name_safe}]({url}) | {desc_safe} | {auth} | {https} | {cors} |")

with open('/home/claude/README_final.md', 'w', encoding='utf-8') as f:
    f.write("\n".join(out))

print("Wrote README_final.md")
