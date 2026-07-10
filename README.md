# Attestation Anchors — Concierge Governed-Agent Platform

Append-only mirror of the platform's attestation records. The primary archive lives at
https://concierge.soloventureos.com/attestations/ — each record is hash-chained to its
predecessor and independently timestamped via RFC-3161 (freetsa.org).

This repository is the **second independent anchor**: every commit here is timestamped by
GitHub's infrastructure, giving each attestation record two unrelated clocks. Verify any
record offline:

    openssl ts -verify -data attestations/att-DATE.json -in attestations/att-DATE.tsr \
      -CAfile attestations/freetsa-cacert.pem -untrusted attestations/freetsa-tsa.crt

Records are never edited or removed. History here that disagrees with the primary archive
is itself evidence of tampering — that is the design.
