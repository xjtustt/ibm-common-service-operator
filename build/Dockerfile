#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

FROM registry.access.redhat.com/ubi8/ubi-minimal:latest
ARG VCS_REF
ARG VCS_URL

LABEL org.label-schema.vendor="IBM" \
    org.label-schema.name="ibm common service operator" \
    org.label-schema.description="Deploy ODLM and related instances" \
    org.label-schema.vcs-ref=$VCS_REF \
    org.label-schema.vcs-url=$VCS_URL \
    org.label-schema.license="Licensed Materials - Property of IBM" \
    org.label-schema.schema-version="1.0" \
    name="common-service-operator" \
    vendor="IBM" \
    description="Deploy ODLM and related instances" \
    summary="Deploy ODLM and related instances"

ENV OPERATOR=/usr/local/bin/ibm-common-service-operator \
    USER_UID=1001 \
    USER_NAME=ibm-common-service-operator

# install operator binary
COPY build/_output/bin/ibm-common-service-operator ${OPERATOR}

COPY build/bin /usr/local/bin
RUN  /usr/local/bin/user_setup

# copy licenses
RUN mkdir /licenses
COPY LICENSE /licenses

ENTRYPOINT ["/usr/local/bin/entrypoint"]

USER ${USER_UID}
