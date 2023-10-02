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
    + src/methods               This directory includes the implementation of different methods to generate programming problems.
     + utils.py             This file implemenents some basic common functions.
     + abstract_methods.py  Implements the abstract class for each method, and the abstract class includes some common functions.
     + demo_mutate.py       This file implements the demo related mutation methods (Add Demo, Delete Demo, and Replace Demo)
     + description_mute.py  This file implements the natual language related mutation methods (Token Mutation and Character Mutation)
     + func_name.py         This file implements the function name mutation.
     + sytanx_mute.py       This file includes some sytanx level mutation (Insert Empty Line)
  + codeGen/model.py
     + semantic_mute.py     This file includes the implementation of our proposed programming problem merging methods.
    + ML/model.py               This file implements the infrastructure of loading large code model for inference.
    + evaluation                This directory inmplements the  infrastructure of executing the generated code and collect the execution outputs.
    + final_res                 This directory stores the results of our experiments.
    + generate.py               This file is used to generate program code from a code model.
    + generate_prompt.py        This file is used to generate prompt for each methods.
    + lambda_problem.py         This file is used to test the accuracy of oiur propsoed lambda problems.
    + pass_k.py                 This file is used to compute the pass@k metrics.
    + utils.py                  This file implements some basic functions.
    + diversity.py              This file is used to evaluate the diversity of the programming problems from each methods.
    
 
# How to Run
 ``python generate.py --model incoder-1b --construct_prompt token_mutation --dataset humaneval --n_samples 100``
   The `model` parameter selects the large code model for inference.
   The `construct_prompt` parameter selects the method to construct prompt. 
   The `dataset` parameter selects the seed dataset.
   The `n_samples` parameter selectes the number of generated candidate programs.
 
## Supported Large Code Models
    {"gpt-4","chatgpt","codegen-2b","codegen-6b","codegen-6b-hf","codegen-16b","codegen2-16b","polycoder","vicuna-7b","vicuna-13b","santacoder","incoder-1b","incoder-6b","stablelm-7b","gptneo-2b","gpt-j","starcoder"}

## Supported Methods.
 {"base", "add_demo", "del_demo", "rep_demo", "char_mutation", "token_mutation", "func_name", "insert_line", "comment", "output_v_mutation", "output_mutation"}
