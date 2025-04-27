## Edge Detection
### Scale Invariant Feature Transform
--
>Definition: SIFT is used for image alignment and 2D object recognition.
#### Interest Points:
- Detector should be compensate for Variations or remove the Variations.
- Matching features is easier when the *size* and *orientation* are same.
- Interest Points have *rich image content*.
- Has well-defined *representation* for comparing with other points.
- Has a well-defined *position* in the image.
- Should be *invariant to image rotation and scaling.*
- Insensitive to *lighting* changes.
- Edges and Corners aren't good *Interest Point* due to it's common presence.
- Blobs as interest points:
	- Should be able to locate the Blob.
	- Determine it's *size*.
	- Determine it's *orientation*.
	- Formulate a *description* or a signature that is independent of size and orientation.
#### Detecting Blobs:
-  Extremum of Derivative of Gaussian denotes an Edge.
![[Pasted image 20250427201510.png]]
- Response of the Operator reduces with raise in Sigma. Change in Sigma allows us to find Blobs in different scales and resolutions.
- We normalize the Operator using $\sigma^2$ . It increases the amplitude in the above case.
- The extremum obtained by varying Sigma is the center of the Blob.
![[Pasted image 20250427201849.png]]
- Size of the Gaussian Operator will be equal to the width of the Blob when an extremum is encountered.
- This allows us to form Stack of images which is represented with Two Parameters. 
	- $x \rightarrow$ Spatial. Location of the Blobs.
	- $\sigma \rightarrow$ Scale of the Blob.
	- Find the local extrema in this coordinate space.
![[Pasted image 20250427202243.png]]
- The $\sigma$ at which $\sigma$-normalized 2nd derivative attains it's extreme value.
- Characteristic Scale $\propto$ Size of the Blob.
- Summary:
	- Given: 1D Signal $f(x)$.
	- Compute: $\sigma^2 \frac{\partial^2 n_{\sigma}}{\partial x^2}*f(x)$ at many scales $(\sigma_0, \sigma_1, ..., \sigma_k)$.
	- Find: $(x^*, \sigma^*) = \underset{(x, \sigma)}{\text{arg max}} \|\sigma^2 \frac{\partial^2 n_{\sigma}}{\partial x^2}*f(x)\|$.
	- $x^*$: Blob Position.
	- $\sigma^*$: Size of Blob.
![[Pasted image 20250427203221.png]]
- Summary for 2D:
	- $(x^*,y^*,\sigma^*)=\underset{(x,y,\sigma)}{\|\sigma^2\nabla^2n_{\sigma}*I(x,y)\|}$
	- $(x^*, y^*)$: Position of the Blob.
	- $\sigma^*$: Size of the Blob.
#### SIFT Detector:
- Fast Normalized LoG Approximation: DoG
	- Difference of Gaussian = $(n_{s\sigma} - n_{\sigma} \approx (s-1)\sigma^2\nabla^2n_{\sigma})$
	![[Pasted image 20250427204250.png]]
	![[Pasted image 20250427204331.png]]
	![[Pasted image 20250427204350.png]]
	- You can employ scale invariance by removing the scale difference. It's just two image where the Interest Point peaks at different Sigma. ![[Pasted image 20250427204625.png]]
	- Removing the Effect of Orientation involved applying gradients operator to every single pixel of the Blob.
	- Create an Histogram of Directions. ![[Pasted image 20250427204830.png]]
#### SIFT Descriptor:
- Segment the Image to any number of Blocks and find the Histogram of Orientation and concatenate them to create a Long Histogram creating a Description Vector. This Normalized Histogram is invariant to Rotation, Scale and Brightness.
- Comparing SIFT Descriptors:
	- L2 Distance: Distance between two Histograms.
	- Normalized Correlation.
	- Intersection Metric.
### Histogram of Oriented Gradients

