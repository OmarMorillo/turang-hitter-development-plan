### Data dictionary

**Turang pitch-by-pitch (`pitches`, `tracked`)**

| Column | Meaning | Units |
|---|---|---|
| game_date | Date of the game (stored as text for now) | YYYY-MM-DD |
| game_year | Season | year |
| batter | Hitter's MLB ID (Turang = 668930) | ID |
| description | What happened on the pitch (called_strike, foul, hit_into_play…) | text |
| bat_speed | Speed of the bat's sweet spot at contact, or where contact would have been | mph |
| attack_angle | Up or down angle of the bat's path at contact; positive = swinging up | degrees |
| attack_direction | Left-right angle of the bat's path at contact; sign convention not confirmed yet (verify) | degrees |
| swing_path_tilt | How steep the bat's plane is through the swing | degrees |

**League table (`league`): one row per qualified hitter per season**

| Column | From | Meaning | Units |
|---|---|---|---|
| player_id | all files | Hitter's MLB ID (renamed from `id` in three files) | ID |
| season | added by me | Season of the leaderboard | year |
| name | expected stats | Hitter's name | text |
| attack_angle | swing path | Season average attack angle | degrees |
| ideal_attack_angle_rate | swing path | Share of swings in Savant's ideal attack angle window (verify range) | 0–1 |
| swing_tilt | swing path | Season average swing plane steepness | degrees |
| attack_direction | swing path | Season average attack direction (verify sign) | degrees |
| avg_bat_speed | bat tracking | Average bat speed on competitive swings | mph |
| swing_length | bat tracking | Distance the bat head travels from start of swing to contact | ft |
| squared_up_per_bat_contact | bat tracking | Share of contact that came close to the best possible exit velocity | 0–1 |
| whiff_per_swing | bat tracking | Share of swings that miss | 0–1 |
| avg_hit_speed | exit velocity | Average exit velocity | mph |
| ev95percent | exit velocity | Share of batted balls hit 95+ mph | % |
| brl_percent | exit velocity | Barrels per batted ball | % |
| pa | expected stats | Plate appearances | count |
| ba / est_ba | expected stats | Actual and expected batting average | rate |
| woba / est_woba | expected stats | Actual and expected wOBA (overall hitting value per plate appearance) | rate |
| gb_rate / ld_rate / fb_rate | batted ball | Ground balls / line drives / fly balls per batted ball | 0–1 |
| pull_rate | batted ball | Batted balls hit to his pull side | 0-1 |