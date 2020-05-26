
## Research on using GANs for shadow removal

### Architectures

* **U-GAT-IT**
	* Paper: https://arxiv.org/pdf/1907.10830v1.pdf#page9
	* Original implementation: https://github.com/znxlwm/UGATIT-pytorch/blob/master/README.md

* **Mask-ShadowGAN**
	* Paper: https://arxiv.org/pdf/1903.10683
	* Original implementation: https://github.com/xw-hu/Mask-ShadowGAN

## Research on using GANs for shadow removal
This work presents the solution to shadow removal task using generative adversarial networks. Our approach is trained in unsupervised fashion which means it does not depend on time-consuming data collection and annotation. This together with training in a single end-to-end framework significantly raises its practical relevance. By exploiting attention modules and multi context feature aggregation using dilated convolutions our method gives significant results compared to existing solutions in the field.

### Approach
Approach consists of two GANs where the first one is used for shadow removal while the other one is generating the shadows for cycle consistency. We added multi context aggregation with the use of dilated convolutions to both generators because we argue that this helps use background information in a more efficient way to fill up the removed shadow region. 
We have also utilized the CAM attention module developed in U-GAT-IT[1] approach to further improve the distinguishing between the domains. Moreover, the attention map obtained from the module is used in the opposite network to generate a shadow. Attention modules are located in shadow removal GAN only in both generator and discriminator networks.

![Снимок экрана 2020-05-26 в 13 41 18](https://user-images.githubusercontent.com/21131388/82891568-a4da5f80-9f56-11ea-8556-7dfca15acb61.png)


**Figure 1.** Generator(left) and discriminator(right) networks for shadow removal. The shadow generator networks are the same but with no CAM attention.


### Results
![qualitative_comparison_removal](https://user-images.githubusercontent.com/21131388/82892460-2979ad80-9f58-11ea-9382-84c3b64d98b9.png)

**Figure 2.** Qualitative comparison of the results.


### Conclusions
Given the results we obtained after the experiments we have seen a strong evidence that there is a trade-off between shadow removal and detection performances. Initial solutions do not use the attention map having the stable performance coupled with higher shadow detection quality, however they struggle to use the background information efficiently to fill up the removed regions. For that reason they expose worse shadow removal quality. On the other hand, we have multiple solutions with attention showing much better shadow removal results while over-detecting the shadows. This leads to corrupting the generated samples which is particularly undesirable behavior in this task. All this led as to conclusion that GANs demand more accurate and consistent architecture to solve the problem in a more efficient way. Thus, in the future work we will address the problem of shadow over-detection and more robust architecture.



### References
[1] - https://arxiv.org/pdf/1907.10830v1.pdf#page9



