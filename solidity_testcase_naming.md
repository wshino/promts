# Solidity Test Case Naming Conventions

- Start every test function with test_, then separate the action, outcome, and conditions with underscores.
- For success paths, describe what we do and what should happen; for failure paths, include RevertIf or RevertWhen so the revert reason is explicit.
- Append Fuzz to property-based tests so CI can spot them quickly.
- Mark cross-module integration suites via the file/contract name (..._Integration.t.sol) or function name.
- Keep helper routines internal, prefix them with _, and name them after their role.
- Favor scenario descriptors over numbering variants so failure logs immediately tell the story.

## Examples

- Happy paths: test_ExecuteTransfer_EmitsEvent, test_ApproveSpend_AfterGuardianRotation
- Revert paths: test_RevertIf_GuardianMissing, test_RevertWhen_NonceAlreadyUsed, test_RevertIf_InvalidSignatureType
- Fuzz: test_Fuzz_GuardianThresholdRespected
- Integration: MynaWalletExecute_Integration.t.sol:test_Execute_AfterGuardianRotation
- Helper: _prepareGuardianArray(address[] memory guardians)
