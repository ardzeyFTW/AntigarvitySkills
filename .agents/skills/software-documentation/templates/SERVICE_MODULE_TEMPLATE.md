# Module / Service: [ServiceName]

- **Path**: `src/services/[ServiceName].[ts|py|dart|go]`
- **Layer**: [Backend Service / API Client / Data Access Object / Middleware]
- **Status**: [Active / Experimental / Deprecated]

---

## 1. Responsibility
[Describe the core business logic, domain boundaries, and capabilities managed by this service or module.]

---

## 2. Public API / Methods

### `methodName(param1: Type, options?: Options): Promise<ResultType>`
* **Description**: [What this method executes]
* **Arguments**:
  - `param1` (`Type`): [Explanation]
  - `options` (`Options`): [Optional flags, timeout, headers]
* **Returns**: `Promise<ResultType>` with resolved payload.
* **Throws**:
  - `NotFoundError`: When entity does not exist.
  - `ValidationError`: When input payload fails schema verification.

---

## 3. Data Schema & Contracts

```typescript
export interface ResultType {
  id: string;
  createdAt: string;
  status: 'pending' | 'completed' | 'failed';
  metadata?: Record<string, unknown>;
}
```

---

## 4. Dependencies & Infrastructure
- **Database / Store**: PostgreSQL / Redis / Cloud Firestore table `users`
- **External APIs**: Third-party payment gateway or sensor stream
- **Configuration Keys**: `DATABASE_URL`, `API_KEY` (managed via environment variables)

---

## 5. Security & Failure Recovery
- **Authentication / Authorization**: Requires valid bearer token with `admin` scope.
- **Rate Limiting**: Enforced at 100 requests / minute per client IP.
- **Circuit Breaker / Retries**: Exponential backoff up to 3 attempts with 500ms initial delay.

---

## 6. Testing Strategy
- Unit test path: `tests/services/ServiceName.test.ts`
- Integration test path: `tests/integration/ServiceName.integration.test.ts`
