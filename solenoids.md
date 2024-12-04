# Solenoid Tutorial

Solenoid Intro text here 


#  Physics 
#  Forces 

- measure necessary force + stroke to drive mechanism 
- define and set "duty cycle"
- calculate electrical power input and necessary supply voltage 
- review solenoid specs/data to find appropriate solenoid for task 
- pick suitable coil gauge given voltage 
- implement a return mechninism (optional) 

## Physics of Solenoid 

Solenoid is... an electromagnetic device that receives electrical energy as input to pull/push a ferromagnetic iron plunger into a coil of wire to do work on some mechanism. 

How much mechanical energy is required for motion of mechanism? 

$$ \begin{equation}
W = Fd
\end{equation}
$$

$W$ = work 
$F$ = force 
$d$ = distance 


$d$ is the amount we want the plunger to move depending on the application.  

$F$ can be thought of as kilogram-force (symbol: kgf), a unit of force in the gravitational metric system. It is defined as the magnitude of force applied to one kilogram of mass under the condition of standard gravity (9.80665 m/s2). One kilogram-force is therefore equal to 9.80665 N. 


Let's say a mass weighing 1 lb (0.45 kg) can properly depress a mechanical button that we want to automate by turning it on and this distance to press the switch is 8 mm. We supply a voltage up to 12 V.  This would mean a $Fd$ of around (9.80664 * 0.45) N * 0.008 (m) = 0.35 J.  

>(NB: Newtons, N, have units of kg*meter/second^2 as you can see above)

We can relate the above equation to electrical force using: 

$$ \begin{equation}
W = Fd = \eta IVt
\end{equation}
$$  

where $\eta$ is efficiency factor, $I$ is current, $V$ is supplied voltage, and $t$ is actuation time (duty cycle). We will approximate $\eta$ to be 0.1 which is on the safe side. 

Heat generation is a desirable/undesirable character of solenoids given the $I^2 R$ losses and their low efficiency. Therefore, we should consider the duty cycle, or the amount of time (period) the input source will power the solenoid for. 

Let's say we want the solenoid to be on for 0.25 of a second which means a duty cycle of 25%. Now we can solve for the power terms of the equation above in Watts. 

$$ \begin{equation} 
{{Fd} \over {\eta t} } = { 0.35 J \over {(0.1)*(0.25)}} = 14 W = IV
\end{equation}
$$  

This means we need a solenoid with at least 14 W of input power to generate the required force at that stroke (d). 

## Force / Stroke Diagrams 

Let's look at an example from a specific push-pull solenoid. 

Typically force will decrease (exponentially) with stroke length for a pushing motion. 


![enter image description here](https://cdn-shop.adafruit.com/product-files/3992/3992_diagram.jpg)
   
NB: 'STRODE' should be 'STROKE'!

We see four different lines representing the Force as a function of stroke at different duty cycles, 10%, 25%, 50%, 100%. At smaller duty cycles, the solenoid can handle more current; the more power that is applied to the solenoid, the more force it is capable at the stroke. But, heat builds up as a function of the square of current and increasing applied power, increases current so it ends up being a tradeoff between time-on and applied power to prevent thermal damage (typically this means melted coil bobbins). 

As an example, if we use a coil rated for 10 W at 4.4 volts, we should see a current of 2.27 A. Giving the same coil 8 W will see a corresponding increase in current which might result in thermal failure 

Ok, so remember we want to move something that weights 1 lb (0.45 kg), with a stroke of 8 mm. We determined that power input constraints demand a power supply that can supply 14 W. Looking at the stroke-force plot, we see that even for the 25 W power source at a stroke of 8 mm, that we can only generate about 0.3 kg force and only for a duty cycle of 10%. This means we would likely need to look for another solenoid that is capable of generating adequate force for the amount of time that we want and at the desired stroke. 

## what about pressing a keyboard key? 

Let's say we want to see if this motor is capable of pressing a typical key from a computer keyboard. Online we find that a typical range for the force needed to depress a key is 0.04 - 0.06 kg-f (0.39 - 0.59 N). Typical key travel distance also varies, but is around 0.8-1.55 mm for laptops and 3.5-4.0 mm for mechanical keyboards. So let's say we want to make sure a solenoid can depress a 0.06 kg key at a distance of 4.0 mm for a 0.25 second period.  

0.59 N * 0.004 (m) = 0.0024 J.

$$ \begin{equation} 
{{Fd} \over {\eta t} } = { 0.0024 J \over {(0.1)*(0.25)}} = 0.1 W = IV
\end{equation}
$$  

With these specs, clearly the solenoid above would meet the needs. 

however, this solenoid would probably be better since it requires less power.  

![enter image description here](https://www.hobbytronics.co.za/Content/external/1274/D2512640695.pdf) 





