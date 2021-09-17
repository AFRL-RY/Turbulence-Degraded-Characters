# Turbulence-Degraded-Characters
A imagery database for machine learning experiments, atmospheric turbulence characterization, and turbulence restoration research.

The TDC database is suitable for machine learning experiments, atmospheric turbulence characterization, and turbulence restoration research. The imagery is generated using the brightness function [1] method of turbulence simulation as implemented in the [WONAT library](https://www.optonicus.com/portfolio/wavefront-beam-control-techniques/). The imaging scenario is defined by a 100 mm aperture telescope imaging a 550 mm wide square field over a range of 1 km.  The wavelength of the simulation is set to 550 nm.   The sample spacing in the object plane is 2.75 mm corresponding to critical sampling at the diffraction limit of the optics.    The phase screen model of homogeneous turbulence throughout this volume of atmosphere is in conformance with the Kolmorogov power spectrum.  The imagery spans turbulence strengths from <img src="https://render.githubusercontent.com/render/math?math=C_n^2 = 2.29\times 10^{-15}"> to <img src="https://render.githubusercontent.com/render/math?math=C_n^2 = 3.28 \times 10^{-14}"> <img src="https://render.githubusercontent.com/render/math?math=m^{-2/3}"> corresponding to <img src="https://render.githubusercontent.com/render/math?math=D/r_0=1"> through <img src="https://render.githubusercontent.com/render/math?math=D/r_0=5"> where <img src="https://render.githubusercontent.com/render/math?math=r_0"> is the coherence diameter and <img src="https://render.githubusercontent.com/render/math?math=C_n^2"> is the refractive index structure parameter.  This scenario was selected because it can be reproduced experimentally with widely available equipment.

The 62 target classes consist of characters in a single font (numbers, lowercase letters, uppercase letters).  Each uppercase character is approximately 47 mm tall and the lowercase letters are somewhat shorter.  1000 samples are generated for each character for a total of 62,000 samples per turbulence level.  A coarse correction for turbulence-induced global motion is applied to each sample to constrain the results on a 50x50 pixel grid.  Examples of the 'E' character for <img src="https://render.githubusercontent.com/render/math?math=D/r_0=2"> are shown in the first figure below.  The second Figure shows a single example of the 'E' character from each of the five levels of turbulence in the database.  The database consists of five HDF5 files, corresponding to <img src="https://render.githubusercontent.com/render/math?math=D/r_0=1"> through <img src="https://render.githubusercontent.com/render/math?math=D/r_0=5">.  Within each HDF5 file, dataset labels correspond to target classes (e.g, 'E', 'e', '3', and so on).

![Six examples of the 'E' character for in the D/r_0=2$ case.](pcAOP_Figure_1.png  "Six examples of the 'E' character for in the $D/r_0=2$ case.")

Six examples of the 'E' character for in the <img src="https://render.githubusercontent.com/render/math?math=D/r_0=2"> case.

![ Examples of the 'E' character across $D/r_0 = 1$ through $5$.](Figure_1b.png  " Examples of the 'E' character across $D/r_0 = 1$ through $5$.")

Examples of the 'E' character across <img src="https://render.githubusercontent.com/render/math?math=D/r_0 ="> 1 through 5.

## <a name="bulk_data_access"></a> Bulk Data Access - Amazon S3
<!-- This section is based on http://arxiv.org/help/bulk_data_s3 -->

The Turbulence Degraded Characters data is available from Amazon
Simple Storage Service (S3) in Requester Pays buckets (i.e., you are charged
by Amazon to access, browse, and download this data). Please see
<a href="http://docs.aws.amazon.com/AmazonS3/latest/dev/RequesterPaysBuckets.html">Requester Pays Buckets</a> in the <a href="http://docs.amazonwebservices.com/AmazonS3/latest/dev/">Amazon S3 Guide</a> for
more information on this service. Your use of Amazon S3 is subject to Amazon's
Terms of Use. The accessibility of SDMS data from Amazon S3 is provided "as is"
without warranty of any kind, expressed or implied, including, but not limited
to, the implied warranties of merchantability and fitness for a particular use.
Please do not contact SDMS for assistance with Amazon services, you can post
a GitHub issue and the authors will try and assist.

The name of the S3 bucket is s3://sdms-turbulence-degraded-characters/

### Tools

We do not track development of tools interacting with Amazon S3, nor endorse any
particular tool.  However, in development of this facility we found the Python
package <a href="http://s3tools.org/s3cmd">s3cmd</a> to be useful on Mac OS X
and Linux.  For Windows the AWS team provided the following suggestions
<a href="http://s3browser.com/requester-pays-buckets.php">s3browser.com</a> and
<a href="http://www.crossftp.com/amazon-s3-client.htm">cross ftp</a>.

### s3cmd Example

The examples shown below were developed and tested with Linux and Mac OS X
using the Python distribution of Enthought Canopy.  First you must  <a
href="http://docs.aws.amazon.com/AmazonS3/latest/gsg/SigningUpforS3.html">
establish a AWS account</a> and download your AWS_ACCESS_KEY_ID and
AWS_SECRET_ACCESS_KEY. Next use the following commands to export your key id and
secret access key to the shell environment replacing the values of
AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY with the values from your newly
established AWS account:

```bash
export AWS_ACCESS_KEY_ID="JSHSHEUESKSK65"
export AWS_SECRET_ACCESS_KEY="kskjskjsAEERERERlslkhdjhhrhkjdASKJSKJS666789"
```

Install s3cmd with pip:

```bash
pip install s3cmd
```

To list the directory of the sdms-unicorn-2008 bucket use the following command:

```bash
s3cmd --requester-pays ls s3://sdms-turbulence-degraded-characters/
```

Please note all the UNICORM 2008 data products are in a single directory.

To determine the amount of disk space in the sdms-unicorn-2008 bucket use the command:

```bash
s3cmd --requester-pays --recursive --human du s3://sdms-turbulence-degraded-characters/
```

To retrieve a file:

```bash
s3cmd --requester-pays get s3://sdms-turbulence-degraded-characters/1_labeled.hdf5
```


### Optimizing Data Download Costs

The  Turbulence Degraded Characters data set is large at approximately 1.5 GB, to download the entire
data set it would cost $0.14. This assumes AWS download fees are $0.09 a gigabyte.
Most researchers will not require the entire Turbulence Degraded Characters data set, carefully
consider the data that you require to meet your research needs and download
costs.  We have divided the dataset into small hdf5 files to make the download
easier and to make it possible for a researcher to select the data they need.

# Citation
When reporting results that use the TDC dataset, please cite:

LeMaster, Daniel A., Steven Leung, and Olga L. Mendoza-Schrock. "Joint object classification and turbulence strength estimation using convolutional neural networks." Applied Optics 60.25 (2021): G40-G48.
https://www.osapublishing.org/ao/abstract.cfm?uri=ao-60-25-G40
# References

[1] Lachinova, Svetlana L., et al. "Anisoplanatic imaging through atmospheric turbulence: Brightness function approach." Atmospheric Optics: Models, Measurements, and Target-in-the-Loop Propagation. Vol. 6708. International Society for Optics and Photonics, 2007.

## Copyright information

This page and data set is in the public domain under [17 U.S.C. 105](https://www.law.cornell.edu/uscode/text/17/105).
