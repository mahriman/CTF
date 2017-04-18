# tw-gr-e1-art unintended solution
# tw-gr-e2-eotds unintended solution
# tw-gr-e3-gtl unintended solution
# tw-gr-e4-stw unintended solution

Having completed Toaster Wars 2-4 the exact same way I completed Toaster Wars 1, I suspected I had found an unintended solution.
Reporting it privately via the Piazza platform confirmed that they indeed had fucked up and granted me a t-shirt (yay!). 
PicoCTF admins were kind enough to let our team keep the points (tw-gr-e4-stw firsts!) from completing the challenges and quickly fixed the issue.

The solution? Grab each challenge **start.sh** from the webroot:

## tw-gr-e1-art
`#!/bin/sh`

`PICO_CTF_FLAG="at_least_the_world_wasnt_destroyed_by_a_meteor_842aea1de69aa7c4069e8aae8815d22b" MONGO_USER="rogue" MONGO_PASS="<censored>"  node server/serv.js --port=55830`


## tw-gr-e2-eotds
`#!/bin/sh`

`PICO_CTF_FLAG="i_dont_want_to_say_goodbye__gets_me_every_time_4ea52e1f6e60b37e759a8134d66bd295" MONGO_USER="rogue" MONGO_PASS="<censored>" node server/serv.js --port=28933`


## tw-gr-e3-gtl
`#!/bin/sh`

`PICO_CTF_FLAG="the_new_feature_where_you_manage_your_own_shelf_in_the_refrigerator_was_an_interesting_addition_f2c608019200816f3768b36f56951e47" MONGO_USER="rogue" MONGO_PASS="<censored>" node server/serv.js --port=62261`

## tw-gr-e4-stw
`#!/bin/sh`

`PICO_CTF_FLAG="im_still_upset_you_dont_get_to_keep_the_cute_scarves_in_the_postgame_a44703668b068b3fa9a7a83a8f466ace" MONGO_USER="rogue" MONGO_PASS="<censored>" node server/serv.js --port=9846`
