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
- As the model trains more, the distribution of generated sample becomes approximately the original distribution.
![Screenshot (269)](https://github.com/usamahassan965/Generative-AI/assets/96824810/03766c09-5650-4fd8-b737-a7a3d59eab8c)

- Pdata(x) is the original distribution for real samples and PZ(z) is the random distribution .
- Similarly, Pg(x) is the generated distribution from the generator. D(G(z)) is the classification output generated from discriminator.
![Screenshot (270)](https://github.com/usamahassan965/Generative-AI/assets/96824810/294a52e8-d081-4527-8470-f082f7b974f2)

## Derivation of Loss function

![Screenshot (272)](https://github.com/usamahassan965/Generative-AI/assets/96824810/360e17cd-1711-42bd-af2d-70e26e065ad2)

- Both log values should be at maximum . For this, D(x) = 1 and D(G(z)) = 0 which is max.
![Screenshot (274)](https://github.com/usamahassan965/Generative-AI/assets/96824810/f6271f69-f08e-415c-97ef-635f382eda34)

