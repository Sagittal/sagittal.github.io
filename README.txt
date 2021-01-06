StaffCode installation instructions

- In Admin Control Panel -> Posting -> BBCodes click "Add a new BBCode". This one is for the block mode.
- Fill in the BBCode usage field with:

[staff={SIMPLETEXT1;optional} interactive={CHOICE1=true,false;defaultValue=false} inline={CHOICE2=true,false;defaultValue=false} font={SIMPLETEXT2;optional} size={SIMPLETEXT3;optional}]{TEXT}[/staff]

- Fill in the "HTML Replacement" field with:

<span class="staff-code" sc-interactive="{CHOICE1}" sc-inline="{CHOICE2}" sc-line-height="{SIMPLETEXT1}" sc-font="{SIMPLETEXT2}" sc-size="{SIMPLETEXT3}">
    <textarea class="input" style="display: none;">{TEXT}</textarea>
</span>
<script src='assets/javascript/staffCode.js'></script>
<script>globalThis.staffCode || document.write('<script src="https://sagittal.github.io/staffCode.js"></script>')</script>

If you want the StaffCode your users provide to always be preceded by certain staff code (such as a particular clef and/or code to turn on the staff), you can put any StaffCode you like just before the {TEXT} token.

If you want to hook into StaffCode's translation with a callback, you can provide one. StaffCode will call your callback any time translation of input staff codes to Unicode occurs. The first argument to the callback is the input codes, and the second argument is the output Unicode. You must provide the callback by inserting a second script tag above the one sourcing staffCode.js, in this format:

<script>
globalThis.staffCodeCallback = (inputSentence, unicodeSentence) => {
    console.warn("testing 1, 2, 3...", unicodeSentence, inputSentence)
}
</script>

- Fill in the "Help line" field with:

Convert staffCodes into a music notation figure: [staff]ston Gcl ; F4 nt[/staff]

- In Admin Control Panel -> Posting -> BBCodes click "Add a new BBCode". This one is for the inline mode.
- Fill in the BBCode usage field with:

[sc={SIMPLETEXT1;defaultValue=0.54} font={SIMPLETEXT2;optional} size={SIMPLETEXT3;defaultValue=2.8}]{TEXT}[/sc]

- Fill in the "HTML Replacement" field with:

See the HTML Replacement section for the [staff] code above for further details if you are interested in customizing.

<span class="staff-code" sc-inline="true" sc-line-height="{SIMPLETEXT1}" sc-font="{SIMPLETEXT2}" sc-size={SIMPLETEXT3}>
    <textarea class="input" style="display: none;">{TEXT}</textarea>
</span>
<script src='assets/javascript/staffCode.js'></script>
<script>globalThis.staffCode || document.write('<script src="https://sagittal.github.io/staffCode.js"></script>')</script>

- Fill in the "Help line" field with:

Convert staffCodes into inline music notation: [sc]/|[/sc]

Optional: if you would rather install the fonts and JavaScript directly on your phpBB server:
- Download https://sagittal.github.io/assets/fonts/BravuraTextBB.otf, https://sagittal.github.io/assets/fonts/BravuraTextBB.woff, and https://sagittal.github.io/staffCode.js.
- Drag `BravuraTextBB.otf` and `BravuraTextBB.woff` to your `assets/fonts` folder, along with any other fonts your users may wish to use. SMuFL-compliant fonts will not work out of the box; a non-trivial amount of modification to a font is required to work with StaffCode.
- Drag `staffCode.js` to your `assets/javascripts` folder.
