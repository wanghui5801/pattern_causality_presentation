# Presentation for pattern causality

This presentation is based on Observable.js, Echarts.js, D3.js and shiny, before starting to run it, we need to make some preparations.

- Download the [Quarto](https://quarto.org/).
- Download the [R](https://www.r-project.org/)
- Install the required R packages, including `shiny`, `deSolve`, `tidyr`, `dplyr`, `patterncausality`

```R
install.packages(c("shiny", "deSolve", "tidyr", "dplyr", "patterncausality"))
```

## Start the presentation on Linux server

On Linux, we usually use the `systemctl` daemon to manage the Quarto service.

We need to download the files at first.

```shell
git clone https://github.com/wanghui5801/pattern_causality_presentation.git
```

Then add the configuration file

```shell
sudo nano /etc/systemd/system/quarto_presentation.service
```

The content is as follows:

```shell
[Unit]
Description=Quarto_Server
After=network.target

[Service]
# Your user name, usually could be got by $USER
User=
# The path of pattern_causality_presentation folder
WorkingDirectory= 
# The path of quarto + "quarto serve presentation.qmd --host 0.0.0.0 --port xxx" you can define the port here
ExecStart=
Restart=always
RestartSec=10
Environment="PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

[Install]
WantedBy=multi-user.target
```

Then update and start the `systemctl` sevice.

```shell
sudo systemctl daemon-reload
sudo systemctl start quarto_presentation.service
sudo systemctl enable quarto_presentation.service # Start automatically at boot
sudo systemctl status quarto_presentation.service # Check the status of service
```

Now the quarto server is running on `http://ip:port`

## Start the server on Windows or Mac

It would be easy to run after installing the necessary dependencies by the following code.

```shell
git clone https://github.com/wanghui5801/pattern_causality_presentation.git
cd pattern_causality_presentation
quarto serve presentation.qmd
```

Relevant information will be presented below.