
# Issues 1
#######

## ** Description: ** 

C:\Users\mm\AppData\Local\ov\pkg\isaac_sim-2023.1.1\kit\python\lib\json_init_.py(293): load
c:/users/mm/appdata/local/ov/pkg/isaac_sim-2023.1.1/exts/omni.isaac.sensor/omni/isaac/sensor/scripts/menu.py(204): init
c:/users/mm/appdata/local/ov/pkg/isaac_sim-2023.1.1/exts/omni.isaac.sensor/omni/isaac/sensor/scripts/extension.py(31): on_startup
C:\Users\mm\AppData\Local\ov\pkg\isaac_sim-2023.1.1/kit/kernel/py\omni\ext_impl_internal.py(164): _startup_ext
C:\Users\mm\AppData\Local\ov\pkg\isaac_sim-2023.1.1/kit/kernel/py\omni\ext_impl_internal.py(224): startup
C:\Users\mm\AppData\Local\ov\pkg\isaac_sim-2023.1.1/kit/kernel/py\omni\ext_impl_internal.py(328): startup_extension
PythonExtension.cpp::startup()(2):
C:\Users\mm\AppData\Local\ov\pkg\isaac_sim-2023.1.1/exts/omni.isaac.kit\omni\isaac\kit\simulation_app.py(304): _start_app
C:\Users\mm\AppData\Local\ov\pkg\isaac_sim-2023.1.1/exts/omni.isaac.kit\omni\isaac\kit\simulation_app.py(192): init
C:\Users\mm\AppData\Local\ov\pkg\isaac_sim-2023.1.1\standalone_examples\api\omni.isaac.sensor\rotating_lidar_rtx.py(16):

2024-06-03 08:56:37 [22,594ms] [Error] [omni.ext.plugin] [ext: omni.isaac.sensor-9.11.1] Failed to startup python extension.


## ** Solv:::**

ov/pkg/isaac_sim-2023.1.1/exts/omni.isaac.sensor/omni/isaac/sensor/scripts/menu.py
And modified the line 210 :
from
data = json.load(open(d+“/”+file )
to
data = json.load(open(d+“/”+file , encoding = ‘UTF8’))

# Issues 2
#######

## ** Description: ** 
- use the local ".usd" file , but fault:
-
- 2024-09-06 11:26:47 [29,863ms] [Warning] [omni.graph.core.plugin] Could not find category 'Replicator:Annotators' for removal
2024-09-06 11:26:47 [29,863ms] [Warning] [omni.graph.core.plugin] Could not find category 'Replicator:Annotators' for removal
2024-09-06 11:26:47 [29,863ms] [Warning] [omni.graph.core.plugin] Could not find category 'Replicator:Annotators' for removal
2024-09-06 11:26:47 [29,864ms] [Warning] [omni.graph.core.plugin] Could not find category 'Replicator:Annotators' for removal
2024-09-06 11:26:47 [29,864ms] [Warning] [omni.graph.core.plugin] Could not find category 'Replicator:Annotators' for removal
2024-09-06 11:26:47 [29,864ms] [Warning] [omni.graph.core.plugin] Could not find category 'Replicator:Annotators' for removal
2024-09-06 11:26:47 [29,865ms] [Warning] [omni.graph.core.plugin] Could not find category 'Replicator:Annotators' for removal
2024-09-06 11:26:47 [29,865ms] [Warning] [omni.graph.core.plugin] Could not find category 'Replicator:Annotators' for removal
2024-09-06 11:26:47 [29,865ms] [Warning] [omni.graph.core.plugin] Could not find category 'Replicator:Annotators' for removal
2024-09-06 11:26:47 [29,866ms] [Warning] [omni.graph.core.plugin] Could not find category 'Replicator:Annotators' for removal
2024-09-06 11:26:47 [29,866ms] [Warning] [omni.graph.core.plugin] Could not find category 'Replicator:Annotators' for removal
2024-09-06 11:26:47 [29,866ms] [Warning] [omni.graph.core.plugin] Could not find category 'Replicator:Core' for removal
2024-09-06 11:26:47 [30,022ms] [Warning] [carb] Recursive unloadAllPlugins() detected!

## ** Solv:::**

This is because the World is not rendered.
add this to code:

** world.step(render=True)


