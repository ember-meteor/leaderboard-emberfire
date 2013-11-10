leaderboard-emberfire
=====================

The Meteor "Leaderboard" example implemented with EmberFire
---------------------

We use an `EmberFire.ObjectArray` to model our list of players.

    App.PlayerList = EmberFire.ObjectArray.extend({
      firebaseURI: "https://ember-meteor-leaderboard.firebaseio.com/players",

      init: function(){
        var firebase = new Firebase(this.get('firebaseURI'));
        this.set('ref', firebase);
        this._super();
      },
    });
    
An `EmberFire.ObjectArray` is an `ArrayProxy` so we can treat it just like an `Array`.

In our template we iterate over each `Player`

    <div class="leaderboard">
      {{#each player in players}}
        {{render 'player' player}}
      {{/each}}
    </div>
    
And each `Player` is an `EmberFire.Object` which is an `ObjectProxy`, which we can treat just like an `Object`.

So we just use regular handlebars binding to render values for the `Player`.

    <div class="player">
      <span class="name">{{name}}</span>
      <span class="score">{{score}}</span>
    </div>
