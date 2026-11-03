# Habitude note integrations · 노트 앱 연결

## AI agent extensions · 에이전트 확장

[Hermes Agent, ChatGPT desktop and Claude Code](https://github.com/legott-ai/habitude-agent-integrations) provide platform-native extensions for explicitly selected Habitude / Obsidian writing. Version **0.2.0 includes the local search runtime** and does not require an installed Habitude app. The runtime runs on macOS or Linux with Python 3.10+ and SQLite FTS5; host availability still applies, and ChatGPT is desktop-only. These packages support search, excerpts, index status/cache refresh and cited reflection, not entry editing or habit checkoffs. Returned excerpts may enter the host's configured model context; setup requires explicit Vault scope and acknowledgement.

**0.2.0에는 로컬 검색 런타임이 포함**되어 Habitude 앱의 별도 설치 없이 직접 선택한 Habitude / Obsidian Vault를 연결합니다. macOS 또는 Linux의 Python 3.10 이상과 SQLite FTS5가 필요하며 호스트별 실행 환경 제한은 유지됩니다. Hermes는 네이티브 플러그인과 스킬, Claude Code는 플러그인, ChatGPT는 데스크톱용 패키지입니다. 기록 검색·발췌·색인 상태/캐시 갱신·근거 기반 회고를 지원하고, 기록 수정이나 습관 완료는 수행하지 않습니다. 검색 발췌가 모델 문맥에 들어갈 수 있으므로 Vault를 직접 고르고 동의해야 합니다. ChatGPT 웹·모바일은 연결하지 않습니다.

| Agent / 에이전트 | Download / 다운로드 | Setup / 설치 안내 |
| --- | --- | --- |
| Hermes Agent | [0.2.0 plugin + skill](https://github.com/legott-ai/habitude-agent-integrations/releases/download/v0.2.0/habitude-hermes-0.2.0.zip) | [Hermes](https://github.com/legott-ai/habitude-agent-integrations/tree/main/hermes) |
| ChatGPT desktop | [0.2.0 desktop plugin](https://github.com/legott-ai/habitude-agent-integrations/releases/download/v0.2.0/habitude-chatgpt-0.2.0.zip) | [ChatGPT desktop](https://github.com/legott-ai/habitude-agent-integrations/tree/main/chatgpt) |
| Claude Code | [0.2.0 plugin](https://github.com/legott-ai/habitude-agent-integrations/releases/download/v0.2.0/habitude-claude-code-0.2.0.zip) | [Claude Code](https://github.com/legott-ai/habitude-agent-integrations/tree/main/claude-code) |

Hermes official community catalog: [submission PR #148671](https://github.com/NousResearch/hermes-agent/pull/148671), open and awaiting maintainer review/CI permission. ChatGPT and Claude official directory submissions have not been completed.

Hermes 공식 커뮤니티 카탈로그 등록 요청은 위 PR로 제출했으며 운영진 검토·CI 실행 승인을 기다립니다. ChatGPT·Claude 공식 디렉터리에는 아직 제출되지 않았습니다.

[Official integrations page / 공식 연동 안내](https://habitude.ai/integrations#ai-agents). Download releases and publisher-managed catalogs are separate from official directory approval. 다운로드 제공·자체 카탈로그와 각 플랫폼의 공식 디렉터리 승인은 별개입니다.

**[한국어 · English / Integrations](https://habitude.ai/integrations)** — the official installation and download page. Choose a language with the page switcher or open [한국어](https://habitude.ai/integrations?lang=ko) / [English](https://habitude.ai/integrations?lang=en).

Use the writing tools you already have, then bring selected text into Habitude. These first releases use **explicit, local file exchange**. They do not silently read accounts or provide automatic two-way synchronization.

기존 노트 앱에서 선택한 기록을 Habitude로 이어 가져옵니다. 현재 배포는 사용자가 직접 확인하는 텍스트 교환 방식입니다.

| App / 앱 | Available / 제공 경로 | Install / 설치 |
|---|---|---|
| Notion | Habitude Mac selected-page read connection + Korean/English journal templates | [Setup below](#notion) · templates in this repo and release |
| Joplin | Desktop plugin: review and export the selected note as Markdown | [Plugin source and releases](https://github.com/legott-ai/habitude-joplin-plugin) |
| Logseq | Markdown file graph plugin: review and export the current page | [Plugin source and releases](https://github.com/legott-ai/habitude-logseq-plugin) |
| OneNote / Evernote web / other websites | Browser extension: preview selected text and save a portable capture | [Clipper source and releases](https://github.com/legott-ai/habitude-note-clipper) |
| Apple Notes | Import an official Markdown export in Habitude Mac | Settings → Import from other note apps → Apple Notes |
| Bear | Import Markdown or text-only TextBundle/TextPack ZIP | Settings → Import from other note apps → Bear |
| Evernote | Import text-only ENEX, or capture selected web text | Settings → Import from other note apps → Evernote |
| Other Markdown apps | Import Markdown files or a text-only ZIP | Settings → Import from other note apps → Markdown |

## Use the Mac importer / Mac에서 가져오기

1. Update Habitude for Mac. Open **Settings → Import from other note apps**.
2. Select the original note app, then choose its exported files. Limit: 20 files, 100 notes, 8 MiB total.
3. Review the titles, dates and warnings; select **Import previewed notes**. The originals stay in their original app. New notes enter the selected Habitude local store/Obsidian Vault.
4. Reimporting the same stable source does not duplicate it. Locally edited, moved or deleted writing is preserved as a conflict. Without a source ID, the original filename is the identity: renaming may create a new source. Missing dates use the first imported local date.

설정에서 원본 앱과 파일을 선택하고 미리 본 뒤 가져오기를 누르세요. 같은 원본의 중복과 로컬 수정·삭제·이동을 확인합니다. 사진·첨부가 포함된 파일은 현재 **전체 가져오기를 중단**합니다. 텍스트만 내보내거나 원래 앱에서 첨부를 보관하세요. 이 기능을 사진 백업으로 표시하지 않습니다.

## Notion

The deployed Mac connection is a **personal read-only internal connection**, not a Notion Marketplace app. Create a read-only internal connection in your own workspace, share only the desired pages with it, and enter its token in **Habitude Mac → Settings → Notion connection**. The token is stored in Mac Keychain. Never paste it into chat, a GitHub issue or a source file.

Enter up to 20 page links. Preview first, then explicitly import. Existing local changes are preserved. Media are kept as source links; no media backup, workspace-wide discovery or live two-way editing is implied.

Notion 공개 OAuth 연결·Marketplace 등록은 별도 계정 등록 및 검수가 필요한 단계입니다. 현재 다운로드 제공이나 개인 연결 구현을 Marketplace 승인으로 표시하지 않습니다.

Templates: **daily**, **habits**, **weekly** in Korean and English. Import them via Notion's Text & Markdown importer, then duplicate pages as needed. These are writing templates; automatic database formulas, recurring tasks and streak calculations are not included.

## Distribution status

Joplin and Logseq provide manually installable download releases. Actual isolated-host checks covered Joplin 3.7.22 and Logseq 0.10.15, native file export, original preservation and Habitude import/reimport. Logseq uses Download as the primary path; optional clipboard writes were denied on the tested host. Its AX/background capture discrepancy and foreground mouse verification are documented in its source repository.

The browser extension remains a preview: its code and package tests pass, but an actual browser UI test has not been completed. Notion currently provides the Mac personal read-only connection and templates. Public OAuth registration remains pending.

GitHub downloads are separate from approval in Notion Marketplace, Joplin's plugin directory, Logseq Marketplace and Chrome Web Store. Check release notes for each exact package and actual publication status. Logseq DB graphs and Org-mode exports are unsupported. The browser extension captures only explicitly selected text, not entire private notebooks or images.

Logseq Marketplace: [registration request #953](https://github.com/logseq/marketplace/pull/953) submitted; acceptance is pending. Joplin npm directory publication awaits publisher authentication. Chrome Web Store submission and Notion public OAuth registration are not complete.

## Privacy and support

The file importer runs in the Mac app without a note-service login or external network request. Browser captures stay in popup memory until you save a local file. Plugins do not modify notes or automatically mark habits complete. If you enable Habitude account cloud sync, its existing account settings govern subsequent syncing of imported writing.

Report a reproducible issue with synthetic sample files at the relevant source repository. **Do not attach private writing, tokens, medical data or unredacted exports.**

[Open Habitude](https://habitude.ai/app) · [Habitude](https://habitude.ai)
