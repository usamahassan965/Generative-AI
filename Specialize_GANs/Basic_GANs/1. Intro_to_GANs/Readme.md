# 1. Generative Models
Welcome to the specialization on generative adversarial
networks or GANs for short. You'll see how to
build models that can generate realistic images, music, and other things. In this video, you're going
to gain some intuition about how GANs and their
family of models work. By the end of the week, you get to build your own GAN that generates
handwritten digits. In this video, I'll introduce you to what generative models are, of which GANs are a type, and how these models compare with other models that you
might already know about. I'll also talk about two of the most popular generative
model architectures. You may be familiar with
discriminative models, but you might not have
known how they fit into the larger context of
machine learning or ML. A discriminative model
is one typically used for classification
in machine learning. They learn how to
distinguish between classes such as dogs and cats, and are often called classifiers. Discriminative models
take a set of features X, such as having a wet
nose or whether it purrs and from these features determine a category
why of whether the image is of a dog or a cat. In other words, they try to
model the probability of class Y given a set of features
X as having a wet nose, but it doesn't purr, so
it's probably a dog. On the other hand, generative
models try to learn how to make a realistic
representation of some class. For instance, a realistic
picture of a dog you see here. They take some random input
represented by the noise here, which could take on the
value, let say three, a random number,
or negative five, or 2.6 or actually just a
vector of all of those values. The point is, the
noise represents a random set of values going
into the generative model. The generative model
also sometimes takes in a class Y such as a dog. From these inputs, it's
goal is to generate a set of features X that look
like a realistic dog. So an image of a
dog with features such as a wet nose or
a tongue sticking out. You might wonder why we need this noise in the first place. Why can't we just tell it, ''Hey, generate a dog for me,'' and
then it'll generate a dog. The noise is larger to ensure
that what's generated isn't actually the same dog each time and you'll see this
theme play out shortly. This is because
generating just one dog is no fun and also
a little pointless. For now, think of this as some random noise that
also goes in as an input. More generally,
generative models try to capture the probability
distribution of X, the different features
of having a wet nose, the tongue sticking out, maybe pointy ears
sometimes but not all the time given that class Y of a dog. With the added noise, these models would generate realistic and diverse
representations of this class Y. Actually, if you're only
generating one class, one Y of a dog, then you probably don't
need this conditioning on Y and instead it's
just the probability over all the features X. You can see from this
side-by-side comparison that the discriminative models and the generative models actually near each other a bit here. As an example for
generative model, in a good run of a
generative model, you could get a picture of this pekingese and in another
run, a Tibetan mastiff. If you continue to
run it multiple times without any restrictions, you'll end up getting more
pictures representing the dataset your generative
model was trained on. That might look like a lot of
queue Labrador retrievers. There are many types
of generative models, and I'll briefly introduce
you to the most popular ones. Variational autoencoders or
VAE for short, and GANs. VAEs work with two models, an encoder and a decoder and these are typically
neural networks. They learn first by feeding in realistic images
into the encoder, such as this really realistic
image of a dog that I drew. Then the encoder's job is to find a good way of representing that image in this
wonky latent space. Let's say it finds
a place right here. Let's say this point
in the latent space can be represented by this vector of numbers 6.2,
negative three, 21. What the VAE does now is take this latent
representation or a point close to it and put it
through the decoder. The goal of the decoder
is to reconstruct the realistic image that
the encoder saw before. That's assuming the decoder has already been trained
to be pretty good. But in the beginning, the decoder won't be able to reconstruct the image and maybe the dog
produced will have evil eyes. After training, we
actually lop off the encoder and we can pick random points in
the latent space, such as here, and the
decoder will have learned to produce a
realistic image of a dog. What I just described is largely the autoencoder part or
variational autoencoder. The variational part
actually inject some noise into this whole
model and training process. Instead of having
the encoder encode the image into a single
point in that latent space, the encoder actually encodes the image onto a whole
distribution and then samples a point on
that distribution to feed into the decoder to then
produce a realistic image. This adds a little
bit of noise since different points can be
sampled on this distribution. GANs work in a rather
different way. They're composed of
two models again, but now there is a generator
which generates images like the decoder and a
discriminator that's actually a discriminative model
hidden inside of this. It's a little bit of
inception going on. The generator takes in
some random noise input, as you saw before, for example, 1.2, three, negative
five as a vector, and that is input
into this generator. Of course an optional
class of dog, but if we're just generating dog, we don't need to input that. As an output, it can generate
that same dog over time, of course, and of
course, in the beginning they can also be evil. The generator's role in
some sense it's very similar to the
decoder in the VAE. What's different is that
there's no guiding encoder this time that determines what noise vector
should look like, that's input into the generator. Instead, there's a discriminator looking at fake and real images and simultaneously
trying to figure out which ones are real and
which ones are fake. Over time, each model tries
to one up each other. These models compete
against each other which is why they're called adversarial, in the name generative
adversarial networks. You can imagine those muscles growing over time as
they compete against each other and learn from each other until they reach
a point where we, again, don't need
this second model anymore, the discriminator, and the generator can take in any random noise and
produce a realistic image. For example, a vector of
random numbers negative five, 6.2, and eight can generate
this cute Labrador retriever. During this specialization, you are going to focus on GANs, but feel free to read more
and VAEs if you find them interesting and
don't worry if you don't quite understand
how GANs work yet. I'm going to dig deeper on
their architecture and the way they learn in the
upcoming videos this week. In summary, generative
models learn to produce realistic examples, like an artist that can paint paintings that look like photos. Meanwhile, discriminative models distinguish between
different classes. In summary, generative
models learn to produce realistic examples such as producing those pictures
of cute dogs you just saw. A generative model is
an artist who's trying to learn how to create
photo-realistic art. Meanwhile, discriminative models distinguish between
different classes, such as a dog or a cat. But of course you also saw that a discriminative model can be a sub-component of
a generative model, such as the discriminator whose classes are real and fake. There are many kinds
of generative models, but in this specialization, you're going to study GANs. At the end of this week, you'll get to build your own GAN, that can be able to produce
handwritten digits. How cool is that? Get ready.
