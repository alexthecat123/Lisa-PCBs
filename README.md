# Lisa-PCBs
Some Apple Lisa PCBs that I've reverse-engineered.


# Introduction
Over the past few months, I've been reverse-engineering some of the PCBs in the Lisa as a fun project to both help people replace corrosion-damaged boards relatively inexpensively and to allow people to build their own Lisa expansion cards without having to track down and pay for the originals. The results of this project are these Gerber files for the Lisa 2/5 motherboard (one of the components that's most likely to be destroyed by corrosion) and the 2-port parallel card (because it's the most interesting and useful expansion card, at least in my opinion, with the Sun SCSI card coming in at a close second). One of my biggest goals with this project is to make the replicas as accurate to the originals as possible, and I think I did a pretty good job with that! See the discrepancies section below for a list of ways in which my boards deviate from the originals if you care about that sort of thing. A SCSI card is also in the works, but it's still a work in progress because I'm having to redesign it around a GAL in order to avoid infringing upon the IP of the original Sun card (which is apparently still owned by someone).

# Pictures!
Here are some photos of the motherboard and parallel card, both bare and assembled. <br>
<br>
![Bare_Motherboard_Top](https://user-images.githubusercontent.com/16897189/172883206-cae6abd1-e042-4164-8e29-cb9d3971ee05.png)
![Bare_Motherboard_Bottom](https://user-images.githubusercontent.com/16897189/172883244-cdb3ae1a-2ab9-4931-873c-7d40a472ed55.png)
![Assembled_Motherboard](https://user-images.githubusercontent.com/16897189/172883284-51a69699-856e-4d61-8dda-4509e524c964.png)
![Card_Cage](https://user-images.githubusercontent.com/16897189/172883316-df286d50-9b11-433f-a39f-1dc68a8d5838.png)
![Motherboard_Ports](https://user-images.githubusercontent.com/16897189/172883337-ba216ece-c477-4c57-bbf2-5c1df59efae8.png)
![Bare_Parallel_Top](https://user-images.githubusercontent.com/16897189/172883352-6fa80ff2-2690-42bf-ab13-1d6e448afbbc.png)
![Bare_Parallel_Bottom](https://user-images.githubusercontent.com/16897189/172883374-ea04b87c-0277-45d2-a093-49b6f7f62b67.png)
![Assembled_Parallel](https://user-images.githubusercontent.com/16897189/172883396-6df6052b-a560-4fbf-b52d-e4a501bffed8.png)


# Total Price
Using [JLCPCB](https://jlcpcb.com/), I was able to get 5 motherboards for $26.20 and 5 parallel cards for $19.20. Shipping will add to this, but not by much if you choose the really slow option. Since the minimum order quantity is 5 boards, you can just keep the others for future Lisa projects or give/sell them to others in the community who need some boards. The parts cost for the motherboard is $64.92 and the parts cost for the parallel card is $50.65, making the total cost of a motherboard $91.12 and the total cost of a parallel card $69.85. Of course, these prices will fluctuate over time, but this should give you a decent idea of how much things will cost.

# PCB Fabrication
I use [JLCPCB](https://jlcpcb.com/) for all of my boards due to the low price and high quality, but of course you can use any manufacturer that you want. There's really nothing special to say about fabricating either of these PCBs, except that you might want to select the "Gold Fingers" option in order for the edge connectors to be gold plated. This will increase the longevity of the boards and will make them look a little closer to the originals, but it also significantly increases the price and I just chose to use the standard silver fingers on my boards because of this. The silver fingers seem to be pretty durable though; I've inserted and removed these boards many times while troubleshooting stuff and they seem no worse for wear.

# Board Customization
I designed both of these boards using EasyEDA. If you want to customize the boards to your own needs, the design files for the motherboard can be found [here](https://oshwlab.com/AlexTheCat123/apple-lisa-2-5-motherboard) and the files for the parallel card can be found [here](https://oshwlab.com/AlexTheCat123/apple-lisa-2-port-parallel-card).

# Required Parts
Most of the parts needed for assembling these boards are still being made today, so I've included links to DigiKey lists for both boards, as well as a list of other parts that will need to be procured elsewhere.

## Motherboard
Most parts can be found in [this DigiKey cart](https://www.digikey.com/short/01c3fd9f), with the exception of the video output jack and the expansion slot connectors. I haven't been able to find any modern sources for these parts (I guess they were custom-made for Apple back in the 1980s), so you'll either have to omit these parts or scavenge them off a broken Lisa motherboard if you want to include them. Note that the motherboard will work fine without these parts; you just won't be able to use the composite video output or connect any expansion cards.

## Parallel Card
- Once again, most of the parts can be found in [this cart](https://www.digikey.com/short/vz0jdzf3), with three exceptions: the 74LS280s, the 6522s, and the EPROM.
- The two 74LS280s can be bought [from eBay](https://www.ebay.com/itm/152030375380?hash=item2365b76dd4:g:CXUAAOSwMj9gB0MT) and the two 6522s can also be bought from eBay, but the prices are way better if you get them [from Jameco instead](https://www.jameco.com/z/W65C22S6TPG-14-Western-Design-Center-Versatile-Interface-Adapter-via-8-Bit-I-O-Ports-14-MHz-40-Pin-PDIP-CMOS-5-Volt_2143591.html).
- If you want to save some money, you can omit all of the sockets on the DigiKey list, although this is not recommended because it makes it a huge pain to remove/replace chips in the future.
- You can use a [2716](https://www.jameco.com/z/2716-1-Major-Brands-IC-2716-1-EPROM-16K-Bit-350ns-NMOS-UV-Erasable-and-Electrically-Programmable-EPROM_40011.html) or [2732](https://www.jameco.com/z/2732-Major-Brands-IC-2732-EPROM-32K-Bit-450ns-NMOS-UV-Erasable-and-Electrically-Programmable-EPROM_40096.html) EPROM with the parallel card. It doesn't matter which one you use (the original used a 2716), but you'll need to duplicate the contents of the ROM if you use a 2732 in order to ensure that you fill up the entire contents of the EPROM.

# Assembly Notes
- Assembly of both the motherboard and parallel card should be pretty straightforward; just follow the schematic PDFs to determine which component values go where. 
- I like to start with the smallest components (resistors and capacitors) and work my way up from there, finishing up with the D-sub connectors and the card edge connectors. 
- Make sure that the edge connectors are fully seated on the board before fully soldering them in; it isn't fun to have to desolder one of those things to reseat it correctly!
- All of the unmarked holes around the mouse port on the motherboard are for the 0.01uF capacitors (see the third page of the schematic). I don't know why Apple only chose to put a silkscreen around one of those capacitors, but they did, so I did the same in my replica.
- You'll need to burn [this firmware](http://bitsavers.trailing-edge.com/bits/Apple/Lisa/firmware/341-0193-A.BIN) into your 2716 or 2732 before using the parallel card. I use a TL866 programmer for this task, but any EPROM programmer should work fine. Note that you need to duplicate the ROM contents if you're using a 2732 so that it fills up the entire 4K of the chip (just open the firmware in a hex editor, copy everything, and then paste it at the end of the file).

# Discrepancies From Actual Boards
## Motherboard
- The original board is 4 layers, but my replica is only 2 layers. I decided to do this because, while it makes the board feel a little less authentic, it decreases manufacturing costs by a pretty significant amount.
- Because my board is only 2 layers, I couldn't completely match the trace layout of the original board, so I just decided to autoroute all of the traces. So the trace layout is very different from that of the original.
- The silkscreen font isn't quite right. I couldn't find the original font that Apple used on these boards, so I settled with the closest one I could find. This causes some of the characters to look a little different, but the most noticable feature (although you probably wouldn't notice it unless you have an original board and one of my boards sitting side by side) is that, for any given font height, the width of the characters in the Apple font is slightly greater than their width in my font. If anyone knows what the original font was, be sure to let me know!
- If you don't choose the "Gold Fingers" option when fabricating your boards, the edge connectors will be silver instead of gold like the originals.
## Parallel Card
- As mentioned above with the motherboard, the silkscreen font isn't quite the same as the original Apple font.
- And once again, the edge connector fingers won't be gold plated like the originals unless you select "Gold Fingers" when fabricating your boards.
