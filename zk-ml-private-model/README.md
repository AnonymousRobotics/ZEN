------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Because the memory consumption of generating parameters and proof in ArkWorks framework is too expensive, we can not generate proof for Lenet Large Face workload with 256GB memory on
a Azure VM. We tried to optimize the memory consumption of ArkWorks, but this slows down the proof generation speed. The `lenet_large_face_optimized.log` contains the log of running 
on our mannually memory consumption optimized version ArkWorks. But if with enough amount of memory, the Lenet Large Face workload should generate proof within a shorter amount of time.
We expect that the time is about 20000 seconds if we have enough memory and use the original ArkWorks library.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

After we upgrade to Arkworks 0.3.0 and newest Poseidon commitment, we can execute `lenet_large_face` with an Azure 875GB memory instance. If you want better performance, please check `zen-arkworks` directory.