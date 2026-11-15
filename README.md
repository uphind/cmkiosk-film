# cmkiosk-film

The background film of the Montenegro consulate kiosk (cmkiosk.vercel.app), cut losslessly into HLS pieces
(H.264 1080p30 + AAC, ~6 s each) so every piece fits GitHub and Vercel. Served at
`https://cmkiosk-film.vercel.app/film/v1/index.m3u8`. A new cut of the film goes in a new folder (`film/v2`), since the
pieces are cached forever.

    ffmpeg -i "Video of Montenegro.mp4" -map 0:v:0 -map 0:a:0 -c copy -f hls -hls_time 6 -hls_playlist_type vod \
      -hls_segment_filename "film/v1/seg%04d.ts" film/v1/index.m3u8
