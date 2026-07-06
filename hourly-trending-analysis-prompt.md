You are running as an hourly cc-connect scheduled task.

Goal:
Find one currently interesting, popular, or historically notable project from GitHub Trending, then produce a detailed, well-designed local HTML analysis report. Do not analyze the same project twice.

Important interpretation:
- Treat "training" as "trending" unless the user later corrects it.
- Prefer GitHub Trending. If GitHub Trending is unavailable, use GitLab Explore/trending-like discovery or another public primary source, and clearly state the fallback in the report.

Local workspace:
- Base directory: /home/renault/workspace/github-training-analysis
- Reports directory: /home/renault/workspace/github-training-analysis/reports
- State file: /home/renault/workspace/github-training-analysis/state/analyzed-projects.json

Required workflow:
1. Ensure the base, reports, and state directories exist.
2. Read the state file if it exists. It should track analyzed repositories by canonical URL, name, source, analysis timestamp, and report path.
3. Browse the web for current GitHub Trending or comparable public project discovery data. Use primary sources where practical.
4. Select exactly one project that has not already been analyzed. Prefer projects that are popular, technically interesting, and suitable for a deep engineering/product analysis.
5. Analyze it in depth:
   - What the project does
   - Why it became popular or notable
   - Core architecture and technical design
   - Key implementation ideas
   - Product/design insight
   - Strengths, risks, limitations
   - What developers can learn from it
   - Links to source pages used
6. Generate a polished standalone HTML report in the reports directory. The report must be visually refined, responsive, and not look like a generic AI page. Use local CSS in the HTML file; no external build step required.
7. Name the report with timestamp plus repo slug, for example:
   /home/renault/workspace/github-training-analysis/reports/2026-07-05-2300-owner-repo.html
8. Update the state file atomically so the same repository is not selected again.
9. Send a concise Feishu/cc-connect response with:
   - Selected repository name and URL
   - One-sentence reason it was selected
   - Local report path
   - Whether the state file was updated successfully

Design requirements for the HTML report:
- Start with a clear editorial/product-style hero, not a centered generic hero.
- Avoid AI default tropes: purple glow gradients, three identical feature cards, generic glassmorphism, emoji, and decorative filler.
- Use a restrained palette with one accent color.
- Use varied section layouts, dense but readable information, and clear hierarchy.
- Include a compact source list at the end.
- The page must work by directly opening the HTML file in a browser.

Failure behavior:
- If no fresh project can be found, do not overwrite an old report. Send a short message explaining the issue and the state file path.
- If web access fails, create no report unless there is enough reliable source material, and state the failure clearly.
