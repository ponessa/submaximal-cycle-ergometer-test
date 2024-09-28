---
title: Markdown Overview
permalink: /en/learning-framework/markdown-overview
abstract: >- # this means to ignore newlines until "baseurl:"
  Markdown cheat sheet providing a quick overview of all the Markdown syntax elements.
---
<style>
.alert-info {
    color: #0c5460;
    background-color: #d1ecf1;
    border-color: #bee5eb;
}
.alert {
    position: relative;
    padding: 0.75rem 1.25rem;
    margin-bottom: 1rem;
    border: 1px solid transparent;
    border-radius: 0.25rem;
}
.svg-inline--fa.fa-w-16 {
    width: 1em;
}
.svg-inline--fa {
    display: inline-block;
    font-size: inherit;
    height: 1em;
    vertical-align: -0.125em;
}
</style>

   
<h2 id="overview">Overview</h2>

<p>Nearly all Markdown applications support the basic syntax outlined in the original Markdown design document. There are minor variations and discrepancies between Markdown processors — those are noted inline wherever possible.</p>

<h2 id="headings">Headings</h2>

<p>To create a heading, add number signs (#) in front of a word or phrase. The number of number signs you use should correspond to the heading level. For example, to create a heading level three (&lt;h3&gt;), use three number signs (e.g., ### My Header).</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>Markdown</th>
      <th>HTML</th>
      <th>Rendered Output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td># Heading level 1</td>
      <td>&lt;h1&gt;Heading level 1&lt;/h1&gt;</td>
      <td><h1 class="no-anchor" data-toc-skip="" id="heading-level-1">Heading level 1</h1></td>
    </tr>
    <tr>
      <td>## Heading level 2</td>
      <td>&lt;h2&gt;Heading level 2&lt;/h2&gt;</td>
      <td><h2 class="no-anchor" data-toc-skip="" id="heading-level-2">Heading level 2</h2></td>
    </tr>
    <tr>
      <td>### Heading level 3</td>
      <td>&lt;h3&gt;Heading level 3&lt;/h3&gt;</td>
      <td><h3 class="no-anchor" data-toc-skip="" id="heading-level-3">Heading level 3</h3></td>
    </tr>
    <tr>
      <td>#### Heading level 4</td>
      <td>&lt;h4&gt;Heading level  4&lt;/h4&gt;</td>
      <td><h4 class="no-anchor" id="heading-level-4">Heading level 4</h4></td>
    </tr>
    <tr>
      <td>##### Heading level 5</td>
      <td>&lt;h5&gt;Heading level 5&lt;/h5&gt;</td>
      <td><h5 class="no-anchor" id="heading-level-5">Heading level 5</h5></td>
    </tr>
    <tr>
      <td>###### Heading level 6</td>
      <td>&lt;h6&gt;Heading level 6&lt;/h6&gt;</td>
      <td><h6 class="no-anchor">Heading level 6</h6></td>
    </tr>
  </tbody>
</table>


<h3 id="heading-best-practices">Heading Best Practices<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#heading-best-practices" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>Markdown applications don’t agree on how to handle a missing space between the number signs (#) and the heading name. For compatibility, always put a space between the number signs and the heading name.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>✅&nbsp; Do this</th>
      <th>❌&nbsp; Don't do this</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>

          # Here's a Heading<br><br>

      </td>
      <td>

          #Here's a Heading

      </td>
    </tr>
  </tbody>
</table>

<p>You should also put blank lines before and after a heading for compatibility.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>✅&nbsp; Do this</th>
      <th>❌&nbsp; Don't do this</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>

        Try to put a blank line before...<br/><br/>

        # Heading<br/><br/>

        ...and after a heading.

      </td>
      <td>

        Without blank lines, this might not look right.<br/>
        # Heading<br/>
        Don't do this!

      </td>
    </tr>
  </tbody>
</table>

<h2 id="paragraphs-1">Paragraphs<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#paragraphs-1" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h2>

<p>To create paragraphs, use a blank line to separate one or more lines of text.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>Markdown</th>
      <th>HTML</th>
      <th>Rendered Output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>

          I really like using Markdown.<br><br>

          I think I'll use it to format all of my documents from now on.

      </td>
      <td>
        &lt;p&gt;I really like using Markdown.&lt;/p&gt;<br><br>

        &lt;p&gt;I think I'll use it to format all of my documents from now on.&lt;/p&gt;
      </td>
      <td>
        <p>I really like using Markdown.</p>

        <p>I think I'll use it to format all of my documents from now on.</p>
      </td>
    </tr>
  </tbody>
</table>

<h3 id="paragraph-best-practices">Paragraph Best Practices<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#paragraph-best-practices" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>Unless the <a href="#paragraphs">paragraph is in a list</a>, don’t indent paragraphs with spaces or tabs.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>✅&nbsp; Do this</th>
      <th>❌&nbsp; Don't do this</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>

          Don't put tabs or spaces in front of your paragraphs.<br><br>

          Keep lines left-aligned like this.<br><br>

      </td>
      <td>

        &nbsp;&nbsp;&nbsp;&nbsp;This can result in unexpected
        formatting problems.<br><br>

        &nbsp;&nbsp;Don't add tabs or spaces in front of paragraphs.

      </td>
    </tr>
  </tbody>
</table>

<h2 id="line-breaks">Line Breaks<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#line-breaks" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h2>

<p>To create a line break or new line (&lt;br&gt;), end a line with two or more spaces, and then type return.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>Markdown</th>
      <th>HTML</th>
      <th>Rendered Output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>

          This is the first line. &nbsp;<br>
          And this is the second line.

      </td>
      <td>
        &lt;p&gt;This is the first line.&lt;br&gt;<br>

        And this is the second line.&lt;/p&gt;
      </td>
      <td>
        <p>This is the first line.<br>   
        And this is the second line.</p>
      </td>
    </tr>
  </tbody>
</table>

<h3 id="line-break-best-practices">Line Break Best Practices<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#line-break-best-practices" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>You can use two or more spaces (commonly referred to as “trailing whitespace”) for line breaks in nearly every Markdown application, but it’s controversial. It’s hard to see trailing whitespace in an editor, and many people accidentally or intentionally put two spaces after every sentence. For this reason, you may want to use something other than trailing whitespace for line breaks. If your Markdown application <a href="#html">supports HTML</a>, you can use the &lt;br&gt; HTML tag.</p>

<p>For compatibility, use trailing white space or the &lt;br&gt; HTML tag at the end of the line.</p>

<p>There are two other options I don’t recommend using. CommonMark and a few other lightweight markup languages let you type a backslash (\) at the end of the line, but not all Markdown applications support this, so it isn’t a great option from a compatibility perspective. And at least a couple lightweight markup languages don’t require anything at the end of the line — just type return and they’ll create a line break.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>✅&nbsp; Do this</th>
      <th>❌&nbsp; Don't do this</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>

          First line with two spaces after. &nbsp;<br>
          And the next line.<br><br>

          First line with the HTML tag after.&lt;br&gt;<br>
          And the next line.<br><br>

      </td>
      <td>

        First line with a backslash after.\<br>
        And the next line.<br><br>

        First line with nothing after.<br>
        And the next line.<br><br>

      </td>
    </tr>
  </tbody>
</table>

<h2 id="emphasis">Emphasis<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#emphasis" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h2>

<p>You can add emphasis by making text bold or italic.</p>

<h3 id="bold">Bold<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#bold" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>To bold text, add two asterisks or underscores before and after a word or phrase. To bold the middle of a word for emphasis, add two asterisks without spaces around the letters.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>Markdown</th>
      <th>HTML</th>
      <th>Rendered Output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>I just love **bold text**.</td>
      <td>I just love &lt;strong&gt;bold text&lt;/strong&gt;.</td>
      <td>I just love <strong>bold text</strong>.</td>
    </tr>
    <tr>
      <td>I just love __bold text__.</td>
      <td>I just love &lt;strong&gt;bold text&lt;/strong&gt;.</td>
      <td>I just love <strong>bold text</strong>.</td>
    </tr>
    <tr>
      <td>Love**is**bold</td> <td>Love&lt;strong&gt;is&lt;/strong&gt;bold</td>
      <td>Love<strong>is</strong>bold</td>
    </tr>
  </tbody>
</table>

<h4 id="bold-best-practices">Bold Best Practices<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#bold-best-practices" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h4>

<p>Markdown applications don’t agree on how to handle underscores in the middle of a word. For compatibility, use asterisks to bold the middle of a word for emphasis.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>✅&nbsp; Do this</th>
      <th>❌&nbsp; Don't do this</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>

          Love**is**bold

      </td>
      <td>

          Love__is__bold

      </td>
    </tr>
  </tbody>
</table>

<h3 id="italic">Italic<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#italic" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>To italicize text, add one asterisk or underscore before and after a word or phrase. To italicize the middle of a word for emphasis, add one asterisk without spaces around the letters.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>Markdown</th>
      <th>HTML</th>
      <th>Rendered Output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Italicized text is the *cat's meow*.</td>
      <td>Italicized text is the &lt;em&gt;cat's meow&lt;/em&gt;.</td>
      <td>Italicized text is the <em>cat’s meow</em>.</td>
    </tr>
    <tr>
      <td>Italicized text is the _cat's meow_.</td>
      <td>Italicized text is the &lt;em&gt;cat's meow&lt;/em&gt;.</td>
      <td>Italicized text is the <em>cat’s meow</em>.</td>
    </tr>
    <tr>
      <td>A*cat*meow</td>
      <td>A&lt;em&gt;cat&lt;/em&gt;meow</td>
      <td>A<em>cat</em>meow</td>
    </tr>
  </tbody>
</table>

<h4 id="italic-best-practices">Italic Best Practices<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#italic-best-practices" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h4>

<p>Markdown applications don’t agree on how to handle underscores in the middle of a word. For compatibility, use asterisks to italicize the middle of a word for emphasis.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>✅&nbsp; Do this</th>
      <th>❌&nbsp; Don't do this</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        
          A*cat*meow
        
      </td>
      <td>
        
          A_cat_meow
        
      </td>
    </tr>
  </tbody>
</table>

<h3 id="bold-and-italic">Bold and Italic<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#bold-and-italic" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>To emphasize text with bold and italics at the same time, add three asterisks or underscores before and after a word or phrase. To bold and italicize the middle of a word for emphasis, add three asterisks without spaces around the letters.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>Markdown</th>
      <th>HTML</th>
      <th>Rendered Output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>This text is ***really important***.</td>
      <td>This text is &lt;em&gt;&lt;strong&gt;really important&lt;/strong&gt;&lt;/em&gt;.</td>
      <td>This text is <em><strong>really important</strong></em>.</td>
    </tr>
    <tr>
      <td>This text is ___really important___.</td>
      <td>This text is &lt;em&gt;&lt;strong&gt;really important&lt;/strong&gt;&lt;/em&gt;.</td>
      <td>This text is <em><strong>really important</strong></em>.</td>
    </tr>
    <tr>
      <td>This text is __*really important*__.</td>
      <td>This text is &lt;em&gt;&lt;strong&gt;really important&lt;/strong&gt;&lt;/em&gt;.</td>
      <td>This text is <em><strong>really important</strong></em>.</td>
    </tr>
    <tr>
      <td>This text is **_really important_**.</td>
      <td>This text is &lt;em&gt;&lt;strong&gt;really important&lt;/strong&gt;&lt;/em&gt;.</td>
      <td>This text is <em><strong>really important</strong></em>.</td>
    </tr>
    <tr>
      <td>This is really***very***important text.</td>
      <td>This is really&lt;em&gt;&lt;strong&gt;very&lt;/strong&gt;&lt;/em&gt;important text.</td>
      <td>This is really<em><strong>very</strong></em>important text.</td>
    </tr>
  </tbody>
</table>

<div class="alert alert-info">
  <svg class="svg-inline--fa fa-info-circle fa-w-16" aria-hidden="true" focusable="false" data-prefix="fas" data-icon="info-circle" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" data-fa-i2svg=""><path fill="currentColor" d="M256 8C119.043 8 8 119.083 8 256c0 136.997 111.043 248 248 248s248-111.003 248-248C504 119.083 392.957 8 256 8zm0 110c23.196 0 42 18.804 42 42s-18.804 42-42 42-42-18.804-42-42 18.804-42 42-42zm56 254c0 6.627-5.373 12-12 12h-88c-6.627 0-12-5.373-12-12v-24c0-6.627 5.373-12 12-12h12v-64h-12c-6.627 0-12-5.373-12-12v-24c0-6.627 5.373-12 12-12h64c6.627 0 12 5.373 12 12v100h12c6.627 0 12 5.373 12 12v24z"></path></svg><!-- <i class="fas fa-info-circle"></i> --> <strong>Note:</strong> The order of the em and strong tags might be reversed depending on the Markdown processor you're using.
</div>

<h4 id="bold-and-italic-best-practices">Bold and Italic Best Practices<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#bold-and-italic-best-practices" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h4>

<p>Markdown applications don’t agree on how to handle underscores in the middle of a word. For compatibility, use asterisks to bold and italicize the middle of a word for emphasis.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>✅&nbsp; Do this</th>
      <th>❌&nbsp; Don't do this</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        
          This is really***very***important text.
        
      </td>
      <td>
        
          This is really___very___important text.
        
      </td>
    </tr>
  </tbody>
</table>

<h2 id="blockquotes-1">Blockquotes<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#blockquotes-1" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h2>

<p>To create a blockquote, add a &gt; in front of a paragraph.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">&gt; Dorothy followed her through many of the beautiful rooms in her castle.
</pre></div></div>

<p>The rendered output looks like this:</p>

<blockquote>
  <p>Dorothy followed her through many of the beautiful rooms in her castle.</p>
</blockquote>

<h3 id="blockquotes-with-multiple-paragraphs">Blockquotes with Multiple Paragraphs<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#blockquotes-with-multiple-paragraphs" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>Blockquotes can contain multiple paragraphs. Add a &gt; on the blank lines between the paragraphs.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">&gt; Dorothy followed her through many of the beautiful rooms in her castle.
&gt;
&gt; The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
</pre></div></div>

<p>The rendered output looks like this:</p>

<blockquote>
  <p>Dorothy followed her through many of the beautiful rooms in her castle.</p>

  <p>The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.</p>
</blockquote>

<h3 id="nested-blockquotes">Nested Blockquotes<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#nested-blockquotes" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>Blockquotes can be nested. Add a &gt;&gt; in front of the paragraph you want to nest.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">&gt; Dorothy followed her through many of the beautiful rooms in her castle.
&gt;
&gt;&gt; The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
</pre></div></div>

<p>The rendered output looks like this:</p>

<blockquote>
  <p>Dorothy followed her through many of the beautiful rooms in her castle.</p>

  <blockquote>
    <p>The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.</p>
  </blockquote>
</blockquote>

<h3 id="blockquotes-with-other-elements">Blockquotes with Other Elements<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#blockquotes-with-other-elements" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>Blockquotes can contain other Markdown formatted elements. Not all elements can be used — you’ll need to experiment to see which ones work.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">&gt; #### The quarterly results look great!
&gt;
&gt; - Revenue was off the chart.
&gt; - Profits were higher than ever.
&gt;
&gt;  *Everything* is going according to **plan**.
</pre></div></div>

<p>The rendered output looks like this:</p>

<blockquote>
  <h4 class="no-anchor" id="the-quarterly-results-look-great">The quarterly results look great!</h4>

  <ul>
    <li>Revenue was off the chart.</li>
    <li>Profits were higher than ever.</li>
  </ul>

  <p><em>Everything</em> is going according to <strong>plan</strong>.</p>
</blockquote>

<h3 id="blockquotes-best-practices">Blockquotes Best Practices<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#blockquotes-best-practices" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>For compatibility, put blank lines before and after blockquotes.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>✅&nbsp; Do this</th>
      <th>❌&nbsp; Don't do this</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        
        Try to put a blank line before...<br><br>

        &gt; This is a blockquote<br><br>

        ...and after a blockquote.
        
      </td>
      <td>
        
        Without blank lines, this might not look right.<br>
        &gt; This is a blockquote<br>
        Don't do this!
        
      </td>
    </tr>
  </tbody>
</table>

<h2 id="lists-1">Lists<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#lists-1" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h2>

<p>You can organize items into ordered and unordered lists.</p>

<h3 id="ordered-lists">Ordered Lists<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#ordered-lists" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>To create an ordered list, add line items with numbers followed by periods. The numbers don’t have to be in numerical order, but the list should start with the number one.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>Markdown</th>
      <th>HTML</th>
      <th>Rendered Output</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      
        1. First item<br>
        2. Second item<br>
        3. Third item<br>
        4. Fourth item
      
    </td>
    <td>
      
        &lt;ol&gt;<br>
          &nbsp;&nbsp;&lt;li&gt;First item&lt;/li&gt;<br>
          &nbsp;&nbsp;&lt;li&gt;Second item&lt;/li&gt;<br>
          &nbsp;&nbsp;&lt;li&gt;Third item&lt;/li&gt;<br>
          &nbsp;&nbsp;&lt;li&gt;Fourth item&lt;/li&gt;<br>
        &lt;/ol&gt;
      
    </td>
    <td>
      <ol>
        <li>First item</li>
        <li>Second item</li>
        <li>Third item</li>
        <li>Fourth item</li>
      </ol>
    </td>
    </tr>
    <tr>
      <td>
        
          1. First item<br>
          1. Second item<br>
          1. Third item<br>
          1. Fourth item
        
      </td>
      <td>
        
          &lt;ol&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;First item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Second item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Third item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Fourth item&lt;/li&gt;<br>
          &lt;/ol&gt;
        
      </td>
      <td>
        <ol>
          <li>First item</li>
          <li>Second item</li>
          <li>Third item</li>
          <li>Fourth item</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td>
        
          1. First item<br>
          8. Second item<br>
          3. Third item<br>
          5. Fourth item
        
      </td>
      <td>
        
          &lt;ol&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;First item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Second item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Third item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Fourth item&lt;/li&gt;<br>
          &lt;/ol&gt;
        
      </td>
      <td>
        <ol>
          <li>First item</li>
          <li>Second item</li>
          <li>Third item</li>
          <li>Fourth item</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td>
        
          1. First item<br>
          2. Second item<br>
          3. Third item<br>
          &nbsp;&nbsp;&nbsp;&nbsp;1. Indented item<br>
          &nbsp;&nbsp;&nbsp;&nbsp;2. Indented item<br>
          4. Fourth item
        
      </td>
      <td>
        
          &lt;ol&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;First item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Second item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Third item<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&lt;ol&gt;<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;li&gt;Indented item&lt;/li&gt;<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;li&gt;Indented item&lt;/li&gt;<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&lt;/ol&gt;<br>
            &nbsp;&nbsp;&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Fourth item&lt;/li&gt;<br>
          &lt;/ol&gt;
        
      </td>
      <td>
        <ol>
          <li>First item</li>
          <li>Second item</li>
          <li>Third item
            <ol>
              <li>Indented item</li>
              <li>Indented item</li>
            </ol>
          </li>
          <li>Fourth item</li>
        </ol>
      </td>
    </tr>
  </tbody>
</table>

<h4 id="ordered-list-best-practices">Ordered List Best Practices<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#ordered-list-best-practices" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h4>

<p>CommonMark and a few other lightweight markup languages let you use a parenthesis ()) as a delimiter (e.g., 1) First item), but not all Markdown applications support this, so it isn’t a great option from a compatibility perspective. For compatibility, use periods only.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>✅&nbsp; Do this</th>
      <th>❌&nbsp; Don't do this</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        
          1. First item<br>
          2. Second item
        
      </td>
      <td>
        
          1) First item<br>
          2) Second item
        
      </td>
    </tr>
  </tbody>
</table>

<h3 id="unordered-lists">Unordered Lists<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#unordered-lists" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>To create an unordered list, add dashes (-), asterisks (*), or plus signs (+) in front of line items. Indent one or more items to create a nested list.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>Markdown</th>
      <th>HTML</th>
      <th>Rendered Output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        
          - First item<br>
          - Second item<br>
          - Third item<br>
          - Fourth item
        
      </td>
      <td>
        
          &lt;ul&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;First item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Second item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Third item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Fourth item&lt;/li&gt;<br>
          &lt;/ul&gt;
        
      </td>
      <td>
        <ul>
          <li>First item</li>
          <li>Second item</li>
          <li>Third item</li>
          <li>Fourth item</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>
        
          * First item<br>
          * Second item<br>
          * Third item<br>
          * Fourth item
        
      </td>
      <td>
        
          &lt;ul&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;First item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Second item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Third item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Fourth item&lt;/li&gt;<br>
          &lt;/ul&gt;
        
      </td>
      <td>
        <ul>
          <li>First item</li>
          <li>Second item</li>
          <li>Third item</li>
          <li>Fourth item</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>
        
          + First item<br>
          + Second item<br>
          + Third item<br>
          + Fourth item
        
      </td>
      <td>
        
          &lt;ul&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;First item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Second item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Third item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Fourth item&lt;/li&gt;<br>
          &lt;/ul&gt;
        
      </td>
      <td>
        <ul>
          <li>First item</li>
          <li>Second item</li>
          <li>Third item</li>
          <li>Fourth item</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>
        
          - First item<br>
          - Second item<br>
          - Third item<br>
          &nbsp;&nbsp;&nbsp;&nbsp;- Indented item<br>
          &nbsp;&nbsp;&nbsp;&nbsp;- Indented item<br>
          - Fourth item
        
      </td>
      <td>
        
          &lt;ul&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;First item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Second item&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Third item<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&lt;ul&gt;<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;li&gt;Indented item&lt;/li&gt;<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;li&gt;Indented item&lt;/li&gt;<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&lt;/ul&gt;<br>
            &nbsp;&nbsp;&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;Fourth item&lt;/li&gt;<br>
          &lt;/ul&gt;
        
      </td>
      <td>
        <ul>
          <li>First item</li>
          <li>Second item</li>
          <li>Third item
            <ul>
              <li>Indented item</li>
              <li>Indented item</li>
            </ul>
          </li>
          <li>Fourth item</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

<h4 id="starting-unordered-list-items-with-numbers">Starting Unordered List Items With Numbers<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#starting-unordered-list-items-with-numbers" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h4>

<p>If you need to start an unordered list item with a number followed by a period, you can use a backslash (\) to <a href="#escaping-characters">escape</a> the period.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>Markdown</th>
      <th>HTML</th>
      <th>Rendered Output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        
          - 1968\. A great year!<br>
          - I think 1969 was second best.
        
      </td>
      <td>
        
          &lt;ul&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;1968. A great year!&lt;/li&gt;<br>
            &nbsp;&nbsp;&lt;li&gt;I think 1969 was second best.&lt;/li&gt;<br>
          &lt;/ul&gt;
        
      </td>
      <td>
        <ul>
          <li>1968. A great year!</li>
          <li>I think 1969 was second best.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

<h4 id="unordered-list-best-practices">Unordered List Best Practices<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#unordered-list-best-practices" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h4>

<p>Markdown applications don’t agree on how to handle different delimiters in the same list. For compatibility, don’t mix and match delimiters in the same list — pick one and stick with it.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>✅&nbsp; Do this</th>
      <th>❌&nbsp; Don't do this</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        
          - First item<br>
          - Second item<br>
          - Third item<br>
          - Fourth item
        
      </td>
      <td>
        
          + First item<br>
          * Second item<br>
          - Third item<br>
          + Fourth item
        
      </td>
    </tr>
  </tbody>
</table>

<h3 id="adding-elements-in-lists">Adding Elements in Lists<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#adding-elements-in-lists" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>To add another element in a list while preserving the continuity of the list, indent the element four spaces or one tab, as shown in the following examples.</p>

<div class="alert alert-success">
  <svg class="svg-inline--fa fa-lightbulb fa-w-11" aria-hidden="true" focusable="false" data-prefix="fas" data-icon="lightbulb" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 352 512" data-fa-i2svg=""><path fill="currentColor" d="M96.06 454.35c.01 6.29 1.87 12.45 5.36 17.69l17.09 25.69a31.99 31.99 0 0 0 26.64 14.28h61.71a31.99 31.99 0 0 0 26.64-14.28l17.09-25.69a31.989 31.989 0 0 0 5.36-17.69l.04-38.35H96.01l.05 38.35zM0 176c0 44.37 16.45 84.85 43.56 115.78 16.52 18.85 42.36 58.23 52.21 91.45.04.26.07.52.11.78h160.24c.04-.26.07-.51.11-.78 9.85-33.22 35.69-72.6 52.21-91.45C335.55 260.85 352 220.37 352 176 352 78.61 272.91-.3 175.45 0 73.44.31 0 82.97 0 176zm176-80c-44.11 0-80 35.89-80 80 0 8.84-7.16 16-16 16s-16-7.16-16-16c0-61.76 50.24-112 112-112 8.84 0 16 7.16 16 16s-7.16 16-16 16z"></path></svg><!-- <i class="fas fa-lightbulb"></i> --> <strong>Tip:</strong> If things don't appear the way you expect, double check that you've indented the elements in the list four spaces or one tab.
</div>

<h4 id="paragraphs">Paragraphs<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#paragraphs" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h4>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">* This is the first list item.
* Here's the second list item.

    I need to add another paragraph below the second list item.

* And here's the third list item.
</pre></div></div>

<p>The rendered output looks like this:</p>

<ul>
  <li>This is the first list item.</li>
  <li>
    <p>Here’s the second list item.</p>

    <p>I need to add another paragraph below the second list item.</p>
  </li>
  <li>And here’s the third list item.</li>
</ul>

<h4 id="blockquotes">Blockquotes<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#blockquotes" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h4>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">* This is the first list item.
* Here's the second list item.

    &gt; A blockquote would look great below the second list item.

* And here's the third list item.
</pre></div></div>

<p>The rendered output looks like this:</p>

<ul>
  <li>This is the first list item.</li>
  <li>
    <p>Here’s the second list item.</p>

    <blockquote>
      <p>A blockquote would look great below the second list item.</p>
    </blockquote>
  </li>
  <li>And here’s the third list item.</li>
</ul>

<h4 id="code-blocks-1">Code Blocks<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#code-blocks-1" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h4>

<p><a href="#code-blocks">Code blocks</a> are normally indented four spaces or one tab.  When they’re in a list, indent them eight spaces or two tabs.</p>

<div class="language-text highlighter-rouge"><div class="highlight"><pre class="highlight">1. Open the file.
2. Find the following code block on line 21:

        &lt;html&gt;
          &lt;head&gt;
            &lt;title&gt;Test&lt;/title&gt;
          &lt;/head&gt;

3. Update the title to match the name of your website.
</pre></div></div>

<p>The rendered output looks like this:</p>

<ol>
  <li>Open the file.</li>
  <li>
    <p>Find the following code block on line 21:</p>

    <div class="language-text highlighter-rouge"><div class="highlight"><pre class="highlight"> &lt;html&gt;
   &lt;head&gt;
     &lt;title&gt;Test&lt;/title&gt;
   &lt;/head&gt;
</pre></div>    </div>
  </li>
  <li>Update the title to match the name of your website.</li>
</ol>

<h4 id="images">Images<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#images" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h4>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">1. Open the file containing the Linux mascot.
2. Marvel at its beauty.

    ![Tux, the Linux mascot](/assets/images/tux.png)

3. Close the file.
</pre></div></div>

<p>The rendered output looks like this:</p>

<ol>
  <li>Open the file containing the Linux mascot.</li>
  <li>
    <p>Marvel at its beauty.</p>

    <p><img srcset="https://mdg.imgix.net/assets/images/tux.png?auto=format&amp;fit=clip&amp;w=100 480w,           https://mdg.imgix.net/assets/images/tux.png?auto=format&amp;fit=clip&amp;q=40&amp;w=100 1080w" src="https://mdg.imgix.net/assets/images/tux.png" class="img-fluid" alt="Tux, the Linux mascot" loading="lazy" sizes="100vw"></p>
  </li>
  <li>Close the file.</li>
</ol>

<h4 id="lists">Lists<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#lists" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h4>

<p>You can nest an unordered list in an ordered list, or vice versa.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">1. First item
2. Second item
3. Third item
    - Indented item
    - Indented item
4. Fourth item
</pre></div></div>

<p>The rendered output looks like this:</p>

<ol>
  <li>First item</li>
  <li>Second item</li>
  <li>Third item
    <ul>
      <li>Indented item</li>
      <li>Indented item</li>
    </ul>
  </li>
  <li>Fourth item</li>
</ol>

<h2 id="code">Code<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#code" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h2>

<p>To denote a word or phrase as code, enclose it in backticks (`).</p>


| Markdown | HTML | Rendered Output |
|----------|------|-----------------|
| At the command prompt, type ``nano``. | At the command prompt, type &lt;code&gt;nano&lt;/code&gt;. | At the command prompt, type `nano`. |

<h3 id="escaping-backticks">Escaping Backticks<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#escaping-backticks" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>If the word or phrase you want to denote as code includes one or more backticks, you can escape it by enclosing the word or phrase in double backticks (``).</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>Markdown</th>
      <th>HTML</th>
      <th>Rendered Output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>``Use `code` in your Markdown file.``</td>
      <td>&lt;code&gt;Use `code` in your Markdown file.&lt;/code&gt;</td>
      <td>Use `code` in your Markdown file.</td>
    </tr>
  </tbody>
</table>

<h3 id="code-blocks">Code Blocks<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#code-blocks" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>To create code blocks, you can either wrap lines of code in 3 ` or use the &lt;pre&gt; tag with the attribute <b>name="code"</b> and <b>class</b> set to the coding language.  For example</p>

```
public boolean isLevelValid(int level, int status) {
  int levelValue = (int)Math.pow(2,level);
  if ((status & levelValue) == levelValue) return false;
  else return true;
}
```

<p>The rendered output looks like this:</p>

<pre name="code" class="java">
public boolean isLevelValid(int level, int status) {
  int levelValue = (int)Math.pow(2,level);
  if ((status & levelValue) == levelValue) return false;
  else return true;
}
</pre>

The available **class** values are:
1. C# (`class="c-sharp"`)
1. CSS (`class="css"`)
1. C++ (`class="cpp"`)
1. Delphi (`class="delphi"`)
1. Java (`class="java"`)
1. JavaScript (`class="js"`)
1. PHP (`class="php"`)
1. Python (`class="python"`)
1. Ruby (`class="ruby"`)
1. SQL (`class="sql"`)
1. Visual Basic (`class="vb"`)
1. XML / HTML (`class="xml"`)


<div class="alert alert-info">
  <svg class="svg-inline--fa fa-info-circle fa-w-16" aria-hidden="true" focusable="false" data-prefix="fas" data-icon="info-circle" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" data-fa-i2svg=""><path fill="currentColor" d="M256 8C119.043 8 8 119.083 8 256c0 136.997 111.043 248 248 248s248-111.003 248-248C504 119.083 392.957 8 256 8zm0 110c23.196 0 42 18.804 42 42s-18.804 42-42 42-42-18.804-42-42 18.804-42 42-42zm56 254c0 6.627-5.373 12-12 12h-88c-6.627 0-12-5.373-12-12v-24c0-6.627 5.373-12 12-12h12v-64h-12c-6.627 0-12-5.373-12-12v-24c0-6.627 5.373-12 12-12h64c6.627 0 12 5.373 12 12v100h12c6.627 0 12 5.373 12 12v24z"></path></svg><!-- <i class="fas fa-info-circle"></i> --> <strong>Note:</strong> When using a class other than XML, any angled brackets (<>) must be escaped with &amp;lt;&amp;gt;.
</div>


<h2 id="horizontal-rules">Horizontal Rules<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#horizontal-rules" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h2>

<p>To create a horizontal rule, use three or more asterisks (***), dashes (---), or underscores (___) on a line by themselves.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">***

---

_________________
</pre></div></div>

<p>The rendered output of all three looks identical:</p>

<hr>

<h3 id="horizontal-rule-best-practices">Horizontal Rule Best Practices<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#horizontal-rule-best-practices" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>For compatibility, put blank lines before and after horizontal rules.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>✅&nbsp; Do this</th>
      <th>❌&nbsp; Don't do this</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        
        Try to put a blank line before...<br><br>

        ---<br><br>

        ...and after a horizontal rule.
        
      </td>
      <td>
        
        Without blank lines, this would be a heading.<br>
        ---<br>
        Don't do this!
        
      </td>
    </tr>
  </tbody>
</table>

<h2 id="links">Links<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#links" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h2>

<p>To create a link, enclose the link text in brackets (e.g., [Duck Duck Go]) and then follow it immediately with the URL in parentheses (e.g., (https://duckduckgo.com)).</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">My favorite search engine is [Duck Duck Go](https://duckduckgo.com).
</pre></div></div>

<p>The rendered output looks like this:</p>

<p>My favorite search engine is <a href="https://duckduckgo.com">Duck Duck Go</a>.</p>


<h3 id="adding-titles">Adding Titles<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#adding-titles" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>You can optionally add a title for a link. This will appear as a tooltip when the user hovers over the link. To add a title, enclose it in quotation marks after the URL.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">My favorite search engine is [Duck Duck Go](https://duckduckgo.com "The best search engine for privacy").
</pre></div></div>

<p>The rendered output looks like this:</p>

<p>My favorite search engine is <a href="https://duckduckgo.com" title="The best search engine for privacy">Duck Duck Go</a>.</p>

<h3 id="urls-and-email-addresses">URLs and Email Addresses<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#urls-and-email-addresses" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>To quickly turn a URL or email address into a link, enclose it in angle brackets.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">&lt;https://www.markdownguide.org&gt;
&lt;fake@example.com&gt;
</pre></div></div>

<p>The rendered output looks like this:</p>

<p><a href="https://www.markdownguide.org">https://www.markdownguide.org</a><br>
<a href="mailto:fake@example.com">fake@example.com</a></p>

<h3 id="formatting-links">Formatting Links<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#formatting-links" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>To <a href="#emphasis">emphasize</a> links, add asterisks before and after the brackets and parentheses. To denote links as <a href="#code">code</a>, add backticks in the brackets.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">I love supporting the **[EFF](https://eff.org)**.
This is the *[Markdown Guide](https://www.markdownguide.org)*.
See the section on [`code`](#code).
</pre></div></div>

<p>The rendered output looks like this:</p>

<p>I love supporting the <strong><a href="https://eff.org">EFF</a></strong>.<br>
This is the <em><a href="https://www.markdownguide.org">Markdown Guide</a></em>.<br>
See the section on <a href="#code">code</a>.</p>

<h3 id="reference-style-links">Reference-style Links<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#reference-style-links" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>Reference-style links are a special kind of link that make URLs easier to display and read in Markdown. Reference-style links are constructed in two parts: the part you keep inline with your text and the part you store somewhere else in the file to keep the text easy to read.</p>

<h4 id="formatting-the-first-part-of-the-link">Formatting the First Part of the Link<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#formatting-the-first-part-of-the-link" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h4>

<p>The first part of a reference-style link is formatted with two sets of brackets. The first set of brackets surrounds the text that should appear linked. The second set of brackets displays a label used to point to the link you’re storing elsewhere in your document.</p>

<p>Although not required, you can include a space between the first and second set of brackets. The label in the second set of brackets is not case sensitive and can include letters, numbers, spaces, or punctuation.</p>

<p>This means the following example formats are roughly equivalent for the first part of the link:</p>

<ul>
  <li>[hobbit-hole][1]</li>
  <li>[hobbit-hole] [1]</li>
</ul>

<h4 id="formatting-the-second-part-of-the-link">Formatting the Second Part of the Link<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#formatting-the-second-part-of-the-link" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h4>

<p>The second part of a reference-style link is formatted with the following attributes:</p>

<ol>
  <li>The label, in brackets, followed immediately by a colon and at least one space (e.g., [label]: ).</li>
  <li>The URL for the link, which you can optionally enclose in angle brackets.</li>
  <li>The optional title for the link, which you can enclose in double quotes, single quotes, or parentheses.</li>
</ol>

<p>This means the following example formats are all roughly equivalent for the second part of the link:</p>

<ul>
  <li>[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle</li>
  <li>[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle "Hobbit lifestyles"</li>
  <li>[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle 'Hobbit lifestyles'</li>
  <li>[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle (Hobbit lifestyles)</li>
  <li>[1]: &lt;https://en.wikipedia.org/wiki/Hobbit#Lifestyle&gt; "Hobbit lifestyles"</li>
  <li>[1]: &lt;https://en.wikipedia.org/wiki/Hobbit#Lifestyle&gt; 'Hobbit lifestyles'</li>
  <li>[1]: &lt;https://en.wikipedia.org/wiki/Hobbit#Lifestyle&gt; (Hobbit lifestyles)</li>
</ul>

<p>You can place this second part of the link anywhere in your Markdown document. Some people place them immediately after the paragraph in which they appear while other people place them at the end of the document (like endnotes or footnotes).</p>

<h4 id="an-example-putting-the-parts-together">An Example Putting the Parts Together<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#an-example-putting-the-parts-together" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h4>

<p>Say you add a URL as a <a href="#links">standard URL link</a> to a paragraph and it looks like this in Markdown:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends
of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to
eat: it was a [hobbit-hole](https://en.wikipedia.org/wiki/Hobbit#Lifestyle "Hobbit lifestyles"), and that means comfort.
</pre></div></div>

<p>Though it may point to interesting additional information, the URL as displayed really doesn’t add much to the existing raw text other than making it harder to read. To fix that, you could format the URL like this instead:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends
of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to
eat: it was a [hobbit-hole][1], and that means comfort.

[1]: &lt;https://en.wikipedia.org/wiki/Hobbit#Lifestyle&gt; "Hobbit lifestyles"
</pre></div></div>

<p>In both instances above, the rendered output would be identical:</p>

<blockquote>
  <p>In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to  eat: it was a <a href="https://en.wikipedia.org/wiki/Hobbit#Lifestyle" title="Hobbit lifestyles">hobbit-hole</a>, and that means comfort.</p>
</blockquote>

<p>and the HTML for the link would be:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">&lt;a href="https://en.wikipedia.org/wiki/Hobbit#Lifestyle" title="Hobbit lifestyles"&gt;hobbit-hole&lt;/a&gt;
</pre></div></div>

<h3 id="link-best-practices">Link Best Practices<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#link-best-practices" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>Markdown applications don’t agree on how to handle spaces in the middle of a URL. For compatibility, try to URL encode any spaces with %20. Alternatively, if your Markdown application <a href="#html">supports HTML</a>, you could use the a HTML tag.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>✅&nbsp; Do this</th>
      <th>❌&nbsp; Don't do this</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        
        [link](https://www.example.com/my%20great%20page)<br><br>

        &lt;a href="https://www.example.com/my great page"&gt;link&lt;/a&gt;<br><br>
        
      </td>
      <td>
        
        [link](https://www.example.com/my great page)<br><br>
        
      </td>
    </tr>
  </tbody>
</table>

<p>Parentheses in the middle of a URL can also be problematic. For compatibility, try to URL encode the opening parenthesis (() with %28 and the closing parenthesis ()) with %29. Alternatively, if your Markdown application <a href="#html">supports HTML</a>, you could use the a HTML tag.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>✅&nbsp; Do this</th>
      <th>❌&nbsp; Don't do this</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        
        [a novel](https://en.wikipedia.org/wiki/The_Milagro_Beanfield_War_%28novel%29)<br><br>

        &lt;a href="https://en.wikipedia.org/wiki/The_Milagro_Beanfield_War_(novel)"&gt;a novel&lt;/a&gt;<br><br>
        
      </td>
      <td>
        
        [a novel](https://en.wikipedia.org/wiki/The_Milagro_Beanfield_War_(novel))
        
      </td>
    </tr>
  </tbody>
</table>

<h2 id="images-1">Images<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#images-1" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h2>

<p>To add an image, add an exclamation mark (!), followed by alt text in brackets, and the path or URL to the image asset in parentheses. You can optionally add a title in quotation marks after the path or URL.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">![The San Juan Mountains are beautiful!](/assets/images/san-juan-mountains.jpg "San Juan Mountains")
</pre></div></div>

<p>The rendered output looks like this:</p>

<p><img srcset="https://mdg.imgix.net/assets/images/san-juan-mountains.jpg?auto=format&amp;fit=clip&amp;w=480 480w,              https://mdg.imgix.net/assets/images/san-juan-mountains.jpg?auto=format&amp;fit=clip&amp;q=40&amp;w=1080 1080w" src="https://mdg.imgix.net/assets/images/san-juan-mountains.jpg" class="img-fluid" title="San Juan Mountains" alt="The San Juan Mountains are beautiful!" loading="lazy" sizes="100vw"></p>


<h3 id="linking-images">Linking Images<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#linking-images" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>To add a link to an image, enclose the Markdown for the image in brackets, and then add the link in parentheses.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">[![An old rock in the desert](/assets/images/shiprock.jpg "Shiprock, New Mexico by Beau Rogers")](https://www.flickr.com/photos/beaurogers/31833779864/in/photolist-Qv3rFw-34mt9F-a9Cmfy-5Ha3Zi-9msKdv-o3hgjr-hWpUte-4WMsJ1-KUQ8N-deshUb-vssBD-6CQci6-8AFCiD-zsJWT-nNfsgB-dPDwZJ-bn9JGn-5HtSXY-6CUhAL-a4UTXB-ugPum-KUPSo-fBLNm-6CUmpy-4WMsc9-8a7D3T-83KJev-6CQ2bK-nNusHJ-a78rQH-nw3NvT-7aq2qf-8wwBso-3nNceh-ugSKP-4mh4kh-bbeeqH-a7biME-q3PtTf-brFpgb-cg38zw-bXMZc-nJPELD-f58Lmo-bXMYG-bz8AAi-bxNtNT-bXMYi-bXMY6-bXMYv)
</pre></div></div>

<p>The rendered output looks like this:</p>

<div>
  <a href="https://www.flickr.com/photos/beaurogers/31833779864/in/photolist-Qv3rFw-34mt9F-a9Cmfy-5Ha3Zi-9msKdv-o3hgjr-hWpUte-4WMsJ1-KUQ8N-deshUb-vssBD-6CQci6-8AFCiD-zsJWT-nNfsgB-dPDwZJ-bn9JGn-5HtSXY-6CUhAL-a4UTXB-ugPum-KUPSo-fBLNm-6CUmpy-4WMsc9-8a7D3T-83KJev-6CQ2bK-nNusHJ-a78rQH-nw3NvT-7aq2qf-8wwBso-3nNceh-ugSKP-4mh4kh-bbeeqH-a7biME-q3PtTf-brFpgb-cg38zw-bXMZc-nJPELD-f58Lmo-bXMYG-bz8AAi-bxNtNT-bXMYi-bXMY6-bXMYv" class="no-underline">
  
<img srcset="https://mdg.imgix.net/assets/images/shiprock.jpg?auto=format&amp;fit=clip&amp;w=480 480w,
             https://mdg.imgix.net/assets/images/shiprock.jpg?auto=format&amp;fit=clip&amp;q=40&amp;w=1080 1080w" src="https://mdg.imgix.net/assets/images/shiprock.jpg" class="img-fluid" title="Shiprock, New Mexico by Beau Rogers" alt="An old rock in the desert" loading="lazy" sizes="100vw">

  </a>
</div>

<h2 id="escaping-characters">Escaping Characters<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#escaping-characters" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h2>

<p>To display a literal character that would otherwise be used to format text in a Markdown document, add a backslash (\) in front of the character.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">\* Without the backslash, this would be a bullet in an unordered list.
</pre></div></div>

<p>The rendered output looks like this:</p>

<p>* Without the backslash, this would be a bullet in an unordered list.</p>

<h3 id="characters-you-can-escape">Characters You Can Escape<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#characters-you-can-escape" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>You can use a backslash to escape the following characters.</p>

<table class="table table-bordered">
  <thead class="thead-light">
    <tr>
      <th>Character</th>
      <th>Name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>\</td>
      <td>backslash</td>
    </tr>
    <tr>
      <td>`</td>
      <td>backtick (see also <a href="#escaping-backticks">escaping backticks in code</a>)</td>
    </tr>
    <tr>
      <td>*</td>
      <td>asterisk</td>
    </tr>
    <tr>
      <td>_</td>
      <td>underscore</td>
    </tr>
    <tr>
      <td>{ }</td>
      <td>curly braces</td>
    </tr>
    <tr>
      <td>[ ]</td>
      <td>brackets</td>
    </tr>
    <tr>
      <td>&lt; &gt;</td>
      <td>angle brackets</td>
    </tr>
    <tr>
      <td>( )</td>
      <td>parentheses</td>
    </tr>
    <tr>
      <td>#</td>
      <td>pound sign</td>
    </tr>
    <tr>
      <td>+</td>
      <td>plus sign</td>
    </tr>
    <tr>
      <td>-</td>
      <td>minus sign (hyphen)</td>
    </tr>
    <tr>
      <td>.</td>
      <td>dot</td>
    </tr>
    <tr>
      <td>!</td>
      <td>exclamation mark</td>
    </tr>
    <tr>
      <td>|</td>
      <td>pipe </td>
    </tr>
  </tbody>
</table>

<h2 id="html">HTML<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#html" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h2>


<p>To use HTML, place the tags in the text of your Markdown-formatted file.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight">This **word** is bold. This &lt;em&gt;word&lt;/em&gt; is italic.
</pre></div></div>

<p>The rendered output looks like this:</p>

<p>This <strong>word</strong> is bold. This <em>word</em> is italic.</p>

<h3 id="html-best-practices">HTML Best Practices<a class="anchorjs-link " aria-label="Anchor" data-anchorjs-icon="" href="#html-best-practices" style="font: 1em / 1 anchorjs-icons; padding-left: 0.375em;"></a></h3>

<p>For security reasons, not all Markdown applications support HTML in Markdown documents. When in doubt, check your Markdown application’s documentation. Some applications support only a subset of HTML tags.</p>

<p>Use blank lines to separate block-level HTML elements like &lt;div&gt;, &lt;table&gt;, &lt;pre&gt;, and &lt;p&gt; from the surrounding content. Try not to indent the tags with tabs or spaces — that can interfere with the formatting.</p>


## Tables
Certainly! Here's a Markdown cheatsheet for creating tables:

### Creating Tables in Markdown

Markdown supports simple table creation using pipes (`|`) and hyphens (`-`) to define the table's structure. Here's how you can create tables:

```markdown
| Header 1 | Header 2 | Header 3 |
| -------- | ------- | ------- |
| Row 1, Cell 1 | Row 1, Cell 2 | Row 1, Cell 3 |
| Row 2, Cell 1 | Row 2, Cell 2 | Row 2, Cell 3 |
```

- Use pipes `|` to separate columns.
- Use hyphens `-` to create the table header row.
- Rows below the header row contain the data.
- The number of pipes in each row must match the number of columns in the header row.

| Header 1 | Header 2 | Header 3 |
| -------- | ------- | ------- |
| Row 1, Cell 1 | Row 1, Cell 2 | Row 1, Cell 3 |
| Row 2, Cell 1 | Row 2, Cell 2 | Row 2, Cell 3 |

### Adjusting Column Alignment

You can specify the alignment of columns using colons within the header row:

- `:` to align left
- `:-` to align left (default)
- `-:` to align right
- `:-:` to align center

Example:

```markdown
| Left-aligned | Center-aligned | Right-aligned |
| :--- | :---: | ---: |
| Left | Center | Right |
```

| Left-aligned | Center-aligned | Right-aligned |
| :--- | :---: | ---: |
| Left | Center | Right |

### Adding Emphasis or Formatting

You can apply formatting and emphasis within table cells using Markdown syntax:

```markdown
| Header | Description |
| --- | --- |
| *Italic* | _Italic_ |
| **Bold** | __Bold__ |
| `Code` | [Link](http://example.com) |
```

| Header | Description |
| --- | --- |
| *Italic* | _Italic_ |
| **Bold** | __Bold__ |
| `Code` | [Link](http://example.com) |

### Multiline Cells

To create multiline cells, use line breaks within a cell and use additional pipes to create new lines:

```markdown
| Header | Description |
| --- | --- |
| This is a single line cell | This cell has multiple lines.  
You can continue on the next line. |
```

| Header | Description |
| --- | --- |
| This is a single line cell | This cell has multiple lines.  
You can continue on the next line. |

### Escape Special Characters

If you need to include pipe characters `|` or hyphens `-` within a cell without interpreting them as table delimiters, you can escape them with a backslash:

```markdown
| Header | Description |
| --- | --- |
| Pipe \ | Hyphen - |
```

| Header | Description |
| --- | --- |
| Pipe \ | Hyphen - |

### Empty Cells

You can include empty cells by leaving the cell content blank. However, you still need to use pipes to indicate the position of the empty cell:

```markdown
| Header 1 | Header 2 |
| --- | --- |
| Data |  |
|  | More Data |
```

| Header 1 | Header 2 |
| --- | --- |
| Data |  |
|  | More Data |

### HTML Tables

For more complex table layouts, you can also use HTML tables within Markdown:

```html
<table>
  <thead>
    <tr>
      <th>Header 1</th>
      <th>Header 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Data 1</td>
      <td>Data 2</td>
    </tr>
  </tbody>
</table>
```

While Markdown tables are suitable for simple tables, HTML tables offer more control over complex structures and styling.