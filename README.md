![Screenshot (299)](https://github.com/usamahassan965/Generative-AI/assets/96824810/6ef8c58e-4cbb-4299-a81c-7a2c04aa6eba)
![Screenshot (302)](https://github.com/usamahassan965/Generative-AI/assets/96824810/517fc96c-2616-4b0e-8973-901b096f9c1a)
# Generative-AI
Projects related to Deep GANs

- GANs are deep neural networks that are trained in an adversarial manner to generate data mimicking some distribution.
- Two classes of models in GANs:
(a) Discriminator: Discriminates between two different classes of data.
(b) Generator: It has to be trained on training data X sampled from some true distribution D is the one which, given some standard random distribution Z produces a distribution D', which is close to D according to some metric. e.g., It means our model should be trained on training datapoints X of Mnist dataset (from its original distribution D) in such a way to give a distibution D' which is generated from some random distribution Z. And the trained final distribution should be like of original distribution D.
##  Basic Working
![Screenshot (263)](https://github.com/usamahassan965/Generative-AI/assets/96824810/2a949219-51ca-4f9f-bd2b-e3b992c4ebfa)

## Methodology Diagram
- First, the random noise is injected to generator to generate sample image which is passed through the discriminator with the real image and discriminator tries to classify properly. The discriminator is trained to improve the fake accuracy close to zero and real accuracy close to one and thus, classification accuracy close to one.
- While the generator is trained while keeping the weights and biases of discriminator fixed to improve the classification accuracy of discriminator to 0.5 so that discriminator would be fooled and predict each fake image as real image.
![Screenshot (265)](https://github.com/usamahassan965/Generative-AI/assets/96824810/baf88147-d161-4e1e-b016-1dab09c2be75)

## Training on Mnist Dataset
- The generator is trained on Mnist data and it will try to pick the values of the attributes from the orginal distribution of each attribute.

![Screenshot (266)](https://github.com/usamahassan965/Generative-AI/assets/96824810/8b1a5579-c8e2-4951-a14e-79ab76b8ada8)


## Loss function
- Discriminator:   Role is to discriminate between real and fake data. Discriminator should give output 1 for distribution D(x) and zero for D(G(z)).
- Generator:       Role is to generate data in such a way so that it can fool the discriminator. Generator should be trained to give classification output of 0.5.
- As the model trains more, the distribution of generated sample becomes approximately the original distribution.
  
![Screenshot (269)](https://github.com/usamahassan965/Generative-AI/assets/96824810/03766c09-5650-4fd8-b737-a7a3d59eab8c)

- D(x,theta) is the discriminator and G(z,theta) is the generator.
- Pdata(x) is the original distribution of real samples and PZ(z) is the prior distribution from random noise .
- Output D(x) is the probability range of classification accuracy of real samples distinguised by discriminator. It should be close to 1 for better discriminator performance.
- Output D(G(z)) is the probability range of classification accuracy of fake samples distinguised by discriminator .
- Similarly, Pg(x) is the generated distribution from the generator. 
  
![Screenshot (270)](https://github.com/usamahassan965/Generative-AI/assets/96824810/294a52e8-d081-4527-8470-f082f7b974f2)

## Derivation of Loss function

- y is the real image and y_hat is the reconstructed image if real/fake image passes from discriminator. We are computing binary cross entropy between them.
- Pdata is coming from original distribution. Hence, for real samples, actual output y = 1. Similarly, y_hat = D(x) = reconstructed image. The ideal value of D(x) should be 1 as we know. Bur for fake samples, actual output y = 0 and hence y_hat = D(G(z)= reconstructed image. The ideal value of D(G(z) should be zero.
 
![Screenshot (272)](https://github.com/usamahassan965/Generative-AI/assets/96824810/360e17cd-1711-42bd-af2d-70e26e065ad2)

## Ideal Discriminator Output
- As ideal output, D(x) = 1 and D(G(z)) = 0. Hence, both log values should be maximized. It will only happen if we have the previous o/p values.
- Below are the log curves for log(D(x) and log(D(G(z)). As D(x) ranges 0-1. Hence, in this case, maximum log value would be zero (at D(x)=1) and minimum log value would be -infinity (at D(x)=0). Similarly, as D(G(z)) ranges 0-1. Hence, in this case, maximum log value would be one (at D(G(z))=0) and minimum log value would be -infinity (at D((G(z))=1).
- So, this is what we want our discriminator to output optimally.

![Screenshot (274)](https://github.com/usamahassan965/Generative-AI/assets/96824810/f6271f69-f08e-415c-97ef-635f382eda34)

## Ideal Generator Output
- The generator would want to fool the discriminator about fake samples. Hence, he would want discriminator to output D(G(z)) = 1.
- For this output, log value would be at minimum. Hence, the generator would try to minimize the objective function defined above.

  ![Screenshot (277)](https://github.com/usamahassan965/Generative-AI/assets/96824810/597da070-b8c5-4299-bc4f-78cef7bac133)

- As , first term is also writter in minimzation but actually this term has no role and it is independent of generator performance. But we are writing it for convenience in making a general function.
  
![Screenshot (275)](https://github.com/usamahassan965/Generative-AI/assets/96824810/087faaf3-d4ac-45af-9fd1-b247129ca5e4)

## Maximization-Minimization
- Now, the objective function is writtern in compact form . But it is for the one sample x and z. For the whole sample X and Z, we will take the expectation which is the final orginal expression given by good fellow.
- For the best discriminator, we need to have the ratio of real data distribution over sum of fake data and real data distrubution. 

![Screenshot (278)](https://github.com/usamahassan965/Generative-AI/assets/96824810/736aece8-52ef-4525-98fd-d1d56bcc64b4)

## Proof of a good discriminator

![Screenshot (280)](https://github.com/usamahassan965/Generative-AI/assets/96824810/ec8af5b4-1138-4938-adf3-84b64e9dc6f3)

![Screenshot (281)](https://github.com/usamahassan965/Generative-AI/assets/96824810/bed40655-caa5-46a0-a6ca-f3eb00598d8c)

### Probability Density Function
- Calculation of probability density function y in terms of random variable X.
- Here, we are mapping this concept to our case which is shown below.
  
![Screenshot (282)](https://github.com/usamahassan965/Generative-AI/assets/96824810/8e61026e-6cc2-4f6e-9ea5-71a8a1bedafc)

- Proof continues...
![Screenshot (284)](https://github.com/usamahassan965/Generative-AI/assets/96824810/178af0d1-b8e6-4b44-8e69-73642669858d)

![Screenshot (285)](https://github.com/usamahassan965/Generative-AI/assets/96824810/47320b9c-d1cd-4bb7-81a1-73c57cf7fbd5)

![Screenshot (286)](https://github.com/usamahassan965/Generative-AI/assets/96824810/8cf1c2a9-df20-493d-b158-4b93ab06c38e)

![Screenshot (287)](https://github.com/usamahassan965/Generative-AI/assets/96824810/0cb733b9-ba0b-48b2-9597-762f8326d82e)

- We have proved it optimal but to check if its maximum then take again derivative,

  ![Screenshot (288)](https://github.com/usamahassan965/Generative-AI/assets/96824810/4c137246-88ff-4c33-aa4a-07bb7126f5e4)

### Proof of a good Generator


![Screenshot (289)](https://github.com/usamahassan965/Generative-AI/assets/96824810/b3f7117f-170a-4823-a8f2-89c3f7dc679b)

![Screenshot (290)](https://github.com/usamahassan965/Generative-AI/assets/96824810/fcd6ae83-6d54-48ed-aa40-c0902ffc37cd)

![Screenshot (296)](https://github.com/usamahassan965/Generative-AI/assets/96824810/b550df32-ff99-4143-91e7-15a90803d988)

![Screenshot (292)](https://github.com/usamahassan965/Generative-AI/assets/96824810/c953a711-e5e2-472d-9026-9a4304fa7389)

![Screenshot (294)](https://github.com/usamahassan965/Generative-AI/assets/96824810/f062c185-20c3-46e4-a519-7d47679107f0)

![Screenshot (295)](https://github.com/usamahassan965/Generative-AI/assets/96824810/ad3415b7-798a-43cd-ae6e-1f445963c08a)

![Screenshot (299)](https://github.com/usamahassan965/Generative-AI/assets/96824810/977bc0f1-9313-4e1b-8001-a492c05b5636)

![Screenshot (300)](https://github.com/usamahassan965/Generative-AI/assets/96824810/b06e712c-4c81-4831-83b9-e2d782d93441)

![Screenshot (301)](https://github.com/usamahassan965/Generative-AI/assets/96824810/254aaca0-b8ff-4748-a27b-cbc06c6d9883)

![Screenshot (302)](https://github.com/usamahassan965/Generative-AI/assets/96824810/5f2e54c7-a688-475f-8262-6a4da146fc30)

## Optimization Algorithm of GANs:

![Screenshot (304)](https://github.com/usamahassan965/Generative-AI/assets/96824810/190db660-131a-4a68-bcb5-dadac142829d)

- Blue dots represents the discriminator distribution function. At initial stages of training (a) , D is able to distinguish between real (Pdata) and fake (Pg(x)) distribution.
- But as the iteration proceeds, at (b) iteration , discriminator updates to give more good classification function. But at iteration (c) , generator updates and distribution of real and fake data looks very much alike.
  
![Screenshot (305)](https://github.com/usamahassan965/Generative-AI/assets/96824810/b25423c8-3f5e-4b2c-904e-666ddab5b2ea)

- Min-Max algorithm creates an issue at the start of training. The reason is at start , the generator generates fake images so discriminator easily classifies them and D(G(z)) approximately equals to zero. Thus, the problem occurs with the generator part of the loss function which is the max function and its log value becomes zero due to which the generator gradient becomes zero and don't update weights in training.
  
![Screenshot (306)](https://github.com/usamahassan965/Generative-AI/assets/96824810/48694830-f18c-4b54-b059-071e9c937ac6)

- To overcome this issue, we replace the loss function of log(1-D(G(z)) to log(D(G(z)). Hence, log0 becomes 1 initially and generator gradients update faster initially. For this to happen, we train both equations of discriminator and generator separately and we don't use min-max algo.

![Screenshot (307)](https://github.com/usamahassan965/Generative-AI/assets/96824810/654cb386-2dd4-4a3f-99b4-c2bc6d41a3b0).

## Limitation of GANs
1. Vanishing gradients of generator which we talked above.
   
2. Mode Collapse
- In this, as the iteration proceeds, the generator starts producing same images and it's called mode collapse.
- We understand this issue in this way...
- Each class of image has different gaussian distribution . The generator instead of learning all distributions. It learns only that distribution in which it is performing better and it's trying to fool the discriminator . Hence, the discriminator also looks for other distributions to improve its classification rather than that in which the generator is performing better.

  ![Screenshot (310)](https://github.com/usamahassan965/Generative-AI/assets/96824810/7e76df58-44f3-4e00-9106-1bbac9cc15f0)

- The main reason of this behavior is that the reward for improving one distribution instead of learning others, in which discriminator is good at , is the same. Hence, the generator doesn't try to improve in other modes or distributions. SImilar, is the behavior with discriminator. He tries to improve only for those classes in which he is good at and the generator is weak at producing.
- In this way, the both model inclined towards one class of distribution and it leads to producing same images and called mode collapsig.

![Screenshot (311)](https://github.com/usamahassan965/Generative-AI/assets/96824810/487ce6a7-5487-4a6a-aeb8-aa531611abbf)

3. Hard to achieve Nash equilibrium
- As the both models are playing non-coorporative game against each other. Their cost updation is independent of each other and in this way, they start to produce oscillations as iteration increases and never become stable.

  ![Screenshot (313)](https://github.com/usamahassan965/Generative-AI/assets/96824810/dc784ba4-fe4b-4dfc-94f6-916155963f53)


4. Problem with Counting
- Like eyes on faces becomes 3 or more...

  ![Screenshot (314)](https://github.com/usamahassan965/Generative-AI/assets/96824810/f90588ed-efec-478a-9a2d-98d80f14ea3f)

  
5. Problem with Perspective
- Couldn't differentiate between 2D and 3D perspective and starts producing according to 2D perspective and hence , mixing backgrounds with the foreground.
  
  ![Screenshot (315)](https://github.com/usamahassan965/Generative-AI/assets/96824810/461379ca-b25b-4df8-8e22-39f9d2bdaea0)

6. Problem with global structure
- Problem with the structure of objects producing unrealistic images.
  
![Screenshot (316)](https://github.com/usamahassan965/Generative-AI/assets/96824810/0a8168f1-1093-446b-ae30-f109ea17b54e)
