# Botguard-RE
Reversing the Google BotGuard identifier (Used for bgrequest)

# Current knowledge

It generates the identifier from the following code

https://github.com/icetroll/botguard-RE/blob/b1a73f8e9e1b9f15950ae7d04e9a4c6e6be52fbc/2022-01-05.js#L259-L296
```
if (base64decoder = window.btoa) {
  p = 0;
  encodedString = "";
    for (; p < StringByteArray.length; p = p + 8192) {
      encodedString = encodedString + String.fromCharCode.apply(null, StringByteArray.slice(p, p + 8192));
    }
  identifier = base64decoder(encodedString).replace(/\+/g, "-").replace(/\//g, "_").replace(/=/g, "");
  } else {
    identifier = void 0;
  }
returnValue = identifier;
}
```

It genereates the ByteArray in the following code. this.fs(array) then calls to the code above ^

```
if (result = ((array = this.Qd(2).concat(J$jscomp$0(177, this)), array[1] = array[0] ^ 204, array[3] = (t = array[1], n = inNames[0], -(t | 0) + (n | 0) + 2 * (t & ~n)), array)[4] = array[1] ^ inNames[1], this.fs(array)))
```


Javascript is created from eval function
```
.eval(F("error", "tl", 6, Y, "", "1")(Array(7824 * Math.random() | 0).join("\n") + '{code}''))(U)(c.substr(0, H), A, k)[0];
```
