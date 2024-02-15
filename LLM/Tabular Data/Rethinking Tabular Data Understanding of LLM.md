![[Pasted image 20240212213945.png]]
* LLMs struggle to understand the context of the table leading to problems like
	* Column localization
		* Read paper why - <Something to do with attentions>
* Symbolic reasoning good at precise location tasks but can lack semantic depth
* Can lead to not clean outputs as keys not present in table
* Textual reasoning can provide semantic information but can lead to hallucination  

[[Pasted image 20240212215748.png]]




Adding simple aggregation seems to work
