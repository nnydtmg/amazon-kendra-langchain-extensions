# AWS Langchain
This repo provides a set of samples to work with [Langchain](https://github.com/hwchase17/langchain/tree/master) and Amazon Kendra. It currently has samples for working with a [Kendra retriever class](https://python.langchain.com/docs/modules/data_connection/retrievers/integrations/amazon_kendra_retriever) to execute a QA chain for SageMaker, Open AI and Anthropic providers. 

## Installing

Clone the repository
```bash
git clone https://github.com/aws-samples/amazon-kendra-langchain-extensions.git
```

Move to the repo dir
```bash
cd amazon-kendra-langchain-extensions
```

Move to the samples dir
```bash
cd kendra_retriever_samples
```

Install the dependencies

If you are using pip
```bash
pip install -r requirements.txt
```

If you are using Conda
```bash
conda env create -f environment.yml 
```

## Running samples
Ensure that the environment variables are set for the aws region, kendra index id and the provider/model used by the sample.
For example, for running the `kendra_chat_flan_xl.py` sample, these environment variables must be set: AWS_REGION, KENDRA_INDEX_ID
and FLAN_XL_ENDPOINT.

You can use commands as below to set the environment variables.
```bash
export AWS_REGION="<YOUR-AWS-REGION>"
export KENDRA_INDEX_ID="<YOUR-KENDRA-INDEX-ID>"
export FLAN_XL_ENDPOINT="<YOUR-SAGEMAKER-ENDPOINT-FOR-FLAN-T-XL>"
export FLAN_XXL_ENDPOINT="<YOUR-SAGEMAKER-ENDPOINT-FOR-FLAN-T-XXL>"
export OPENAI_API_KEY="<YOUR-OPEN-AI-API-KEY>"
export ANTHROPIC_API_KEY="<YOUR-ANTHROPIC-API-KEY>"
```

### Running samples from the streamlit app
The samples directory is bundled with an `app.py` file that can be run as a web app using streamlit. 

```bash
streamlit run app.py anthropic
```

The above command will run the `kendra_chat_anthropic` as the LLM chain. In order to run a different chain, pass a different provider, for example for running the `open_ai` chain run this command `streamlit run app.py openai`.

### Running samples from the command line
```bash
python <sample-file-name.py>
```

## Contributing
Create your fork and submit your changes via a pull request.
See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License
This library is licensed under the MIT-0 License. See the LICENSE file.

## Sample
```bash
python -V
sudo amazon-linux-extras install -y python3.8
sudo ln -sf /usr/bin/python3.8 /usr/bin/python3
python -V
export AWS_REGION="<YOUR-AWS-REGION>"
export KENDRA_INDEX_ID="<YOUR-KENDRA-INDEX-ID>"
export OPENAI_API_KEY="<YOUR-OPEN-AI-API-KEY>"
git clone https://github.com/aws-samples/amazon-kendra-langchain-extensions.git
cd amazon-kendra-langchain-extensions/
cd kendra_retriever_samples
pip install -r requirements.txt
python kendra_chat_open_ai.py
streamlit run app.py openai
```

prompt
```
The following is a friendly conversation between a human and an AI. 
  The AI is talkative and provides lots of specific details from its context.
  If the AI does not know the answer to a question, it truthfully says it 
  does not know.
  {context}
  Instruction: Based on the above documents, provide a detailed answer for, {question} Answer "don't know" 
  if not present in the document. 
  Solution:
```

```
以下は人間とAIの間の友好的な会話です。
  AI はおしゃべりで、コンテキストから多くの具体的な詳細を提供します。
  AI は質問に対する答えが分からない場合、正直にわからないと答えます。
  {context}
  指示: 上記の文書に基づいて、次の詳細な回答を提供してください。{question} 分からない場合は分からないと答えてください。
  解決策：
```
