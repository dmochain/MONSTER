# FALCON

<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8" />
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<meta http-equiv="x-ua-compatible" content="ie=edge,chrome=1" />

<title>Falcon</title>
<meta name="description" content="" />
<meta name="keywords" content="" />

<meta http-equiv="Content-Language" content="EN" />
<meta name="Language" content="EN" />
<meta name="viewport" content="width=960, initial-scale=0.33, maximum-sclae=1" />
<link rel="stylesheet" href="default.css" />
</head>

<body>


<hr />

<h2>About <span class="falconfont">Falcon</span></h2>

<p><span class="falconfont">Falcon</span> is a cryptographic signature
algorithm submitted to NIST <a
href="https://csrc.nist.gov/projects/post-quantum-cryptography">Post-Quantum
Cryptography Project</a> on November 30th, 2017. It has been designed
by: Pierre-Alain Fouque, Jeffrey Hoffstein, Paul Kirchner, Vadim
Lyubashevsky, Thomas Pornin, Thomas Prest, Thomas Ricosset, Gregor
Seiler, William Whyte, Zhenfei Zhang.</p>

<p>The point of a post-quantum cryptographic algorithm is to keep on
ensuring its security characteristics even faced with <a
href="https://en.wikipedia.org/wiki/Quantum_computing">quantum
computers</a>. Quantum computers are deemed feasible, according to our
current understanding of the laws of physics, but some significant
technological issues remain to be solved in order to build a fully
operational unit. Such a quantum computer would very efficiently break
the usual asymmetric encryption and digitial signature algorithms based
on number theory (RSA, DSA, Diffie-Hellman, ElGamal, and their elliptic
curve variants).

<p><span class="falconfont">Falcon</span> is based on the <a
href="https://eprint.iacr.org/2007/432">theoretical framework of Gentry,
Peikert and Vaikuntanathan</a> for lattice-based signature schemes. We
instantiate that framework over NTRU lattices, with a trapdoor sampler
called "fast Fourier sampling". The underlying hard problem is the <a
href="https://en.wikipedia.org/wiki/Short_integer_solution_problem">short
integer solution</a> problem (SIS) over NTRU lattices, for which no
efficient solving algorithm is currently known in the general case, even
with the help of quantum computers.</p>

<h2>Algorithm Highlights</h2>

<p><span class="falconfont">Falcon</span> offers the following features:</p>
<ul>
<li><strong>Security:</strong> a true Gaussian sampler is used internally,
which guarantees negligible leakage of information on the secret key up to
a practically infinite number of signatures (more than 2<sup>64</sup>).
<li><strong>Compactness:</strong> thanks to the use of NTRU lattices,
signatures are substantially shorter than in any lattice-based signature
scheme with the same security guarantees, while the public keys are
around the same size.</li>
<li><strong>Speed:</strong> use of fast Fourier sampling allows for very
fast implementations, in the thousands of signatures per second on a
common computer; verification is five to ten times faster.</li>
<li><strong>Scalability:</strong> operations have cost <em>O(n</em> log
<em>n)</em> for degree <em>n</em>, allowing the use of very long-term
security parameters at moderate cost.
<li><strong>RAM Economy:</strong> the enhanced key generation algorithm
of <span class="falconfont">Falcon</span> uses less than 30 kilobytes
of RAM, a hundredfold improvement over previous designs such as
NTRUSign. <span class="falconfont">Falcon</span> is compatible with
small, memory-constrained embedded devices.</li>
</ul>

<h2>Performance</h2>

<p>While resistance to quantum computers is the main drive for the
design and development of <span class="falconfont">Falcon</span>, the
algorithm may achieve significant adoption only if it is also reasonably
efficient in our current world, where quantum computers do not really
exist. Using the reference implementation on a common desktop computer
(Intel® Core® i5-8259U at 2.3 GHz, TurboBoost disabled), <span
class="falconfont">Falcon</span> achieves the following performance:</p>

<table>
<tr class="titlerow">
  <th>variant</th>
  <th>keygen (ms)</th>
  <th>keygen (RAM)</th>
  <th>sign/s</th>
  <th>verify/s</th>
  <th>pub size</th>
  <th>sig size</th>
</tr>
<tr>
  <td><span class="falconfont">Falcon</span>-512</td>
  <td class="values">8.64</td>
  <td class="values">14336</td>
  <td class="values">5948.1</td>
  <td class="values">27933.0</td>
  <td class="values">897</td>
  <td class="values">666</td>
</tr>
<tr>
  <td><span class="falconfont">Falcon</span>-1024</td>
  <td class="values">27.45</td>
  <td class="values">28672</td>
  <td class="values">2913.0</td>
  <td class="values">13650.0</td>
  <td class="values">1793</td>
  <td class="values">1280</td>
</tr>
</table>

<p>Sizes (key generation RAM usage, public key size, signature size) are
expressed in bytes. Key generation time is given in milliseconds.
Private key size (not listed above) is about three times that of a
signature, and it could be theoretically compressed down to a small PRNG
seed (say, 32 bytes), if the signer accepts to run the key generation
algorithm every time the key must be loaded.</p>

<p>To give a point of comparison, <span
class="falconfont">Falcon</span>-512 is roughly equivalent, in classical
security terms, to RSA-2048, whose signatures and public keys use 256
bytes each. On the specific system on which these measures were taken,
OpenSSL's thoroughly optimized assembly implementation achieves about
1140 signatures per second; thus, <span
class="falconfont">Falcon</span>'s reference implementation, which is
portable and uses no inline assembly on x86 CPUs, is already more than
five times faster, and it scales better to larger sizes (for long-term
security).</p>

<h2>Resources</h2>

<ul>
<li><span class="falconfont">Falcon</span> submission package <a href="falcon-round3.zip">[zip]</a> (specification, source code, scripts and test vectors)</li>
<li><span class="falconfont">Falcon</span> specification <a href="falcon.pdf">[pdf]</a></li>
<li><span class="falconfont">Falcon</span> reference implementation:</li>
  <ul>
  <li>Source code archive <a href="Falcon-impl-round3.zip">[zip]</a></li>
  <li>Browse source code online <a href="impl/falcon.h.html">[html]</a></li>
  </ul>
<li>An implementation in Python <a href="https://github.com/tprest/falcon.py">[html]</a></li>
<li>For reference, submission packages for previous rounds: Round 1 <a href="falcon-round1.zip">[zip]</a> and Round 2 <a href="falcon-round2.zip">[zip]</a></li>
<li>Presentations at the NIST PQC Standardization Conferences: Round 1 <a href="https://csrc.nist.gov/CSRC/media/Presentations/Falcon/images-media/Falcon-April2018.pdf">[pdf]</a> and Round 2 <a href="https://csrc.nist.gov/CSRC/media/Presentations/falcon-round-2-presentation/images-media/falcon-prest.pdf">[pdf]</a></li>
</ul>


<h2>Related works</h2>

<ul>
<li>Thomas Pornin and Thomas Prest <br>
  <i>More Efficient Algorithms for the NTRU Key Generation using the Field Norm</i> <a href="https://eprint.iacr.org/2019/015.pdf">[pdf]</a>
<li> Xingye Lu, Man Ho Au and Zhenfei Zhang <br>
  <i> Raptor: A Practical Lattice-Based (Linkable) Ring Signature</i> <a href="https://eprint.iacr.org/2018/857.pdf">[pdf]</a>
<li> Thomas Pornin <br>
  <i> New Efficient, Constant-Time Implementations of Falcon</i> <a href="https://eprint.iacr.org/2019/893.pdf">[pdf]</a>
<li> Pierre-Alain Fouque, Paul Kirchner, Mehdi Tibouchi, Alexandre Wallet and Yang Yu <br>
  <i> Key Recovery from Gram-Schmidt Norm Leakage in Hash-and-Sign Signatures over NTRU Lattices</i> <a href="https://eprint.iacr.org/2019/1180.pdf">[pdf]</a>
<li> James Howe, Thomas Prest, Thomas Ricosset and Mélissa Rossi <br>
  <i> Isochronous Gaussian Sampling: From Inception to Implementation</i> <a href="https://eprint.iacr.org/2019/1411.pdf">[pdf]</a>
</ul>
</body>
</html>
