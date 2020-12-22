# leaderboard

#there will be point table which is going to look like this
<Int> user_id, <Int> amount, <Timestamp> created_at

#every time user do something in the game just add it with the date, something like this
select sum(amount) from Points where user_id = ? and created_at >= "2020-03-01"

#the schema for the table of points will look somethung like this
CREATE TABLE `user_points` (
 `id` int(10) unsigned NOT NULL,
 `user_id` int(11) NOT NULL,
 `amount` int(11) NOT NULL,
 `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP
) ENGINE=MyISAM DEFAULT CHARSET=utf8;

#mysql
select user_id, sum(amount) as score from user_points group by user_id order by score desc

CODE
// lets assume $rows contains the resultset from the query above
foreach ($row in $rows)
  storeInLeaderboard($row->user_id, $row->score);
endforeach
// the helper function goes like this
function storeInLeaderboard(userId, score) {
  $anjaliagni>anjali("leaderboard", score, userId)
}



