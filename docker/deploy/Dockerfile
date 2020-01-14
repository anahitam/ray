# The deploy Docker image build a self-contained Ray instance suitable
# for end users.

FROM ray-project/base-deps
ADD ray.tar /ray
ADD git-rev /ray/git-rev
RUN /ray/ci/travis/install-bazel.sh
ENV PATH=$PATH:/root/bin
WORKDIR /ray/python
RUN pip install msgpack
RUN pip install dask==0.17.0 
RUN pip install setuptools==41.0.0
RUN pip install click==7.0
RUN pip install cloudpickle==1.2.0
RUN pip install wrapt --upgrade --ignore-installed
RUN ["apt-get", "install", "-y", "libsm6", "libxext6", "libxrender-dev"]
RUN pip install -e .[all]
WORKDIR /ray
RUN pip install gym ipdb tensorflow 
