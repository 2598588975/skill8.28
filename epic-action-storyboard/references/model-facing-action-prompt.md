# Model-facing epic action prompt mode

Use this mode when the user wants one complete prompt to paste directly into an AI-video model, especially for fast combat, superpowers, liquid simulation, destruction, giant-scale entities, or multi-shot sequences under roughly 30 seconds.

## Control priority

Apply controls in this order:

1. Source story, exact duration, assets, dialogue, and required final state.
2. First visible frame of every shot.
3. Screen position, body orientation, face visibility, eyeline, active hand, and prop state.
4. Observable action, camera response, and VFX consequence in one causal chain.
5. Irreversible damage states and continuity across cuts.
6. Lighting direction, material response, environmental interaction, and audio.
7. Optional optical metadata.

The first frame is not a decorative note. It must say what is already visible. For a character shot, specify the visible side of the body and face, whether both eyes are visible, which hand is active, and where the target lies. For an action-wide shot, specify every required subject and their left/right relationship in the first frame. For a reveal, place the revealed object in the first frame unless an empty opening is explicitly requested.

## Camera language

Default to short, observable camera descriptions:

- 正面三分之四近景，脸和右手同时可见
- 水面高度的侧面高速跟拍
- 第三刀斩出时爆发式后撤至大全景，画面形成轻微荷兰角
- 硬切垂直俯拍，第一帧已经包含两名角色
- 水面高度双人中近景，摄影机缓慢后退

Do not output focal length, diagonal field of view, camera distance, exact camera height, or roll angle by default. Use numbers only when the user already supplied them, when matching a measured plate or previs, or when a specific failed result shows that the number is necessary. A number never replaces a visible composition statement.

Do not stack unrelated moves in one beat. Camera motion must be caused by something visible: follow a charge, pull back to reveal an attack scale, tilt because a character looks upward, or settle when an impact ends.

## Action and VFX writing

Write action as a visible causal chain:

`body/hand action -> effect formation -> target contact -> material response -> irreversible end state -> camera reaction`

For each strike or impact, identify the contact location and the resulting state. Do not let severed, shattered, dispersed, extinguished, or dropped elements reset after a cut unless the story explicitly restores them.

Use frame counts only for intentionally instantaneous actions. Use decimal-second ranges for the surrounding preparation, impact, and aftermath so the model is not asked to complete several incompatible actions at once.

## Compact output shape

Preserve the user's proven format when one is supplied. Otherwise use only the sections needed from this structure:

```text
一、成片要求
二、资产信息、物理规则、特效方案
三、最高优先级
四、分镜内容

镜头1｜0.0-3.0秒｜景别与运镜
起幅第一帧：...
0.0-0.6秒：...
0.6-1.3秒：...
落幅：...

【对话模块】
【物理接戏】
【音频】
```

Omit per-shot English prompts, render-toggle lists, continuity tables, rhythm charts, and repeated quality adjectives unless the user explicitly requests a production document rather than a model-facing prompt.

## Final check

Before delivery, verify that every cut has an explicit first frame, all screen directions remain readable, the camera never starts on an unintended back view, props stay in the correct hand, VFX damage does not reset, dialogue fits inside its assigned time, and the last frame matches the requested ending.
