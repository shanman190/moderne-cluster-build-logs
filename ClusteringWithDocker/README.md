### Clustering build logs to analyse common build issues

# Docker

* build the image using `docker build -t cluster_logs . `
* run the container using `docker run --rm -it --entrypoint bash cluster_logs`

# Start LLM server

Run in the terminal `nohup ./server -m "codellama.gguf" -c 8000 --port "8080" &` 
`nohup` and `&` keeps the process running in the background, although I recommend running the process in the foreground first to make sure it is set up correctly, and then stopping using `Ctrl+C` and starting it again with `nohup` and `&`. You might need to enter `enter` after running `nohup` to be able to keep running other commands.


# Run clustering
Run in order
01.load_logs.py
02.generate_summaries_from_logs.py // this step will take the longest time
03.embed_summaries_and_cluster.py
04.cluster_summaries_results.py