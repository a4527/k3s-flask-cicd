## console result##

Started by GitHub push by a4527
Obtained Jenkinsfile from git https://github.com/a4527/k3s-flask-cicd
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/lib/jenkins/workspace/k3s-flask-cicd
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Declarative: Checkout SCM)
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
using credential github-pat
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/k3s-flask-cicd/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/a4527/k3s-flask-cicd # timeout=10
Fetching upstream changes from https://github.com/a4527/k3s-flask-cicd
 > git --version # timeout=10
 > git --version # 'git version 2.34.1'
using GIT_ASKPASS to set credentials github token
 > git fetch --tags --force --progress -- https://github.com/a4527/k3s-flask-cicd +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse origin/main^{commit} # timeout=10
Checking out Revision c209b7d6fcdbfd4a26f6a1d53c5e02046081245c (origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f c209b7d6fcdbfd4a26f6a1d53c5e02046081245c # timeout=10
Commit message: "test"
 > git rev-list --no-walk 8e313c9c321b888778fa3f6593ccc4a0d6158574 # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Checkout)
[Pipeline] git
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/k3s-flask-cicd/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/a4527/k3s-flask-cicd # timeout=10
Fetching upstream changes from https://github.com/a4527/k3s-flask-cicd
 > git --version # timeout=10
 > git --version # 'git version 2.34.1'
 > git fetch --tags --force --progress -- https://github.com/a4527/k3s-flask-cicd +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
Checking out Revision c209b7d6fcdbfd4a26f6a1d53c5e02046081245c (refs/remotes/origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f c209b7d6fcdbfd4a26f6a1d53c5e02046081245c # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git branch -D main # timeout=10
 > git checkout -b main c209b7d6fcdbfd4a26f6a1d53c5e02046081245c # timeout=10
Commit message: "test"
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build Flask1)
[Pipeline] sh
+ docker build -f Dockerfile1 -t flask1:latest .
DEPRECATED: The legacy builder is deprecated and will be removed in a future release.
            Install the buildx component to build images with BuildKit:
            https://docs.docker.com/go/buildx/

Sending build context to Docker daemon  165.4kB
Step 1/5 : FROM python:3.10-slim
 ---> df5efab85283
Step 2/5 : WORKDIR /app
 ---> Using cache
 ---> 2217c5eaaeda
Step 3/5 : COPY app1/app.py .
 ---> 6013df4f911a
Step 4/5 : RUN pip install flask
 ---> Running in 53563f0e940e
Collecting flask
  Downloading flask-3.1.2-py3-none-any.whl (103 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 103.3/103.3 kB 1.7 MB/s eta 0:00:00
Collecting markupsafe>=2.1.1
  Downloading markupsafe-3.0.3-cp310-cp310-manylinux2014_aarch64.manylinux_2_17_aarch64.manylinux_2_28_aarch64.whl (22 kB)
Collecting click>=8.1.3
  Downloading click-8.3.1-py3-none-any.whl (108 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 108.3/108.3 kB 1.2 MB/s eta 0:00:00
Collecting blinker>=1.9.0
  Downloading blinker-1.9.0-py3-none-any.whl (8.5 kB)
Collecting jinja2>=3.1.2
  Downloading jinja2-3.1.6-py3-none-any.whl (134 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 134.9/134.9 kB 2.6 MB/s eta 0:00:00
Collecting werkzeug>=3.1.0
  Downloading werkzeug-3.1.3-py3-none-any.whl (224 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 224.5/224.5 kB 11.1 MB/s eta 0:00:00
Collecting itsdangerous>=2.2.0
  Downloading itsdangerous-2.2.0-py3-none-any.whl (16 kB)
Installing collected packages: markupsafe, itsdangerous, click, blinker, werkzeug, jinja2, flask
Successfully installed blinker-1.9.0 click-8.3.1 flask-3.1.2 itsdangerous-2.2.0 jinja2-3.1.6 markupsafe-3.0.3 werkzeug-3.1.3
[91mWARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv
[0m[91m
[notice] A new release of pip is available: 23.0.1 -> 25.3
[notice] To update, run: pip install --upgrade pip
[0m ---> Removed intermediate container 53563f0e940e
 ---> e8bc77914c25
Step 5/5 : CMD ["python", "app.py"]
 ---> Running in 79a99f70194d
 ---> Removed intermediate container 79a99f70194d
 ---> ddcaafc601c8
Successfully built ddcaafc601c8
Successfully tagged flask1:latest
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build Flask2)
[Pipeline] sh
+ docker build -f Dockerfile2 -t flask2:latest .
DEPRECATED: The legacy builder is deprecated and will be removed in a future release.
            Install the buildx component to build images with BuildKit:
            https://docs.docker.com/go/buildx/

Sending build context to Docker daemon  165.4kB
Step 1/5 : FROM python:3.10-slim
 ---> df5efab85283
Step 2/5 : WORKDIR /app
 ---> Using cache
 ---> 2217c5eaaeda
Step 3/5 : COPY app2/app.py .
 ---> Using cache
 ---> 35ad351543ec
Step 4/5 : RUN pip install flask
 ---> Using cache
 ---> 82e45c7b0f7a
Step 5/5 : CMD ["python", "app.py"]
 ---> Using cache
 ---> 22fbb93f1934
Successfully built 22fbb93f1934
Successfully tagged flask2:latest
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (OCIR Login)
[Pipeline] withCredentials
Masking supported pattern matches of $OCIR_PASS
[Pipeline] {
[Pipeline] sh
+ docker login yny.ocir.io -u axvejxrm1ole/jenkins -p ****
WARNING! Using --password via the CLI is insecure. Use --password-stdin.
Login Succeeded
[Pipeline] }
[Pipeline] // withCredentials
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Push Images)
[Pipeline] sh
+ docker tag flask1:latest yny.ocir.io/axvejxrm1ole/flask1:latest
+ docker tag flask2:latest yny.ocir.io/axvejxrm1ole/flask2:latest
+ docker push yny.ocir.io/axvejxrm1ole/flask1:latest
The push refers to repository [yny.ocir.io/axvejxrm1ole/flask1]
7a5e2cb133c3: Preparing
467b1323bc96: Preparing
ee28b7df1bae: Preparing
d726acc4028e: Preparing
2965b6f53218: Preparing
1c2841c36946: Preparing
4819483eb3e4: Preparing
1c2841c36946: Waiting
4819483eb3e4: Waiting
d726acc4028e: Layer already exists
ee28b7df1bae: Layer already exists
2965b6f53218: Layer already exists
1c2841c36946: Layer already exists
4819483eb3e4: Layer already exists
467b1323bc96: Pushed
7a5e2cb133c3: Pushed
latest: digest: sha256:16175c624d547a0fdc4c2d75b1f5d6416d7bdb01e99772901f21dd904f72efbb size: 1783
+ docker push yny.ocir.io/axvejxrm1ole/flask2:latest
The push refers to repository [yny.ocir.io/axvejxrm1ole/flask2]
a5d7846c977e: Preparing
853d24db089d: Preparing
ee28b7df1bae: Preparing
d726acc4028e: Preparing
2965b6f53218: Preparing
1c2841c36946: Preparing
4819483eb3e4: Preparing
1c2841c36946: Waiting
4819483eb3e4: Waiting
853d24db089d: Layer already exists
2965b6f53218: Layer already exists
d726acc4028e: Layer already exists
a5d7846c977e: Layer already exists
1c2841c36946: Layer already exists
4819483eb3e4: Layer already exists
ee28b7df1bae: Layer already exists
latest: digest: sha256:bb899e4a9e5dc27269ec3f24a7c472f3f83da7b2533f75eb5fd80f9c433c579a size: 1783
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Deploy to K8s)
[Pipeline] sh
+ kubectl apply -f k8s/
deployment.apps/flask1 unchanged
service/flask1-service unchanged
deployment.apps/flask2 unchanged
service/flask2-service unchanged
ingress.networking.k8s.io/flask-ingress unchanged
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
