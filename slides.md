---
# try also 'default' to start simple
theme: seriph
title: Heartian_slides
class: text-center
drawings:
  persist: false
transition: fade-out
comark: true
colorSchema: dark
fonts:
  serif: Libre Baskerville
  sans: Libre Baskerville
  mono: Fira Code
---

# 💓 Heartian: Physiology-Aware Relightable Gaussian Head Avatar 

<div class="flex justify-center">
  <div class="text-center w-36 -mt-3">
    <img src="/Merry.jpg" class="w-26 h-26 rounded-full object-cover mx-auto" />
    <div class="text-sm font-bold mt-2 decoration-dotted">Xiaoyue Fan<sup>1</sup></div>
  </div>
  <div class="text-center w-36 mt-1">
    <img src="/jose.jpg" class="w-20 h-20 rounded-full object-cover mx-auto" />
    <div class="text-sm mt-2 decoration-dotted">Jose Echevarria<sup>2</sup></div>
  </div>
  <div class="text-center w-36 mt-1">
    <img src="/Akshay.jpg" class="w-20 h-20 rounded-full object-cover mx-auto" />
    <div class="text-sm mt-2 decoration-dotted">Akshay Paruchuri<sup>3</sup></div>
  </div>
  <div class="text-center w-36 mt-1">
    <img src="/Kaan.jpg" class="w-20 h-20 rounded-full object-cover mx-auto" />
    <div class="text-sm mt-2 decoration-dotted">Kaan Akşit<sup>1</sup></div>
  </div>
</div>

<div class="text-sm mt-4 opacity-80">
<sup>1</sup>University College London &nbsp; <sup>2</sup>Adobe Research &nbsp; <sup>3</sup>Stanford University<br>
<br>
SIGGRAPH Asia 2026 Technical Communications
</div>

<SyncVideos :names="['1','2','3','4','4_1','4_2','4_3','4_4']" class="mt-4" />


<div class="flex justify-between items-center w-full mt-1">
  <div class="flex items-center gap-1">
    <img src="/Siggraph_logo.png" class="h-8 items-center bg-white p-1" />
    <img src="/logo_all.png" class="h-8" />
  </div>

  <div class="flex flex-col items-center">
    <span class="text-xs opacity-80" style="letter-spacing: 0.1em;">
      Project Page
    </span>
    <img src="/site.png" class="w-16 mt-1" />
  </div>
</div>


<style>
.slidev-layout.default {
  justify-content: flex-start !important;
  padding-top: 1.5rem !important;
}
</style>

<!--
Hi everyone. I'm Xiaoyue Fan. Very happy to be here to share our work, Heartian: Physiology-Aware Relightable Gaussian Head Avatar. Before I start, I would like to give a shout-out to all my co-authors, Jose, Akshay and Kaan for all the support and guidance throughout this project.
-->

---
transition: fade-out
---

# <span v-if="$clicks < 2">What is <span class="text-blue">Remote Photoplethysmography (rPPG)</span>?</span><span v-else>Where can rPPG be <span class="text-blue">Applied</span>?</span>

<br>
<div v-click=1>
rPPG is a non-contact method that captures subtle, cardiac-driven color variations of the skin in video to recover the blood volume pulse, from which heart rate can be derived.
</div>

<div v-click="[1, 2]" class="flex flex-col items-center mt-6">
  <video :src="base + 'rppg_sim.mp4'" class="h-75" autoplay muted loop playsinline></video>
</div>

<div v-click="[1, 2]" class="absolute bottom-5 left-10 right-16 text-[10px] opacity-70 text-left">
  S. Sakib, Z. Hasan, and N. Roy,
  <a href="https://doi.org/10.1002/widm.70039" target="_blank">
    "A State-of-the-Art Survey of Remote Photoplethysmography for Contactless Health Parameters Sensing,"
  </a>
  <i>WIREs Data Mining and Knowledge Discovery</i>,
  vol. 15, no. 3, Art. no. e70039, 2025.
</div>


<div
  v-click="2"
  class="absolute top-50 left-0 w-full"
  style="height: 350px;"
>
  <video
    v-for="i in 5"
    :key="i"
    :src="`/${base}${i}_app.mp4`"
    autoplay
    muted
    loop
    playsinline
    class="absolute object-contain rounded"
    :style="{
      width: $clicks === i + 1 ? (i >= 4 ? '480px' : '360px') : (i <= 3 ? '160px' : '220px'),
      height: $clicks === i + 1 ? (i >= 4 ? '340px' : '276px') : (i <= 3 ? '130px' : '160px'),
      left: $clicks === i + 1
        ? '50%'
        : (
            i === 1 ? '4%' :
            i === 2 ? '4%' :
            i === 3 ? '79%' :
            i === 4 ? '76%' :
            '82%'
          ),
      top: $clicks === i + 1
        ? (i >= 4 ? '-32px' : '0px')
        : (
            i === 1 ? '0px' :
            i === 2 ? '145px' :
            i === 3 ? '0px' :
            i === 4 ? '133px' :
            '245px'
          ),
      transform: $clicks === i + 1
        ? 'translateX(-50%) scale(1)'
        : 'translateX(0) scale(0.95)',
      opacity: $clicks >= i + 1 ? 1 : 0,
      zIndex: $clicks === i + 1 ? 20 : 1,
      transition: 'width 0.8s ease-in-out, height 0.8s ease-in-out, left 0.8s ease-in-out, top 0.8s ease-in-out, transform 0.8s ease-in-out, opacity 1.0s ease-in-out',
      transitionDelay: $clicks === i + 1
        ? '0s, 0s, 0s, 0s, 0s, 0.4s'
        : '0s'
    }"
  ></video>
</div>

<div v-click="2" class="absolute bottom-5 left-10 right-16 text-[10px] opacity-70 text-left">
  T. Curran, D. McDuff, and E. Yang,
  <a href="https://doi.org/10.20517/chatmed.2022.25" target="_blank">
    "Camera-based remote photoplethysmography for blood pressure measurement: current evidence, clinical perspectives, and future applications,"
  </a>
  <i>Connected Health and Telemedicine</i>,
  vol. 2, Art. no. 200004, 2023.
</div>

<div v-click="6" class="hidden"></div>

<script setup>
const base = import.meta.env.BASE_URL
</script>

<!--
Let me start by giving a brief idea of the term Remote Photoplethysmography (rPPG).

[click] It's a non-contact technique that uses a camera to capture subtle cardiac-driven color changes of the skin. An rPPG algorithm then processes the video to recover heart rate and other physiological signals.

(Heart rate, Heart rate variability, respiratory rate, oxygen saturation)

[click] Its application include Daily monitoring via your phone

[click] Clinical monitoring via CCTV

[click] Mass monitoring while tracking the moving subjects 

[click] Basically, in different daily scenarios, as long as a camera is over there

[click] One of the exciting applications is live monitoring in telemedicine.
-->

---
transition: fade-out
---

# Why do <span class="text-blue">Gaussian Head Avatars</span> need <span class="text-blue">rPPG Signals</span>?

<div class="w-80 flex flex-col items-center">
  <p>Telemedicine increasingly relies on video-based consultation, yet its remote monitoring still mostly depends on <span class="text-red">contact sensors</span>.</p>
  <video v-if="$clicks < 1" :src="base + 'contact.mp4'" class="h-70" autoplay muted loop playsinline></video>

  <div v-click="1" class="absolute w-80 top-55">
    <p>
      3D Gaussian Splatting has emerged as a prominent research trend in human representation.<br>
      Example: Microsoft's
      <a href="https://microsoft.github.io/VoluMe/" target="_blank">VoluMe</a>
    </p>
    <LoopVideo :src="base + '4.mp4'" class="w-38 absolute left-15 gap-12 mt-1" />
  </div>
</div> 

<v-drag-arrow v-click="2" pos="294,423,35,0" one-way op70 width="1" />
<img v-click="2" src="/PURE_baseline.png" class="absolute left-88 bottom-24 w-100" />

<div v-click="2" class="absolute right-25 top-40 w-fit max-w-115 border border-dashed border-gray-100 px-3 py-2">
  <p>Gaussian head avatars typically model intrinsic facial appearance as temporally <span class="text-red">static</span> <br>👉 Omitting subtle skin-color variation that rPPG relies on to recover physiological signals</p>
</div>

<div v-click="2" class="absolute right-121 bottom-12 text-xs opacity-70 flex flex-col items-start gap-1">
  <div class="flex items-center gap-2">
    <span class="inline-block w-3 h-0.5" style="background:#f59e0b"></span>
    Ground Truth
  </div>
  <div class="flex items-center gap-2">
    <span class="inline-block w-3 h-0.5" style="background:#3b82f6"></span>
    <a href="https://eastbeanzhang.github.io/HRAvatar/" target="_blank">HRAvatar</a>Baseline
  </div>
</div>

<div
  v-click="3"
  class="absolute inset-0 z-40 bg-white/70"
></div>

<div
  v-click="3"
  class="absolute inset-0 z-50 flex items-center justify-center"
>
  <div class="bg-black/85 text-white px-8 py-5 rounded-xl text-xl font-semibold shadow-2xl whitespace-nowrap">
    Can Gaussian Head Avatars be
    <span v-mark.line.green="{at: 4}">physiology-aware</span>,
    and thus
    <span v-mark.line.green="{at: 4}">rPPG-consistent</span>?
  </div>
</div>

<div v-click="1" class="absolute bottom-5 left-10 right-16 text-[10px] opacity-70 text-left">
  <a href="https://eastbeanzhang.github.io/HRAvatar/" target="_blank">
    "HRAvatar: High-Quality and Relightable Gaussian Head Avatar,"
  </a>
  <i>Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)</i>,
  2025.
</div>

<!-- (real-time 3D video calls through live Gaussian splat prediction) -->
<style>
h1 {
  color: #fff !important;
  font-size: 1.6rem !important;
  white-space: nowrap;
  line-height: 1.2;
}
h1 .text-blue {
  color: #2B90B6 !important;
}
.slidev-vclick-target {
  transition: opacity 0.6s ease !important;
}
</style>

<script setup>
const base = import.meta.env.BASE_URL
</script>

<!--
However, while video consultations are becoming increasingly common in telemedicine, remote monitoring still largely relies on contact sensors, which are uncomfortable and inconvenient to use, especially for elderly people and kids.

[click] As many of you may know, 3D Gaussian Splatting has attracted a lot of attention in human representation. For example, VoluMe released by Microsoft predicts 3D Gaussians in real time from a standard webcam feed, enabling live 3D video calls.

[click] However, its reconstructed appearance is typically static over time, inherently omitting the subtle skin-color variations that rPPG relies on to recover physiological signals.

[click] Therefore, we asked a question: 

[click] Can Gaussian Head Avatars be physiology-aware, thus rPPG-consistent?
-->

---
transition: fade-out
---

<div v-if="$clicks < 1" key="hero" class="absolute inset-0 flex flex-col items-center justify-center text-center">
  <h1 class="text-4xl">💓 <span class="text-blue">Heartian</span><span class="text-[0.8em] opacity-80">: Physiology-Aware Relightable Gaussian Head Avatar</span>
  </h1>

  <p class="text-[0.8em] mt-4">A physiology-aware modulation framework that embeds prescribed rPPG signals into relightable Gaussian head avatars.
  </p>
</div>

<div v-else key="pipeline" class="absolute top-6 left-10 right-10">
  <h1 class="text-4xl">💓 <span class="text-white">Heartian</span><span class="text-[0.8em]">:</span><span class="text-blue"> Pipeline</span></h1>

  <p class="text-[0.8em] mt-4">A physiology-aware modulation framework that embeds prescribed rPPG signals into relightable Gaussian head avatars.
  </p>
</div>

<v-click>
<div class="flex items-center mt-23" :style="{ opacity: ($clicks >= 3 && $clicks < 9) ? 0.3 : undefined, transition: 'opacity 0.3s' }">
  <LoopVideo :src="base + '1.mp4'" class="h-28" />
</div>
<div class="flex items-center mt-2" :style="{ opacity: ($clicks >= 3 && $clicks < 9) ? 0.3 : undefined, transition: 'opacity 0.3s' }">
  <LoopVideo :src="base + '4.mp4'" class="h-28" />
</div>
<div class="flex items-center gap-12 mt-2" :style="{ opacity: ($clicks >= 3 && $clicks < 9) ? 0.3 : undefined, transition: 'opacity 0.3s' }">
  <LoopVideo :src="base + '3.mp4'" class="h-28" />
</div>

<script setup>
const base = import.meta.env.BASE_URL
</script>

<div class="absolute right3 bottom-6 text-xs opacity-70 flex flex-col items-end gap-1" :style="{ opacity: $clicks >= 9 ? 0 : ($clicks >= 3 ? 0.3 : undefined), transition: 'opacity 0.3s' }">
  <div class="flex items-center gap-2">
    <a href="https://eastbeanzhang.github.io/HRAvatar/" target="_blank">HRAvatar</a>Baseline
  </div>
</div>

</v-click>
<v-click>

<v-drag-arrow pos="174,430,35,0" one-way op70 width="1" :style="{ opacity: $clicks >= 9 ? 0 : $clicks >= 3 ? 0.3 : undefined, transition: 'opacity 0.3s' }"/>
<v-drag-arrow pos="174,193,35,0" one-way op70 width="1" :style="{ opacity: $clicks >= 9 ? 0 : $clicks >= 3 ? 0.3 : undefined, transition: 'opacity 0.3s' }"/>
<v-drag-arrow pos="174,313,35,0" one-way op70 width="1" :style="{ opacity: $clicks >= 9 ? 0 : $clicks >= 3 ? 0.3 : undefined, transition: 'opacity 0.3s' }"/>


<div class="absolute top-28 left-55 flex items-center gap-12 mt-5" :style="{ opacity: ($clicks >= 4 && $clicks < 7) ? 0.3 : undefined, transition: 'opacity 0.3s' }">
  <img src="/p18_skin.png" class="h-28 w-32" />
</div>
<div class="absolute top-61 left-55 flex items-center gap-12 mt-2" :style="{ opacity: ($clicks >= 4 && $clicks < 7) ? 0.3 : undefined, transition: 'opacity 0.3s' }">
  <img src="/pure_skin.png" class="h-28 w-32" />
</div>
<div class="absolute top-91 left-55 flex items-center gap-12 mt-2" :style="{ opacity: ($clicks >= 4 && $clicks < 7) ? 0.3 : undefined, transition: 'opacity 0.3s' }">
  <img src="/ubfc_skin.png" class="h-28 w-32" />
</div>

</v-click>

<div v-click=[3,10] class="absolute right-30 top-32 w-[48%] text-[0.85em]" :style="{ opacity: ($clicks >= 4 && $clicks <= 10) ? 0.3 : undefined, transition: 'opacity 0.3s' }">

<p class="absolute bottom-8 left-46">Albedo Modulation</p>

$$
\mathbf{c}_i^{\text{m}}(t) = \mathbf{c}_i^{\text{base}}(t) + A
$$

</div>

<div v-click=[3,10] class="absolute right-3 top-32 w-[48%] text-[0.85em]">

$$
\cdot \space m_i(t)
$$

</div>

<div v-click=[4,10] class="absolute left-58 top-52 w-[48%] text-[0.85em]" :style="{ opacity: ($clicks >= 5 && $clicks < 7) ? 0.3 : undefined, transition: 'opacity 0.3s' }">

$$
m_i(t) =
$$

</div>

<div v-click=[4,10] class="absolute right-32 top-48 w-[48%] text-[0.85em]" :style="{ opacity: $clicks === 6 ? 0.3 : undefined, transition: 'opacity 0.3s' }">

$$
 \underbrace{\sum_{k=1}^{2} A_k \exp\left(-\frac{d(\theta(t), \mu_k)^2}{2\sigma_k^2}\right)}_{\text{fundamental}} 
$$

</div>

<div v-click=[4,10] class="absolute left-126 top-52 w-[48%] text-[0.85em]" :style="{ opacity: ($clicks >= 5 && $clicks < 7) ? 0.3 : undefined, transition: 'opacity 0.3s' }">

$$
+
$$

</div>

<div v-click=[4,10] class="absolute left-150 top-52 w-[48%] text-[0.85em]" :style="{ opacity: $clicks === 5 ? 0.3 : undefined, transition: 'opacity 0.3s' }">

$$
B \cdot \underbrace{f_{\text{MLP}}(\theta(t), b(t), p_i)}_{\text{residual}}
$$

</div>

<div v-click="[5, 6]" class="absolute top-70 left-85 flex flex-col items-center gap-2 mt-5">

  <div class="text-[0.7em]">

$$
d(\theta, \mu) = \arctan2(\sin(\theta - \mu), \cos(\theta - \mu))
$$

  </div>
  <img src="/modulation.png" class="w-65" />
  <p class="relative -top-3 text-[0.5em] opacity-70">A typical PPG waveform with systolic (blue) and diastolic waves (red) in the time (a) and phase domains (b).</p>
</div>

<div v-click="[5, 7]" class="absolute top-50 left-185 flex flex-col items-center gap-1 mt-5">

  <div class="text-[0.7em] opacity-80 mt-20">Accumulated phase</div>

  <div class="text-[0.7em] -mt-4">

$$
\begin{gathered}
\phi(t) = \phi_0 + \sum_{k=0}^{t} \delta_k \\
\theta(t) = \arctan2(\sin(\phi(t)), \cos(\phi(t)))
\end{gathered}
$$

  </div>

</div>

<div v-click="[6, 7]" class="absolute top-64 left-188 flex flex-col items-center gap-1 mt-5">
  
  <div class="text-[0.7em] opacity-80 -mt-21">Per-Gaussian Scalar Residual</div>

</div>

<div v-click="[6, 7]" class="absolute left-[380px] top-[365px] w-[555px] text-white">

<svg viewBox="-80 0 590 170" width="100%" xmlns="http://www.w3.org/2000/svg" fill="none" stroke="currentColor" stroke-width="1">
  <defs>
    <marker id="ah" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
      <path d="M2 1L8 5L2 9" stroke="currentColor" stroke-width="1.5" fill="none" />
    </marker>
  </defs>

  <g fill="currentColor" stroke="none" text-anchor="end" dominant-baseline="central">
    <text x="-8" y="29" style="font-size:12px">Phase</text>
    <text x="-8" y="43" style="font-size:11px">Embedding</text>
    <text x="-8" y="79" style="font-size:12px">Beat Index</text>
    <text x="-8" y="93" style="font-size:11px">Embedding</text>
    <text x="-8" y="129" style="font-size:12px">Positional</text>
    <text x="-8" y="143" style="font-size:11px">Embedding</text>
  </g>

  <rect x="0" y="20" width="50" height="30" rx="3" />
  <rect x="0" y="70" width="50" height="30" rx="3" />
  <rect x="0" y="120" width="50" height="30" rx="3" />
  <g fill="currentColor" stroke="none" text-anchor="middle" dominant-baseline="central">
    <text x="25" y="35" style="font-size:14px">θ(t)</text>
    <text x="25" y="85" style="font-size:14px">b(t)</text>
    <text x="25" y="135" style="font-size:14px">pᵢ</text>
  </g>

  <line x1="50" y1="35" x2="150" y2="35" />
  <line x1="50" y1="85" x2="150" y2="85" />
  <line x1="50" y1="135" x2="150" y2="135" />
  <line x1="150" y1="35" x2="150" y2="135" />
  <g fill="currentColor" stroke="none">
    <text x="55" y="28" style="font-size:11px">Fourier PE · R²⁰</text>
    <text x="55" y="78" style="font-size:11px">Embed · R⁸</text>
    <text x="55" y="128" style="font-size:11px">2-layer enc. · R⁸</text>
  </g>

  <line x1="150" y1="85" x2="208" y2="85" marker-end="url(#ah)" />
  <text x="178" y="76" text-anchor="middle" fill="currentColor" stroke="none" style="font-size:11px">R³⁶</text>

  <rect x="210" y="62" width="65" height="46" rx="3" />
  <line x1="275" y1="85" x2="293" y2="85" marker-end="url(#ah)" />
  <rect x="295" y="62" width="80" height="46" rx="3" />
  <line x1="375" y1="85" x2="393" y2="85" marker-end="url(#ah)" />
  <rect x="395" y="62" width="65" height="46" rx="3" />
  <line x1="460" y1="85" x2="476" y2="85" marker-end="url(#ah)" />

  <g fill="currentColor" stroke="none" text-anchor="middle" dominant-baseline="central">
    <text x="242" y="76" style="font-size:12px">Linear</text>
    <text x="242" y="94" style="font-size:11px">→ 128</text>
    <text x="335" y="76" style="font-size:12px">ResBlock ×2</text>
    <text x="335" y="94" style="font-size:11px">tanh</text>
    <text x="427" y="76" style="font-size:12px">Linear</text>
    <text x="427" y="94" style="font-size:11px">→ 1</text>
  </g>
  <text x="480" y="85" fill="currentColor" stroke="none" style="font-size:13px" dominant-baseline="central">rᵢ</text>
</svg>

</div>

<v-drag-arrow v-click="[7, 10]" pos="440,260,-83,167" one-way op70 width="1" />
<v-drag-arrow v-click="[7, 10]" pos="430,230,-70,-42" one-way op70 width="1" />
<v-drag-arrow v-click="[7, 10]" pos="427,250,-68,57" one-way op70 width="1" />

<div v-click="[8, 9]" class="absolute left-120 top-77 w-[48%] flex flex-col items-stretch gap-1">

  <div class="text-[0.8em] font-bold text-center">Training Loss</div>

  <div class="text-[0.6em] opacity-70 mt-1">Phase loss: beat-aligned phase for consistent morphology</div>
  <div class="left-math text-[0.7em] -mt-3">

$$
\mathcal{L}_{\text{phase}} = \mathbb{E}\!\left[\operatorname{atan2}\!\big(\sin(\theta-\theta_{\text{gt}}),\cos(\theta-\theta_{\text{gt}})\big)^2\right]
$$

  </div>

  <div class="text-[0.6em] opacity-70 -mt-2">POS loss: soft prior from POS-estimated phase, stable periodicity against drift</div>
  <div class="left-math text-[0.7em] -mt-3">

$$
\mathcal{L}_{\text{pos}} = \mathbb{E}\!\left[\operatorname{atan2}\!\big(\sin(\theta-\theta_{\text{pos}}),\cos(\theta-\theta_{\text{pos}})\big)^2\right]
$$

  </div>

  <div class="left-math text-[0.7em] -mt-4">

$$
\mathcal{L}_{\text{reg}} = \lambda_{A}\mathcal{L}_{A} + \lambda_{\sigma}\mathcal{L}_{\sigma} + \lambda_{\mu}\mathcal{L}_{\mu}
$$

$$
\mathcal{L} = \mathcal{L}_{\text{base}}
+ \lambda_{\text{pha}}\mathcal{L}_{\text{phase}}
+ \lambda_{\text{pos}}\mathcal{L}_{\text{pos}}
+ \lambda_{\text{m}}\mathcal{L}_{\text{mse}}
+ \lambda_{\text{p}}\mathcal{L}_{\text{pearson}}
+ \lambda_{\text{reg}}\mathcal{L}_{\text{reg}}
$$

  </div>
</div>

<div
  v-motion
  :initial="{ opacity: 0, y: 173, scale: 0.7 }"
  :click-8="{ opacity: 0, y: 174, x:40, scale: 0.82 }"
  :click-9="{ opacity: 1, y: 0, scale: 0.9, transition: { duration: 800, ease: 'easeInOut' } }"
  :click-10="{ opacity: 0, y: 0, scale: 0.9 }"
  class="left-math absolute left-108 top-[313px] w-[60%] origin-left text-[0.85em] text-white"
>

$$
\mathcal{L} = \mathcal{L}_{\text{base}}
+ \lambda_{\text{pha}}\mathcal{L}_{\text{phase}}
+ \lambda_{\text{pos}}\mathcal{L}_{\text{pos}}
+ \lambda_{\text{m}}\mathcal{L}_{\text{mse}}
+ \lambda_{\text{p}}\mathcal{L}_{\text{pearson}}
+ \lambda_{\text{reg}}\mathcal{L}_{\text{reg}}
$$

</div>

<v-drag-arrow pos="209,430,-35,0" one-way width="1" :style="{ opacity: $clicks === 9 ? 1 : 0, transition: 'opacity 0.3s' }"/>
<v-drag-arrow pos="209,193,-35,0" one-way width="1" :style="{ opacity: $clicks === 9 ? 1 : 0, transition: 'opacity 0.3s' }"/>
<v-drag-arrow pos="209,313,-35,0" one-way width="1" :style="{ opacity: $clicks === 9 ? 1 : 0, transition: 'opacity 0.3s' }"/>

<v-drag-arrow pos="174,430,35,0" one-way op70 width="1" v-click="10"/>
<v-drag-arrow pos="174,193,35,0" one-way op70 width="1" v-click="10"/>
<v-drag-arrow pos="174,313,35,0" one-way op70 width="1" v-click="10"/>

<v-drag-arrow pos="360,430,35,0" one-way op70 width="1" v-click="10"/>
<v-drag-arrow pos="360,193,35,0" one-way op70 width="1" v-click="10"/>
<v-drag-arrow pos="360,313,35,0" one-way op70 width="1" v-click="10"/>

<div v-click="10" class="absolute left-102 top-20 right-14 mt-6">
  <div class="flex items-center gap-12 mt-15">
    <img src="/p18_ours.png" class="w-100" />
  </div>
  <div class="flex items-center gap-12 mt-14">
    <img src="/PURE_ours.png" class="w-100" />
  </div>
  <div class="flex items-center gap-12 mt-14">
    <img src="/ubfc_ours.png" class="w-100" />
  </div>
</div>

<div class="absolute left-25 bottom-6 text-xs opacity-70 flex flex-col gap-1" v-click="9">
  <div class="flex items-center gap-2">
    Ours
  </div>
</div>

<div v-click="10" class="absolute right-116 bottom-6 text-xs opacity-70 flex flex-col items-start gap-1">
  <div class="flex items-center gap-2">
    <span class="inline-block w-3 h-0.5" style="background:#f59e0b"></span>
    Ground Truth
  </div>
  <div class="flex items-center gap-2">
    <span class="inline-block w-3 h-0.5" style="background:#3b82f6"></span>
    Ours
  </div>
</div>

<!--
To answer it, we propose Heartian, a physiology-aware modulation framework that embeds prescribed rPPG signals into a relightable Gaussian head avatar.

[click] Our pipeline is built on HRAvatar as our baseline, following a two-stage strategy.

[click] Heartian selects the facial skin-region Gaussians of the baseline avatars utilizing the parametric face model as the first step, locating the primitive for the next-step embedding

[click] For each Skin-region Gaussian, a spatially varied transient offset is applied to the green
channel albedo c on a per-frame basis, while all other attributes remain unchanged. 

(The A here is a learnable scaling factor.)

[click] The modulation factor m includes a characteristic fundamental waveform and a spatially varied learned residual.

[click] A typical PPG waveform within each cardiac cycle exhibits two peaks: a systolic and a diastolic wave. Their structure can be embedded in phase space by mapping the temporal signal to a unit circle, as shown in the right figure. 

Therefore, the PPG waveform morphology can be modeled as a sum of two Gaussian functions in phase space. 

(Phase is modelled as the initial phase 𝜙 accumulated with per-frame increments projected onto the unit circle.)

(d here denotes the shortest angular distance on the unit circle between the specific phase and center.) 

[click] Since the natural heart rate signals are always not perfectly periodic, right? We design a lightweight MLP to learn the spacially varied residual term, conditioned on three features. 

Including the temporal phase embedding for intra-cycle periodicity, followed by the beat index embedding for inter-cycle variation, with a positional embedding for the specific facial position that the Gaussian is at. 

(The MLP structure is shown in this diagram.)

[click] The modulation is ultimately applied to the selected skin-region Gaussian

[click] supervised by phase-related losses, regularization, and the based photometric losses.

(including the face model and Gaussian parameters)

[click] In the end, the modulation does not affect the perceptual appearance of our reconstructed avatars

[click] while they do, in fact, carry the embedded rPPG signals.
-->

---
layout: center
class: text-center
transition: fade-out
---

# 💓 <span class="text-blue"> Evaluation</span>

<div class="text-[0.8em] max-w-lg text-left">

- Evaluate the fidelity and recoverability of embedded rPPG signals in rendered videos using <a href="https://github.com/ubicomplab/rPPG-Toolbox" target="_blank">rPPG-Toolbox</a>

<v-clicks>

- Employ traditional unsupervised methods and three cutting-edge pre-trained supervised neural networks
- Across three widely recognised real-world datasets

</v-clicks>

</div>

<!--
We evaluate the fidelity and recoverability of per-subject embedded rPPG signals in rendered videos utilizing the rPPG-Toolbox

[click] employing traditional unsupervised methods and pre-trained neural networks

[click] across three public real-world rPPG datasets
-->

<div class="absolute bottom-5 left-10 right-16 text-[10px] opacity-70 text-left">
  <a href="https://proceedings.neurips.cc/paper_files/paper/2023/hash/d7d0d548a6317407e02230f15ce75817-Abstract-Datasets_and_Benchmarks.html" target="_blank">
    "rPPG-Toolbox: Deep Remote PPG Toolbox,"
  </a>
  <i>Advances in Neural Information Processing Systems (NeurIPS)</i>,
  2023.
</div>

---
transition: fade-out
---

# 💓 <span class="text-blue"> Quantitative</span> Results (MAE <span class="text-blue">↓</span>, MAPE<span class="text-blue">↓</span>)

<p class="text-[0.8em]" v-if="$clicks < 5"> Benchmark Evaluation Results. Performance of benchmark methods on our rendered 💓Heartian videos, evaluated across datasets. Green highlights indicate metrics where embedded signals remain recoverable on par with the original benchmark results on the same selected subsets.</p>

<div class="mt-3 w-full overflow-x-auto">

  <table v-if="$clicks < 4" :class="{ 'methods-active': $clicks >= 1, 'headers-active': $clicks >= 2, 'values-active': $clicks >= 3 }" class="benchmark-progress w-full table-fixed text-center border-collapse text-[10px] leading-tight">
    <thead>
      <tr class="bg-gray-700 text-white">
        <th rowspan="2" class="!text-center border border-gray-500 p-1.5 highlight-method">Method</th>
        <th rowspan="2" class="!text-center border border-gray-500 p-1.5">Train Set</th>
        <th colspan="2" class="!text-center border border-gray-500 p-1.5"><a href="https://sites.google.com/view/ybenezeth/ubfcrppg?pli=1&authuser=0" target="_blank">UBFC-rPPG</a></th>
        <th colspan="2" class="!text-center border border-gray-500 p-1.5"><a href="https://www.tu-ilmenau.de/universitaet/fakultaeten/fakultaet-informatik-und-automatisierung/profil/institute-und-fachgebiete/institut-fuer-technische-informatik-und-ingenieurinformatik/fachgebiet-neuroinformatik-und-kognitive-robotik/data-sets-code/pulse-rate-detection-dataset-pure" target="_blank">PURE</a></th>
        <th colspan="2" class="!text-center border border-gray-500 p-1.5"><a href="https://github.com/McJackTang/MMPD_rPPG_dataset" target="_blank">MMPD</a></th>
      </tr>
      <tr class="bg-gray-200 text-gray-900">
        <th class="!text-center border border-gray-500 p-1">MAE ↓</th>
        <th class="!text-center border border-gray-500 p-1">MAPE ↓</th>
        <th class="!text-center border border-gray-500 p-1">MAE ↓</th>
        <th class="!text-center border border-gray-500 p-1">MAPE ↓</th>
        <th class="!text-center border border-gray-500 p-1">MAE ↓</th>
        <th class="!text-center border border-gray-500 p-1">MAPE ↓</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td class="border border-gray-300 p-1.5 font-semibold highlight-method"><a href="https://ieeexplore.ieee.org/document/7565547" target="_blank">POS</a></td>
        <td class="highlight-train border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1 text-green-500">1.23 ± 0.77</td>
        <td class="border border-gray-300 p-1 text-green-500">1.01 ± 0.62</td>
        <td class="border border-gray-300 p-1">14.23 ± 6.78</td>
        <td class="border border-gray-300 p-1">29.34 ± 13.98</td>
        <td class="border border-gray-300 p-1 text-green-500">1.53 ± 0.63</td>
        <td class="border border-gray-300 p-1 text-green-500">2.66 ± 1.20</td>
      </tr>
      <tr>
        <td class="border border-gray-300 p-1 font-semibold highlight-method" rowspan="2"><a href="https://papers.nips.cc/paper/2020/file/e1228be46de6a0234ac22ded31417bc7-Paper.pdf" target="_blank">TS-CAN</a></td>
        <td class="highlight-train border border-gray-300 p-1">UBFC-rPPG</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1">10.01 ± 4.52</td>
        <td class="border border-gray-300 p-1">17.89 ± 8.68</td>
        <td class="border border-gray-300 p-1 text-green-500">2.59 ± 0.52</td>
        <td class="border border-gray-300 p-1 text-green-500">3.89 ± 0.94</td>
      </tr>
      <tr>
        <td class="highlight-train border border-gray-300 p-1">PURE</td>
        <td class="border border-gray-300 p-1">9.22 ± 7.47</td>
        <td class="border border-gray-300 p-1">7.41 ± 5.56</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1 text-green-500">2.51 ± 0.57</td>
        <td class="border border-gray-300 p-1 text-green-500">3.87 ± 1.03</td>
      </tr>
      <tr>
        <td class="border border-gray-300 p-1 font-semibold highlight-method"><a href="https://arxiv.org/pdf/2303.12059" target="_blank">TS-CAN (MA)</a></td>
        <td class="highlight-train border border-gray-300 p-1">UBFC-rPPG</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1 text-green-500">4.74 ± 4.22</td>
        <td class="border border-gray-300 p-1 text-green-500">5.23 ± 4.67</td>
        <td class="border border-gray-300 p-1 text-green-500">0.97 ± 0.27</td>
        <td class="border border-gray-300 p-1 text-green-500">1.21 ± 0.31</td>
      </tr>
      <tr>
        <td class="border border-gray-300 p-1 font-semibold highlight-method" rowspan="2"><a href="https://openaccess.thecvf.com/content/CVPR2022/papers/Yu_PhysFormer_Facial_Video-Based_Physiological_Measurement_With_Temporal_Difference_Transformer_CVPR_2022_paper.pdf" target="_blank">PhysFormer</a></td>
        <td class="highlight-train border border-gray-300 p-1">UBFC-rPPG</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1">17.40 ± 6.55</td>
        <td class="border border-gray-300 p-1">34.29 ± 13.78</td>
        <td class="border border-gray-300 p-1 text-green-500">8.69 ± 1.31</td>
        <td class="border border-gray-300 p-1 text-green-500">13.96 ± 2.21</td>
      </tr>
      <tr>
        <td class="highlight-train border border-gray-300 p-1">PURE</td>
        <td class="border border-gray-300 p-1">5.53 ± 4.44</td>
        <td class="border border-gray-300 p-1">4.37 ± 3.32</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1 text-green-500">3.12 ± 1.08</td>
        <td class="border border-gray-300 p-1 text-green-500">5.27 ± 1.95</td>
      </tr>
      <tr>
        <td class="border border-gray-300 p-1 font-semibold highlight-method" rowspan="2"><a href="https://proceedings.neurips.cc/paper_files/paper/2024/hash/af1c61e4dd59596f033d826419870602-Abstract-Conference.html" target="_blank">FactorizePhys</a></td>
        <td class="highlight-train border border-gray-300 p-1">UBFC-rPPG</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1">14.58 ± 6.82</td>
        <td class="border border-gray-300 p-1">29.95 ± 14.13</td>
        <td class="border border-gray-300 p-1 text-green-500">2.88 ± 0.98</td>
        <td class="border border-gray-300 p-1 text-green-500">4.83 ± 1.70</td>
      </tr>
      <tr>
        <td class="highlight-train border border-gray-300 p-1">PURE</td>
        <td class="border border-gray-300 p-1">6.41 ± 5.09</td>
        <td class="border border-gray-300 p-1">5.05 ± 3.80</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1 text-green-500">1.38 ± 0.50</td>
        <td class="border border-gray-300 p-1 text-green-500">2.40 ± 0.99</td>
      </tr>
    </tbody>
  </table>

  <table v-if="$clicks < 5 && $clicks >= 4 " class="w-full table-fixed text-center border-collapse text-[10px] leading-tight">
    <thead>
      <tr class="bg-gray-700 text-white">
        <th rowspan="2" class="!text-center border border-gray-500 p-1.5">Method</th>
        <th rowspan="2" class="!text-center border border-gray-500 p-1.5">Train Set</th>
        <th colspan="2" class="!text-center border border-gray-500 p-1.5"><a href="https://sites.google.com/view/ybenezeth/ubfcrppg?pli=1&authuser=0" target="_blank">UBFC-rPPG</a></th>
        <th colspan="2" class="!text-center border border-gray-500 p-1.5"><a href="https://www.tu-ilmenau.de/universitaet/fakultaeten/fakultaet-informatik-und-automatisierung/profil/institute-und-fachgebiete/institut-fuer-technische-informatik-und-ingenieurinformatik/fachgebiet-neuroinformatik-und-kognitive-robotik/data-sets-code/pulse-rate-detection-dataset-pure" target="_blank">PURE</a></th>
        <th colspan="2" class="!text-center border border-gray-500 p-1.5"><a href="https://github.com/McJackTang/MMPD_rPPG_dataset" target="_blank">MMPD</a></th>
      </tr>
      <tr class="bg-gray-200 text-gray-900">
        <th class="!text-center border border-gray-500 p-1">MAE ↓</th>
        <th class="!text-center border border-gray-500 p-1">MAPE ↓</th>
        <th class="!text-center border border-gray-500 p-1">MAE ↓</th>
        <th class="!text-center border border-gray-500 p-1">MAPE ↓</th>
        <th class="!text-center border border-gray-500 p-1">MAE ↓</th>
        <th class="!text-center border border-gray-500 p-1">MAPE ↓</th>
      </tr>
    </thead>
    <tbody>
      <tr class="bg-gray-300 text-gray-900">
        <td colspan="8" class="border-x border-gray-500 border-y-0 p-1.5 text-left font-semibold">
          Ours vs Baseline (%)
        </td>
      </tr>
      <tr>
        <td class="border border-gray-300 p-1 font-semibold">POS</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1 text-green-500">−21.97</td>
        <td class="border border-gray-300 p-1 text-green-500">−18.88</td>
        <td class="border border-gray-300 p-1 text-green-500">−10.72</td>
        <td class="border border-gray-300 p-1 text-green-500">−13.78</td>
        <td class="border border-gray-300 p-1 text-green-500">−12.72</td>
        <td class="border border-gray-300 p-1 text-green-500">−17.78</td>
      </tr>
      <tr>
        <td class="border border-gray-300 p-1 font-semibold">TS-CAN</td>
        <td class="border border-gray-300 p-1">PURE</td>
        <td class="border border-gray-300 p-1 text-green-500">−26.98</td>
        <td class="border border-gray-300 p-1 text-green-500">−24.72</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1 text-green-500">−12.87</td>
        <td class="border border-gray-300 p-1 text-green-500">−16.28</td>
      </tr>
      <tr>
        <td class="border border-gray-300 p-1 font-semibold">TS-CAN (MA)</td>
        <td class="border border-gray-300 p-1">UBFC-rPPG</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1">–</td>
        <td class="border border-gray-300 p-1 text-green-500">−15.73</td>
        <td class="border border-gray-300 p-1 text-green-500">−25.01</td>
        <td class="border border-gray-300 p-1 text-green-500">−13.31</td>
        <td class="border border-gray-300 p-1 text-green-500">−17.28</td>
      </tr>
    </tbody>
  </table>
</div>

<p class="text-[0.8em] opacity-70" v-if="$clicks >= 5" v-click="5"> Attribute-level Evaluation. rPPG signal metrics extracted from the Gaussian albedo of baseline and 💓Heartian.</p>

<table v-click="5" class="w-full table-fixed text-center border-collapse text-[0.6em] leading-tight">
  <thead>
    <tr class="bg-gray-700 text-white">
      <th rowspan="2" class="!text-center border border-gray-500 p-1.5">Dataset</th>
      <th colspan="3" class="!text-center border border-gray-500 p-1.5">Baseline</th>
      <th colspan="3" class="!text-center border border-gray-500 p-1.5">Ours</th>
    </tr>
    <tr class="bg-gray-200 text-gray-900">
      <th class="!text-center border border-gray-500 p-1">MAE ↓</th>
      <th class="!text-center border border-gray-500 p-1">MAPE ↓</th>
      <th class="!text-center border border-gray-500 p-1">SNR ↑</th>
      <th class="!text-center border border-gray-500 p-1">MAE ↓</th>
      <th class="!text-center border border-gray-500 p-1">MAPE ↓</th>
      <th class="!text-center border border-gray-500 p-1">SNR ↑</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="border border-gray-300 p-1.5 text-left font-semibold">UBFC-rPPG</td>
      <td class="border border-gray-300 p-1.5">59.00</td>
      <td class="border border-gray-300 p-1.5">53.81</td>
      <td class="border border-gray-300 p-1.5">−21.52</td>
      <td class="border border-gray-300 p-1.5 text-green-500">0.00</td>
      <td class="border border-gray-300 p-1.5 text-green-500">0.00</td>
      <td class="border border-gray-300 p-1.5 text-green-500">1.45</td>
    </tr>
    <tr>
      <td class="border border-gray-300 p-1.5 text-left font-semibold">PURE</td>
      <td class="border border-gray-300 p-1.5">21.53</td>
      <td class="border border-gray-300 p-1.5">25.37</td>
      <td class="border border-gray-300 p-1.5">−7.13</td>
      <td class="border border-gray-300 p-1.5 text-green-500">0.17</td>
      <td class="border border-gray-300 p-1.5 text-green-500">0.27</td>
      <td class="border border-gray-300 p-1.5 text-green-500">3.47</td>
    </tr>
    <tr>
      <td class="border border-gray-300 p-1.5 text-left font-semibold">MMPD</td>
      <td class="border border-gray-300 p-1.5">39.11</td>
      <td class="border border-gray-300 p-1.5">34.81</td>
      <td class="border border-gray-300 p-1.5">−11.47</td>
      <td class="border border-gray-300 p-1.5 text-green-500">0.33</td>
      <td class="border border-gray-300 p-1.5 text-green-500">0.42</td>
      <td class="border border-gray-300 p-1.5 text-green-500">4.04</td>
    </tr>
  </tbody>
</table>

<div v-click="6" class="text-[0.9em] mt-20">Maintain reconstruction quality comparable to the baseline, with negligible average PSNR degradation of <span class="text-green">0.005</span> dB and an average of <span class="text-green">35.38</span> PSNR, <span class="text-green">0.9697</span> SSIM, and <span class="text-green">0.0374</span> LPIP. </div>

<style>
.benchmark-progress th,
.benchmark-progress td {
  opacity: 0.6;
  transition: opacity 250ms ease;
}

.benchmark-progress.methods-active .highlight-method,
.benchmark-progress.headers-active thead th,
.benchmark-progress.headers-active .highlight-train,
.benchmark-progress.values-active tbody td {
  opacity: 1;
}
</style>


<!--
This table shows benchmark results of [click] five different methods [click] on three datasets using off-the-shelf rPPG estimators.

[click] Green highlights show metrics where embedded signals remain recoverable, comparable to the original benchmark results on the same selected subsets.

The varied performance across datasets reveals domain gaps in real-world scenarios and model behaviour.

[click] Compared with the rPPG signals estimated from baseline rendered videos, Heartian clearly restores physiological signal recovery, while the baseline results are extracted as a flat line with no meaningful signal.

[click] The same conclusion can be found in the attribute-level evaluation from the modulated albedo.

[click] In terms of visual quality, Heartian maintains reconstruction quality comparable to the baseline, with negligible average PSNR degradation of 0.005 dB.
-->

---
transition: fade-out
---

# 💓 <span class="text-blue"> Qualitative</span> Results 
<SyncVideos :names="['pure_1','pure_2','pure_3','pure_5','pure_7','pure_8','pure_9', 'pure_10','mmpd_1','mmpd_2','mmpd_3','mmpd_4','mmpd_5','mmpd_6','mmpd_7','mmpd_8','ubfc_1','ubfc_2','ubfc_3','ubfc_4','ubfc_5','ubfc_6','ubfc_7','ubfc_8']" :start="0" :end="5" class="mt-4" />

<SyncVideos v-click="1" :names="['ubfc_3_4','ubfc_3_1','ubfc_3_2','ubfc_3_3','ubfc_6_4','ubfc_6_1','ubfc_6_2','ubfc_6_3']" :start="0" :end="5" class="mt-3" />

<div class="text-[0.8em] absolute left-130 top-6"><span class="text-green">Skin Tone Robust</span> across Fitzpatrick Scale Type  III to VI <span class="text-green">√</span></div>

<div v-click="1" class="text-[0.8em] absolute left-130 top-11"><span class="text-green">Relighting Robust</span> across Synthetic Uniform Lights and a <br>Real-World Captured Hospital Environment Maps <span class="text-green">√</span></div>

<!--
In terms of qualitative results, our methods is skin tone robust across Fitzpatrick Scale Type 3-6.

[click] and relighting robust across synthetic uniform lights and a real-world captured hospital environment maps.

[remarks]
First line: PURE
Second line: MMPD
Third line: UBFC-rPPG
-->

---
transition: fade-out
---

<span v-click="1" class="absolute"></span>
<span v-click="2" class="absolute"></span>

<h1
  class="absolute w-max whitespace-nowrap"
  :style="{
    left: $clicks < 1 ? '50%' : '40px',
    top: $clicks < 1 ? '45%' : '26px',
    transform: $clicks < 1 ? 'translate(-50%, -50%)' : 'translate(0, 0)',
    transition: 'all 0.8s ease-in-out',
  }"
>
  💓 <span style="color: #2B90B6;">Summary</span><span :style="{ opacity: $clicks >= 2 ? 0 : 1, transition: 'opacity 0.8s' }">&nbsp;&&nbsp;</span>
  <span
    class="inline-block"
    :style="{
      color: '#2B90B6',
      transform: $clicks >= 2 ? 'translate(-170px, 250px)' : 'translate(0, 0)',
      transition: 'transform 0.8s ease-in-out',
    }"
  >Future Work</span>
</h1>

<p
  class="absolute w-max whitespace-nowrap text-[0.8em]"
  :style="{
    left: $clicks < 1 ? '50%' : '40px',
    top: $clicks < 1 ? '54%' : '72px',
    transform: $clicks < 1 ? 'translate(-50%, -50%)' : 'translate(0, 0)',
    transition: 'all 0.8s ease-in-out',
  }"
>
  A physiology-aware modulation framework that embeds prescribed rPPG signals into relightable Gaussian head avatars.
</p>

<ul v-click="1" class="text-[0.9em] list-disc mt-18">
  <li>Per-frame spatial modulation acts on the albedo of facial skin-region Gaussians</li>
  <li>Heart rate recovered from embedded signals: MAE <span class="text-green">0.29</span> bpm, MAPE <span class="text-green">0.38</span> %</li>
  <li>Reconstruction quality changes are negligible: <span class="text-green">0.005</span> dB PSNR, <span class="text-green">0.00003</span> SSIM, <span class="text-green">0.0003</span> LPIPS</li>
  <li>Embedded signals <span class="text-green">remain recoverable</span> in reconstructed avatar videos</li>
  <li><span class="text-green">Robustness</span> across skin tones and relighting conditions</li>
</ul>

<ul v-click="2" class="text-[0.9em] list-disc mt-18">
  <li>Enable <span class="text-green">cross-subject control</span> with prescribed waveform in Gaussian representations</li>
  <li>Enable controlled physiological training augmentation</li>
  <li v-click="3">Toward real-time physiology-aware avatars built on existing avatar infrastructure for future telemedicine applications</li>
</ul>

<span v-click="2" class="slow-heart absolute left-10 bottom-60 text-2xl">💓</span>

<style>
ul.slidev-vclick-target:nth-of-type(1) {
  transition: opacity 2s ease-in !important;
}
.slow-heart.slidev-vclick-target {
  transition: opacity 2s ease-in !important;
}
</style>

<!--
In summary

[click] Our main contribution is to make the Gaussian avatars heart-rate-plausible without losing perceptual quality, while recoverable in rendered videos by cutting-edge rPPG technique.

[click] Regarding future work, I think our work provides a basis for heart-rate-aware human reconstruction, enabling cross-subject control with prescribed waveforms in Gaussian representation, as well as controlled physiological data augmentation.

[click] It could also be integrated into existing Gaussian-based avatar infrastructure to support real-time rPPG monitoring in future telemedicine applications.
-->

---
layout: default
class: text-left
---

<div class="absolute left-10 top-40 flex flex-col items-start">

  <h1 class="text-4xl font-serif font-bold mb-8">
    Thank You for Listening!
  </h1>

  <!-- Authors -->
  <div class="flex justify-start gap-2 mt-5">
    <div class="text-center w-28 -mt-3">
      <img src="/Merry.jpg" class="w-23 h-23 rounded-full object-cover mx-auto" />
      <div class="text-xs font-bold mt-2 whitespace-nowrap">
        Xiaoyue Fan<sup>1</sup>
      </div>
    </div>
    <div class="text-center w-28">
      <img src="/jose.jpg" class="w-18 h-18 rounded-full object-cover mx-auto" />
      <div class="text-xs mt-2 whitespace-nowrap">
        Jose Echevarria<sup>2</sup>
      </div>
    </div>
    <div class="text-center w-28">
      <img src="/Akshay.jpg" class="w-18 h-18 rounded-full object-cover mx-auto" />
      <div class="text-xs mt-2 whitespace-nowrap">
        Akshay Paruchuri<sup>3</sup>
      </div>
    </div>
    <div class="text-center w-28">
      <img src="/Kaan.jpg" class="w-18 h-18 rounded-full object-cover mx-auto" />
      <div class="text-xs mt-2 whitespace-nowrap">
        Kaan Akşit<sup>1</sup>
      </div>
    </div>
  </div>

  <!-- Affiliations -->
  <div class="text-xs mt-6 opacity-80">
    <sup>1</sup>University College London &nbsp;
    <sup>2</sup>Adobe Research &nbsp;
    <sup>3</sup>Stanford University
  </div>

  <!-- Logos -->
  <div class="flex items-center justify-start mt-5">
    <img src="/logo_all.png" class="h-8" />
  </div>

</div>

<!-- Project Page -->
<div class="absolute right-20 bottom-85 flex flex-col items-center p-2 rounded">
  <span class="text-xs opacity-80" style="letter-spacing: 0.1em;">
    Project Page
  </span>
  <img src="/site.png" class="w-40 mt-1" />
</div>

<!-- SIGGRAPH Logo -->
<div class="absolute left-10 top-3 flex flex-col items-center mt-5 bg-white p-1">
  <img src="/Siggraph_logo.png" class="w-30 mt-1" />
</div>

<!-- Pointing Hand -->
<div class="i-twemoji:backhand-index-pointing-right-light-skin-tone text-5xl absolute left-160 bottom-85 rotate-[-20deg] point-pulse"></div>

<script setup>
import { ref } from 'vue'
import { onSlideEnter, onSlideLeave } from '@slidev/client'

const base = import.meta.env.BASE_URL

const people = [
  { video: base + '4.mp4', image: base + 'PURE_ours.png' },
  { video: base + '1.mp4', image: base + 'p18_ours.png' },
  { video: base + '3.mp4', image: base + 'ubfc_ours.png' },
]

const personIndex = ref(0)
let timer

function stopSwitching() {
  clearInterval(timer)
}

onSlideEnter(() => {
  stopSwitching()
  personIndex.value = 0

  timer = setInterval(() => {
    personIndex.value = (personIndex.value + 1) % people.length
  }, 2000)
})

onSlideLeave(stopSwitching)
</script>

<!-- Example -->
<div class="absolute right-22 bottom-45 w-40 h-28">
  <Transition name="person-fade">
    <div
      :key="personIndex"
      class="absolute inset-0 flex items-center justify-center"
    >
      <LoopVideo
        :src="people[personIndex].video"
        class="h-28 max-w-full object-contain"
      />
    </div>
  </Transition>
</div>

<v-drag-arrow pos="814,383,0,30" one-way op70 width="1" />

<div class="absolute bottom-18 right-2">
  <div class="person-stack">
    <Transition name="person-fade">
      <img
        :key="personIndex"
        :src="people[personIndex].image"
        class="person-layer w-80"
      />
    </Transition>
  </div>
</div>

<style>
.person-stack {
  display: grid;
}

.person-layer {
  grid-area: 1 / 1;
}

.person-fade-enter-active,
.person-fade-leave-active {
  transition: opacity 500ms ease-in-out;
}

.person-fade-enter-from,
.person-fade-leave-to {
  opacity: 0;
}
</style>


<!--
That brings us to the end of my sharing. Before we move on to the Q&A, I would like to thank all my co-authors again for their input to this work. 

The QR code for our project webpage is on the right over here. Feel free to scan it for more details if you’re interested. Thank you for your attention!
-->
