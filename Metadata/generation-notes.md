# Generation Notes

## Scope

Only complete sets containing 1,000 readable images are published. Incomplete and smoke-test outputs are excluded.

## Standardized and original settings

The standardized variants use an L-inf budget of 16/255 where the method supports a pixel-bounded perturbation. If an official configuration uses a different budget, an additional directory with `Original` in its name preserves that budget.

## Attack objectives

The methods in this repository do not share a single objective:

- FOA-Attack, MPC-Attack, M-Attack, and AttackVLM consume paired source and target images.
- X-Transfer uses its released universal adversarial perturbation. The perturbation was applied to each source image independently of the target-image directory.
- SSA-CWA uses an untargeted ensemble objective with source-image labels predicted by the surrogate ensemble.
- AnyAttack uses the released pretrained attack model and does not consume the paired target-image directory.

These distinctions must be retained in downstream comparisons and publications.

## File naming

Each directory uses numeric image identifiers from `0` through `999`. Identical numeric identifiers across methods refer to the same source-image index, but do not imply that every method optimizes against a paired target image.

