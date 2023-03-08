# html-css-js-project-boilerplate

const apiFetch = async () => {
  const result = await fetch(
    "https://api.napster.com/v2.1/tracks/top?apikey=ZTk2YjY4MjMtMDAzYy00MTg4LWE2MjYtZDIzNjJmMmM0YTdm"
  );
  const data = await result.json();
  const list = document.getElementById("music_list");
  const an = document.getElementById("structure");
  music_list = data?.tracks;
  console.log(music_list);
  data?.tracks?.forEach((item, index) => {
    const child = document.createElement("div");
    child.className = "musicListDiv";
    const img = document.createElement("img");
    const songname = document.createElement("h3");
    const arname = document.createElement("h5");
    songname.innerText = item.name;
    arname.innerText = item.artistName;
    child.appendChild(img);
    child.appendChild(songname);
    child.appendChild(arname);
    child.onclick = () => {
      track_index = index;
      now_playing.innerText = item.name;
      audioPlay(item.previewURL)
    };

    an.appendChild(child);
    list.appendChild(child);
  });
  previewData = data.tracks[0].previewURL;
};


This is a JavaScript function that fetches music data from an API.
It creates HTML elements to display the fetched data, including song name and artist name.
It sets an onclick event on each element to play the corresponding preview of the song.
It appends each element to a parent container element in the HTML document.
It assigns the first song's preview URL to a global variable.
It uses the optional chaining operator to prevent errors if there is no data returned from the API.
It uses async/await syntax to handle the asynchronous fetch and JSON parsing.
It logs the fetched music data to the console for debugging purposes.
It assumes the existence of HTML elements with the IDs "music_list" and "structure".
It uses an API key to authenticate the API request.
