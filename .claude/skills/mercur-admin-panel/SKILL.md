# mercur-admin-panel Development Patterns

> Auto-generated skill from repository analysis

## Overview

The mercur-admin-panel is a React-based TypeScript application serving as an administrative interface for e-commerce management. It features comprehensive order management, promotion handling, and internationalization support with a focus on maintainable code structure and consistent development workflows.

## Coding Conventions

### File Naming
- Use **kebab-case** for all file names
- Component files: `component-name.tsx`
- Test files: `component-name.test.tsx`
- Route files: organized in nested directories under `src/routes/`

### Import/Export Style
- Use **absolute imports** from project root
- Use **named exports** for components and utilities
- Import example:
  ```typescript
  import { ComponentName } from 'src/components/component-name'
  import { translations } from 'src/i18n/translations/en.json'
  ```

### Commit Messages
- Use **freeform** style with descriptive messages
- Common prefix: `fix` for bug fixes
- Keep messages around 55 characters average
- Example: `fix: resolve validation issue in order forms`

## Workflows

### Release Workflow
**Trigger:** When preparing a new version release
**Command:** `/release`

1. Update version number in `package.json`
2. Document changes in `CHANGELOG.md` with new version section
3. Create a release branch from main
4. Review all changes and test functionality
5. Merge release branch to main
6. Tag the release with version number

### Internationalization Update
**Trigger:** When adding new translatable strings or updating existing ones
**Command:** `/add-translation`

1. Update translation schema in `src/i18n/translations/$schema.json`
2. Add new translation keys to `src/i18n/translations/en.json`
3. Propagate new keys to all other language files (`*.json`)
4. Verify translation key consistency across all languages
5. Test UI with different language settings

Example translation addition:
```json
// en.json
{
  "orders": {
    "refund": {
      "title": "Process Refund",
      "amount": "Refund Amount"
    }
  }
}
```

### Order Management Feature
**Trigger:** When adding new order operations like refunds, claims, exchanges
**Command:** `/add-order-feature`

1. Create form component in `src/routes/orders/order-[feature]/components/[feature]-form/`
2. Implement validation logic for the form
3. Add necessary translation keys to `src/i18n/translations/en.json`
4. Update order detail routes to include new feature
5. Add navigation and UI integration
6. Test the complete order workflow

Form structure example:
```typescript
// src/routes/orders/order-refund/components/refund-form/refund-form.tsx
export const RefundForm = () => {
  // Form implementation
}
```

### Bug Fix Workflow
**Trigger:** When fixing identified bugs in the system
**Command:** `/fix-bug`

1. Identify the problematic component in `src/routes/` or `src/components/`
2. Analyze the issue and implement the fix
3. Update related translations in `src/i18n/translations/en.json` if needed
4. Create or update test cases for the fixed functionality
5. Verify the fix doesn't break existing features
6. Commit with descriptive message starting with "fix:"

### Promotion Management Feature
**Trigger:** When modifying promotion rules, forms, or validation logic
**Command:** `/update-promotion`

1. Update promotion creation forms in `src/routes/promotions/promotion-create/components/`
2. Modify promotion editing forms in `src/routes/promotions/promotion-edit-details/components/`
3. Update rule components in `src/routes/promotions/common/edit-rules/components/`
4. Add or update translations for new promotion features
5. Test complete promotion creation and editing flow
6. Verify rule validation works correctly

### Dependency Update Workflow
**Trigger:** When updating npm packages or build configuration
**Command:** `/update-deps`

1. Update dependencies in `package.json`
2. Run package manager to update `yarn.lock`
3. Update configuration files if needed (`.eslintrc.json`, `vite.config.mts`)
4. Test build process and resolve any breaking changes
5. Run full test suite to ensure compatibility
6. Update documentation if API changes affect usage

## Testing Patterns

- Test files follow pattern: `*.test.*`
- Tests are co-located with components
- Focus on component behavior and user interactions
- Test internationalization by verifying translation key usage
- Include form validation testing for order and promotion features

Example test structure:
```typescript
// component-name.test.tsx
describe('ComponentName', () => {
  it('should render correctly', () => {
    // Test implementation
  })
})
```

## Commands

| Command | Purpose |
|---------|---------|
| `/release` | Create and merge release versions with changelog updates |
| `/add-translation` | Update translation files across all supported languages |
| `/add-order-feature` | Add new order management functionality with forms |
| `/fix-bug` | Fix bugs with component updates and translation adjustments |
| `/update-promotion` | Update promotion creation and editing functionality |
| `/update-deps` | Update project dependencies and configuration files |