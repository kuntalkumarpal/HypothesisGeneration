# HypothesisGeneration


### Main Paper
[Transforming Question Answering Datasets Into Natural Language Inference Datasets](https://arxiv.org/pdf/1809.02922.pdf)
### Repo
https://github.com/kelvinguu/qanli

### Pipeline
1. Generate empty conllu and txt from data
2. Update the conllu file using the above two files as input to the parser tagger.
3. Once the conllu files gets updated use it as input to the rulebasedqa python file(which is there in our obqa repo).
4. The above generates the hypothesis
5. Merge it back to the original data to consolidate.

### Things to keep in mind
* Never put space/blank in case where there is no answer/data in answer options. Else issues during hypothesis generation
* The parser generates the parsed file with a footer. Remove that so that it can be parsed by conllu parser
* python 3.6 or else there will be issue. Soln : Change in following file line 609 instead of "raise StopIteration" used return /Users/kuntal/miniconda3/envs/work/lib/python3.7/site-packages/pattern/text/__init__.py

### Requirements :
  * pip install sacremoses
  * pip install conllu
  * brew install mysql 
  * pip install pattern

### How to run
python rule_based_qa.py --inputfile ../output/train.parsed --outputfile ../output/trainqa.txt
python rule_based_qa.py --inputfile ../output/test.parsed --outputfile ../output/testqa.txt
python rule_based_qa.py --inputfile ../output/dev.parsed --outputfile ../output/devqa.txt
