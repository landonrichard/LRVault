## **Unsupervised Learning**

**Input Layer**
: Composed of artificial input neurons, and brings the initial data into the system for further processing by subsequent layers of artificial neurons. The input layer is the very beginning of the workflow for the artificial neural network.

**Hidden Layers**
`def here`

**Output Layer**
`def here`

>![[Neural Networks/Images/Architecture.jpg]]
>Each step in Layers are notated by stepping up L1, L2, L3, etc. There are more than one hidden layer that steps down. This is just an example for comprehension. 

Notice how each layer and subsequent hidden layer can have a different number of ==nodes== (neurons). This is because each Layer is held in an ==array==.

>**The example layers above array would look like:**
L1 - `[1,2,3]`
L2 - `[1,2,3,4,5]`
L3 - `[1,2]`

The ==array== of layers is then wrapped into a ==two-dimensional matrix== with every single row in the matrix having the ability to have ==variable lengths==.
>**This would look something like:**
![[Matrix Example.png]]

In C#, this idea of having N x M matrix where m is a variable length is called a Jagged Array. 

**Jagged Array** - `An array whose elements are arrays, possibly of different sizes. Also called an array of arrays`

In C# [][] means a jagged array. 
>An example of this is `float[][]neruons = new float [numberOflayers][]`