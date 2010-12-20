<h1>kns</h1>
<h3>A Kynetx library for use with node.js.</h3>

<p>
  Below is an example application using Kynetx to raise events and respond to a directive:

  <code>
    var kns = require('kns');<br />
  </code>

    var appid = new kns('appid');

    appid.on("helloworld",function(responseParams){
      console.log(responseParams['text']; // Should equal hello world. These are set via the with's on the send_directive action.
    });

    appid.signal("anyonethere", {"eventargument":"yes"});
  </code>
</p>
