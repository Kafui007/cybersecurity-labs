# Lab 07 — Conducting a simulated phishing attack

A controlled phishing simulation: build a lookalike login page, host it through a
tunnel, send the link to participants who were briefed about the experiment, and
see who opens it. Run only in a lab or with explicit consent — never against real
users without authorisation.

## Setup

```bash
git clone https://github.com/techchipnet/CamPhish
cd CamPhish
./camphish
```

Choose a tunnel service when prompted (the lab used Surfshark's tunnel option, then
ngrok). To run ngrok in a second terminal:

```bash
snap install ngrok
ngrok config add-authtoken <token>
ngrok http 80
```

Pick ngrok as the tunnel server in CamPhish. The service comes up and ngrok gives
you a public URL — that is the link to send to the participants.

## The simulation

The link was sent by email to the selected participants (people briefed about the
experiment in advance). When a participant opens the link, the simulation records
the visit — in the full CamPhish flow, a camera-access prompt can also be presented.

## How to avoid phishing scams

1. Identify available training resources and train employees how to spot phishing.
2. Alert employees to the risks.
3. Develop a culture of awareness.

## Takeaway

The whole attack takes minutes to set up and costs nothing — that is the point of
the exercise. The defence is not a product, it is people who recognise the trick:
check the URL, treat unexpected links with suspicion, and report instead of
clicking.
