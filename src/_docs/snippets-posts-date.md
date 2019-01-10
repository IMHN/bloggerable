<!--
@@@title:Date@@@
@@@description:Date of the post.@@@
@@@section:Snippets@@@
@@@subsection:Posts@@@
-->

Date of the post.


## Default (published)

```html
<!-- Date (published) -->
<time expr:datetime='data:post.date.iso8601' expr:title='data:post.date.iso8601'>
  <data:post.date/>
</time>
```

**+ Custom format**

```html
<!-- Date (published) -->
<time expr:datetime='data:post.date.iso8601' expr:title='data:post.date.iso8601'>
  <b:eval expr='format(data:post.date, "dd/MM/YYYY")'/>
</time>
```


## Last updated

```html
<!-- Date (updated) -->
<time expr:datetime='data:post.lastUpdated.iso8601' expr:title='data:post.lastUpdated.iso8601'>
  <data:post.lastUpdated/>
</time>
```

**+ Custom format**

```html
<!-- Date (updated) -->
<time expr:datetime='data:post.lastUpdated.iso8601' expr:title='data:post.lastUpdated.iso8601'>
  <b:eval expr='format(data:post.lastUpdated, "dd/MM/YYYY")'/>
</time>
```


## Custom format

<table>
  <thead>
    <tr>
      <th>Period</th>
      <th>Symbol</th>
      <th>Example output</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="2">Year</td>
      <td><code>YY</code></td>
      <td><code>17</code></td>
      <td>Year, 2 digits</td>
    </tr>
    <tr>
      <td><code>YYYY</code></td>
      <td><code>2017</code></td>
      <td>Year, 4 digits</td>
    </tr>
    <tr>
      <td rowspan="5">Month</td>
      <td><code>M</code></td>
      <td><code>1</code>, <code>11</code></td>
      <td>Month, minimum 1 digit</td>
    </tr>
    <tr>
      <td><code>MM</code></td>
      <td><code>01</code>, <code>11</code></td>
      <td>Month, 2 digits</td>
    </tr>
    <tr>
      <td><code>MMM</code></td>
      <td><code>Jan</code>, <code>Nov</code></td>
      <td>Month, 3 Letters</td>
    </tr>
    <tr>
      <td><code>MMMM</code></td>
      <td><code>January</code>, <code>November</code></td>
      <td>Month, full name</td>
    </tr>
    <tr>
      <td><code>MMMMM</code></td>
      <td><code>J</code>, <code>N</code></td>
      <td>Month, 1st letter</td>
    </tr>
    <tr>
      <td rowspan="3">Week</td>
      <td><code>w</code></td>
      <td><code>1</code>, <code>11</code></td>
      <td>Week of the year, minimum 1 digit</td>
    </tr>
    <tr>
      <td><code>ww</code></td>
      <td><code>01</code>, <code>11</code></td>
      <td>Week of the year, 2 digits</td>
    </tr>
    <tr>
      <td><code>W</code></td>
      <td><code>4</code></td>
      <td>Week of the month, 1 digit</td>
    </tr>
    <tr>
      <td rowspan="10">Day</td>
      <td><code>d</code></td>
      <td><code>1</code>, <code>11</code></td>
      <td>Day of the month, minimum 1 digit</td>
    </tr>
    <tr>
      <td><code>dd</code></td>
      <td><code>01</code>, <code>11</code></td>
      <td>Day of the month, 2 digits</td>
    </tr>
    <tr>
      <td><code>D</code></td>
      <td><code>1</code>, <code>55</code>, <code>362</code></td>
      <td>Day of the year, minimum 1 digit</td>
    </tr>
    <tr>
      <td><code>DD</code></td>
      <td><code>01</code>, <code>55</code>, <code>362</code></td>
      <td>Day of the year, minimum 2 digits</td>
    </tr>
    <tr>
      <td><code>DDD</code></td>
      <td><code>001</code>, <code>055</code>, <code>362</code></td>
      <td>Day of the year, minimum 3 digits</td>
    </tr>
    <tr>
      <td><code>F</code></td>
      <td><code>3</code></td>
      <td>Xth day of the month. Example, the 3rd Tuesday of the month.</td>
    </tr>
    <tr>
      <td><code>E</code></td>
      <td><code>M</code>, <code>T</code></td>
      <td>Name of the day of the week. 1 letter</td>
    </tr>
    <tr>
      <td><code>EE</code></td>
      <td><code>Mo</code>, <code>Tu</code></td>
      <td>Name of the day of the week. 2 letters</td>
    </tr>
    <tr>
      <td><code>EEE</code></td>
      <td><code>Mon</code>, <code>Tue</code></td>
      <td>Name of the day of the week. 3 letters</td>
    </tr>
    <tr>
      <td><code>EEEE</code></td>
      <td><code>Monday</code>, <code>Tuesday</code></td>
      <td>Full name of the day of the week.</td>
    </tr>
    <tr>
      <td rowspan="3">Time of day</td>
      <td><code>aaaa</code></td>
      <td><code>AM</code>, <code>PM</code></td>
      <td rowspan="3">Names may vary depending on the region.</td>
    </tr>
    <tr>
      <td><code>bbbb</code></td>
      <td rowspan="2"><code>Morning</code>, <code>Afternoon</code>, <code>Evening</code></td>
    </tr>
    <tr>
      <td><code>BBBB</code></td>
    </tr>
    <tr>
      <td rowspan="4">Hour</td>
      <td><code>h</code></td>
      <td><code>1</code>, <code>11</code></td>
      <td>Time [1-12], minimum 1 digit</td>
    </tr>
    <tr>
      <td><code>hh</code></td>
      <td><code>01</code>, <code>11</code></td>
      <td>Time [1-12], 2 digits</td>
    </tr>
    <tr>
      <td><code>H</code></td>
      <td><code>1</code>, <code>21</code></td>
      <td>Time [0-23], minimum 1 digit</td>
    </tr>
    <tr>
      <td><code>HH</code></td>
      <td><code>01</code>, <code>21</code></td>
      <td>Time [0-23], 2 digits</td>
    </tr>
    <tr>
      <td rowspan="2">Minute</td>
      <td><code>m</code></td>
      <td><code>1</code>, <code>59</code></td>
      <td>Minute, minimum 1 digit</td>
    </tr>
    <tr>
      <td><code>mm</code></td>
      <td><code>01</code>, <code>59</code></td>
      <td>Minute, 2 digits</td>
    </tr>
  </tbody>
</table>
