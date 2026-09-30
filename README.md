# Tool Pocket Generator V147

## Provenance
Built directly from Tool_Pocket_Generator_V139_FINAL(1).zip, the user's explicitly requested baseline. No V140-V146 code was used as the source.

## Exact change
Curve handling for a single Curve point between two Straight points:
- The Curve point is treated as a point ON the outline.
- The outline between the neighbouring Straight points is a circular arc passing through the Curve point.
- The rendered profile uses the same sampled curve data used by Geometry Check and STL generation.
- Near-collinear triples use a quadratic fallback constrained to pass through the Curve point at the midpoint.
- Multi-Curve runs retain the V139 composite quadratic-chain behaviour; only the one-Curve-between-Straights case is changed.

## What was not changed
- Add Point insertion/placement
- Existing point positions, point numbers, and mode assignments
- Finger Relief functions or other FR-related behaviour
- Dimensions, grid workflow, workspace, Geometry Check criteria, JSON workflow, STL construction, and controls/layout, except version identifiers
- Existing saved-tools localStorage key is retained for continuity

## Retest instructions
1. Open V147 and load the same outline used for the V146 test.
2. Select the middle point between two Straight points and set it to Curve.
3. Drag that Curve point away from the straight line.
4. Check that the black outline becomes a circular arc and passes through the centre of the C dot.
5. Run Geometry Check. Confirm the displayed arc still passes through C and the profile does not shift.
6. If Geometry Check passes, export JSON and STL and confirm dimensions and outline remain as expected.

## Verification status
- ZIP integrity checked.
- JavaScript syntax checked.
- Source confirms drawing and Geometry Check call the same sampled() curve logic.
- Not tested in iPad/Safari; user's retest is required.
