.. _nsml model pull:

Pull models
-----------

    Usage:
        +---------------------------------------------------------+
        | **nsml model pull** SESSION_NAME *CHECKPOINT* PATH      |
        +---------------------------------------------------------+

    Description:
        :ref:`nsml.save<nsml.save()>` 로 저장된 모델들을 local로 가져옵니다. :ref:`nsml model ls<nsml model ls>` 로 모델 목록을 확인할 수 있습니다.

    Example:
        .. code-block:: console

            nsml model pull nsmlteam/ir_ph1/4 24 ./
