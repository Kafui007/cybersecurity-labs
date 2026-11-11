# Lab 09 — Distinction between WEP, WPA, WPA2 and WPA3

## WEP — Wired Equivalent Privacy (1997)

Created to secure wireless networks with access control and encryption comparable
to wired networks. It relied on shared-key authentication and the flawed RC4
encryption, and hackers quickly broke it. Easy to use and widely adopted at first,
but its inherent vulnerabilities overwhelmed its advantages — and it was abandoned.

## WPA — Wi-Fi Protected Access (2003)

Replaced WEP, fixing its worst problems with TKIP (Temporal Key Integrity
Protocol) for better integrity checks and key management. WPA-Personal is for home
networks; WPA-Enterprise uses a RADIUS server in commercial settings. More secure
than WEP with 128-bit encryption, but weaker than WPA2, with possible
compatibility problems — and some implementations needed hardware changes.

## WPA2 — Wi-Fi Protected Access II (2004)

The most widely used wireless security standard. Uses AES encryption, is far less
vulnerable than WPA, and is the industry standard, so device compatibility is
broad. Weaknesses exist — notably the KRACK (key reinstallation) attack — and
older hardware may not support it, but WPA2 remains essential for wireless
security.

## WPA3 — Wi-Fi Protected Access III (2018)

The current standard. Adds Wi-Fi Easy Connect for simpler device setup, stronger
encryption, and defence against dictionary brute-force attacks. Three variants:
WPA3-Personal (home), WPA3-Enterprise (business), and Wi-Fi Enhanced Open (open
networks). Adoption is still gradual — setup can be complex and old hardware may
not support it.

## The most secure: WPA3

- **Improved security:** individual encryption keys per device make interception
  and decryption far harder than under WPA2.
- **Protection against password brute-force attacks:** the Dragonfly mechanism
  (SAE — Simultaneous Authentication of Equals) uses unique pseudo-random features
  that make offline guessing attacks much more difficult.
- **Secure access to public networks:** Enhanced Open encrypts traffic even on
  networks without a password.
- **Advanced authentication:** SAE replaces the pre-shared-key handshake with a
  more secure, attack-resistant authentication process.
