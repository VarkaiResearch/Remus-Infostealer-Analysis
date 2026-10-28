# Remus Infostealer — Static Reverse Engineering

**Varkai Research** | **Research report: October 23, 2026**  
**Method:** Offline static analysis | **Family assessment:** Remus (high confidence)

## Overview

This repository presents an independent investigation of a Remus infostealer sample. The research examines a Go-based loader, reconstructs its embedded native Windows payload, and documents code paths related to information collection, command handling, uploads, and blockchain-based infrastructure discovery.

The investigation was performed **without executing the malware or contacting its command-and-control infrastructure**. Findings describe capabilities supported by static evidence, not behaviors observed on an infected host.

**[Read the complete eight-page research report (PDF)](./Varkai_Remus_Report.pdf)**

## Key findings

| Area | Finding |
| --- | --- |
| Loader reconstruction | Extracted a 336,560-byte embedded data blob and reconstructed a 336,567-byte PE32+ x64 payload. |
| Information collection | Identified static call paths for screen capture, Unicode clipboard access, and Windows protected-data decryption. |
| API obfuscation | Documented a nonstandard reflected CRC32-based API resolution routine. |
| Command protocol | Identified step-indexed HTTP requests, several task-handler paths, and a multipart/form-data upload implementation. |
| Infrastructure discovery | Recovered Ethereum JSON-RPC request parameters and a contract address also described in independent Remus research. |

## Sample identifiers

**Outer loader SHA-256**

```text
744f82adda79c794c3462ded64800cd9a50f47fb9f198c95e0235abe341944f2
```

**Reconstructed stage-two payload SHA-256**

```text
4306d3d9c3c7563784c792d9e99d2afa3c0e338fc109ea233af69c804ab94aa5
```

These hashes identify the artifacts examined in this investigation. **No malware binaries are distributed in this repository.**

## Research approach

The analysis correlated Ghidra decompilation and disassembly, extracted embedded data, Windows API references, deobfuscated strings, function references, and external family research. The report documents relevant function addresses and distinguishes direct observations from inferences and unverified runtime behavior.

### Scope and limitations

- Neither the outer loader nor the reconstructed payload was executed during this investigation.
- No successful network exchange, command execution from a server, exfiltration, persistence, or host compromise was observed.
- The current off-chain command-and-control destination was not resolved.
- The public Ethereum RPC gateway referenced by the sample is **not**, by itself, evidence that the gateway is attacker-controlled.

For the full evidence, confidence assessments, technical addresses, and investigative guidance, consult the [PDF report](./Varkai_Remus_Report.pdf).

## Prior research and corroboration

- [SpyCloud Labs — *Remus: A New Infostealer Hunting Wallets, Passwords, and AI Credentials*](https://spycloud.com/blog/remus-a-new-infostealer/)
- [Iossefy — *Inside Remus Stealer: Obfuscation, Direct Syscalls, and Blockchain-Based C2*](https://iossefy.github.io/malware/remus-stealer)

These references provide external context and corroboration; they are not substitutes for the sample-specific evidence documented in the report.

## About Varkai Research

Varkai Research is an independent cybersecurity research initiative focused on malware reverse engineering, threat analysis, and digital forensics.

**Website:** [varkairesearch.com](https://varkairesearch.com)

## Responsible research notice

This repository is published for defensive security research, threat intelligence, and education. Its technical descriptions should be interpreted within the documented methodology and limitations. It does not include executable malware, and publication does not imply authorization to access or interfere with third-party systems.

© 2026 Varkai Research.
