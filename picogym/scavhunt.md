# Scavenger Hunt

Description: There is some interesting information hidden around this site http://mercury.picoctf.net:39491/. Can you find it?

The first part of the flag is hidden in the page’s HTML source. 

```html
<div id="tababout" class="tabcontent">
		<h3>What</h3>
		<p>I used these to make this site: <br/>
		  HTML <br/>
		  CSS <br/>
		  JS (JavaScript)
		</p>
	<!-- Here's the first part of the flag: picoCTF{t -->
      </div>
```

The second part is inside the “mycss.css” file: 

```css
.tabcontent {
    color: #111;
    display: none;
    padding: 50px;
    text-align: center;
}

#tabintro { background-color: #ccc; }
#tababout { background-color: #ccc; }

/* CSS makes the page look nice, and yes, it also has part of the flag. Here's part 2: h4ts_4_l0 */
```

And the third part is hinted at inside the “myjs.js” file: “How can I keep google from indexing my site?” Which brings us to the robots.txt file. A cURL gives us: 

```css
User-agent: *
Disallow: /index.html
# Part 3: t_0f_pl4c
# I think this is an apache server... can you Access the next flag?
```

Apache servers contain various configuration files, one of these is the .htaccess file used for making config changes on a per-directory basis (although httpd.conf is recommended). A cURL for this file returns:

```html
# Part 4: 3s_2_lO0k
# I love making websites on my Mac, I can Store a lot of information there.
```

Hmm. The capitalised Store gives a hint here. On Mac systems there is a file storing custom attributes of its containing folder, such as folder view options, icon positions and other visual information. This is called .DS_Store, abbreviated for Desktop Services Store. The function is similar to desktop.ini in Windows. Anyways, a cURL for this returns:

```html
Congrats! You completed the scavenger hunt. Part 5: _f7ce8828}
```

And the hunt is completed.
