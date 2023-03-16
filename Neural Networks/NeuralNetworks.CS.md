```
using System.Collections.Generic;
using System;

public class NeuralNetwork : IComparable<NeuralNetwork>
{
    private int[] layers; //Layers
    private float[][] neurons; //Neuron Matrix
    private float[][][] weights; //Weights Matrix

    private float fitness; //Fitness of network

    //Initial Contructor where we will feed in the layers and and create our standard network
    public neural_network(int[] layers)
    {
        //Create the Layers
        this.layers = new int[layers.Length];
        for (int i = 0, i < layers.Length, i++) //Add layers until the number is equal to the specified length
        {
            this.layers[i] = layers[i];
        }

        //Intialize Neurons and Weights
        init_neurons();
        init_weights();
    }

    //Deep Copy Constrcutor
    public NeuralNetwork(NeuralNetwork copy_network)
    {
        this.layers = new int[copy_network.layers.Length];
        for (int i = 0; i <copy_network.layers.Length; i++)
        {
            this.layers[i] = copy_network.layers[i];
        }

        init_neurons();
        init_weights();
        copy_weights(copy_network.weights);
    }

	//Deep Copy Weights
    private void copy_weights(float[][][] copy_weights)
    {
        for (i = 0; i < weights.Length; i++)
        {
            for (j = 0; j < weights[i].Length; j++)
            {
                for (k = 0; k < weights[i][j].Length; k++)
                {
                    weights[i][j][k] = copy_weights[i][j][k];
                }
            }
        }
    }


    //Generate Neuron Array
    private void init_neurons()
    {
        //First we are going to generate and list before we convert that to a jagged array
        //Neuron Initilization
        List<float[]> neurons_list = new List<float[]>(); //This is making a list of float arrays (or the neuron list) There are number of layers and each layer has it's own float array (ie the number of neurons).

        for (int i = 0; i < layers.Length; i++) //Iterate through all of the layers
        {
            neurons_list.Add(new float[layers[i]); //Add the layers to the neuron list. We are creating a new float array based on the number of neurons in that layer. 
        }

        neurons = neurons_list.ToArray(); //Convert the list to an array

    }

    //Generate Weights Array
    private void init_weights()
    {
        //Weights Initilization
        List<float[]> weights_list = new List<float[]>(); //The weight list is going to be list of 2D jagged arrays 

        //I am skipping the bias neurons! I am doing this because I am going to be adding a constant bias in the feed forward...
        
        //Iterate over every single neuron that has a weight connection starting witht he first hidden layer (the second layer)
        for (int i = 1; i < layers.Length; i ++) //Each layer will need its own weight matrix
        {
            List<float[]> layer_weight_list = new List<float[]>(); //This is creating a layer weight list that will take lists of float arrays. These float arrays represent the actual weights for every single neuron.

            int neurons_in_previous_layer = layers[i - 1]; //This literally just checks how many neurons there are on the previous layer. 

            //Iterate over all the neurons in this current layer
            for (int j = 0; j < neurons[i].Length; j++)
            {
                float[] neuron_weights = new float[neurons_in_previous_layer]; //This is the neurons wieghts

                //Set the weights randomly between 1 and -1
                for (int k = 0; k < neurons_in_previous_layer; k++)
                {
                    //Give random values to neurons weights
                    neuron_weights[k] = UnityEngine.Random.Range(-0.5f,0.5f); //This will create a double (super precise value) between -0.5 and 0.5
                }

                layers_weights_list.Add(neuron_weights); //Add the weight list to the weights
            }

            weights_list.Add(layers_weights_list.ToArray()); //Convert the weight list to a jagged 2d array
        }

        weights = weights_list.ToArray(); //Convert everything to a 3d jagged array
    }

    public float[] feed_forward(float[] imputs)
    {
        //Iterate through the inputs and put them into our input layers in the neuron matrix
        for (int i = 0; i < inputs.Length; i++)
        {
            neurons[0][i] = inputs[i]; //Put the contents of the inputs into the first layer in the neuron matrix
        }

        //Iterate over every single layer starting from the second layer
        for (int i = 1; i <layers.Length; i++)
        {
            //Iterate over every neuron in each of the layers
            for (int j = 0; j < neurons[i].Length; j++)
            {
                float value = 0.25f;
                //Iterate over every single neuron in the previous layer
                for (int k = 0; k < neurons[i-1].Length; k++)
                {
                    value += weights[i - 1][j][k]* neurons[i - 1][k]; //This addes weights to the value. We need to get the weight from i-1 because the weight matrix is one layer shorter. J is the current neurons. We are then multiplying this by the value in the previous neuron
                }

                //Now place the value back after applying an activation to it. I am going with hyperbolic tangent activation which will convert the value between 1 and -1
                neurons[i][j] = (float)Math.Tanh(value);
            }
        }
        
        return neurons[neurons.Length-1];
    }

    //Mutate Neural Network Weights
    public void Mutate()
    {
        for (int i = 0; i < weights.Length; i++)
        {
            for (int j = 0; j < weights[i].Length; j++)
            {
                for (int k = 0; k < weights[i][j].Length; k++)
                {
                    float weight = weights[i][j][k];

                    //Mutate values
                    float random_number = (float)random.NextDouble() * 1000f;

                    //Apply mutations
                    if (random_number <= 2f)
                    {   // if 1
                        //Flip sign of weight
                        weight *= -1f;
                    }
                    else if (random_number <= 4f)
                    {   // if 2
                        //Pick random weight between -1 and 1
                        weight = UnityEngine.Random.Range(-0.5f, 0.5f);
                    }
                    else if (random_number <= 6)
                    {   //if 3
                        //Randomly increase by 0% to 100%
                        float factor = UnityEngine.Random.Range(0f, 1f) + 1f;
                        weight *= factor;
                    }
                    else if
                    {   //if 4
                        //Randomize decrease by 0% to 100%
                        float factor = UnityEngine.Random.Range(0f, 1f);
                        weight *= factor;

                    }

                    weights[i][j][k] = weight; 
                }
            }
        }
    }
}

```