# psoc-db | psoc mappings in a triplestore for flexible querying


# usage

Start the shell:

    ./shell

Query for possible HC, HV, and HS bits and register offsets to set if we want to go from an HC column 97 to an HC column 8 in an adjacent DSI:

    SELECT * WHERE { ?hc0 a <:hc> . ?hc0 <:v> "8" . ?hc1 a <:hc> . ?hc1 <:v> "97" . ?hc0 <:h> ?h . ?hc1 <:h> ?h . ?hs a <:hs> . ?hv a <:hv> . ?hv <:checker> <:B> . ?hv <:h> ?h . ?hc0 <:bit> ?hc0_bit . ?hc0 <:offset> ?hc0_offset . ?hc1 <:bit> ?hc1_bit . ?hc1 <:offset> ?hc1_offset . ?hs <:h> ?h . ?hs <:bit> ?hs_bit . ?hs <:offset> ?hs_offset . ?hs <:direction> "-1" . ?hv <:bit> ?hv_bit . ?hv <:offset> ?hv_offset . ?hv <:direction> "-1" . }

The results:

    ?hc0                 ?hc1                ?h   ?hs                 ?hv                  ?hc0_bit  ?hc0_offset  ?hc1_bit  ?hc1_offset  ?hs_bit  ?hs_offset  ?hv_bit  ?hv_offset
    _:b10861e00000000c1  _:b2891e0000000089  "1"  _:b8a1e0000000082   _:b1c841e00000000f1  "0"       "0x08"       "0"       "0x64"       "0"      "0x98"      "0"      "0x84"
    _:b10861e00000000c2  _:b2891e000000008a  "4"  _:b18a1e0000000085  _:b14841e00000000d3  "1"       "0x08"       "1"       "0x64"       "1"      "0x98"      "1"      "0x80"
    _:b10861e00000000c2  _:b2891e000000008a  "4"  _:b18a1e0000000085  _:b16841e00000000db  "1"       "0x08"       "1"       "0x64"       "1"      "0x98"      "1"      "0x80"
    _:b10861e00000000c2  _:b2891e000000008a  "4"  _:b18a1e0000000085  _:b14841e00000000d3  "1"       "0x08"       "1"       "0x64"       "1"      "0x98"      "1"      "0x80"
    _:b10861e00000000c2  _:b2891e000000008a  "4"  _:b18a1e0000000085  _:b16841e00000000db  "1"       "0x08"       "1"       "0x64"       "1"      "0x98"      "1"      "0x80"

Plug any of these configurations into [sample config #1](https://github.com/azonenberg/openfpga/wiki/UDB-%26-Routing-Examples#sample-config-1-route-from-portpin-62-to-portpin-21-blue-led-through-two-dsi-tiles) and the blue led will light up.

# contact

I'm Andreas Wagner, you can ping me (pointfree) on freenode.
