<!--

@license Apache-2.0

Copyright (c) 2018 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# incrme

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Compute the [mean error][mean-absolute-error] (ME) incrementally.

<section class="intro">

The [mean error][mean-absolute-error] is defined as

<!-- <equation class="equation" label="eq:mean_error" align="center" raw="\operatorname{ME} = \frac{1}{n} \sum_{i=0}^{n-1} (y_i - x_i)" alt="Equation for the mean error."> -->

```math
\mathop{\mathrm{ME}} = \frac{1}{n} \sum_{i=0}^{n-1} (y_i - x_i)
```

<!-- <div class="equation" align="center" data-raw-text="\operatorname{ME} = \frac{1}{n} \sum_{i=0}^{n-1} (y_i - x_i)" data-equation="eq:mean_error">
    <img src="https://cdn.jsdelivr.net/gh/stdlib-js/stdlib@7d6e6319f451be0997d35a6cf491b08e1f2cb5cf/lib/node_modules/@stdlib/stats/incr/me/docs/img/equation_mean_error.svg" alt="Equation for the mean error.">
    <br>
</div> -->

<!-- </equation> -->

</section>

<!-- /.intro -->

<section class="installation">

## Installation

```bash
npm install @stdlib/stats-incr-me
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm`][esm-url] branch (see [README][esm-readme]).
-   If you are using Deno, visit the [`deno`][deno-url] branch (see [README][deno-readme] for usage intructions).
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd`][umd-url] branch (see [README][umd-readme]).

The [branches.md][branches-url] file summarizes the available branches and displays a diagram illustrating their relationships.

To view installation and usage instructions specific to each branch build, be sure to explicitly navigate to the respective README files on each branch, as linked to above.

</section>

<section class="usage">

## Usage

```javascript
var incrme = require( '@stdlib/stats-incr-me' );
```

#### incrme()

Returns an accumulator `function` which incrementally computes the [mean error][mean-absolute-error].

```javascript
var accumulator = incrme();
```

#### accumulator( \[x, y] )

If provided input values `x` and `y`, the accumulator function returns an updated [mean error][mean-absolute-error]. If not provided input values `x` and `y`, the accumulator function returns the current [mean error][mean-absolute-error].

```javascript
var accumulator = incrme();

var m = accumulator( 2.0, 3.0 );
// returns 1.0

m = accumulator( -1.0, -4.0 );
// returns -1.0

m = accumulator( -3.0, 5.0 );
// returns 2.0

m = accumulator();
// returns 2.0
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   Input values are **not** type checked. If provided `NaN` or a value which, when used in computations, results in `NaN`, the accumulated value is `NaN` for **all** future invocations. If non-numeric inputs are possible, you are advised to type check and handle accordingly **before** passing the value to the accumulator function.
-   Be careful when interpreting the [mean error][mean-absolute-error] as errors can cancel. This stated, that errors can cancel makes the [mean error][mean-absolute-error] suitable for measuring the bias in forecasts.
-   **Warning**: the [mean error][mean-absolute-error] is scale-dependent and, thus, the measure should **not** be used to make comparisons between datasets having different scales.

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var randu = require( '@stdlib/random-base-randu' );
var incrme = require( '@stdlib/stats-incr-me' );

var accumulator;
var v1;
var v2;
var i;

// Initialize an accumulator:
accumulator = incrme();

// For each simulated datum, update the mean error...
for ( i = 0; i < 100; i++ ) {
    v1 = ( randu()*100.0 ) - 50.0;
    v2 = ( randu()*100.0 ) - 50.0;
    accumulator( v1, v2 );
}
console.log( accumulator() );
```

</section>

<!-- /.examples -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

* * *

## See Also

-   <span class="package-name">[`@stdlib/stats-incr/mae`][@stdlib/stats/incr/mae]</span><span class="delimiter">: </span><span class="description">compute the mean absolute error (MAE) incrementally.</span>
-   <span class="package-name">[`@stdlib/stats-incr/mean`][@stdlib/stats/incr/mean]</span><span class="delimiter">: </span><span class="description">compute an arithmetic mean incrementally.</span>
-   <span class="package-name">[`@stdlib/stats-incr/mme`][@stdlib/stats/incr/mme]</span><span class="delimiter">: </span><span class="description">compute a moving mean error (ME) incrementally.</span>

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2025. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/stats-incr-me.svg
[npm-url]: https://npmjs.org/package/@stdlib/stats-incr-me

[test-image]: https://github.com/stdlib-js/stats-incr-me/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/stats-incr-me/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/stats-incr-me/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/stats-incr-me?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/stats-incr-me.svg
[dependencies-url]: https://david-dm.org/stdlib-js/stats-incr-me/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/stats-incr-me/tree/deno
[deno-readme]: https://github.com/stdlib-js/stats-incr-me/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/stats-incr-me/tree/umd
[umd-readme]: https://github.com/stdlib-js/stats-incr-me/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/stats-incr-me/tree/esm
[esm-readme]: https://github.com/stdlib-js/stats-incr-me/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/stats-incr-me/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/stats-incr-me/main/LICENSE

[mean-absolute-error]: https://en.wikipedia.org/wiki/Mean_absolute_error

<!-- <related-links> -->

[@stdlib/stats/incr/mae]: https://github.com/stdlib-js/stats-incr-mae

[@stdlib/stats/incr/mean]: https://github.com/stdlib-js/stats-incr-mean

[@stdlib/stats/incr/mme]: https://github.com/stdlib-js/stats-incr-mme

<!-- </related-links> -->

</section>

<!-- /.links -->
