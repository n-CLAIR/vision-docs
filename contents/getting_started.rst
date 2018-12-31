.. _getting started:

Getting started
===============

Sign-up
-------

    https://hack.nsml.navercorp.com/signup 에서 Github 계정으로 가입합니다.
    모든 참가자는 Team 안에 속해 있어야 합니다. Team에 속한 사람들끼리 session을 공유할 수 있습니다.

    .. note:: Github 계정과 Team 이름은 다음과 같은 규칙을 만족해야 합니다.

        - Github username은 **5자리 이상** 으로 지정해야 합니다.
        - Team 이름은 **대/소문자 영어 5~20자리, 특수문자는 “_” 만** 사용하여 지정해야 합니다.
        - Team 이름과 동일한 Github username이 없어야 합니다. 모두 **다르게** 지정해야 합니다.

    .. note:: **Github에서 Two-factor authentication을 해제해야 사용 가능합니다.**

        (확인 방법 : Settings > Security > Two-factor authentication 체크)


Install nsml
------------

    https://hack.nsml.navercorp.com/download 페이지에서 자신의 플랫폼에 맞는 NSML을 다운받습니다.

    혹은 `wget` 명령어를 이용해서 받습니다. (아래 예제는 mac버전의 NSML을 다운받습니다.)

    .. code-block:: console

        wget https://github.com/n-CLAIR/nsml_client-hack/raw/master/nsml_client.darwin.amd64.hack.tar.gz



Install local-nsml
------------------

    What is a local-nsml?
        NSML에 올리는 코드를 로컬 환경에서 디버깅할 때, NSML의 라이브러리에 대해서 생기는 `ImportError` 를 방지하기 위한 파이썬 패키지입니다.

    pip가 이미 설치되어 있다는 전제 하에, 아래 명령어를 입력하면 됩니다.

    .. code-block:: console

        pip install git+https://github.com/n-CLAIR/nsml-local


Login
------

    NSML을 사용하기 위해선 로그인을 해야 합니다.
    Github 아이디와 비밀번호로 로그인합니다. 아래 소스 코드에서는 ``nsmlteam`` 을 Github 아이디로 사용하여 로그인하겠습니다.

    .. code-block:: console

        $ nsml login
        INFO[2018/11/19 12:31:40.032] connecting to hack-cli.nsml.navercorp.com:18553
        INFO[2018/11/19 12:31:42.058] there is no update
        GitHub Username: nsmlteam
        GitHub Password: **********
        INFO[2018/11/19 12:33:42.355] Welcome to NSML!

Path registration
------------------

    다양한 위치에서 nsml을 실행하기 위해서 path 설정을 해주는 것을 권장합니다.
    nsml login을 실행했을 때 다음과 같은 오류 메시지가 뜨는 경우가 발생하는 경우에도 Path 설정을 해주어야 합니다.

    .. code-block:: console

        -bash: nsml: command not found


    path 설정법을 알아보겠습니다. 먼저 nsml 실행파일이 있는 폴더에 들어간 뒤, pwd를 입력하고 나온 path를 복사합니다.
    pwd로 ``/Users/user/Documents/nsml_client.darwin.amd64.hack`` 가 나왔다고 가정합니다.

    .. code-block:: console

        $ pwd
        /Users/user/Documents/nsml_client.darwin.amd64.hack

    그리고 ``export PATH=$PATH:`` 명령어 뒤에 pwd에서 나온 path를 붙여주고 명령어를 실행합니다.
    ``export PATH=$PATH:[pwd path]`` 형식입니다.

    .. code-block:: console

        $ export PATH=$PATH:/Users/user/Documents/nsml_client.darwin.amd64.hack
        $

    경로 설정이 완료되면 어떤 path 상에서도 nsml login이 가능합니다.


Run a session
-------------

    이번 해커톤 대회에서 nsml run을 할 때는 dataset을 -d 옵션으로 반드시 지정해야 합니다. dataset의 이름이 ir_ph1이며 ``-d ir_ph1`` 로 지정합니다.

    .. code-block:: console

        nsml run -d ir_ph1


    아래 예제에서는 `nsml-examples`_  예제코드와 ``hello_nsml`` dataset를 사용합니다.
    대회와는 상관 없이 nsml의 명령어와 session의 개념을 익히기 위해 사용하실 수 있습니다.
    :ref:`nsml run <nsml run>` 을 이용해 실행해 보겠습니다.
    Github의 example 레파지토리를 먼저 clone합니다.


    .. _nsml-examples: https://github.com/n-CLAIR/nsml-hack-examples

    .. code-block:: console

        $ git clone git@github.com:n-CLAIR/nsml-hack-examples.git
        Cloning into 'nsml-hack-examples'...
        remote: Enumerating objects: 92, done.
        remote: Counting objects: 100% (92/92), done.
        remote: Compressing objects: 100% (76/76), done.
        remote: Total 92 (delta 12), reused 92 (delta 12), pack-reused 0
        Receiving objects: 100% (92/92), 958.63 KiB | 284.00 KiB/s, done.
        Resolving deltas: 100% (12/12), done.

        $ cd nsml-hack-examples/01.Basic/01_hello_nsml/

        $ ls
        abc.abc  dataset/  main.py  prepare_dataset.sh  README.md  setup.py

        $ nsml run -d hello_nsml
        INFO[2018/11/19 16:35:44.284] file integrity check - start
        INFO[2018/11/19 16:35:44.285] file integrity check - done
        INFO[2018/11/19 16:35:44.285] README.md 333 B - start
        INFO[2018/11/19 16:35:44.285] README.md 333 B - done (1/6 16.67%) (333 B/19 KiB 1.69%)
        INFO[2018/11/19 16:35:44.285] abc.abc 18 KiB - start
        INFO[2018/11/19 16:35:44.286] abc.abc 18 KiB - done (2/6 33.33%) (18 KiB/19 KiB 95.16%)
        INFO[2018/11/19 16:35:44.286] dataset/data.txt 12 B - start
        INFO[2018/11/19 16:35:44.286] dataset/data.txt 12 B - done (3/6 50.00%) (18 KiB/19 KiB 95.22%)
        INFO[2018/11/19 16:35:44.286] main.py 530 B - start
        INFO[2018/11/19 16:35:44.286] main.py 530 B - done (4/6 66.67%) (19 KiB/19 KiB 97.91%)
        INFO[2018/11/19 16:35:44.286] prepare_dataset.sh 149 B - start
        INFO[2018/11/19 16:35:44.287] prepare_dataset.sh 149 B - done (5/6 83.33%) (19 KiB/19 KiB 98.67%)
        INFO[2018/11/19 16:35:44.287] setup.py 263 B - start
        INFO[2018/11/19 16:35:44.287] setup.py 263 B - done (6/6 100.00%) (19 KiB/19 KiB 100.00%)
        .....
        Building docker image. It might take for a while
        .........
        Session nsmlteam/hello_nsml/1 is started


    지금까지 NSML의 기본 사용법을 알아보았습니다.  다음 파트부터는 NSML에서 사용하는 명령어들을 알아보겠습니다.
