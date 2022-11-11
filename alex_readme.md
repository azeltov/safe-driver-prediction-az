az login --use-device-code
az account set --subscription "5763fde3-4253-480c-928f-dfe1e8888a57"
az configure --defaults group="safedriveraz" workspace="aml_safedriver_ws"

git config --global user.email "alzeltov@microsoft.com"
git config --global user.name "Alex Zeltov"

  python  prep-data.py 'id' \
  --input-data /home/vscode/data/safedriver/input \
  --labels-output /home/vscode/data/safedriver/output/labels \
  --features-output /home/vscode/data/safedriver/output/features \
  --label-column target

python train.py \
  --feature-data /home/vscode/data/safedriver/output/features \
  --label-data /home/vscode/data/safedriver/output/labels \
  --output-folder /home/vscode/data/safedriver/output/train 

  
https://typer.tiangolo.com/tutorial/