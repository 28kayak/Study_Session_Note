### Hello

Chatbot review 
2018/12/17

---
### AIML Perser's functionality

- Before getting user input 
   1. AIML を read する
   2. Pattern を抽出する
   3. Pattern を tokenize する
   4. Tokenized pattern を Linkedlistのように繋げる。（Path class）
    - このとき Leaf Nodeの後ろにtemplateをつけておく。
   5. GraphにLinkedListっぽいpatternを追加する。
   
   全てのカテゴリーにこのプロセスを適応する。
---
### AIML Data Strcture 
- Data Strcture 
   Graph Strcture with Depth First Search 
   
   ```xml
   <category>
    <pattern> TELL ME ABOUT LUCENE</pattern>
    <template>Lucene is ============</template>
   </category>
   <category>
    <pattern>TELL ME ABOUT APACHE XXXXX</pattern>
    <template>Apache xxxxx is ~~~~~~~~~~~~~~~~~~~~~~~~~~</template>
   </category>
   <category>
    <pattern>I like about Solr</pattern>
    <template>You like Solr, ok.</template>
   </category>

   ```
### AIML Data Strcture 

   With this example AIML file input, AIML-Original Parser will construct a graph like below.
  ![AIML Data Strcture1](https://github.com/28kayak/Study_Session_Note/blob/master/ChatbotReview20181217.jpg)

---
### AIML Perser's functionality  

- When user input is entered 
   1. input を tokenizeする
   2. input を linked list 式に繋げる。
   3. Depth First Search でGraph を探索する。
    - 探索時のチェック事項　
        1. if node contains wildcard "_"?  
            yes: keep search subgraph   
            no : go to the next if-statement.  
        2. if node contains `\[ k_h \]`
            yes: keep search subgraph  
            no:  go to the next if-statement.  
        3. if node contains "*" ?  
            yes: keep search subgraph
            no : go to the next if-statement.  
    
   
