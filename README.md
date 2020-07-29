# MovieLens-API
Node Js based API to fetch data from MovieLens
Installing

# Using yarn

$ yarn add movielens
Using npm

$ npm install --save movielens
# Methods

login(email, password)

Logs you into your account and returns a Promise containing your cookie (yeah yeah I know, but that the only way movielens authorizes your requests).

const movielens = require('movielens');

movielens.login('your@email.com', 'password')
  .then(function(cookie) {
    console.log('tada', cookie);
  })
  .catch(function(err) {
    console.error(err);
  });
# getMe(cookie)

Gets your user information such as: Number of Ratings, Email, User Name, Preferences, and Recommender Type.

# getGenres(cookie)

Gets the list of move genres and the top(?) tags in those genres.

# getMyTags(cookie)

Gets the tags you have made.

const movielens = require('movielens');

movielens.getMe(cookie)
  .then(function(data) {
    console.log('tada', data);
  })
  .catch(function(err) {
    console.error(err);
  });
# rate(cookie, movieId, rating)

 Rate a movie.

const movielens = require('movielens');

// give "The Shawshank Redemption" 5 stars
movielens.rate(cookie, 318, 5)
  .then(function(data) {
    console.log('tada', data);
  })
  .catch(function(err) {
    console.error(err);
  });
# hide(cookie, movieId)

 Hide a movie.

unhide(cookie, movieId)

Unhide a movie.

# addToWishlist(cookie, movieId)

Add a movie to your wishlist.

removeFromWishlist(cookie, movieId)

Remove a movie from your wishlist.

# explore(cookie, params)

explore() is the query engine to search for movies.

const movielens = require('movielens');

// Get movies acted by 'tom hardy' which I've rated
// 6 results found
var params = {
  actors: 'tom hardy',
  hasRated: 'yes'
}

movielens.explore(cookie, params)
  .then(function(data) {
    console.log('tada', data);
  })
  .catch(function(err) {
    console.error(err);
  });
params references:


# List of languages I've found, there may be more.

Afrikaans      afrikaans
Albanian       shqip
Arabic         العربية
Bambara        bamanankan
Bengali        বাংলা
Bosnian        босански
Bulgarian      български език
Catalan        català
Croatian       hrvatski
Czech          český
Danish         dansk
Dutch          nederlands
English        english
Estonian       eesti
Finnish        suomi
French         français
Galician       galego
Georgian       ქართული
German         deutsch
Greek          ελληνικά
Hebrew         עִבְרִית
Hindi          हिन्दी
Hungarian      magyar
Icelandic      íslenska
Indonesian     bahasa indonesia
Irish          gaeilge
Italian        italiano
Japanese       日本語
Latin          latin
Mandarin       普通话
Norwegian      norsk
Pashto         پښتو
Polish         polski
Portuguese     português
Punjabi        ਪੰਜਾਬੀ
Romanian       română
Russian        pусский
Slovak         slovenčina
Spanish        español
Swahili        kiswahili
Swedish        svenska
Tamil          தமிழ்
Telugu         తెలుగు
Thai           ภาษาไทย
Turkish        türkçe
Ukrainian      український
Urdu           اردو
Vietnamese     tiếng%20việt
Welsh          cymraeg
Wolof          wolof
# Various explore() Shortcut Methods

topPicks(cookie, params)

Your top picks

{
  hasRated: 'no',
  sortBy: 'prediction'
}
recentReleases(cookie, params)

# Recently released movies.

{
  hasRated: 'no',
  maxDaysAgo: 90,
  maxFutureDays: 0,
  sortBy: 'releaseDate'
}
favoritesYear(cookie, params)

# Favorites within the last year.

{
  hasRated: 'no',
  maxDaysAgo: 365,
  maxFutureDays: 0,
  minPop: 100,
  sortBy: 'avgRating'
}
newAdditions(cookie, params)

# The movies most recently added to MovieLens.

{
  sortBy: 'dateAdded'
}
getMyRatings(cookie, params)

# Movies which you've rated.

{
  hasRated: 'yes',
  sortBy: 'userRatedDate'
}
getMyWishlist(cookie, params)

# Movies in your wishlist.

{
  hasWishlisted: 'yes',
  sortBy: 'userListedDate'
}
getMyHiddenMovies(cookie, params)

# Movies you've hidden.

{
  hasHidden: 'yes'
}
