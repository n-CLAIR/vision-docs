.. _nsml.bind():

nsml.bind
---------
.. py:function:: nsml.bind(save=None, load=None, **kwargs)

    NSML에서 내부적으로 사용하는 함수 또는 변수들을 하나로 묶어주는 함수입니다.

    :param fn save:
        모델을 저장하는 :ref:`save 함수<nsml.bind-save>` 입니다.

    :param fn load:
        저장된 모델을 불러오는 :ref:`load 함수<nsml.bind-load>` 입니다.

    Example ::

        def load(filename):
            torch.load(filename)
            ...
        def save(filename, **kwargs):
            if kwargs['real']:
                torch.save(object,filename)
            ...
        # kwargs got a ‘real=True’.
        nsml.bind(save=save, load=load, real=True)

.. _nsml.bind-save:

nsml.bind-save
^^^^^^^^^^^^^^

    :ref:`nsml.bind()<nsml.bind()>` 에 넘겨지는 save 함수는 model, optimizer 등 python object를 저장하는 함수입니다.

    다음과 같이 첫번째 인자로 저장할 수 있는 경로를 받고, \*\*kwargs를 받습니다.

    유저는 입력받은 경로에 하나 이상의 파일을 저장합니다.

    함수를 넘겨주지 않았다면, NSML에서 기본으로 제공하는 save 함수를 사용합니다. torch, tensorflow, keras의 save를 지원하며, 나머지는 *pickle* 로 저장합니다. `pickle <https://docs.python.org/3/library/pickle.html>`_ 은 파이썬에서 사용하는 모듈입니다.

    이미 생성된 session을 활용하는 :ref:`nsml fork<nsml fork>` , :ref:`nsml submit<nsml submit>` 등의 명령어는 save 함수를 통해 저장된 object를 사용합니다.

    :param str path: 저장할 위치가 담긴 경로입니다.

    파일로 바로 저장하는 예제입니다.

        Example ::

            def nsml_save(path, **kwargs):
                state = {
                'model': model.state_dict(),
                'optimizer': optimizer.state_dict()
                }
                filename = os.path.join(path, 'model.pt')

    받은 경로로 폴더를 만들어서, 하위에 파일들을 저장하는 예제입니다.

        Example ::

            def nsml_save(path, **kwargs):
                state = {
                'model': model.state_dict(),
                'optimizer': optimizer.state_dict()
                }
                os.mkdirs(path) # make folder(directory) in path
                torch.save(checkpoint, os.path.join(path, 'model.pt'))
                with open(os.path.join(path, 'class.pkl'), 'wb') as fp:
                    pickle.dump(class_to_save, fp)


    .. warning:: 폴더를 만들어서 저장하려면, 파일이 최소한 2개 이상 필요합니다.


.. _nsml.bind-load:

nsml.bind-load
^^^^^^^^^^^^^^

    저장된 모델을 불러오는 load 함수를 binding 합니다.

    load 함수는 첫번째 인자로 반드시 파일명 또는 폴더명을 변수로 받아야 합니다.

    :ref:`nsml fork<nsml fork>`, :ref:`nsml submit<nsml submit>` 등의 모델을 불러오는 명령어에서 load 함수를 호출합니다.

    :param str path: 저장된 파일 또는 폴더의 경로입니다.

    :ref:`bind-save<nsml.bind-save>` 에서 1개의 파일만 저장했을 때 불러오는 예제입니다.

        Example ::

            def nsml_load(path):
                checkpoint = torch.load(path)
                ...

            nsml.bind(load=nsml_load)

    :ref:`bind-save<nsml.bind-save>` 에서 2개 이상의 파일을 저장했을 때 불러오는 예제입니다.

        Example ::

            def nsml_load(path):
                checkpoint = torch.load(os.path.join(path, 'model.pt'))
                ...

            nsml.bind(load=nsml_load)
