#
# Licensed to the Apache Software Foundation (ASF) under one
# or more contributor license agreements. See the NOTICE file
# distributed with this work for additional information
# regarding copyright ownership. The ASF licenses this file
# to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance
# with the License. You may obtain a copy of the License at
#
#   http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing,
# software distributed under the License is distributed on an
# "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
# KIND, either express or implied. See the License for the
# specific language governing permissions and limitations
# under the License.
#

DESTDIR ?= /

if HAVE_BUNDLER

all-local:
	$(BUNDLER) install
	$(BUNDLER) exec rake build_ext

install-exec-hook:
	$(BUNDLER) exec rake install

clean-local:
	$(BUNDLER) install
	$(BUNDLER) exec rake clean
	$(RM) -r spec/gen-rb/

check-local: all
	$(BUNDLER) install
	$(BUNDLER) exec rake

endif

dist-hook:
	$(RM) -r $(distdir)/spec/gen-rb/

distdir:
	$(MAKE) $(AM_MAKEFLAGS) distdir-am

EXTRA_DIST = \
	coding_standards.md \
	Rakefile \
	Gemfile \
	thrift.gemspec \
	lib \
	ext \
	benchmark \
	script \
	spec \
	README.md
