---
layout: page
title: "JavaScript rand function"
comments: true
sharing: true
footer: true
sidebar: false
alias:
- /functions/view/rand:498
- /functions/view/rand
- /functions/view/498
- /functions/rand:498
- /functions/498
---
<!-- Generated by Rakefile:build -->
A JavaScript equivalent of PHP's rand

{% codeblock math/rand.js lang:js https://raw.github.com/kvz/phpjs/master/functions/math/rand.js raw on github %}
function rand (min, max) {
  // http://kevin.vanzonneveld.net
  // +   original by: Leslie Hoare
  // +   bugfixed by: Onno Marsman
  // %          note 1: See the commented out code below for a version which will work with our experimental (though probably unnecessary) srand() function)
  // *     example 1: rand(1, 1);
  // *     returns 1: 1
  var argc = arguments.length;
  if (argc === 0) {
    min = 0;
    max = 2147483647;
  } else if (argc === 1) {
    throw new Error('Warning: rand() expects exactly 2 parameters, 1 given');
  }
  return Math.floor(Math.random() * (max - min + 1)) + min;

/*
  // See note above for an explanation of the following alternative code

  // +   reimplemented by: Brett Zamir (http://brett-zamir.me)
  // -    depends on: srand
  // %          note 1: This is a very possibly imperfect adaptation from the PHP source code
  var rand_seed, ctx, PHP_RAND_MAX=2147483647; // 0x7fffffff

  if (!this.php_js || this.php_js.rand_seed === undefined) {
    this.srand();
  }
  rand_seed = this.php_js.rand_seed;

  var argc = arguments.length;
  if (argc === 1) {
    throw new Error('Warning: rand() expects exactly 2 parameters, 1 given');
  }

  var do_rand = function (ctx) {
    return ((ctx * 1103515245 + 12345) % (PHP_RAND_MAX + 1));
  };

  var php_rand = function (ctxArg) { // php_rand_r
    this.php_js.rand_seed = do_rand(ctxArg);
    return parseInt(this.php_js.rand_seed, 10);
  };

  var number = php_rand(rand_seed);

  if (argc === 2) {
    number = min + parseInt(parseFloat(parseFloat(max) - min + 1.0) * (number/(PHP_RAND_MAX + 1.0)), 10);
  }
  return number;
  */
}
{% endcodeblock %}

 - [view on github](https://github.com/kvz/phpjs/blob/master/functions/math/rand.js)
 - [edit on github](https://github.com/kvz/phpjs/edit/master/functions/math/rand.js)

### Example 1
This code
{% codeblock lang:js example %}
rand(1, 1);
{% endcodeblock %}

Should return
{% codeblock lang:js returns %}
1
{% endcodeblock %}


### Other PHP functions in the math extension
{% render_partial _includes/custom/math.html %}
## Legacy comments
These were imported from our old site. Please use disqus below for new comments
<div style="overflow-y: scroll; max-height: 500px;">
{% render_partial functions/rand/_comments.html %}
</div>
