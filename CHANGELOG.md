# Changelog

## [1.0.1] - 2026-01-02

### Added

**Setup & Help**:
- Interactive setup wizard (`/founder-support-system:setup`)
  - Step-by-step Notion MCP server verification
  - Guided Notion page creation
  - Automatic `.claude/config.md` generation
  - Connection testing
- Help command (`/founder-support-system:help`)
  - Complete setup guide
  - Quick start instructions
  - Troubleshooting section
  - Quick reference card

**Documentation**:
- CLAUDE.md file for future Claude Code instances
- Updated README with interactive setup instructions
- Configuration loading priority documentation

### Changed

- README installation section now highlights interactive setup wizard
- Improved onboarding experience for new users

## [1.0.0] - 2026-01-02

### Initial Release

**Founder Support System** - Strategic planning and executive coaching for founders.

#### Features

**Planning & Review**:
- Year Plan skill and command (OKR-based annual planning)
- Quarterly Review skill and command (structured reviews)
- Vision skill and command (manifesto creation)
- Personal Operating Model skill and command (comprehensive self-assessment)
- Working with Me skill and command (user manual creation)

**Coaching**:
- Executive Coach skill (strategic alignment, daily decisions)
- Financial Coach skill (burn rate, runway, revenue planning)

**Utilities**:
- Get Year and Quarter command (bundled internally, zero external dependencies)

#### Configuration

- Config file system for Notion page URLs (`.claude-plugin/config.json`)
- Template configuration provided (`.claude-plugin/config.template.json`)
- All 6 Notion pages configurable (Vision, Year Plan, POM, Golden Rules, Logbook, Founder Wisdom)

#### Resources

- Founder Wisdom resource file (`.claude-plugin/resources/founder-wisdom.md`)
- Bundled curated wisdom from 11 thought leaders (Pieter Levels, Naval, Jason Fried, etc.)
- Referenced by executive-coach and financial-coach skills

#### Integration

- Notion MCP for page fetching and updates
- Interactive workflows with AskUserQuestion
- Console-only coaching (< 2 min sessions)
- Long-form planning sessions (60-90 min)

#### Philosophy

Based on:
- OKR frameworks (Google, Measure What Matters)
- Personal Operating Model (Reboot.io)
- Pieter Levels' bootstrapping philosophy
- Stage 2 Capital's Base/Best/Worst planning
- Clare Hughes Johnson's leadership frameworks

**Prime Directive**: Turn reflection into decisions.

#### Removed from Original

- Levels Coach (Pieter Levels shipping coach) - removed to simplify plugin
- SuperCoach agent - removed to simplify plugin

## License

MIT
