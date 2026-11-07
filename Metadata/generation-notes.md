# Generation Notes

## Current benchmark scope

The active benchmark contains only complete 1,000-image sets configured for an L-infinity budget of 16/255 and paired source-target attacks:

- FOA-Attack-Eps16
- MPC-Attack-Eps16
- M-Attack-Eps16
- AttackVLM-Eps16
- X-Transfer-Paired-Eps16

The exact original FOA numeric source-target correspondence is preserved in `foa-source-target-pairs.json`. Image IDs are 0 through 999. The manifest records source and target hashes rather than relying on filenames alone.

The pixel audit compares each published adversarial PNG with the numerically corresponding canonical FOA source. All retained files must match their original published Git LFS SHA-256 and length, be readable 224-by-224 images, and have a maximum absolute RGB pixel difference no greater than 16. `benchmark-audit.json` records these checks per image. Target pairing is declared by the existing benchmark generation configuration; its provenance is distinct from the independently checked image hashes and source-relative pixel budgets.

## Method distinctions

The old M-Attack-v2-Eps16 directory was a revised V1 pipeline, not the official M-Attack-V2 from arXiv:2602.17645, and has been removed. The genuine upstream project is pinned in Projects/M-Attack-V2. Its author-released budget-16 set contains 100 images and is preserved separately in Author-Releases/M-Attack-V2-Eps16 with upstream metadata and per-file hashes. It is not counted as a complete matched 1,000-image benchmark, and no old pipeline scores are reused.

X-Transfer-Paired-Eps16 is an adapted protocol. The released X-Transfer perturbation initializes each sample, followed by 300 steps of target-feature optimization using the corresponding target image and OpenAI CLIP ViT-B/32. It is a paired adaptation rather than an output of the official universal-perturbation protocol.

## Removed benchmark sets

Sets configured with budgets 8 or 12 were removed from the active image directories. AnyAttack, SSA-CWA, and universal X-Transfer outputs were also removed because these configurations do not consume the paired target images. `benchmark-cleanup.json` lists the removed directories and their reasons. Paper references and official project submodules are retained.
