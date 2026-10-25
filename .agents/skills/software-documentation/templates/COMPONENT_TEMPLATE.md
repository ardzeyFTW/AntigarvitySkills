# Component: [ComponentName]

- **Path**: `src/components/[Path]/[ComponentName].[ts|tsx|vue|dart|py]`
- **Layer**: [UI / Presentational / Container / Hook / State Controller]
- **Status**: [Stable / Active Development / Deprecated]
- **Maintainer / Agent**: [Owner]

---

## 1. Overview & Purpose
[Provide a clear 2-3 sentence description of what this component is responsible for and why it exists. Follow the Single Responsibility Principle.]

---

## 2. Interface Contract

### Props / Inputs / Parameters

| Property / Parameter | Type | Required? | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `id` | `string` | Yes | — | Unique identifier |
| `variant` | `'primary' \| 'secondary'` | No | `'primary'` | Visual styling variant |
| `disabled` | `boolean` | No | `false` | Disables interaction |
| `onAction` | `(data: Payload) => void` | No | `undefined` | Callback invoked on submit |

### Emitted Events / Callbacks / Outputs
- `onAction(Payload)`: Triggered when user confirms input.
- `onError(AppError)`: Emitted if internal validation fails.

---

## 3. Internal State & Invariants
* **State Variables**:
  - `isLoading: boolean`: Tracks active asynchronous mutation.
  - `validationErrors: Record<string, string>`: Holds localized field errors.
* **Invariants**:
  - The submit action cannot be triggered if `isLoading === true` or `disabled === true`.
  - State resets when the `id` prop changes.

---

## 4. Dependencies & Collaborators
- **Subcomponents**: `[ButtonComponent]`, `[InputField]`
- **Services / Stores**: `useAuthStore()`, `apiClient`
- **External Packages**: `lucide-react`, `zod`

---

## 5. Error Handling & Edge Cases
- **Network Disconnection**: Renders an inline retry banner without discarding user input.
- **Empty / Null Data**: Displays the empty state illustration defined in `EmptyPlaceholder`.
- **Overflow / Large Text**: Clamps text at 2 lines with an accessible tooltip.

---

## 6. Example Usage

```tsx
import { ComponentName } from '@/components/ComponentName';

export function ExampleView() {
  return (
    <ComponentName
      id="user-profile-header"
      variant="primary"
      onAction={(payload) => console.log('Action dispatched', payload)}
    />
  );
}
```

---

## 7. Testing & Verification
- **Unit Test Path**: `tests/unit/components/ComponentName.test.ts`
- **Key Test Cases**:
  - [x] Renders default state with required props.
  - [x] Disables button when `disabled` is true.
  - [x] Fires `onAction` callback on button click.
  - [x] Handles empty array response gracefully without throwing unhandled exceptions.
