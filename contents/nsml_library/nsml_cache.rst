nsml.cache
----------

.. py:function:: nsml.cache(preprocess_fn=None, **kwargs)

    preprocess_fn 함수를 통해 나온 결과값의 파일을 캐싱하는 함수입니다.

    :param fn preprocess_fn:
        preprocess 과정이 정의된 함수를 인수로 받습니다.

        preprocess 함수는 output_path=['./preprocess.pt'] 의 형식으로 인수를 받을 수 있어야 하고,

        결과 파일을 output_path 에 저장해야 합니다.

        정의가 되어있지 않으면 output_path 는 자동으로 ['./processed'] 로 설정됩니다.

    :param \*\*kwargs:
        preprocess_fn 에 전달할 인수입니다.

    Example ::

            def preprocess(output_path, data):
                data_set = {'train': _normalize_image(data['train']['data'],
                        data['train']['label'], transform),
                        'test': _normalize_image(data['test']['data'],
                        data['test']['label'], transform)
                       }
                with open(output_path[0], 'wb') as file:
                    torch.save(data_set, file)

            nsml.cache(preprocess, output_path=['./preprocess.pt'], data=data_loader(DATASET_PATH))
