.. _nsml model rm:

Delete a model
--------------

    Usage:
        +-----------------------------------------------+
        | **nsml model rm** SESSION_NAME *CHECKPOINT*   |
        +-----------------------------------------------+

    Description:
        하나 또는 여러 개의 model 을 삭제합니다. 생성된 CHECKPOINT 번호를 입력합니다. 정규식의 * 와 ? 를 이용하면 여러 개의 model을 삭제할 수 있습니다.

    Example:
        .. code-block:: console

            nsml model rm nsmlteam/ir_ph1_v2/4 24

        .. code-block:: console

            nsml model rm nsmlteam/ir_ph1_v2/4 "24"

        .. code-block:: console

            $ nsml model ls nsmlteam/ir_ph1_v2/4
            Checkpoint    Last Modified    Elapsed    Summary                                                                  Size
            ------------  ---------------  ---------  -----------------------------------------------------------------------  ---------
            29            4 hours ago      70.171     step=29, test/loss=0.031099648046493532, test/accuracy=0.9892, epoch=29  175.81 KB
            39            4 hours ago      60.381     step=39, test/loss=0.02888070044517517, test/accuracy=0.9904, epoch=39   175.81 KB
            49            4 hours ago      64.250     step=49, test/loss=0.02667991955280304, test/accuracy=0.9906, epoch=49   175.81 KB
            59            4 hours ago      69.031     step=59, test/loss=0.026230290055274965, test/accuracy=0.9913, epoch=59  175.81 KB
            69            4 hours ago      68.230     step=69, test/loss=0.027098055839538573, test/accuracy=0.9915, epoch=69  175.81 KB
            $ nsml model rm nsmlteam/ir_ph1_v2/4 2*
            $ nsml model ls nsmlteam/ir_ph1_v2/4
            Checkpoint    Last Modified    Elapsed    Summary                                                                  Size
            ------------  ---------------  ---------  -----------------------------------------------------------------------  ---------
            39            4 hours ago      60.381     step=39, test/loss=0.02888070044517517, test/accuracy=0.9904, epoch=39   175.81 KB
            49            4 hours ago      64.250     step=49, test/loss=0.02667991955280304, test/accuracy=0.9906, epoch=49   175.81 KB
            59            4 hours ago      69.031     step=59, test/loss=0.026230290055274965, test/accuracy=0.9913, epoch=59  175.81 KB
            69            4 hours ago      68.230     step=69, test/loss=0.027098055839538573, test/accuracy=0.9915, epoch=69  175.81 KB
