Body-Bound Vault (BBV)

A protocol for sovereign, biometric-gated, non-custodial Bitcoin custody

⸻

🚀 Overview

Body-Bound Vault (BBV) is a proposed custody protocol designed to make Bitcoin access as sovereign and magical as a Gringotts vault — funds spendable only with the live consent of the rightful owner.

Unlike today’s wallets (seed phrases, custodial apps), BBV uses biometric-gated threshold signatures and on-chain policy enforcement to ensure:
	•	Only you can move your coins (no vendor resets, no backdoors).
	•	No single point of failure (device theft, seed loss, coercion).
	•	Human-friendly recovery (no 12 words on paper).
	•	Clear consent ceremony for every spend.

⸻

🎯 Goals
	•	Non-custodial: private keys never leave user devices or guardianship.
	•	Biometric-gated: live consent required; biometrics unlock keys but never are the keys.
	•	Recoverable: robust, social-backed recovery with on-chain delays.
	•	Anti-coercion: duress paths & withdrawal delays built into the vault.
	•	Portable: works across devices and hardware without central servers.

⸻

🏗️ Architecture

1. Key Management
	•	Threshold signatures (FROST / MuSig2): 2-of-3 or 3-of-5 scheme.
	•	Shares:
	•	Share A → Phone Secure Enclave, biometric-gated.
	•	Share B → Hardware key (YubiKey / Ledger).
	•	Share C → Recovery split with guardians (SLIP-39 + encryption).

2. On-Chain Policy (Taproot / Miniscript)
	•	Branch 1: Everyday spend → 2-of-3, small limits.
	•	Branch 2: High-value → 2-of-3 + time delay (CSV).
	•	Branch 3: Recovery → 3-of-5 guardians + timelock.
	•	Branch 4: Duress → “coerced” path routes to safe vault + timelock.

3. Consent Ceremony
	1.	Wallet builds PSBT.
	2.	Device A requests biometric + liveness check.
	3.	Secure Enclave signs a short-lived Consent Token (CT) bound to tx details.
	4.	Device B confirms with PIN/touch.
	5.	Threshold aggregator combines partials → final Schnorr sig.
	6.	Broadcast to network.

⸻

🔒 Security Features
	•	Biometric stays local: never uploaded, never stored externally.
	•	Consent Tokens: prevent replay or misuse of biometric unlocks.
	•	Duress gestures: trigger safe-vault path instead of real spend.
	•	Withdrawal limits & delays: enforced by script, not app.
	•	Social recovery: guardian shares reconstruct access without central authority.

⸻

🔮 Future Extensions
	•	Zero-knowledge biometric proofs.
	•	Geofenced/time-bound spending policies.
	•	Multisig family vaults with shared policies.
	•	Covenant-style vaults for automated daily limits.

⸻

📚 Resources
	•	Schnorr Signatures / MuSig2
	•	FROST threshold signatures
	•	SLIP-39 Shamir backup
	•	Miniscript vault patterns

⸻

⚠️ Disclaimer

This repository documents a research & design concept.
It is not production-ready software and should not be used to secure real Bitcoin without expert review, formal cryptographic audits, and extensive testing.
