from flask import Flask, render_template, request
import spotipy
from spotipy.oauth2 import SpotifyClientCredentials

app = Flask(__name__)

sp = spotipy.Spotify(auth_manager=SpotifyClientCredentials(client_id="5ef3272dcd5e49598a655deb26b81aeb", client_secret="f6b712b3f7c1407396dc3cc2ed9f0e5f"))

@app.route('/', methods=['GET', 'POST'])
def search_artist():
    if request.method == 'POST':
        artist_name = request.form.get('artist_name')
        artist_search = sp.search(artist_name, type='artist')['artists']['items'][0]
        new_features = artist_features(artist_search)
        return render_template('display.html', features=new_features) # display.html should be a template showing your features
    return render_template('search.html') # search.html should be a form where users can enter an artist name

if __name__ == '__main__':
    app.run(debug=True)
