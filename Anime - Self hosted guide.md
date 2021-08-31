<iframe width="1280" height="720" src="https://www.youtube.com/embed/9UfKcrxfZeI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Root Folder Structure

data
	/anime
		/anime-tv
		/anime-movies
	/downloads
		/anime-tv
		/anime-movies
	

	For hardlinks download and anime must be in the same under the same root volume
	
	Generally you can use docker config to map /data on the containers to your root data folder 

DHCP Reservations & Static IP Address

	Either reserve your IP address on your router or set a static IP address on the host machine. It can be incredibly frustrating to troubleshoot when an IP adress changess due to a power outage or similar events
	
	[[Windows Settings - Static IP Address]]
	[[Powershell - Static IP Address]]
	[[Static IP Address (unraid)]]

Torrent Clients

	Be sure to port forward on your router and verify port connectivity from the internet
	
	qBittorrent is my recommended/favorite
		Create Catagories for Anime-tv & Anime-movies
	RuTorrent typically on seedboxes
	Deluge uses the same libraries as RuTorrent

Prowlarr

	Recently been replacing jackett with Prowlarr. Works great most of time.
	
Radarr
	
	Create a duplicate instance after the app installed
	
Sonarr

	Monitor and Search for Shows easily

	Run multiple instances by changing the port maps
	
- misc
- https://youtu.be/h9j89L8eQQk
	- video on banding