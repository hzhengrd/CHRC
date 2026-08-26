# CHRC Resource Coding Codebook

## Scope and unit of analysis

The coding table contains one row per consolidated CHRC data resource. A resource may be documented by more than one publication. In those cases, publication identifiers and citation keys are separated by semicolons, and resource-level fields reflect the union of documented information. The original auditable resource identifiers from the coding workbook are retained.

The coding distinguishes **information coverage** (the 17 H/R/T/E categories) from **data-instantiation properties** (the nine I_ fields). Environmental configuration is a scale field: it counts distinct sites, rooms, workcell layouts, sensor arrangements, or simulation scenes used to instantiate the environment. It is not an additional H/R/T/E category and does not substitute for environment geometry, semantics, or operating conditions.

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
- `environment_configurations`: distinct sites, rooms, workcell layouts, sensor arrangements, or simulation scenes. A new trial in an unchanged configuration is not a new configuration.
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

## Cross-referent relations

`cross_referent_relations` lists relations connecting two or more H/R/T/E referents that were identified by the existing evidence-matching pass. Controlled labels used in this release are `communication`, `coordination`, `handover`, `proximity`, `shared attention`, `directed trust`, `collision risk`, and `task authority`. Multiple relations are semicolon-separated. These relation codes remain machine-assisted candidates pending author audit. `notReported` means that the evidence-matching pass did not identify a documented relation; it is not evidence that collaboration lacked relations.

## Missingness and interpretation

All undocumented values remain missing. No value is estimated or imputed. In particular, `notReported` is a lower bound on what the publication makes visible, not a claim that the underlying resource lacks the information. The finalized workbook contained no category-level cases with sufficiently explicit negative evidence to assign `notCaptured`; the value remains in the public vocabulary for future coding and corrections.

One full-text study was excluded because its non-English full text did not permit assessment under the review protocol. Because the public exclusion vocabulary has no language category, this study is represented as `no-eligible-resource`; this is a vocabulary mapping rather than a substantive judgment that the publication contains no resource.
