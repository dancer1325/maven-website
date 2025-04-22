- Plugin goal
    - := **specific task** (👁️finer than a build phase 👁️) which about a project contributes to the
        - building &
        - managing
    - can be bound to
        - 0 build phases
            - === can be executed directly, outside the build lifecycle
        - ≥ 1 build phases
            - → is called in all these build phases
    - it’s execution order
        - depends on the invocation order of
            - plugin goals
            - build phases

---

- TODO: