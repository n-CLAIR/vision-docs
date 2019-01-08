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
            Checkpoint    Last Modified    Elapsed    Summary                                                                    Size
            ------------  ---------------  ---------  -------------------------------------------------------------------------  ---------
            0             32 minutes ago   3.785      epoch=0, loss=7.015200052175436, epoch_total=5, acc=0.0021114864864864866  366.74 MB
            1             31 minutes ago   25.032     epoch=1, loss=6.762363957929182, epoch_total=5, acc=0.0059121621621621625  366.74 MB
            2             31 minutes ago   24.942     epoch=2, loss=6.377185855899845, epoch_total=5, acc=0.020551801801801804   366.74 MB
            3             30 minutes ago   25.053     epoch=3, loss=5.742813685992816, epoch_total=5, acc=0.05419481981981982    366.74 MB
            4             30 minutes ago   24.971     epoch=4, loss=4.847646936640009, epoch_total=5, acc=0.14273648648648649    366.74 MB
            $ nsml model rm nsmlteam/ir_ph1_v2/4 2*
            $ nsml model ls nsmlteam/ir_ph1_v2/4
            Checkpoint    Last Modified    Elapsed    Summary                                                                  Size
            ------------  ---------------  ---------  -----------------------------------------------------------------------  ---------
            39            4 hours ago      60.381     step=39, test/loss=0.02888070044517517, test/accuracy=0.9904, epoch=39   175.81 KB
            49            4 hours ago      64.250     step=49, test/loss=0.02667991955280304, test/accuracy=0.9906, epoch=49   175.81 KB
            59            4 hours ago      69.031     step=59, test/loss=0.026230290055274965, test/accuracy=0.9913, epoch=59  175.81 KB
            69            4 hours ago      68.230     step=69, test/loss=0.027098055839538573, test/accuracy=0.9915, epoch=69  175.81 KB
