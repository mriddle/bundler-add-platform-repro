### Reproducing a bundler error

_Unable to add the linux platform_

**Setup**

    bundler --version
    // Bundler version 2.2.8
    bundler init
    // add gem 'nokogiri'
    bundle lock
    bundle package --all-platforms

**Reproduce** with `DEBUG_RESOLVER=1 bundle lock --add-platform x86_64-linux`

    :   0: Starting resolution (2021-02-10 16:23:09 +0100)
    :   0: User-requested dependencies: [#<Gem::Resolver::DependencyRequest:0x00007fe6e28589e8 @dependency=<Gem::Dependency type=:runtime name="did_you_mean" requirements="= 1.3.0">, @requester=nil>, #<Gem::Resolver::DependencyRequest:0x00007fe6e28589c0 @dependency=<Gem::Dependency type=:runtime name="bundler" requirements="= 2.2.8">, @requester=nil>]
    Resolving dependencies...:   0: Creating possibility state for did_you_mean (= 1.3.0) (1 remaining)
    :   1: Attempting to activate [did_you_mean-1.3.0]
    :   1: Activated did_you_mean at [did_you_mean-1.3.0]
    :   1: Requiring nested dependencies ()
    :   1: Creating possibility state for bundler (= 2.2.8) (1 remaining)
    :   2: Attempting to activate [bundler-2.2.8]
    :   2: Activated bundler at [bundler-2.2.8]
    :   2: Requiring nested dependencies ()

    :   0: Finished resolution (2 steps) (Took 0.005865 seconds) (2021-02-10 16:23:09 +0100)
    :   0: Unactivated:
    :   0: Activated: did_you_mean, bundler
    Fetching gem metadata from https://rubygems.org/.......
    BUNDLER: Starting resolution (2021-02-10 16:23:10 +0100)
    BUNDLER: User-requested dependencies: [#<Bundler::DepProxy:0x00007fe6de969840 @dep=<Bundler::Dependency type=:runtime name="nokogiri" requirements="= 1.11.1">, @__platform=#<Gem::Platform:0x00007fe6df2daca8 @cpu="x86_64", @os="darwin", @version="19" @cpu="x86_64", @os="darwin", @version="19">>, #<Bundler::DepProxy:0x00007fe6de9697a0 @dep=<Bundler::Dependency type=:runtime name="nokogiri" requirements="= 1.11.1">, @__platform=#<Gem::Platform:0x00007fe6de963148 @cpu="x86_64", @os="linux", @version=nil @cpu="x86_64", @os="linux", @version=nil>>, #<Bundler::DepProxy:0x00007fe6de973db8 @dep=<Bundler::Dependency type=:runtime name="Ruby\u0000" requirements=">= 0">, @__platform=#<Gem::Platform:0x00007fe6df2daca8 @cpu="x86_64", @os="darwin", @version="19" @cpu="x86_64", @os="darwin", @version="19">>, #<Bundler::DepProxy:0x00007fe6de973d18 @dep=<Bundler::Dependency type=:runtime name="Ruby\u0000" requirements=">= 0">, @__platform=#<Gem::Platform:0x00007fe6de963148 @cpu="x86_64", @os="linux", @version=nil @cpu="x86_64", @os="linux", @version=nil>>, #<Bundler::DepProxy:0x00007fe6de973c28 @dep=<Bundler::Dependency type=:runtime name="RubyGems\u0000" requirements="= 3.2.5">, @__platform=#<Gem::Platform:0x00007fe6df2daca8 @cpu="x86_64", @os="darwin", @version="19" @cpu="x86_64", @os="darwin", @version="19">>, #<Bundler::DepProxy:0x00007fe6de973b88 @dep=<Bundler::Dependency type=:runtime name="RubyGems\u0000" requirements="= 3.2.5">, @__platform=#<Gem::Platform:0x00007fe6de963148 @cpu="x86_64", @os="linux", @version=nil @cpu="x86_64", @os="linux", @version=nil>>]
    Resolving dependencies...
    BUNDLER: Creating possibility state for nokogiri (= 1.11.1) x86_64-darwin-19 (2 remaining)
    BUNDLER(1): Attempting to activate [nokogiri (1.11.1) (x86_64-darwin-19, x86_64-linux)]
    BUNDLER(1): Activated nokogiri at [nokogiri (1.11.1) (x86_64-darwin-19, x86_64-linux)]
    BUNDLER(1): Requiring nested dependencies (racc (~> 1.4) x86_64-darwin-19, racc (~> 1.4) x86_64-linux, Ruby (< 3.1.dev, >= 2.5) x86_64-linux)
    BUNDLER(1): Creating possibility state for nokogiri (= 1.11.1) x86_64-linux (2 remaining)
    BUNDLER(2): Attempting to activate [nokogiri (1.11.1) (x86_64-darwin-19, x86_64-linux)]
    BUNDLER(2): Found existing spec ([nokogiri (1.11.1) (x86_64-darwin-19, x86_64-linux)])
    BUNDLER(2): Creating possibility state for racc (~> 1.4) x86_64-darwin-19 (1 remaining)
    BUNDLER(3): Attempting to activate [racc (1.5.2) (ruby), racc (1.5.2) (x86_64-darwin-19, x86_64-linux)]
    BUNDLER(3): Activated racc at [racc (1.5.2) (ruby), racc (1.5.2) (x86_64-darwin-19, x86_64-linux)]
    BUNDLER(3): Requiring nested dependencies ()
    BUNDLER(3): Creating possibility state for racc (~> 1.4) x86_64-linux (1 remaining)
    BUNDLER(4): Attempting to activate [racc (1.5.2) (ruby), racc (1.5.2) (x86_64-darwin-19, x86_64-linux)]
    BUNDLER(4): Found existing spec ([racc (1.5.2) (ruby), racc (1.5.2) (x86_64-darwin-19, x86_64-linux)])
    BUNDLER(4): Creating possibility state for Ruby x86_64-darwin-19 (1 remaining)
    BUNDLER(5): Attempting to activate [Ruby (2.6.6.146) (x86_64-darwin-19), Ruby (2.6.6.146) (x86_64-darwin-19)]
    BUNDLER(5): Activated Ruby at [Ruby (2.6.6.146) (x86_64-darwin-19), Ruby (2.6.6.146) (x86_64-darwin-19)]
    BUNDLER(5): Requiring nested dependencies ()
    BUNDLER(5): Creating possibility state for RubyGems (= 3.2.5) x86_64-darwin-19 (1 remaining)
    BUNDLER(6): Attempting to activate [RubyGems (3.2.5) (ruby), RubyGems (3.2.5) (x86_64-darwin-19, x86_64-linux)]
    BUNDLER(6): Activated RubyGems at [RubyGems (3.2.5) (ruby), RubyGems (3.2.5) (x86_64-darwin-19, x86_64-linux)]
    BUNDLER(6): Requiring nested dependencies ()
    BUNDLER(6): Creating possibility state for Ruby (< 3.1.dev, >= 2.5) x86_64-linux (1 remaining)
    BUNDLER(7): Attempting to activate [Ruby (2.6.6.146) (x86_64-linux), Ruby (2.6.6.146) (x86_64-linux)]
    BUNDLER(7): Found existing spec ([Ruby (2.6.6.146) (x86_64-darwin-19), Ruby (2.6.6.146) (x86_64-darwin-19)])
    BUNDLER(7): Unsatisfied by existing spec ([Ruby (2.6.6.146) (x86_64-darwin-19), Ruby (2.6.6.146) (x86_64-darwin-19)])
    BUNDLER(7): Unwinding for conflict: Ruby (< 3.1.dev, >= 2.5) x86_64-linux to 0
    BUNDLER: Creating possibility state for nokogiri (= 1.11.1) x86_64-darwin-19 (1 remaining)
    BUNDLER(1): Attempting to activate [nokogiri (1.11.1) (ruby)]
    BUNDLER(1): Activated nokogiri at [nokogiri (1.11.1) (ruby)]
    BUNDLER(1): Requiring nested dependencies (racc (~> 1.4), mini_portile2 (~> 2.5.0))
    BUNDLER(1): Creating possibility state for nokogiri (= 1.11.1) x86_64-linux (2 remaining)
    BUNDLER(2): Attempting to activate [nokogiri (1.11.1) (x86_64-darwin-19, x86_64-linux)]
    BUNDLER(2): Found existing spec ([nokogiri (1.11.1) (ruby)])
    BUNDLER(2): Unsatisfied by existing spec ([nokogiri (1.11.1) (ruby)])
    BUNDLER(2): Unwinding for conflict: nokogiri (= 1.11.1) x86_64-linux to 1
    BUNDLER(1): Creating possibility state for nokogiri (= 1.11.1) x86_64-linux (1 remaining)
    BUNDLER(2): Attempting to activate [nokogiri (1.11.1) (ruby)]
    BUNDLER(2): Found existing spec ([nokogiri (1.11.1) (ruby)])
    BUNDLER(2): Creating possibility state for racc (~> 1.4) (1 remaining)
    BUNDLER(3): Attempting to activate [racc (1.5.2) (ruby), racc (1.5.2) (x86_64-darwin-19, x86_64-linux)]
    BUNDLER(3): Activated racc at [racc (1.5.2) (ruby), racc (1.5.2) (x86_64-darwin-19, x86_64-linux)]
    BUNDLER(3): Requiring nested dependencies ()
    BUNDLER(3): Creating possibility state for Ruby x86_64-darwin-19 (1 remaining)
    BUNDLER(4): Attempting to activate [Ruby (2.6.6.146) (x86_64-darwin-19), Ruby (2.6.6.146) (x86_64-darwin-19)]
    BUNDLER(4): Activated Ruby at [Ruby (2.6.6.146) (x86_64-darwin-19), Ruby (2.6.6.146) (x86_64-darwin-19)]
    BUNDLER(4): Requiring nested dependencies ()
    BUNDLER(4): Creating possibility state for Ruby x86_64-linux (1 remaining)
    BUNDLER(5): Attempting to activate [Ruby (2.6.6.146) (x86_64-linux), Ruby (2.6.6.146) (x86_64-linux)]
    BUNDLER(5): Found existing spec ([Ruby (2.6.6.146) (x86_64-darwin-19), Ruby (2.6.6.146) (x86_64-darwin-19)])
    BUNDLER(5): Unsatisfied by existing spec ([Ruby (2.6.6.146) (x86_64-darwin-19), Ruby (2.6.6.146) (x86_64-darwin-19)])
    BUNDLER(5): Unwinding for conflict: Ruby x86_64-linux to -1

    BUNDLER: Finished resolution (13 steps) (Took 0.007066 seconds) (2021-02-10 16:23:10 +0100)
    Bundler found conflicting requirements for the Ruby version:
      In Gemfile:
        Ruby

    Bundler could not find compatible versions for gem "nokogiri":
      In snapshot (Gemfile.lock):
        nokogiri (= 1.11.1)

      In Gemfile:
        nokogiri (= 1.11.1)

    Running `bundle update` will rebuild your snapshot from scratch, using only
    the gems in your Gemfile, which may resolve the conflict.
