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
  The kns object (see Creating a KNS object) has four functions which can be called and emits events.<br />
  <h4>signal(eventname, options)</h4>
  Signals an event of "eventname" to "eventdomail" as specified in the KNS object (defaults to "node") with options as event parameters. For example:<br />
  <code>
    var appid = new kns('a41x00');<br />
    appid.signal("test", {"testparam":"foo"});
  </code><br />
  would be selected with the select statement <code>select when node test testparam ".*(.)" setting(testparam)</code> and capturing "o" as testparam.<br />
  This function does not return anything<br /><br />

  <h4>on(eventname, callback)</h4>
    Calls the callback function with the directives paramaters when a directive with the name of eventname is returned from KNS (see Events for more info);
  
  <h4>appid(newappid)</h4>
    Accepts one optional parameter. If newappid is defined, the appid of the object is changed.<br />
    Returns the appid of the object.<br /><br />

  <h4>appversion(newversion)</h4>
    Accepts one optional parameter. If newversion is defined, the app version of the object is changed.<br />
    Return the app version of the object<br /><br />
</p>

<p>
  <h2>Events</h2>
   Events which are emmited by the KNS module are of the same name as the directive returned by KNS. For example, if the action "send_directive" was called like<br /><code>send_directive("say") with text = "hello world!";</code>,<br />the event emmited by the module would be say. In order to respond to this event, one would call the "on" method of the kns object: <br />
  <code>
    appid.on("say", function(eventargs){<br />
      &nbsp;&nbsp;console.log(eventargs.text);<br />
    });
  </code>
</p>
