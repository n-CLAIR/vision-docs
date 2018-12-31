.. _nsml.copy():

nsml.copy
---------
.. py:function:: nsml.copy(source, target)

    :ref:`nsml.save<nsml.save()>` 에서 저장된 pickle 파일을 call by value 형식으로 load 할때 사용됩니다.

    dict 와 class attributes 는 copy 가 되지만 list type 은 지원하지 않습니다.

    :param source: source object 입니다.
    :param target: target object 입니다.

    .. note::
        source 와 target 의 type 이 똑같아야 합니다.

    Example ::

            def bind_model(model, class_to_save):
                def save(filename, **kwargs):
                    with open(os.path.join(filename, ‘class.pkl’), ‘wb’) as fp:
                        pickle.dump(class_to_save, fp)
                    ...
                def load(filename, **kwargs):
                    with open(os.path.join(filename, ‘class.pkl’, ‘rb’) as fp:
                        temp_class = pickle.load(fp)
                    assert type(temp_class) is type(class_to_save)
                    nsml.copy(temp_class, class_to_save)
                    ...
                nsml.bind(save=save, load=load)

            class ClasToSave:
                def __init___(self):
                     self.elem = 0
                     self.elem2 = 1

            class_to_save=ClassToSave()
            bind_model(model=model, class_to_save=class_to_save)
