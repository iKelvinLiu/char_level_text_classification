##### Multi-KernelSize CNN & GRU Char-Level Text Classification

##### Core Idea:
The data is in a deterministic mapping and there is no tokenization,  
so we choose the Char-Level text classification to solve the problem.  
Using multi-size kernel CNN with GRU by comparing several methods from some papers. Reference as below.  
To make the code clean and readable, just putting all the codes in one file.  
To make the training process faster, just using smaller kernel size in CNN and also the training epoch is limited.  
In the experiment stage, tf.saver is used, for the submitted version, the tf.saver is switched off.  
  
  
  
##### Reference:  
Kim, Y. (2014). Convolutional neural networks for sentence classification. arXiv preprint arXiv:1408.5882.  
Zhang, X., Zhao, J., & LeCun, Y. (2015). Character-level convolutional networks for text classification. In Advances in neural information processing systems (pp. 649-657).  
Lai, S., Xu, L., Liu, K., & Zhao, J. (2015, January). Recurrent Convolutional Neural Networks for Text Classification. In AAAI (Vol. 333, pp. 2267-2273).  
  
    
    
##### Model Explanation:
One-hot of document as the input, it has 3 dimensions (batchsize, sentence_length, one_hot_length)  
The first CNN layers, kernel size 7 and 5 were used to extract different n-grams.  
The higher CNN layers extract higher level of abstraction.  
The max-pooling layers were used to down-sampling without overlap, by using stride=3 and k_size = 3  
Batch-Normalization were used in each cnn layers.  
In this work, I chose the GRU instead of CNN flatten, supposed that this helps to add some positional learning of sentence.  
After GRU layer, the drop_out layer was used to decrease overfitting.  
Batch size is 128, validate data set is 1600, Learning rate is 0.001, Adam_optimizer was used. And for the drop_out layer, is_training parameter is used.    
  
  
  
##### Training instructions：
Keep adjusting the parameters in model, and after achieving the 0.817 validation accuracy, seems like it works.  
I also put the best checkpoint in the folder, you can use it to train and validate.  
If you want to use the checkpoint, please change "restore_train_model = False".    
  
    
    
