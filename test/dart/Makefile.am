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

gen-dart/thrift_test/lib/thrift_test.dart: ../v0.16/ThriftTest.thrift
	$(THRIFT) --gen dart ../v0.16/ThriftTest.thrift

pub-get-gen: gen-dart/thrift_test/lib/thrift_test.dart
	cd gen-dart/thrift_test; ${DARTPUB} get

pub-get: pub-get-gen
	cd test_client; ${DARTPUB} get

stubs: gen-dart/thrift_test/lib/thrift_test.dart pub-get

precross: stubs

check: stubs

clean-local:
	$(RM) -r gen-dart/ test_client/.pub
	find . -type d -name ".dart_tool" | xargs $(RM) -r
	find . -type d -name "packages" | xargs $(RM) -r
	find . -type f -name ".packages" | xargs $(RM)
	find . -type f -name "pubspec.lock" | xargs $(RM)

dist-hook:
	$(RM) -r $(distdir)/gen-dart/ $(distdir)/test_client/.pub
	find $(distdir) -type d -name ".dart_tool" | xargs $(RM) -r
	find $(distdir) -type d -name "packages" | xargs $(RM) -r
	find $(distdir) -type f -name ".packages" | xargs $(RM)

client: stubs
	${DART} test_client/bin/main.dart

distdir:
	$(MAKE) $(AM_MAKEFLAGS) distdir-am

EXTRA_DIST = \
	test_client
