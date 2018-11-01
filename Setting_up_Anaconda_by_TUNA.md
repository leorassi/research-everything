# Installing up Anaconda

Motivation: Due to poor internet connection in certain regions, using integrated tools such as Anaconda is always painful, especially consider the hefty size of 600MB for its installer (much less to say about 3rd-party packages/modules). Most users might be frustrated. This instruction is written to solve this issue. The main idea behind the following approach: use a mirror site to accelerate the download process to enhance user experience and boost productivity.

目标：由于国际出口带宽的瓶颈限制，下载和使用Anaconda是一件苦差事。安装文件本身就达到600MB，第三方包会更大。如果不用本文中提到的方法加速，一方面用户的等待时间会很长，另一方面一旦出错就会前功尽弃，导致用户或初学者很有挫折感。本指南就是通过TUNA的镜像来解决上述问题，从而提升用户体验和生产力。

By (its website)[https://www.anaconda.com/],  "Anaconda is The Most Popular Python Data Science Platform". 

Anaconda 是一个用于科学计算的“全家桶”，支持 Linux, Mac, Windows, 包含了Python，包含了Jupyter Notebook，更集成了众多流行的科学计算、数据分析的包。


1.  Download and install Anaconda from TUNA's mirror 从 TUNA 的镜像下载和安装 Anaconda
    1.  Visit 访问 https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/
    1.  Chosse the Anaconder version (preferrably the latest one), and pick up the version that matches your OS. 先选择Anaconda的版本（建议选择最新的，页面的最下方），并且选择与自己操作系统对应的
        1.  As of writing this instruction, the latest version is 5.3, and I use 64-bit Windows, so I picked up 在写这篇指南时，最新的版本是5.3.0，并且我用64位Windows，所以我选了这个版本 (Anaconda3-5.3.0-Windows-x86_64.exe)[https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/Anaconda3-5.3.0-Windows-x86_64.exe]
    1.  Download and install it 下载安装之


1.  Setting up channels, and install PyTorch 设置相应的“通道”，下载和安装PyTorch

    说明：Anaconda 的 `conda` 命令是一个类似于 `pip` 的第三方包管理器，里面有“channel（通道）”这种概念，所谓的通道，就是一组包名和相应的来源网址。Anaconda在刚安装完成时，默认是从官方网站下载，这样会导致速度比较慢。我们可以将其设置为TUNA的通道，这样就会快很多。

    1.  Start menu, locate and right-mouse-click “Anaconda Prompt” -> “Run as Administrator” 

        开始菜单，找到“Anaconda Prompt”并右键->“以管理员运行”

    1.  Run the following commands

        执行下列命令（注意，这期间有可能会中断或者提示，请留意相应的信息）
        ``` 
        pip install pip -U

        pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

        conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
        conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
        conda config --set show_channel_urls yes
        
        pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
        
        pip install -i https://pypi.tuna.tsinghua.edu.cn/simple filterpy

        
        ```

# Change the Jupyter start-up folder

If you're using a Windows System, you might encouter difficulties in setting the default path for Jupyter Notebook. Current information available online is pretty scattered. Below there is a working solution tested by me. 

1.  Add it to the global config file

    1.  Open "Anaconda Prompt" and type `jupyter notebook --generate-config`

    1.  Find the file in `C:\Users\username\.jupyter\jupyter_notebook_config.py`

    1.  Change the line of `#c.NotebookApp.notebook_dir = ''` to `c.NotebookApp.notebook_dir = 'c:\yourworkbench\'`

        1.  Remeber to remove the comment hashbang `#`

1.  Then, change the shortcut of Jupyter Notebook

    1.  go to `C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Anaconda3 (64-bit)`, right-mouse-click the "Jupyter Notebook" shortcut icon and open "Properties" dialog

    1.  In the Target field, remove `%USERPROFILE%`

    1.  In the field of "Start in", type the same directory of `c:\yourworkbench\` as abovementioned.

1.  Done!


