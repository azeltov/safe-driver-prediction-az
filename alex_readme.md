az login --use-device-code
az account set --subscription "5763fde3-4253-480c-928f-dfe1e8888a57"
az configure --defaults group="safedriveraz" workspace="aml_safedriver_ws"

git config --global user.email "alzeltov@microsoft.com"
git config --global user.name "Alex Zeltov"

//interactive job debugging on aml 
python -m debugpy --listen localhost:5678 --wait-for-client prep-data.py --input-data $AZURE_ML_INPUT_input_dataset --labels-output ${{outputs.labels}} --features-output ${{outputs.features}} --label-column target id

https://ml.azure.com/data?wsid=/subscriptions/5763fde3-4253-480c-928f-dfe1e8888a57/resourcegroups/safedriveraz/workspaces/aml_safedriver_ws&tid=72f988bf-86f1-41af-91ab-2d7cd011db47


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