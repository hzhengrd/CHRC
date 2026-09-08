# CHRC Resource Coding Codebook

## Scope and unit of analysis

The coding table contains one row per consolidated CHRC data resource. A resource may be documented by more than one publication. In those cases, publication identifiers and citation keys are separated by semicolons, and resource-level fields reflect the union of documented information. The original auditable resource identifiers from the coding workbook are retained.

The coding distinguishes **information coverage** (the 17 H/R/T/E categories) from **data-instantiation properties** (the nine I_ fields). Environmental configuration is a scale field: it counts distinct sites, rooms, workcell layouts, or simulation scenes used to instantiate the environment. Variation in sensor arrangement alone is collection metadata, not a distinct environmental configuration. Environmental configuration is not an additional H/R/T/E category and does not substitute for environment geometry, semantics, or operating conditions.

## Coding procedure and release status

Each resource was independently coded by four of the five authors against the shared operational definitions and boundary rules in this codebook. The independent coding covered the 17 H/R/T/E categories, the nine data-instantiation properties, resource scale and context, access status, record basis, and cross-referent relations. The four coders then compared their decisions, reviewed the supporting full-text evidence, and resolved disagreements through discussion until consensus. The public table contains only these final consensus decisions.

Inter-coder agreement was high: Fleiss' κ = 0.79 for the 17 information categories (90.1% pairwise agreement) and κ = 0.94 for the nine data-instantiation properties (97.6% pairwise agreement). The residual disagreements concentrated in the intent-versus-action and specification-versus-execution distinctions, which the illustrative edge cases below document. The four independent coder-level coding files are published alongside this codebook as `independent-coding-coder1.csv` through `independent-coding-coder4.csv`.

Computational tools were used to assemble records and to help locate candidate passages in the full texts. They did not determine the released codes. A value was retained only after manual examination of the source evidence by the authors and completion of the consensus procedure. No machine-generated candidate or unaudited relation code remains in this release.

## Value vocabulary

### Coverage categories

- `captured`: the publication explicitly documents that the resource contains data about the category.
- `notCaptured`: the publication or resource design explicitly rules the category out.
- `notReported`: the category is undocumented. This is a lower-bound code and is not evidence that the information is absent from files that were not available for inspection.

### Data-instantiation properties

- `reported`: the publication states a value for the property for at least one captured category.
- `notReported`: the property is undocumented. This is a lower-bound code and is not evidence that no such metadata exists outside the publication.

### Other controlled fields

- `setting`: `on-site`, `off-site production`, `laboratory mock-up`, `immersive/VR`, `simulation`, `teleoperation`, or `not reported`.
- `record_basis`: `episode`, `elicited`, `model-generated`, or `mixed`.
- `origin`: `real`, `synthetic`, `mixed`, or `not reported`.
- `access_status`: `open public`, `metadata only`, `available on request`, `planned release`, `restricted`, `explicitly unavailable`, or `not reported`.
- Missing metadata and scale values use `not reported`; the relation field uses `notReported` to match the categorical coding vocabulary.

## Metadata and scale fields

- `resource_id`: stable identifier retained from the consolidated coding workbook.
- `citation_key`: source BibTeX key retained from the bibliographic export. Multiple documenting publications are semicolon-separated. Some source databases assigned the same author-year key to different publications; therefore, this field is not guaranteed to be unique and `linked_publications` should be used for DOI-based joins.
- `short_label`: first-author surname and publication year. Multiple documenting publications are semicolon-separated.
- `year`: earliest publication year associated with the consolidated resource.
- `linked_publications`: normalized DOI strings; `not reported` is retained where a DOI was unavailable.
- `setting`: primary collection or generation setting reported in the full text. A technology such as VR is a setting only when it defines the collection environment.
- `record_basis`: `episode` for records of an actual collaborative activity; `elicited` for responses obtained from people about CHRC; `model-generated` for data generated computationally without recorded human participation; `mixed` when more than one basis supplies the resource.
- `origin`: whether the underlying observations are real, synthetic, or a documented mixture.
- `focal_task`: construction task labels reported by the publication. Conditions or repeated trials of one objective are not separate tasks.
- `participants`: distinct humans whose activity forms part of the resource. Researchers, observers, annotators, and operators are excluded unless their activity is recorded as participant data.
- `robot_instances`: participating robot instances. A modular robot assembled into one operating system counts as one instance unless multiple robots participate concurrently.
- `robot_platforms`: distinct platform types identified by model or stable platform description.
- `focal_tasks`: number of distinct construction work objectives, not the number of conditions or repetitions.
- `environment_configurations`: distinct sites, rooms, workcell layouts, or simulation scenes. A new trial in an unchanged configuration is not a new configuration. Variation in camera number, camera placement, or another sensor arrangement alone is retained as collection metadata and does not create a new environmental configuration.
- `sessions_or_trials`: the reported count of sessions, runs, trials, rounds, or episodes. The count is retained without converting among these experimental units.
- `duration`: reported duration with its original unit. Units are not converted or combined.
- `access_status`: strongest verified access statement associated with the resource. `open public` means public files were verifiably accessible; it does not by itself establish that every underlying experimental record was released.

## Human categories

### H_capabilityAndRole

**Operational definition:** participant profile, assigned role, skill, authority, capability, training, permissions, or limitations relevant to the episode. **Boundary cases:** participant count or demographics alone do not establish capability or role; an identifier counts only when it differentiates participating roles or profiles.

### H_physicalState

**Operational definition:** bodily state before task-level interpretation, including location, posture, pose, gaze, hand state, motion, proximity to work objects, or ergonomic exposure. **Boundary cases:** a semantic action label without recorded bodily state is coded under H_action, not automatically here.

### H_action

**Operational definition:** operational or communicative human activity, including lifting, fastening, guiding, inspecting, speech, gesture, confirmation, warning, or interface input. **Boundary cases:** goals or planned actions belong to H_intent; passive posture belongs to H_physicalState.

### H_intent

**Operational definition:** forward-looking human goal, plan, request, preference, need, or intended next operation. **Boundary cases:** an observed action is not intent unless the source reports, labels, elicits, or infers a forward-looking state.

### H_internalState

**Operational definition:** cognitive, affective, or physiological condition relevant to performance, safety, or collaboration, including workload, attention, fatigue, stress, trust, perceived safety, situational awareness, or discomfort. **Boundary cases:** gaze direction alone is H_physicalState unless interpreted as attention; physiological signals count here only when used to represent an internal condition.

## Robot categories

### R_capabilityAndConfiguration

**Operational definition:** platform characteristics relevant to the episode, including kinematics, dynamics, payload, reach, end-effector, sensing, autonomy mode, control interface, safety functions, or operating limits. **Boundary cases:** a robot model name alone counts only when it establishes configuration information; instantaneous pose belongs to R_physicalState.

### R_physicalState

**Operational definition:** instantaneous spatial or mechanical state, including base pose, joint state, end-effector pose, velocity, acceleration, force, torque, or gripper state. **Boundary cases:** rated payload and reach are capabilities; robot activity labels belong to R_action.

### R_action

**Operational definition:** operational or communicative robot activity, including navigation, manipulation, placement, scanning, tool use, speech, display, status cue, or expressive motion. **Boundary cases:** a trajectory that has only been planned belongs to R_intent; measured movement belongs here and may also instantiate R_physicalState.

### R_intent

**Operational definition:** forward-looking robot state, including planned trajectory, selected policy, next operation, committed task sequence, navigation goal, manipulation target, or replanning decision. **Boundary cases:** executed motion alone is R_action; a controller architecture without a recorded or represented plan is insufficient.

## Task categories

### T_specification

**Operational definition:** task goal, requirements, success criteria, tolerances, quality or safety constraints, and relevant design or project specifications. **Boundary cases:** a task name alone is insufficient when no goal or criterion is represented in the resource.

### T_structure

**Operational definition:** decomposition into operations, sequencing, precedence, preconditions, effects, alternatives, or dependencies. **Boundary cases:** repeated trials do not constitute task structure; a flat activity label is not a decomposition.

### T_allocation

**Operational definition:** division or sharing of responsibility among participants, including fixed or dynamic allocation, handover points, authority, or fallback responsibility. **Boundary cases:** the mere presence of a human and robot does not establish allocation.

### T_workObjectState

**Operational definition:** identity, pose, geometry, properties, availability, completion, or quality state of materials, components, tools, temporary works, or work products directly involved in the focal task. **Boundary cases:** surrounding objects that do not form part of the focal work belong to E_semanticContent or E_geometricStructure.

### T_execution

**Operational definition:** operations completed or underway, deviations, errors, interruptions, recovery actions, timing, and task outcome. **Boundary cases:** intended or prescribed sequences belong to T_structure; task success criteria belong to T_specification.

## Environment categories

### E_geometricStructure

**Operational definition:** spatial form of the surroundings, including layout, work zones, surfaces, obstacles, traversable space, exclusion zones, surrounding geometry, or changing as-built conditions. **Boundary cases:** the geometry of a focal work object belongs to T_workObjectState; a named site without represented geometry is insufficient.

### E_semanticContent

**Operational definition:** identity or function of surrounding equipment, materials, temporary structures, non-participating workers or robots, signage, hazards, access routes, or workspace boundaries. **Boundary cases:** focal task objects belong to T_workObjectState; geometry without identity or function belongs to E_geometricStructure.

### E_operatingConditions

**Operational definition:** lighting, weather, dust, noise, vibration, visibility, ground condition, congestion, adjacent activity, site rules, schedule pressure, or project phase. **Boundary cases:** fixed spatial layout belongs to E_geometricStructure; a generic claim that construction sites are variable does not establish recorded operating-condition data.

## Data-instantiation properties

### I_modality

**Operational definition:** signal or record type, such as RGB video, depth, thermal imagery, LiDAR, audio, inertial signal, force/torque signal, controller log, BIM record, survey, text, or symbolic annotation. **Boundary cases:** naming a sensor without stating or unambiguously identifying its recorded output is insufficient.

### I_representationForm

**Operational definition:** stored data structure, such as scalar, vector, class label, bounding box, segmentation mask, keypoints, pose, trajectory, point cloud, mesh, graph, event log, time series, or document field. **Boundary cases:** modality and file extension alone do not establish representation form.

### I_unitOfObservation

**Operational definition:** basic analytical record, such as frame, event, action segment, object instance, operation, episode, trial, participant, shift, work zone, or project phase. **Boundary cases:** measurement units such as seconds or metres belong to I_measurementUnit.

### I_measurementUnit

**Operational definition:** numeric unit or scale, including metres, millimetres, degrees, radians, seconds, frames, normalized coordinates, force, torque, confidence score, or ordinal rating. **Boundary cases:** a sampling rate does not by itself define the observation unit.

### I_source

**Operational definition:** origin of the record, including fixed, wearable, robot-mounted, or aerial sensors; robot controllers; BIM models; schedules; site systems; annotations; surveys; or inspection records. **Boundary cases:** the publication, author, or repository is not the data source in this sense.

### I_perspective

**Operational definition:** observation viewpoint or reference position, including egocentric, allocentric, fixed third-person, aerial, robot-mounted, tool-mounted, BIM/world, or site-level. **Boundary cases:** camera location counts only when it establishes viewpoint; coordinate frames belong to I_spatialReference.

### I_encodingMethod

**Operational definition:** how information becomes encoded, including direct measurement, system logging, manual annotation, automatic inference, computation from other fields, self-report, expert assessment, or document extraction. **Boundary cases:** an algorithm name alone is insufficient unless its role in producing the recorded value is stated.

### I_spatialReference

**Operational definition:** coordinate system or spatial frame, including image, human-body, robot-base, end-effector, tool, task-local, world/site, BIM, geographic, or zone-based references. **Boundary cases:** viewpoint is not a coordinate frame; qualitative location without an identified spatial reference is insufficient.

### I_temporalReference

**Operational definition:** temporal indexing scheme, including timestamp, frame index, control cycle, start-end interval, event time, operation period, episode boundary, shift, schedule activity, or project phase. **Boundary cases:** total duration alone does not establish how records are temporally indexed or synchronized.

## Illustrative edge cases

The boundary cases above state the rule; the worked examples below show how the rule is applied when two categories compete for the same evidence. In every case, the code records what the publication documents, not what the underlying data might contain.

### H_intent vs H_action

- **Scenario.** A publication shows a worker reaching toward a wall panel and states that the worker intends to install it.
- **Resolution.** The reaching is observed behavior and is coded `captured` under `H_action`; the stated intention is a forward-looking state and is coded `captured` under `H_intent`. If the publication shows the reaching but never reports a goal or plan, `H_intent` is `notReported`.

### T_workObjectState vs E_geometricStructure / E_semanticContent

- **Scenario.** A robot drills into a panel held by a worker, while the surrounding room walls only constrain the workspace.
- **Resolution.** The panel is a focal work-object and is coded `captured` under `T_workObjectState`. The walls are environment, coded under `E_geometricStructure` only if their geometry is represented; a named room without represented geometry is `notReported`.

### H_physicalState vs H_action

- **Scenario.** A publication reports a worker's joint angles and posture during a lift.
- **Resolution.** Joint angles and posture are bodily state and are coded `captured` under `H_physicalState`; the lift itself is a meaningful activity and is coded `captured` under `H_action`. A semantic label such as "lifting" without recorded posture or kinematics supports `H_action` but not `H_physicalState`.

### R_action vs R_intent vs R_physicalState

- **Scenario.** A controller outputs a trajectory that has not yet been executed; elsewhere the paper plots the executed motion.
- **Resolution.** The planned trajectory is `captured` under `R_intent`. The executed motion is `captured` under `R_action` and, if its pose or velocity is recorded, also under `R_physicalState`.

### H_internalState vs H_physicalState

- **Scenario.** An eye-tracker records gaze, and the paper interprets dwell time as attention on the robot.
- **Resolution.** Raw gaze is `captured` under `H_physicalState`; gaze interpreted as attention is `captured` under `H_internalState`. Both are coded when the publication documents both the signal and its interpretation.

### E_operatingConditions vs E_geometricStructure

- **Scenario.** A paper reports the site's dust level and lighting alongside the room layout.
- **Resolution.** Dust and lighting are variable conditions and are coded `captured` under `E_operatingConditions`; the layout is fixed spatial form and is coded `captured` under `E_geometricStructure`.

### T_specification vs T_execution

- **Scenario.** A paper states the target tolerance and the measured deviation of the finished assembly.
- **Resolution.** The tolerance is `captured` under `T_specification`; the measured deviation is `captured` under `T_execution`. A target value alone does not establish `T_execution`, and an outcome alone does not establish `T_specification`.

## Cross-referent relations

`cross_referent_relations` lists relations connecting two or more H/R/T/E referents that were established from the full-text evidence and coded through the same independent four-author review and consensus procedure used for the other resource fields. Controlled labels used in this release are `communication`, `handover/contact`, `proximity`, `coordination/synchronization`, `shared attention/awareness`, `directed psychological relation`, `collision/safety`, and `task allocation/authority`. Multiple relations are semicolon-separated. `notReported` means that the reviewed publication did not document a qualifying relation under this protocol; it is not evidence that the collaboration itself lacked relations.

## Missingness and interpretation

All undocumented values remain missing. No value is estimated or imputed. In particular, `notReported` is a lower bound on what the publication makes visible, not a claim that the underlying resource lacks the information. In this corpus, the consensus review found no category-level case with sufficiently explicit negative evidence to assign `notCaptured`. This is an outcome of the coding rather than an omitted category; `notCaptured` remains in the controlled vocabulary for future resources and corrections.

One full-text study was excluded because its non-English full text did not permit assessment under the review protocol. Because the public exclusion vocabulary has no language category, this study is represented as `no-eligible-resource`; this is a vocabulary mapping rather than a substantive judgment that the publication contains no resource.
