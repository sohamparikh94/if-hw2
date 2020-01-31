## Part 2

The modified parser uses both WordNet annotations as well as the sentence embeddings for recognizing a higher number of commands. Given a command, we first check if the command exists in the list of alternative commands created using the WordNet annotations. If there is no match, then we use the cosine distance to get the most similar command from a list of known commands. However, this method is guaranteed to return a valid command, regardless of whether the input command is meaningless. Hence, we only return a valid command if the cosine distance is less than 0.5. 

We chose to use the WordNet-based alternative commands before using the sentence vectors because we felt that averaging the embeddings gave us quite noisy results.

## Part 3

Given a command, our parser first uses coreference resolution to replace pronouns with the respective nouns. Next, the command is broken into one or more individual commands by first segmenting into sentences and then extracting individual commands based on `,` and `and`. Each of these individual commands is then used to find the most similar command (from a list of known commands) using sentence embeddings (as in Part 2). These commands are then executed in sequence. 

For the extra component involving NLP, we have included a door at the end of the game which unlocks only if you can distinguish between human and AI generated text! We have used the GPT-2 model provided by HuggingFace for generating text. To
directly reach here, give these commands: `take jug, w, n, e, fill jug with water, w, s, s, water plant, eat plant, n, n, down, down, take torch, light torch, up, up, south, up, up, take spear, down, down, north, down, down, s, break case, take armor, wear armor, n, up, up, unlock door`. 
