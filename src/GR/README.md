# Goal Recogntion (GR) System for p4 

This system allows p4 to be used as an engine to perform goal recognition.

The main script is `gr.py` is the main script. 
Check the settings at the top of the file. Modify call at bottom of file to select quality, density, etc., and run as `python gr.py`. Outputs to nominated csv file, e.g.:

    recog = GR( "../maps/gr/test.gr", "../maps/gr/test_results.csv")
    recog.runBatch(OPTIMAL, SPARSE, PREFIX)

## NOTES

* You will need to download `.scen` and map files from [movingai.com](https://movingai.com/benchmarks/), then run `gr_probs.py` to generate a GR-compatible problem set.
    * this generates extra goals and creates a `.GR` file. Extra parameters specify number of problems and maximum number of extra goals to generate, e.g:

            python gr_probs.py ..\maps\AR0316SR.map.scen 5 4 30 ..\maps\gr\test.gr

* Beware that some problems in the GR file may not be usable - i.e. if goals happen to be generated in terrain not accessible from the start location). 
You can check particular start and goal locations by loading map into the p4 simulator in the usual way.
* You require one agent to generate observations, another agent to perform goal recognition (here `gr_agent`). Drop both agents into the same directory - probably `src/agents/`
* run `gr.py` from the `src/GR` directory
