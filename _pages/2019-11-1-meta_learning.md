---
layout: default
title: "Introduction to Meta-Learning"
---

## Introduction to Meta-Learning

One of the most critical limitations of deep neural networks is that they are bound to a very specific task. For example, a neural network trained on identifying different breeds of dogs, will perform poorly on identifying different breeds of cats and a new neural network will have to be trained from scratch for that purpose. The inability of fast adaptation to new tasks has two significant complications. Firstly, it costs enormous computational power (which means both millions of dollars and extensive electrical power usage) since it requires training different networks for different tasks from scratch. Secondly, it promotes specialised models and neural networks for tasks that might share knowledge thus steering away from unified models. Hence, solving these obstacles would be highly beneficial for the rapid advancement of machine learning research and the trillion-dollar objective of artificial general intelligence.


There have been numerous approaches on how to tackle this problem in recent years as part of the field of knowledge transfer. The basic goal of knowledge transfer methods is to leverage existing knowledge in neural networks in order to solve new various tasks. Some of the most popular examples of such advancements have been in the areas of computer vision and natural language processing. In computer vision related tasks (such as object detection, image segmentation etc) a widely used technique which can lead to decent results fast, is to use pre-trained models on ImageNet [2, 4]. Specifically, large networks are trained on millions of images of various content and then using this knowledge, they are fine-tuned in the particular task in question. A similar approach is also frequently used in natural language processing tasks (such as voice recognition, text generation etc) by using a large pre-trained network called BERT [3]. Other more general approaches includes to just try and find suitable initialisation parameter values of the neural networks in order to accelerate and boost the learning procedure [7], with a few studies on trying to also use learned initialisations [6, 9].


A trending area of research, as part of knowledge transfer, is meta-learning. Similarly to the previously mentioned approaches, the goal of meta-learning is to provide a framework where models can easily adapt to new tasks. The basic intuition of this approach is to teach the models _how_ to learn tasks or "learning to learn" by treating entire tasks as training samples, instead of explicitly optimising for the current task in hand as in traditional deep learning methods. By training the models in such manner, the hope is that they will be able to quickly and efficiently learn new skills without the need of extensive training procedures or large amount of data. This problem is also known as few-shot learning.


One of the most promising works in the field of meta-learning has been MAML by Finn et al [5]. They proposed an algorithmic framework that can be used alongside any other gradient descent based model for numerous applications with intriguing results in regression, classification and reinforcement learning. As with most meta-learning methods, MAML is firstly pre-trained on one part of the data to find a good generalised representation of the parameters and then during online training (testing) new tasks are introduced of limited samples to evaluate its performance on those. Its success is based on the principle of knowledge transfer / sharing that some internal representation of the parameters can be used across different tasks, meaning they are more \textit{transferrable} than others.

The training procedure of MAML consists of an inner and an outer loop of updates on batches of related tasks. The inner loop optimises for the loss function of a specific task each time and finds network parameters based on the according gradients of the task. In the outer loop, the network parameters are updated in order to optimise for when a new task is introduced. In other words, \textit{the method aims to optimise the model parameters such that with the least amount of gradient steps on a newly introduced task, the model will perform as effectively as possible}.

A benefit of this approach is that it does not require any additional meta-learning parameters to learn since it basically acts as a weight initialisation technique. On the other hand, MAML as with many few-shot learning methods, is prone to overfitting due to the significantly limited amount of training samples per class (often even less than 50). 


Recently, an extension to MAML was introduced called CAVIA by Zintgraf et al [10]. They propose that during testing (online training) instead of updating the entire network's parameter to only update a specific set of input parameters, which they call context parameters $\phi$. Similarly to MAML, the training procedure consists of an inner and an outer loop, but this time the inner loop only update the $\phi$ parameters whereas the outer all the remaining $\theta$ parameters. These context parameters can also be seen as task embeddings which adjust the model to the task in hand thus further improving fast adaptation to new tasks.

Finally, some other interesting papers related to the topic are the following:

<ul>
<li> [How transferable are features in deep neuralnetworks? (a bit more general about transfer learning](https://papers.nips.cc/paper/5347-how-transferable-are-features-in-deep-neural-networks.pdf)
<li> [Transferring Knowledge Across Learning Processes](https://arxiv.org/pdf/1812.01054.pdf)
</ul>

### _References_

[1]  Xi  Chen,  Yan  Duan,  Rein  Houthooft,  John  Schulman,  Ilya  Sutskever,  and  Pieter  Abbeel.   Infogan: Interpretable representation learning by information maximizing generative adversarial nets. In Advances in neural information processing systems , pages 2172–2180, 2016.

[2]  Jia Deng, Wei Dong, Richard Socher, Li-Jia Li, Kai Li, and Li Fei-Fei.  Imagenet:  A large-scale hierarchical image database.  In 2009 IEEE conference on computer vision and pattern recognition , pages 248–255. Ieee, 2009.

[3]  Jacob  Devlin,  Ming-Wei  Chang,  Kenton  Lee,  and  Kristina  Toutanova.   Bert:   Pre-training  of  deep bidirectional transformers for language understanding. arXiv preprint arXiv:1810.04805 , 2018.

[4]  Jeff Donahue, Yangqing Jia, Oriol Vinyals, Judy Hoffman, Ning Zhang, Eric Tzeng, and Trevor Darrell. Decaf: A deep convolutional activation feature for generic visual recognition. In International conference on machine learning, pages 647–655, 2014.

[5]  Chelsea Finn, Pieter Abbeel, and Sergey Levine.  Model-agnostic meta-learning for fast adaptation of deep networks.  In Proceedings of the 34th International Conference on Machine Learning-Volume 70, pages 1126–1135. JMLR. org, 2017.

[6]  Michael Husken and Christian Goerick.  Fast learning for problem classes using knowledge based network initialization.  In Proceedings of the IEEE-INNS-ENNS International Joint Conference on Neural Networks. IJCNN 2000. Neural Computing: New Challenges and Perspectives for the New Millennium, volume 6, pages 619–624. IEEE, 2000.

[7]  James  Kirkpatrick,  Razvan  Pascanu,  Neil  Rabinowitz,  Joel  Veness,  Guillaume  Desjardins,  Andrei  A Rusu,  Kieran  Milan,  John  Quan,  Tiago  Ramalho,  Agnieszka  Grabska-Barwinska,  et  al.   Overcoming  catastrophic  forgetting  in  neural  networks. Proceedings of the national academy of sciences , 114(13):3521–3526, 2017.

[8]  Zachary  C  Lipton  and  Jacob  Steinhardt.   Troubling  trends  in  machine  learning  scholarship. arXiv preprint arXiv:1807.03341 , 2018.

[9]  Dougal Maclaurin, David Duvenaud, and Ryan Adams.  Gradient-based hyperparameter optimization through reversible learning.  In International Conference on Machine Learning, pages 2113–2122, 2015. 

[10]  Luisa M Zintgraf, Kyriacos Shiarlis, Vitaly Kurin, Katja Hofmann, and Shimon Whiteson.  Caml:  Fast context adaptation via meta-learning. arXiv preprint arXiv:1810.03642, 2018.
