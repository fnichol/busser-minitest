# <a name="title"></a> Busser::RunnerPlugin::Minitest

[![Gem Version](https://badge.fury.io/rb/busser-minitest.png)](http://badge.fury.io/rb/busser-minitest)
[![Build Status](https://travis-ci.org/test-kitchen/busser-minitest.png?branch=master)](https://travis-ci.org/test-kitchen/busser-minitest)
[![Code Climate](https://codeclimate.com/github/test-kitchen/busser-minitest.png)](https://codeclimate.com/github/test-kitchen/busser-minitest)

A Busser runner plugin for the [minitest][minitest_site] testing library

## Status

This software project is no longer under active development as it has no active maintainers. The software may continue to work for some or all use cases, but issues filed in GitHub will most likely not be triaged. If a new maintainer is interested in working on this project please come chat with us in #test-kitchen on Chef Community Slack.

## <a name="installation"></a> Installation and Setup

Until proper reference documentation is complete, the [Writing a Test](http://kitchen.ci/docs/getting-started/writing-test) section of the Test Kitchen's [Getting Started Guide](http://kitchen.ci/docs/getting-started/) gives a working example of creating test.

## <a name="usage"></a> Usage
Assuming a cookbook with with the following structure (some directories omitted for
brevity), and a .kitchen.yml has been written with one suite per recipe.

```
.
├── Berksfile
├── Berksfile.lock
├── CHANGELOG.md
├── README.md
├── Thorfile
├── attributes
│   └── default.rb
├── chefignore
├── definitions
├── files
│   └── default
│       ├── bar.txt
│       ├── foo.txt
│       └── foobar.txt
├── libraries
├── metadata.rb
├── providers
├── recipes
│   ├── bar.rb
│   ├── default.rb
│   └── foo.rb
├── resources
├── templates
│   └── default
```

The test directory follows a similar structure to the recipes directory.  In the integration directory,
there should be a directory for each recipe, which contains a directory for each busser being used.  In
this example, we're only using minitest.  Finally, the actual test files themselves live inside the busser
directory.  The test files must be named either test_*.rb or *_spec.rb in order to be parsed.

```
└── test
    └── integration
        ├── bar
        │   └── minitest
        │       └── test_bar.rb
        ├── default
        │   └── minitest
        │       └── test_default.rb
        └── foo
            └── minitest
                └── test_foo.rb
```

The test files use standard minitest assertions, constructs etc.  As an example, the test_default.rb file
listed above might have the following content to check for the existence of a particulare file.


```
require 'minitest/autorun'

describe "foobar::default" do

  it "has created foobar.txt" do
    assert File.exists?("/usr/local/foobar.txt")
  end
end
```

## <a name="development"></a> Development

* Source hosted at [GitHub][repo]
* Report issues/questions/feature requests on [GitHub Issues][issues]

Pull requests are very welcome! Make sure your patches are well tested.
Ideally create a topic branch for every separate change you make. For
example:

1. Fork the repo
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## <a name="authors"></a> Authors

Created and maintained by [Fletcher Nichol][author] (<fnichol@nichol.ca>)

## <a name="license"></a> License

Apache 2.0 (see [LICENSE][license])


[author]:           https://github.com/enter-github-user
[issues]:           https://github.com/enter-github-user/busser-minitest/issues
[license]:          https://github.com/enter-github-user/busser-minitest/blob/master/LICENSE
[repo]:             https://github.com/enter-github-user/busser-minitest

[minitest_site]:    https://github.com/seattlerb/minitest
