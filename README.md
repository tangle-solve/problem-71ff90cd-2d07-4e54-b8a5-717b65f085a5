<!-- solve-problem:71ff90cd-2d07-4e54-b8a5-717b65f085a5 -->
# QMA versus QCMA

A [Tangle Solve problem](https://solve.tangle.tools/problems/71ff90cd-2d07-4e54-b8a5-717b65f085a5).

## What is the problem?

Determine whether QMA = QCMA.

- **QMA** (Quantum Merlin–Arthur): a language L is in QMA if there exists a polynomial-time quantum verifier V such that (completeness) x ∈ L ⟹ ∃ quantum state |ψ⟩ on poly(|x|) qubits with Pr[V(x, |ψ⟩) accepts] ≥ 2/3, and (soundness) x ∉ L ⟹ no quantum state makes V accept with probability > 1/3.
- **QCMA** is the same class except the witness must be a classical string (possibly random, but a classical bit string) read by the quantum verifier.

The question: can polynomial-size quantum states serve as strictly more powerful certificates than polynomial-size classical strings for quantum verifiers? The natural precise goal is an unconditional separation QMA ≠ QCMA (or equality). Note that "classical witness" can mean a deterministic string or a distribution over strings; the standard definition is deterministic (mixed witness variants change the class only in trivial ways since soundness is worst-case).

## Why does it matter?

This asks whether quantum information itself — entanglement, amplitudes, non-orthogonal states — is intrinsically necessary for efficiently verifiable proof systems, a foundational question about the nature of quantum evidence. A resolution would sharpen our understanding of QMA-hard problems (e.g., the local Hamiltonian problem: are its witnesses necessarily quantum?). It also bears on the "quantum proofs = quantum states" analogy to NP and on cryptography (QSZK-type hiding of quantum data). The analogous separation NP ⊆ QMA with unknown classical witness is a key structural unknown in quantum complexity theory.

## What's already known?

- **Containment:** QCMA ⊆ QMA trivially; also QCMA ⊆ A0PP and QMA ⊆ PP (Kitaev–Watrous / Marriott–Watrous amplification and in-place measurement), so both sit inside PP.
- **Oracle separations:** Aaronson and Kuperberg (2007) constructed a quantumly accessible oracle relative to which QMA ⊄ QCMA; earlier oracle evidence came from Aaronson (2006, "QMA/qpoly"). These separations use oracles that hide classical information in quantum states (e.g., via black-box groups / hidden subgroups-like structure), so they give no unrelativized answer.
- **Non-closure results:** QMA/qpoly contains undecidable languages (Aaronson 2006), showing quantum advice is powerful — related but different from the witness question.
- **Structural results:** Marriott–Watrous (2005) give in-place amplification for QMA and QCMA and show both are closed under complement. Aharonov–Naveh (2002) formalized QCMA and posed the question.
- No unconditional technique is known for proving query/communication lower bounds in the verifier-interaction model without an oracle.

## What would count as solving it?

1. **Separation:** An unconditional proof of a language in QMA ∖ QCMA (full solution), or a partial result such as QMA ∖ QCMA ∩ some class, or a separation with restricted verifiers (e.g., log-depth verifiers).
2. **Equality:** A procedure converting any QMA verifier to a QCMA verifier with poly overhead (would be shocking but is the other resolution).
3. Intermediate progress: proving QCMA ≠ QMA(2) or amplified-circuit lower bounds against classical witnesses for the local Hamiltonian problem; or removing the oracle from Aaronson–Kuperberg.

## How to start

1. Read Watrous's survey chapter (arXiv:0804.3401, §§ on QMA and QCMA) for definitions and amplification; then Aharonov–Naveh (2002, quant-ph/0210077).
2. Read Aaronson–Kuperberg (quant-ph/0603045) carefully: understand exactly why the oracle is needed and what breaks without it — the verifier can't query hidden subgroups directly.
3. Try restricted-verifier separations: constant-depth verifiers, single-query verifiers, or "QMA with classical verifier interactions" — check what's known (verify) about QCMA vs QMA with few qubits of witness.
4. Candidate hard case: local Hamiltonian instances whose ground states are "unexplainable classically" — relate to the (independent) problem of short classical descriptions of ground states / area-law limitations.

## Key references

- Aharonov, D., Naveh, T. (2002), "Quantum NP — A Survey", arXiv:quant-ph/0210077. Defines QCMA, surveys QMA, poses the QMA vs QCMA question explicitly.
- Watrous, J. (2008), "Quantum Complexity Theory (Part 1/2)" lecture notes / survey, arXiv:0804.3401. Clean formal treatment of QMA, QCMA, amplification, PP containment.
- Marriott, C., Watrous, J. (2005), "Quantum Arthur–Merlin Games", Computational Complexity 14(2). Proves in-place amplification and complement-closure of QMA and QCMA.
- Aaronson, S., Kuperberg, G. (2007), "Quantum Versus Classical Proofs: Advice and Verification", Proc. QIP 2006 / arXiv:quant-ph/0603045. Oracle separation QMA^O ⊄ QCMA^O (verify exact venue).
- Aaronson, S. (2006), "QMA/qpoly Is Contained in PSPACE/poly: De-Merlinizing Quantum Protocols", arXiv:quant-ph/0510230. Tools for stripping quantum information; relevant context (verify).

## Warnings

- Oracle separations here use *quantumly accessible* oracles (unitaries/black-box groups); they cannot be transferred to the unrelativized setting, and naive attempts to "implement the oracle" fail because the oracle hides classical structure.
- Careful with witness definitions: classical witness = deterministic string; allowing mixed states as witnesses does not define QCMA.
- Common dead end: trying to use the PP upper bound to separate — both classes are in PP, so counting-class techniques can't distinguish them.
- Check all citations above marked "(verify)" before relying on them; the census record's key works are confirmed but the finer results should be verified against original sources.

---
*`ALGO-000189` · unverified*

## Acceptance guidance

1. **Separation:** An unconditional proof of a language in QMA ∖ QCMA (full solution), or a partial result such as QMA ∖ QCMA ∩ some class, or a separation with restricted verifiers (e.g., log-depth verifiers).
2. **Equality:** A procedure converting any QMA verifier to a QCMA verifier with poly overhead (would be shocking but is the other resolution).
3. Intermediate progress: proving QCMA ≠ QMA(2) or amplified-circuit lower bounds against classical witnesses for the local Hamiltonian problem; or removing the oracle from Aaronson–Kuperberg.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/71ff90cd-2d07-4e54-b8a5-717b65f085a5?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000189.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000189)
