# DATA620004_hw3_pytorch_NeRF

复旦大学 DATA620004 神经网络和深度学习 期末作业

## 任务3：基于 NeRF 的物体重建和新视图合成

### 基本要求：
1. **选取身边的物体拍摄多角度图片/视频**，并使用 COLMAP 估计相机参数，随后使用现成的框架进行训练。
2. **基于训练好的 NeRF 渲染环绕物体的视频，并在预留的测试图片上评价定量结果**。


![image](https://github.com/Win7win/DATA620004_hw3_pytorch_NeRF/assets/148932142/1459988d-4d8d-4f78-ad5b-92cd8e9fcfeb)

![image](https://github.com/Win7win/DATA620004_hw3_pytorch_NeRF/assets/148932142/e3c7d012-81e3-4aad-bca9-2c062763096d)

本项目是在 [nerf-pytorch](https://github.com/yenchenlin/nerf-pytorch) 基础上完成的。

### 准备
请确保安装以下依赖：
- requirements.txt 中的库
- tensorboard

### 数据集准备
1. 对需要重建的物体进行环绕拍照，使用 COLMAP 进行参数估计，计算位姿。
2. 使用 [LLFF](https://github.com/Fyusion/LLFF) 中的 `imgs2poses.py` 脚本创建数据集。

### 训练
1. 在 `/configs` 目录下新建 `target.txt`，参数设置可以参考 `souji.txt`。
2. 执行以下命令开始训练：
   ```sh
   python run_nerf.py --config configs/target.txt --spherify --no_ndc
   ```

### 测试
1. 直接执行以下命令进行测试：
   ```sh
   python run_nerf.py --config configs/test.txt --render_only
   ```
2. 或者在全部训练完成的基础上执行以下命令进行测试，自动加载最后的检查点：
   ```sh
   python run_nerf.py --config configs/test.txt --spherify --no_ndc
   ```



