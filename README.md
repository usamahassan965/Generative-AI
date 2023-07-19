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
- Now, the objective function is writtern in compact form . But it is for the one sample. For the whole sample X and Z, we will take the expectation which is the final orginal expression given by good fellow.
  
![Screenshot (276)](https://github.com/usamahassan965/Generative-AI/assets/96824810/50aa1aaf-687d-44ba-aab0-76cc479bc21e)

