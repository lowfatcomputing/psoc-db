# psoc-db | psoc mappings in a triplestore for flexible querying


# usage

Start the shell:

    ./shell

Query for HC and HS bits and register offsets to set if we want to go from an HC column 97 to an HC column 8 in an adjacent DSI:

    SELECT * WHERE { ?hc0 a <:hc> . ?hc0 <:v> "8" . ?hc1 a <:hc> . ?hc1 <:v> "97" . ?hc0 <:h> ?h . ?hc1 <:h> ?h . ?hs a <:hs> . ?hc0 <:bit> ?hc0_bit . ?hc0 <:offset> ?hc0_offset . ?hc1 <:bit> ?hc1_bit . ?hc1 <:offset> ?hc1_offset . ?hs <:h> ?h . ?hs <:bit> ?hs_bit . ?hs <:offset> ?offset . ?hs <:direction> "-1" . }

The results:

    ?hc0                 ?hc1                ?h   ?hs                 ?hc0_bit  ?hc0_offset  ?hc1_bit  ?hc1_offset  ?hs_bit  ?offset
    _:b10861e00000000c1  _:b2891e0000000089  "1"  _:b8a1e0000000082   "0"       "0x08"       "0"       "0x64"       "0"      "0x98"
    _:b10861e00000000c2  _:b2891e000000008a  "4"  _:b18a1e0000000085  "1"       "0x08"       "1"       "0x64"       "1"      "0x98"


# contact

I'm Andreas Wagner, you can ping me (pointfree) on freenode.
