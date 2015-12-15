# xigtviz
IGT Visualizer for Xigt data

## Usage

Add something like this to your HTML header:

```html
  <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/3.5.6/d3.min.js" charset="utf-8"></script>
  <script src="/static/xigtviz.js" charset="utf-8"></script>
  <script>var settings = {{settings|tojson|safe}};</script>
  <link rel="stylesheet" type="text/css" href="/static/xigtviz.css"/>
```

This assumes you are using Flask. Load `config.json` and render the template like this:

```python
with open('config.json') as f:
    settings = json.loads(f.read())

@app.route('/')
def index():
    return render_template('index.html', settings=settings)
```

In your HTML, create a `<div id="igt"></div>`, load the Xigt IGT as a
XigtJSON object, and then render it with a call to `igtLayout()`:

```javascript
igtLayout("#igt", xigtJsonData);
```

