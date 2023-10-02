<p align="center">
 <a href="https://github.com/anonymousGithub2022/main/LICENSE"><img src="https://img.shields.io/github/license/anonymousGithub2022/DyCL"></a>
 <a href="https://github.com/anonymousGithub2022/main/LICENSE"><img src="https://img.shields.io/pypi/pyversions/tvm"></a>
 <a href="https://github.com/anonymousGithub2022/main/LICENSE"><img src="https://img.shields.io/github/languages/code-size/anonymousGithub2022/DyCL"></a>
</p>



# PPM
This code repository includes the main implementation of Programming Problem Merging, which can generate new programming problems to benchmark the programming capability of code generation models.

# Design Overview
<div  align="center">    
 <img src="https://github.com/anonymousGithub2022/PPM/blob/main/fig/PPM-overview.jpg" width="680" height="230" alt="Design Overview"/><br/>
</div>    



# File Structure

    generate.py			            Generate code using a specified large language model
    model.py				    load LLMS
    utils.py                                    load HumanEval dataset   return {task["task_id"]: task for task in human_eval}

## LLMS
    {"gpt-4","chatgpt","codegen-2b","codegen-6b","codegen-6b-hf","codegen-16b","codegen2-16b","polycoder","vicuna-7b","vicuna-13b","santacoder","incoder-1b","incoder-6b","stablelm-7b","gptneo-2b","gpt-j","starcoder"}
