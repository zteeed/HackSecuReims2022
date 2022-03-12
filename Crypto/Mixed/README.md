# Mixed - 100 points
Le texte est encodé en utilisant différentes bases:
	- du binaire qu'on va détecter grâce à sa longueur, 6 ou 7 bits.
	- de l'hexadécimal, qui commence toujours par '0x'.
	- de l'octal, qui commence toujouts par '0'.
	- du décimale, tout le reste.
	
```
enc = "0127 0x65 0x6c 99 1101111 0x6d 0x65 32 116 0157 100000 1110100 0150 0x65 32 0x48 1100001 1100011 1101011 1010011 0x65 1100011 1110101 1010010 0145 105 0155 115 040 0x32 0x30 0x32 0x32 101110 100000 0x54 0x68 0x65 32 85 0122 0x43 65 0x20 1000011 1010100 0106 32 105 115 0x20 0x74 0x68 0x65 0x20 98 105 103 103 0x65 115 0x74 0x20 0150 0141 0x63 107 0145 0x72 100000 0143 0157 110 1110100 0145 1110011 1110100 32 1101001 0156 0x20 0x47 0162 0141 0x6e 0x64 101101 0105 0x73 1110100 100000 0x69 1101110 040 0106 0162 1100001 0156 0x63 0x65 0x2e 040 0x4f 1001111 1101111 0x6f 1101111 0157 1101111 112 115 0x2c 100000 0171 0x6f 0165 100000 0167 1100001 0156 116 0x20 0x74 0x6f 040 0153 0156 0157 119 32 1110100 0150 0x65 100000 0x66 0x6c 0141 103 054 100000 0144 0x6f 0156 047 0x74 32 1111001 0x6f 1110101 0x20 077 0x20 72 0145 1110010 1100101 040 121 0157 117 0x20 0x61 0162 0x65 46 0110 0x53 0x52 123 0111 0x5f 0x68 110000 0160 51 95 0171 110000 1110101 0x5f 1100100 0151 0144 1011111 1101110 060 116 95 0164 82 121 0x5f 0x74 0x30 0137 1100100 110011 99 1010010 1111001 1110000 0x74 0137 1101111 0156 51 0x5f 0142 89 0x5f 1101111 110 0x33 1011111 110100 0x67 52 0x31 0x6e 1011111 66 51 99 110100 0x75 0123 110011 0137 0x31 1110100 1110011 95 0x76 0x33 0x72 0x79 0137 0126 51 0162 0x59 0x5f 0x4c 110000 1101110 0x67 0x7d 100000 0110 0x61 1110110 1100101 100000 0x66 0165 1101110 33 100001 041 0x20 78 1101111 119 0x20 0x69 116 047 1110011 0x20 0x6a 117 1110011 1110100 040 0x70 0141 100 100 0x69 110 0x67 0x20 101110 056 101110 056 101110 040 0x3b 0x2d 051 040 0102 1100101 99 97 0165 0163 1100101 100000 1101110 0x65 0166 0x65 0x72 100000 1110000 117 116 100000 0164 0150 0x65 100000 102 1101100 97 103 040 0141 1110100 0x20 116 1101000 101 32 1100101 110 100 32 0157 102 32 0x61 32 115 0x65 1101110 0x74 101 1101110 0x63 0x65 0x20 056 0x21 077"
msg = ""
for char in enc.split(" "):
        # bin
        if len(char) == 7 or len(char) == 6:
                msg += chr(int("0b"+char,2))
                continue
        # hexa
        if char[:2] == '0x':
                msg += chr(int(char,16))
                continue
        # octal
        if char[0] == '0':
                msg += chr(int(char,8))
                continue
        # decimale
        msg += chr(int(char,10))
print(msg)

```

Ce qui donne le message suivant : "Welcome to the HackSecuReims 2022. The URCA CTF is the biggest hacker contest in Grand-Est in France. OOooooops, you want to know the flag, don't you ? Here you are.HSR{I_h0p3_y0u_did_n0t_tRy_t0_d3cRypt_on3_bY_on3_4g41n_B3c4uS3_1ts_v3ry_V3rY_L0ng} Have fun!!! Now it's just padding ..... ;-) Because never put the flag at the end of a sentence .!?"