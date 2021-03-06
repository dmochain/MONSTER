# MONSTER

<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8" />
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<meta http-equiv="x-ua-compatible" content="ie=edge,chrome=1" />

<meta name="description" content="" />
<meta name="keywords" content="" />

<meta http-equiv="Content-Language" content="EN" />
<meta name="Language" content="EN" />
<meta name="viewport" content="width=960, initial-scale=0.33, maximum-sclae=1" />
<link rel="stylesheet" href="default.css" />
</head>

<body>

<hr />

<h2>About <span class="Monsterfont">Monster</span></h2>

<p><span class="Monsterfont">Monster</span>  is a cryptographic signature
algorithm which has been designed
by: Pierre-Alain Fouque, Jeffrey Hoffstein, Paul Kirchner, Vadim
Lyubashevsky, Thomas Pornin, Thomas Prest, Thomas Ricosset, Gregor
Seiler, William Whyte.</p>

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

<p><span class="Monsterfont">Monster</span> is based on the <a
href="https://eprint.iacr.org/2007/432">theoretical framework of Gentry,
Peikert and Vaikuntanathan</a> for lattice-based signature schemes. We
instantiate that framework over NTRU lattices, with a trapdoor sampler
called "fast Fourier sampling". The underlying hard problem is the <a
href="https://en.wikipedia.org/wiki/Short_integer_solution_problem">short
integer solution</a> problem (SIS) over NTRU lattices, for which no
efficient solving algorithm is currently known in the general case, even
with the help of quantum computers.</p>

<h2>Algorithm Highlights</h2>

<p><span class="Monsterfont">Monster</span> offers the following features:</p>
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
of <span class="Monsterfont">Monster</span> uses less than 30 kilobytes
of RAM, a hundredfold improvement over previous designs such as
NTRUSign. <span class="Monsterfont">Monster</span> is compatible with
small, memory-constrained embedded devices.</li>
</ul>

<h2>Performance</h2>

<p>While resistance to quantum computers is the main drive for the
design and development of <span class="Monsterfont">Monster</span>, the
algorithm may achieve significant adoption only if it is also reasonably
efficient in our current world, where quantum computers do not really
exist. Using the reference implementation on a common desktop computer
(Intel® Core® i5-8259U at 2.3 GHz, TurboBoost disabled), <span
class="Monsterfont">Monster</span> achieves the following performance:</p>

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
  <td><span class="Monsterfont">Monster</span>-512</td>
  <td class="values">8.64</td>
  <td class="values">14336</td>
  <td class="values">5948.1</td>
  <td class="values">27933.0</td>
  <td class="values">897</td>
  <td class="values">666</td>
</tr>
<tr>
  <td><span class="Monsterfont">Monster</span>-1024</td>
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
class="Monsterfont">Monster</span>-512 is roughly equivalent, in classical
security terms, to RSA-2048, whose signatures and public keys use 256
bytes each. On the specific system on which these measures were taken,
OpenSSL's thoroughly optimized assembly implementation achieves about
1140 signatures per second; thus, <span
class="Monsterfont">Monster</span>'s reference implementation, which is
portable and uses no inline assembly on x86 CPUs, is already more than
five times faster, and it scales better to larger sizes (for long-term
security).</p>


<h2>Resources</h2>

<ul>
<li><span class="Monsterfont">Monster</span> submission package <a href="https://github.com/dmochain/MONSTER/blob/main/Monster-round3.zip">[zip]</a> (specification, source code, scripts and test vectors)</li>
<li><span class="Monsterfont">Monster</span> reference implementation:</li>
  <ul>
  <li>Source code archive <a href="https://github.com/dmochain/MONSTER/blob/main/Monster-impl-round3.zip">[zip]</a></li>
  </ul>
<li>For reference, submission packages for previous rounds: Round 1 <a href="https://github.com/dmochain/MONSTER/blob/main/Monster-round1.zip">[zip]</a> and Round 2 <a href="https://github.com/dmochain/MONSTER/blob/main/Monster-round2.zip">[zip]</a></li>
</ul>

</body>
</html>

