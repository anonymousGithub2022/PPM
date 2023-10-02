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

The figure above illustrates the design overview of PPM, encompassing three primary steps for generating a new programming problem. PPM's input is an existing programming problem, consisting of a natural language prompt, a corresponding implementation, and some test inputs. During the initial step, PPM analyzes the return value types of the given problem by executing the implementation on the provided test inputs. Subsequently, PPM selects a lambda programming task based on these return value types. Finally, PPM concatenates the existing problem with the lambda programming task to craft a new problem.

During the benchmarking stage, PPM feeds the newly created prompt to the code model and retrieves the generated program code. The generated code is then executed on the test inputs, and the resulting outputs are compared against the outputs from the new implementation.


# File Structure

    generate.py			            Generate code using a specified large language model
    model.py				    load LLMS
    utils.py                                    load HumanEval dataset   return {task["task_id"]: task for task in human_eval}


# How to Run


## Supported Large Code Models
    {"gpt-4","chatgpt","codegen-2b","codegen-6b","codegen-6b-hf","codegen-16b","codegen2-16b","polycoder","vicuna-7b","vicuna-13b","santacoder","incoder-1b","incoder-6b","stablelm-7b","gptneo-2b","gpt-j","starcoder"}
