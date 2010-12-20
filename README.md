<h1>kns</h1>
<h3>A Kynetx library for use with node.js.</h3>

<p>
  Below is an example application using Kynetx to raise events and respond to a directive:<br />

  <code>
    var kns = require('kns');<br /><br />

    var appid = new kns('appid');<br /><br />

    appid.on("helloworld",function(responseParams){<br />
&nbsp;&nbsp;      console.log(responseParams['text']; // Should equal hello world. These are set via the with's on the send_directive action.<br />
    });<br /><br />

    appid.signal("anyonethere", {"eventargument":"yes"});
  </code>
</p>

<p>
  <h2>Documentation:</h2>
</p>

<h3>Creating a KNS object</h3>
<p>
  To interact with KNS through Node require the kns module and then create a new kns object. When creating the kns object, there is one required and one optional parameter. The first (and requried param) is the Kynetx Application ID (appid) and the second (optional) parameter is an object. You can overide default settings by passing in a hash. Supported options in the object are:
    <ul>
      <li>eventdomain: A string that is the domain that the event is to be raised to. Default is node.</li>
      <li>appversion: A string containing the version of your appliction to run. Default is "production".
    </ul>
</p>

<h3>The KNS object</h3>
<p>
  The kns object (see Creating a KNS object) has three functions which can be called and emits one event.<br />
  <h4>signal(eventname, options)</h4><br />
  Signals an event of "eventname" to "eventdomail" as specified in the KNS object (defaults to "node") with options as event parameters. For example:<br />
  <code>
    var appid = new kns('a41x00');<br />
    appid.signal("test", {"testparam":"foo"});
  </code><br />
  would select on <code>select when node test testparam ".*(.)" setting(testparam)</code> capturing "o" as testparam.<br />
</p>
