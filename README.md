# Bert-VITS2_train

## 本项目fork自https://github.com/YYuX-1145/Bert-VITS2-Integration-package/tree/2.0.2

## 安装依赖

```
pip install -r requirements.txt
```

## 下载bert模型 放入bert目录

```
链接：https://pan.baidu.com/s/11vLNEVDeP_8YhYIJUjcUeg?pwd=v3uc 
```

```
E:\work\Bert-VITS2-v202\bert>tree /f
Folder PATH listing for volume myssd
Volume serial number is 7CE3-15AE
E:.
│   bert_models.json
│
├───bert-base-japanese-v3
│       config.json
│       README.md
│       tokenizer_config.json
│       vocab.txt
│
├───bert-large-japanese-v2
│       config.json
│       README.md
│       tokenizer_config.json
│       vocab.txt
│
├───chinese-roberta-wwm-ext-large
│       added_tokens.json
│       config.json
│       pytorch_model.bin
│       README.md
│       special_tokens_map.json
│       tokenizer.json
│       tokenizer_config.json
│       vocab.txt
│
├───deberta-v2-large-japanese
│       config.json
│       pytorch_model.bin
│       README.md
│       special_tokens_map.json
│       tokenizer.json
│       tokenizer_config.json
│
└───deberta-v3-large
        config.json
        generator_config.json
        pytorch_model.bin
        README.md
        spm.model
        tokenizer_config.json
```

## 下载预训练模型，放入pretrained_models目录

```
https://openi.pcl.ac.cn/Stardust_minus/Bert-VITS2/modelmanage/model_readme_tmpl?name=Bert-VITS2%E4%B8%AD%E6%97%A5%E8%8B%B1%E5%BA%95%E6%A8%A1-fix
```

```
E:\work\Bert-VITS2-v202\pretrained_models>tree /f
Folder PATH listing for volume myssd
Volume serial number is 7CE3-15AE
E:.
    DUR_0.pth
    D_0.pth
    G_0.pth

No subfolders exist
```

## 下载数据集

```
https://pan.ai-hobbyist.org/Genshin%20Datasets/%E4%B8%AD%E6%96%87%20-%20Chinese/%E5%88%86%E8%A7%92%E8%89%B2%20-%20Single/%E8%A7%92%E8%89%B2%E8%AF%AD%E9%9F%B3%20-%20Character
```

## 以刻晴为例 解压缩后，放入项目的Data/keqing/raw/keqing目录

```
E:\work\Bert-VITS2-v202\Data\keqing\raw\keqing>tree /f
Folder PATH listing for volume myssd
Volume serial number is 7CE3-15AE
E:.
    vo_card_keqing_endOfGame_fail_01.lab
    vo_card_keqing_endOfGame_fail_01.wav
```

## 转写标注文件

```

python3 transcribe_genshin.py

```


## 如果是自主构建数据集，把音频素材以当前模型命名为*.wav文件，如meimei.wav，放入raw目录，随后运行脚本进行切分

```
python3 audio_slicer.py
```

```
E:\work\Bert-VITS2-v202_demo\Data\meimei\raw\meimei>tree /f
Folder PATH listing for volume myssd
Volume serial number is 7CE3-15AE
E:.
    meimei_0.wav
    meimei_1.wav
    meimei_2.wav
    meimei_3.wav
    meimei_4.wav
    meimei_5.wav
    meimei_6.wav
    meimei_7.wav
    meimei_8.wav
```

## 文本预处理和生成bert模型可读文件：

```
python3 preprocess_text.py

python3 bert_gen.py

```

## 开始训练

```
python3 train_ms.py
```

## 训练好的模型目录

```

E:\work\Bert-VITS2-v202\Data\keqing\models>tree /f
Folder PATH listing for volume myssd
Volume serial number is 7CE3-15AE
E:.
│   DUR_0.pth
│   DUR_550.pth
│   DUR_600.pth
│   DUR_650.pth
│   D_0.pth
│   D_600.pth
│   D_650.pth
│   events.out.tfevents.1700625154.ly.24008.0
│   events.out.tfevents.1700630428.ly.20380.0
│   G_0.pth
│   G_450.pth
│   G_500.pth
│   G_550.pth
│   G_600.pth
│   G_650.pth
│   train.log
│
└───eval
        events.out.tfevents.1700625154.ly.24008.1
        events.out.tfevents.1700630428.ly.20380.1

```

## 模型推理验证

```
python3 server_fastapi.py
```
