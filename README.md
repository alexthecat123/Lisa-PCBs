# Lisa-PCBs
Some Apple Lisa PCBs that I've reverse-engineered.


# Introduction
Over the past few months, I've been reverse-engineering some of the PCBs in the Lisa as a fun project to both help people replace corrosion-damaged boards relatively inexpensively and to allow people to build their own Lisa expansion cards without having to track down and pay for the originals. The results of this project are these Gerber files for the Lisa 2/5 I/O board, the 2/5 motherboard, and the 2-port parallel card. One of my biggest goals with this project is to make the replicas as accurate to the originals as possible, and I think I did a pretty good job with that! See the discrepancies section below for a list of ways in which my boards deviate from the originals if you care about that sort of thing. I've also created a custom GAL-based SCSI card for the Lisa that allows you to reprogram the ROM without removing it from the Lisa, which you can find [here](https://github.com/alexthecat123/Lisa-GALSCSI-Card) if you're interested.

# Pictures!
Here are some photos of the boards, both bare and assembled. Note that the motherboard and parallel card pictures are from an older revision where the silkscreen fonts don't quite match the original boards; rest assured that the Gerbers in this repository are up to date with the correct font. Also ignore the different font on the C38 silkscreen on the I/O board; this has also been fixed in the Gerbers. <br>
<br>
![IMG_6337](https://user-images.githubusercontent.com/16897189/195627724-df5e833d-c739-4e7c-9901-fa37a2edce23.jpeg)
![IMG_6338](https://user-images.githubusercontent.com/16897189/195627810-ae8123fb-86e2-4cb2-98c1-a8180b7091f2.jpeg)
![IMG_6339](https://user-images.githubusercontent.com/16897189/195627861-0bf1ce6c-73c0-4383-9fb3-f1dbe8cc8e8f.jpeg)
![Bare_Motherboard_Top](https://user-images.githubusercontent.com/16897189/172883206-cae6abd1-e042-4164-8e29-cb9d3971ee05.png)
![Bare_Motherboard_Bottom](https://user-images.githubusercontent.com/16897189/172883244-cdb3ae1a-2ab9-4931-873c-7d40a472ed55.png)
![Assembled_Motherboard](https://user-images.githubusercontent.com/16897189/172883284-51a69699-856e-4d61-8dda-4509e524c964.png)
![Card_Cage](https://user-images.githubusercontent.com/16897189/172883316-df286d50-9b11-433f-a39f-1dc68a8d5838.png)
![Motherboard_Ports](https://user-images.githubusercontent.com/16897189/172883337-ba216ece-c477-4c57-bbf2-5c1df59efae8.png)
![Bare_Parallel_Top](https://user-images.githubusercontent.com/16897189/172883352-6fa80ff2-2690-42bf-ab13-1d6e448afbbc.png)
![Bare_Parallel_Bottom](https://user-images.githubusercontent.com/16897189/172883374-ea04b87c-0277-45d2-a093-49b6f7f62b67.png)
![Assembled_Parallel](https://user-images.githubusercontent.com/16897189/172883396-6df6052b-a560-4fbf-b52d-e4a501bffed8.png)


# Total Price
Using [JLCPCB](https://jlcpcb.com/), I was able to get 5 I/O boards for $35.41, 5 motherboards for $26.20, and 5 parallel cards for $19.20. Shipping will add to this, but not by much if you choose the really slow option. Since the minimum order quantity is 5 boards, you can just keep the others for future Lisa projects or give/sell them to others in the community who need some boards. The parts cost for the I/O board is $215.67, the parts cost fot the motherboard is $64.92, and the parts cost for the parallel card is $50.65, making the total cost of an I/O board $251.08, the total cost of a motherboard $91.12, and the total cost of a parallel card $69.85. Of course, these prices will fluctuate over time, but this should give you a decent idea of how much things will cost. If you choose to reuse most of the weird and hard to find chips from your old and broken I/O board like I did, you can get your I/O board parts cost down to around $100, so I would highly recommend doing this!

# PCB Fabrication
I use [JLCPCB](https://jlcpcb.com/) for all of my boards due to the low price and high quality, but of course you can use any manufacturer that you want. There's really nothing special to say about fabricating any of these PCBs, except that you might want to select the "Gold Fingers" option in order for the edge connectors to be gold plated. This will increase the longevity of the boards and will make them look a little closer to the originals, but it also significantly increases the price and I just chose to use the standard silver fingers on my boards because of this. The silver fingers seem to be pretty durable though; I've inserted and removed these boards many times while troubleshooting stuff and they seem no worse for wear.

# Board Customization
I designed all three of these boards using EasyEDA. If you want to customize the boards to your own needs, the design files for the I/O board can be found [here](https://oshwlab.com/alexthecat123/lisa-2-5-i-o-board), the files for the motherboard can be found [here](https://oshwlab.com/AlexTheCat123/apple-lisa-2-5-motherboard), and the files for the parallel card can be found [here](https://oshwlab.com/AlexTheCat123/apple-lisa-2-port-parallel-card).

# Required Parts
Many of the parts needed for assembling these boards are still being made today, so I've included links to DigiKey lists for all of the boards, as well as a list of other parts that will need to be procured elsewhere.

## I/O Board
Pretty much all of the non-IC parts can be found in [this DigiKey cart](https://www.digikey.com/short/7p1cb5rw) and most of the standard TTL chips can be procured from Jameco (see the .csv file in this repository). Unfortunately, there doesn't seem to be a way to provide a link to a Jameco cart, so the csv file will have to do. Everything else will need to be ordered from eBay. A list of these parts follows.
- 1x 6504 CPU
- 1x 74LS323
- 1x 74C174
- 2x 6522 VIA
- 1x 8530 SCC
- 2x 74LS280
- 1x 26LS30
- 1x 26LS32
- 1x 8T97
- 1x MAX4193
- 1x 4011B
- 2x 2N4258 <br>

The COP and the PROM at U4B can be most easily procured by stealing them from your old nonfunctional I/O board, but there are some other options too if you don't feel like doing that or if they're defective. The PROM is a 6309, so you can just buy one of those or an equivalent and burn it with the ROM image found [here on Bitsavers](http://bitsavers.trailing-edge.com/bits/Apple/Lisa/firmware/342-0172A_IO_28L22_U48.BIN). The COP can be replaced with [this neat adapter designed by Patrick Schafer](http://john.ccac.rwth-aachen.de:8000/patrick/COPSreader.htm#emulator) that allows you to use a COP402 or the KR1820VE1A Russian equivalent along with an external ROM to emulate the original COP.

## Motherboard
Most parts can be found in [this DigiKey cart](https://www.digikey.com/short/01c3fd9f), with the exception of the video output jack and the expansion slot connectors. The expansion slot connectors appear to be a custom Apple design, so we'll probably never be able to find a modern replacement for those, but there might be some hope for the video jack. Looking on Digikey, [this](https://www.digikey.co.uk/en/products/detail/keystone-electronics/902/317243) appears to be the correct part, but it seems like you have to get a quote from the manufacturer in order to get one. That's more effort than I would want to put in, but if you really want a video jack, that could be an option. Note that the motherboard will work fine without these parts; you just won't be able to use the composite video output or connect any expansion cards.

## Parallel Card
- Once again, most of the parts can be found in [this cart](https://www.digikey.com/short/vz0jdzf3), with three exceptions: the 74LS280s, the 6522s, and the EPROM.
- The two 74LS280s can be bought [from eBay](https://www.ebay.com/itm/152030375380?hash=item2365b76dd4:g:CXUAAOSwMj9gB0MT) and the two 6522s can also be bought from eBay, but the prices are way better if you get them [from Jameco instead](https://www.jameco.com/z/W65C22S6TPG-14-Western-Design-Center-Versatile-Interface-Adapter-via-8-Bit-I-O-Ports-14-MHz-40-Pin-PDIP-CMOS-5-Volt_2143591.html).
- If you want to save some money, you can omit all of the sockets on the DigiKey list, although this is not recommended because it makes it a huge pain to remove/replace chips in the future.
- You can use a [2716](https://www.jameco.com/z/2716-1-Major-Brands-IC-2716-1-EPROM-16K-Bit-350ns-NMOS-UV-Erasable-and-Electrically-Programmable-EPROM_40011.html) or [2732](https://www.jameco.com/z/2732-Major-Brands-IC-2732-EPROM-32K-Bit-450ns-NMOS-UV-Erasable-and-Electrically-Programmable-EPROM_40096.html) EPROM with the parallel card. It doesn't matter which one you use (the original used a 2716), but you'll need to duplicate the contents of the ROM if you use a 2732 in order to ensure that you fill up the entire contents of the EPROM.

# Assembly Notes

## I/O Board
- All of the bodge wires are integrated into this design, so you don't have to worry about any of that!
- The I/O board is by far the most complicated to assemble out of these three boards. Most of the parts are pretty self-explanatory; just follow the EasyEDA schematic to make sure that you're installing everything in the right places. There are, however, quite a few confusing parts that I need to go over. And who knows, there might be a few notes that I'm completely forgetting about, so send me an email if you're ever confused about something.
- Substitute the 2SA1859 transistor for the MPS-U51s at Q3 and Q6. Also, substitute the 2SC4883 for the MPS-U01 at Q4. When installing these transistors, ensure that the side of the transistor with the part number written on it is facing towards the top of the board. Also, the pinouts of these transistors are different than those of the originals, so cross the center and right leads when installing them.
- The 2114 RAM chips should be installed in place of the 444C-3 chips at U1B and U2B.
- I couldn't find a 3-pin version of C36, so the new capacitor only has two pins. Solder it between the center and righthand pads of the footprint, leaving the lefthand pad empty.
- Install the 8T97 at U2F, despite the silkscreen insisting that it's supposed to be an LS367. Installing the LS367 can lead to really perplexing problems with the floppy disk controller, so don't do that!
- No parts should be installed in D1, R29, R30, R33, and Q10. Unless you have a Lisa 1, the same holds true for R41 and R47.
- Despite having no silkscreens, the two pads to the bottom-right of L1 and the two pads immediately below C36 are C13 and C37, respectively.
- The 1N5819 can be substituted in place of the ERA81 for D3.
- The "6.2V Zener" specified on the schematic for D8 is actually the 1N5234.
- C55 doesn't actually have a footprint on the board; just solder it straight to pins 6 and 10 of the LS244 at U4F.
- The EPROM at U1A will need to be programmed with the appropriate I/O board ROM. There are three versions: the Twiggy version, the 400K Sony version, and the 800K Sony version. All of these can be found [on BitSavers](http://bitsavers.trailing-edge.com/bits/Apple/Lisa/firmware/).
- The contrast latch resistor ladder at RP3 seems to be a custom Apple part, so you'll have to make your own unless you want to steal one from your original board. That's what the 10K, 22K, 40.2K, 80.6K, 160K, and 324K resistors in the DigiKey cart are for. They don't need to be 1% tolerance, but I chose to do that so that they're easy to differentiate from all of the other resistors on the board. It's a little hard to describe how to make the ladder, so here's a picture instead. Note that the bottommost hole of the footprint is empty; only the top seven pads are used.
![IMG_6340](https://user-images.githubusercontent.com/16897189/195641913-c29db223-03d9-4e78-b1dd-7e19a2a79524.jpeg)


## Motherboard and Parallel Card
- Assembly of both the motherboard and parallel card should be pretty straightforward; just follow the schematic PDFs to determine which component values go where. 
- I like to start with the smallest components (resistors and capacitors) and work my way up from there, finishing up with the D-sub connectors and the card edge connectors. 
- Make sure that the edge connectors are fully seated on the board before fully soldering them in; it isn't fun to have to desolder one of those things to reseat it correctly!
- All of the unmarked holes around the mouse port on the motherboard are for the 0.01uF capacitors (see the third page of the schematic). I don't know why Apple only chose to put a silkscreen around one of those capacitors, but they did, so I did the same in my replica.
- You'll need to burn [this firmware](http://bitsavers.trailing-edge.com/bits/Apple/Lisa/firmware/341-0193-A.BIN) into your 2716 or 2732 before using the parallel card. I use a TL866 programmer for this task, but any EPROM programmer should work fine. Note that you need to duplicate the ROM contents if you're using a 2732 so that it fills up the entire 4K of the chip (just open the firmware in a hex editor, copy everything, and then paste it at the end of the file).

## 3D-Printed Motherboard Mount
If you're building yourself a DIY Lisa and don't have a motherboard tray for your motherboard, download and 3D-print the STL file in the 3D folder to make a nice little stand for your Lisa. It even has mounting holes for an RGBtoHDMI! Thanks to Andrew Diller for designing this!

# Discrepancies From Actual Boards
## I/O Board
- I haven't tested any of the battery circuitry, so I'm not sure if it actually works. But the rest of the board works just fine, so chances are the battery stuff does too.
- All of the traces are autorouted, so they don't match the layout of the original traces. I might manually route them later, but I'm not sure if I'll ever get around to it.
- If you don't choose the "Gold Fingers" option when fabricating your boards, the edge connectors will be silver instead of gold like the originals.

## Motherboard
- The original board is 4 layers, but my replica is only 2 layers. I decided to do this because, while it makes the board feel a little less authentic, it decreases manufacturing costs by a pretty significant amount.
- Because my board is only 2 layers, I couldn't completely match the trace layout of the original board, so I just decided to autoroute all of the traces. So the trace layout is very different from that of the original.
- If you don't choose the "Gold Fingers" option when fabricating your boards, the edge connectors will be silver instead of gold like the originals.

## Parallel Card
- Once again, the edge connector fingers won't be gold plated like the originals unless you select "Gold Fingers" when fabricating your boards.

# Changelog
- 6/8/22  - Initial release of motherboard and parallel card.
- 10/2/22 - Updated the fonts on the motherboard and parallel card to match the original boards' fonts. Also increased the size of the Apple logos and added the "13" silkscreen to the upper port of the parallel card to make the boards a little more accurate to the originals.
- 10/13/22 - Initial release of the 2/5 I/O board.
- 3/2/23 - Updated the readme to provide alternatives to stealing the COP, floppy controller PROM, and video output jack from your old boards.
- 8/2/23 - It turns out that I was dumb and I somehow reversed the two RAM slot footprints on the motherboard. So the slot labeled MEM 1 was actually addressed by the CPU board as if it was MEM 2 and vice versa. This didn't affect normal functionality, but it did cause the Lisa to report the wrong board being bad in the event of a memory error. Thanks to DosFox for finally discovering this issue and letting me know so that I could fix it!
- 1/5/25 - Added STL files for a 3D-printed 2/5 motherboard holder. Thanks to Andrew Diller for designing it and submitting a pull request!
