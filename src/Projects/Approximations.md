
<script id="MathJax-script2">
	import { onMount } from 'svelte';
	onMount(() => {
		let script = document.createElement('script');
    script.src = "https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-svg.js";
    document.head.append(script);
		script.onload = () => {
      MathJax = {
        tex: {inlineMath: [['$', '$'], ['\\(', '\\)']],
        extensions: ["AMSmath.js", "AMSsymbols.js"]},
        svg: {fontCache: 'global'}
      };
		};
	});
</script>
# Approximating Behaviors of Hodgkin-Huxley Neuron Models With Networks of Simpler Models
## With Calvin Zhang-Molina, Fall 2019-Spring 2021. [Poster Presentation](PIR_Pres.pdf)
Can small networks of simple neurons approximate more complex ones? From the field of non-biological neural networks, we know that this is the case. Deep spiking neural networks can approximate a wide range of time series functions arbitrarily well. Each of the components in a spiking neural network is made of some variation of the following leaky integrate and fire (LIF) neuron:
{`$$\\tau_k\\dfrac{dV_k}{dt} = -V_k + I_k + \\alpha(t)\\sum_{t_{ij}}w_j\\delta(t-t_{ji})$$`}
Where {`\\(t_{ij}\\)`} gives the ith firing time of neuron j in the network, {`\\(t_{w_j}\\)`} is the weight of the firing strength of neuron j on neuron k, and {`\\(\\alpha(t)\\)`} gives the decay function on the firing, {`\\(I_k\\)`} is the steady state voltage, and {`\\(\\tau_k\\)`} is the time constant of the neuron. A LIF neuron "fires" when it's voltage reaches some threshold value. At this point, it's voltage resets to 0. This equation is extremely simple in comparison to more biologically plausible Hodgkin-Huxley type model neurons which consits of four coupled nonlinear differential equations. Because of this, an LIF neuron cannot display the same amount of rich behavior that biological and Hodgkin-Huxley neurons can. In fact, an LIF neuron has a very similar equation to how a single ion channel neuron would behave, of which a Hodgkin-Huxley type has many. However, if we pass in a set of time series voltage inputs into a neuron and then retrieve the spike times of that neuron, we can treat a neuron as a nonlinear function from one time series to another. This behavior can be approximated by a spiking neural network of some size. Now, we might ask how small can an LIF network be and still approximate some property of a biological neuron.

In this project, we investigated the minimum number of LIF neurons needed to display the property of Post-Inhibitory Rebound (PIR). PIR is an effect in biological neurons where after recieving a strong inhibitory pulse, a neuron may release a spike. This is due to the fact that the currents of exitatory channels in a neuron are faster than inhibitory channels, meaning that closing both channel types with a low voltage will lead to the exitatory currents recovering faster and potentially leading to a runaway spike before the inhibitory currents can react. This is in sharp contrast to how a neuron typically fires by having its exitatory currents activated by a strong, positive current. We defined a PIR-like effect to be a temporary increase in the firing rate of a neuron following a strong inhibitory current. We were able to show that while this effect is impossible to replicate in a single LIF neuron, we can get it in a network of 2 neurons. In addition, we were able to derive a sufficient condition for obtaining this effect.

The part of this project that I found to be the most interesting was how complicated the dynamics a network of two coupled integrate and fire neurons could produce. For example we were able to analytically capture a set of recursive equations for the switching times of the network (switching from when one neuron would supress the voltage of the other to the opposite), and they displayed very interesting limit cycles.

<img src = "./images/limitCycle.png" alt="responsive" style="border:solid #292b2c; width:65vw;height:auto"/>

I also really enjoyed how much geometry was present in the problem. There was a point at which I realized that we could model a set of n linear integrate and fire neurons as sort of bouncing around inside a box spanned by {`\\(\(-\\infty,1)^n\\)`}while being linearly attracted to some point outside of the box. Here is a cool demonstration of this box visualization, where the limit cycles of two neurons evolve as the coupling strength between them is strengthened.

<img src = "./images/limitSet.gif" alt="responsive" style="border:solid #292b2c;width:65vw;height:auto"/>

