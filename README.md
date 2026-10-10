# FabricOps

A read-only dashboard for Arista CloudVision and EOS eAPI fabric validation, reports, and interactive topology views.

## Start on your computer

Download `FabricOps_shareable.zip` from this repository and extract it. Install Python 3.11 or newer and open the extracted FabricOps folder. On macOS or Linux, run `bash start.sh`. On Windows, double-click `start.bat`.

Or start manually from the FabricOps folder:

```bash
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

Open http://localhost:8501 after the server starts.

## Connect your own network

The CloudVision address and credentials start blank. Enter your own CloudVision URL, username, and password. Enter EOS/eAPI credentials if they differ. The computer running FabricOps must be able to reach CloudVision and the switches, directly or through your VPN. For self-signed lab certificates, certificate verification can be disabled in the connection form.

Passwords are held in server memory for the current session, not written to disk by the app. Use Clear session to remove the current session's connection details and results. Topology layouts are saved in the user's browser. Reports are downloaded only when requested.

## Share with other users

Share this ZIP so each person can run FabricOps against their own network. No personal network address or saved credentials are included.

For a hosted Streamlit deployment, use `app.py` as the entry point and `requirements.txt` for dependencies. This is a Python server application; GitHub Pages cannot run it. A hosted server must have network access to each network it checks. A public server cannot directly reach private network addresses behind users' routers or VPNs.

## Docker

```bash
docker build -t fabricops .
docker run --rm -p 8501:8501 fabricops
```

Open http://localhost:8501. The container must be able to reach your network.

## Features

- CloudVision inventory and live EOS/eAPI checks
- Health findings and recommendations
- HTML and JSON reports
- Interactive topology with browser-local layouts
- MLAG evidence detection

Checks use read-only show commands. FabricOps does not deploy switch configurations.
