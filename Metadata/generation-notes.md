# Generation Notes

## Current benchmark scope

The active benchmark contains only complete 1,000-image sets configured for an L-infinity budget of 16/255 and paired source-target attacks:

- FOA-Attack-Eps16
- MPC-Attack-Eps16
- M-Attack-Eps16
- M-Attack-v2-Eps16
- AttackVLM-Eps16

The exact original FOA numeric source-target correspondence is preserved in `foa-source-target-pairs.json`. Image IDs are 0 through 999. The manifest records source and target hashes rather than relying on filenames alone.

The pixel audit compares each published adversarial PNG with the numerically corresponding canonical FOA source. All retained files must match their original published Git LFS SHA-256 and length, be readable 224-by-224 images, and have a maximum absolute RGB pixel difference no greater than 16. `benchmark-audit.json` records these checks per image. Target pairing is declared by the existing benchmark generation configuration; its provenance is distinct from the independently checked image hashes and source-relative pixel budgets.

## Method distinctions

M-Attack-v2-Eps16 uses the official M-Attack-V2 implementation from arXiv:2602.17645, pinned in Projects/M-Attack-V2. Its old revised V1 outputs and temporary 100-image author release have been replaced by 1,000 newly generated canonical FOA pairs. The official attack and loss code are unchanged. Retrieval uses the public COCO-Caption2017 validation split (5,000 images), rather than the train2014 pool shown in upstream documentation; two auxiliary images are selected per target by CLIP-B/16 cosine similarity. The actual configuration and per-image provenance are recorded under Metadata/M-Attack-v2-Eps16.

The previous X-Transfer-Paired-Eps16 outputs have been removed at the user's request. A fresh official XTransferBench checkout is being prepared for a new 16/255, 300-step experiment on the original FOA pairs. Its protocol must distinguish the official universal perturbation method from any per-pair target-image adaptation; incomplete outputs are excluded from the active benchmark.

## Removed benchmark sets

Sets configured with budgets 8 or 12 were removed from the active image directories. AnyAttack, SSA-CWA, and universal X-Transfer outputs were also removed because these configurations do not consume the paired target images. `benchmark-cleanup.json` lists the removed directories and their reasons. Paper references and official project submodules are retained.
