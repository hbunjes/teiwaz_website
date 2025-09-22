# Teiwaz Website Development Instructions

**Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.**

## Repository Overview
Teiwaz Website (Webseite für Teiwaz / BC Apps) is currently a minimal repository containing only documentation. This repository is in its early development phase and may evolve to include various web technologies such as static HTML/CSS/JS, React, Vue, or other modern web frameworks.

## Current Repository State
- **Minimal setup**: Contains only README.md file
- **No build system**: Currently no package.json, build scripts, or configuration files
- **No dependencies**: No package managers or dependency files present
- **No CI/CD**: No GitHub Actions workflows configured yet

## Working Effectively

### Initial Repository Setup
```bash
# Clone and navigate to repository
git clone https://github.com/hbunjes/teiwaz_website.git
cd teiwaz_website

# Verify current state
ls -la
# Should show: README.md and .git directory only
```

### Development Workflow - Current State
Since the repository is minimal, most development commands will need to be added as the project grows:

**Important**: The following commands are NOT YET AVAILABLE but represent common patterns to expect:
- `npm install` - will fail (no package.json exists)
- `npm run build` - will fail (no package.json exists)
- `npm run dev` - will fail (no package.json exists)
- `npm test` - will fail (no package.json exists)

### Expected Future Development Patterns
Based on typical website development, anticipate these patterns as the project evolves:

#### For Static Websites
```bash
# When HTML/CSS/JS files are added:
# - Open index.html directly in browser
# - Use live server extensions for development
# - Simple file structure: /css/, /js/, /images/
```

#### For Node.js/NPM-based Projects
```bash
# When package.json is added:
npm install
npm run dev
npm run build
npm test
```

#### For Python-based Projects (Flask/Django)
```bash
# When requirements.txt or pyproject.toml is added:
pip install -r requirements.txt
python app.py
# or
python manage.py runserver
```

### Build and Test Expectations - Future State
**CRITICAL TIMING NOTES - ALWAYS SET APPROPRIATE TIMEOUTS:**

- **npm install**: Typically 1-5 minutes. Set timeout: 10 minutes minimum.
- **npm run build**: Can vary widely (2-30 minutes depending on complexity). Set timeout: 45+ minutes. **NEVER CANCEL** - wait for completion.
- **npm test**: Usually 30 seconds - 10 minutes. Set timeout: 20+ minutes. **NEVER CANCEL** - test suites can be comprehensive.
- **Python pip install**: Usually 1-5 minutes. Set timeout: 10 minutes minimum.
- **Docker builds**: Often 5-20 minutes. Set timeout: 30+ minutes. **NEVER CANCEL**.

### Validation Requirements
**ALWAYS perform these validation steps after making changes:**

1. **File integrity check**:
   ```bash
   ls -la
   git status
   ```

2. **When build system is added, run full build**:
   ```bash
   # For npm-based projects:
   npm install && npm run build
   # For Python projects:
   pip install -r requirements.txt && python -m pytest
   ```

3. **Manual testing scenarios** (when applicable):
   - Open the website in a browser
   - Navigate through all main pages
   - Test any interactive features
   - Verify responsive design on different screen sizes
   - Test forms and user interactions
   - Validate that all links work correctly

4. **Code quality checks** (when applicable):
   ```bash
   # Common linting commands to expect:
   npm run lint
   npm run format
   eslint .
   prettier --check .
   ```

### Common File Locations to Expect
As the project grows, look for these key areas:

- **Root configuration**: `package.json`, `requirements.txt`, `Dockerfile`, `docker-compose.yml`
- **Source code**: `/src/`, `/public/`, `/static/`, `/templates/`
- **Styles**: `/css/`, `/styles/`, `/scss/`
- **Scripts**: `/js/`, `/scripts/`
- **Assets**: `/images/`, `/assets/`, `/media/`
- **Build output**: `/dist/`, `/build/`, `/public/`
- **Configuration**: `/config/`, `.env files`, `webpack.config.js`, `vite.config.js`

### CI/CD Pipeline Expectations
Monitor for these files that indicate CI/CD setup:
- `.github/workflows/*.yml` - GitHub Actions
- `Dockerfile` - Container builds
- `netlify.toml` - Netlify deployment
- `vercel.json` - Vercel deployment

**When CI/CD is added, always run local validation before pushing:**
```bash
# Run the same checks that CI will run
npm run lint
npm run test
npm run build
```

### Troubleshooting Common Issues

#### "Command not found" errors
- **npm/node commands**: Install Node.js first
- **python/pip commands**: Install Python first
- **Missing scripts**: Check if package.json defines the script

#### Build failures
- **Dependency issues**: Run `npm install` or `pip install -r requirements.txt`
- **Version conflicts**: Check Node.js/Python version requirements
- **Missing environment variables**: Check for .env.example files

#### Development server won't start
- **Port conflicts**: Try different ports or kill existing processes
- **Permission errors**: Check file permissions and user access
- **Missing dependencies**: Verify all packages are installed

### Performance and Timing Guidelines
**CRITICAL - ALWAYS SET THESE TIMEOUTS:**

| Command Type | Expected Time | Minimum Timeout | Never Cancel |
|-------------|---------------|-----------------|--------------|
| npm install | 1-5 min | 10 min | ✓ |
| npm build | 2-30 min | 45 min | ✓ CRITICAL |
| npm test | 30s-10 min | 20 min | ✓ |
| Docker build | 5-20 min | 30 min | ✓ |
| pip install | 1-5 min | 10 min | ✓ |
| webpack build | 2-15 min | 30 min | ✓ |

**Remember**: Some builds can legitimately take 30+ minutes. Be patient and never cancel long-running operations.

## Repository-Specific Notes

### Current Contents
```bash
# ls -la output:
total 24
drwxr-xr-x 4 runner runner 4096 Sep 22 08:03 .
drwxr-xr-x 3 runner runner 4096 Sep 22 07:56 ..
drwxrwxr-x 7 runner runner 4096 Sep 22 08:00 .git
drwxrwxr-x 2 runner runner 4096 Sep 22 07:59 .github
-rw-rw-r-- 1 runner runner  532 Sep 22 08:03 .gitignore
-rw-rw-r-- 1 runner runner   48 Sep 22 07:56 README.md

# Key files:
# .github/copilot-instructions.md - These instructions (234+ lines)
# .gitignore - Prevents temporary files from being committed
# README.md - Basic project description
```

### Temporary Files to Watch For
When testing commands, be aware these files may be created temporarily:
- `package-lock.json` - Created by npm commands even when package.json doesn't exist
- `node_modules/` - Created if any npm installs succeed
- `.DS_Store` - macOS system files
- `*.log` - Various log files from build processes

**Always clean up test artifacts** unless they're intended to be part of the project.

### README.md Contents
```markdown
# teiwaz_website
Webseite für Teiwaz / BC Apps
```

### Git Information
- **Repository**: https://github.com/hbunjes/teiwaz_website
- **Current state**: Initial commit with minimal content
- **Language**: Project appears to be German-focused (Webseite = Website in German)

## Key Reminders for Coding Agents

1. **ALWAYS check current repository state first** - don't assume build tools exist
2. **NEVER CANCEL long-running operations** - builds and tests can take significant time
3. **SET EXPLICIT TIMEOUTS** - use 45+ minutes for builds, 20+ minutes for tests
4. **VALIDATE ALL CHANGES** - run complete user scenarios after modifications
5. **CHECK FOR NEW FILES** - as project grows, update these instructions accordingly
6. **RESPECT TIMING** - some operations genuinely require patience
7. **CLEAN UP TEST ARTIFACTS** - remove temporary files created during validation

## Environment Validation
Before starting development work, validate that required tools are available:

```bash
# Check development tools (these should all succeed)
which node      # Should output: /usr/local/bin/node
which npm       # Should output: /usr/local/bin/npm  
which python3   # Should output: /usr/bin/python3
which git       # Should output: /usr/bin/git

# Check versions
node --version  # Current: v20.x.x or higher expected
npm --version   # Current: 10.x.x or higher expected
python3 --version # Current: Python 3.x.x expected
git --version   # Current: git version 2.x.x expected
```

## Validation Checklist for Changes
When making any changes to this repository, run through this checklist:

- [ ] Check repository state: `ls -la` and `git status`
- [ ] Verify instructions accuracy by testing documented commands
- [ ] Clean up any temporary files created during testing
- [ ] Validate file permissions and accessibility
- [ ] Test common failure scenarios (missing files, wrong directories, etc.)
- [ ] Document any new patterns or discoveries in these instructions

When in doubt, start with basic file operations and gradually identify what build system is in use as files are added to the repository.