# puntaje github

## como saber tu puntaje en github según los siguientes valores
const eventScores = {
   'PushEvent': 5,
   'CreateEvent': 4,
   'IssuesEvent': 3,
   'CommitCommentEvent': 2,
 };
 
## definimos el nombre de usuario 
const username = 'alexunjm';

## consumimos el api de github así para pintar en consola el puntaje
fetch(`https://api.github.com/users/${username}/events`).then(
   response => response.json()
 ).then(
   events =>
     console.log(
       events.map(e => e['type'])
       .map(e => eventScores[e] ? eventScores[e] : 1)
       .reduce((acc, val, i, arr) => (val ? (acc + val) : acc), 0)
     )
 )
