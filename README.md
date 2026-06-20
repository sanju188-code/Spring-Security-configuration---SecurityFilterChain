       [ REQUEST ] 
            │
            ▼
┌──────────────────────────────────────┐
│             FILTER CHAIN             │ ──► [ RESPONSE ]
│  ┌─────┐    ┌─────┐    ┌─────┐       │
│  │     │ ──►│     │ ──►│     │       │ ──► [ Your Application Controllers ]
│  └─────┘    └─────┘    └─────┘       │
└──────────────────┬───────────────────┘
                   │
                   ▼
┌──────────────────────────────────────┐
│        Authentication Filter         │ ──► [ SECURITY CONTEXT ]
└──────────────────▲───────────────────┘
                   │ (Delegates)
                   ▼
┌──────────────────────────────────────┐
│        AuthenticationManager         │
└──────────────────┬───────────────────┘
                   │ (authenticate())
                   ▼
┌──────────────────────────────────────┐
│       DaoAuthenticationProvider      │
└──────────┬────────────────┬──────────┘
           │                │
           │ (matches())    │ (loadUserByUsername())
           ▼                ▼
┌────────────────────┐    ┌────────────────────┐
│  PasswordEncoder   │    │ UserDetailsService │
└────────────────────┘    └─────────┬──────────┘
                                    │ (findByUsername())
                                    ▼
                               ( Database )
