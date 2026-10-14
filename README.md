# Spotify Streaming Analysis — MKT 282 Data Briefing

**Does how a song sounds predict how much it gets streamed?**

OLS regression analysis on the 951 most-streamed Spotify songs of 2023.  
Course: MKT 282 Marketing Analytics | MSBA Program | Fall 2026  
Author: John Young

---

## Finding

Playlist count (log) explains **68% of the variance** in streams.  
Danceability, energy, and valence — three measures of how the song actually sounds — add **0.09%**.

The song itself barely moves the needle. Where it lands does.

---

## Files

| File | Description |
|------|-------------|
| `Spotify 2023 Top Hits.Rmd` | R notebook with full analysis |
| `Spotify 2023 Top Hits.nb.html` | Rendered notebook output |
| `spotify-2023.xlsx` | Dataset: Most Streamed Spotify Songs 2023 (Kaggle) |
| `scatter.png` | log(playlists) vs log(streams) scatterplot |
| `John_Young_Data_Briefing.pptx` | 3-slide presentation deck |

---

## Model

```
log(streams) = β₀ + β₁·log(playlists) + β₂·danceability + β₃·energy + β₄·valence
```

| Predictor | b | p | β |
|---|---|---|---|
| Spotify Playlist Count (log) | 0.672 | <.001 | .83 |
| Danceability % | 0.00003 | .986 | .00 |
| Energy % | −0.0016 | .206 | −.03 |
| Valence % | 0.0013 | .196 | .03 |

**R² = 0.680** (playlists alone: 0.6795)

---

## Data

Source: [Most Streamed Spotify Songs 2023](https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023) by Nidula Elgiriyewithana on Kaggle  
n = 951 songs after removing 2 records with corrupted stream counts

---

## Limitations

- Dataset does not distinguish Spotify-curated editorial playlists from user-created ones. Editorial placement is what labels pitch for; if the effect concentrates there, the practical implication is stronger than the headline number suggests.
- Analysis is correlational. Playlists and streams likely reinforce each other — big songs land on more playlists, which drives more streams.
- All songs are already hits. Audio features may have mattered at an earlier filtering stage not captured here (range restriction).
