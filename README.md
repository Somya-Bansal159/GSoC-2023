# GSoC-2023

<p align="center">
<a href="https://summerofcode.withgoogle.com/"><img style="padding: 20px;" alt="drawing" src="./assets/gsoc.png" height="200"></a>
<a href="https://hepsoftwarefoundation.org/"><img style="padding: 20px;" alt="drawing" src="./assets/hsf.png" height="200"></a>
</p>

You can find my project proposal here:

[Project Proposal](https://summerofcode.withgoogle.com/media/user/f290ccb7f767/proposal/gAAAAABk7KlmJvmWGfpDhE6exm_H5k7fhmi5Y46wW5s5jmy_UslzgCclcwl8jwFbsoFPxo-E-AU-MlsMuKu3WJSG4_p4yUcGJA-T7iJ0wxZGXcWtIpMxMvU=.pdf)

## Phoenix
I worked on an Angular application named [Phoenix](https://phoenixatlas.web.cern.ch/), that renders the 3D simulation of the collision experiments at CERN using ThreeJS.

It has two projects: phoenix-event-display and phoenix-ng. phoenix-event-display contains the models, loaders and manager files, that work behind the scenes to render the meshes and event data, while phoenix-ng consists of six sub-applications - LHCb, Atlas, TrackML, Playground, CMS, and Geometry Display - as well as deals with the UI Menu to be displayed in each sub-app, that will call the respective functions in the phoenix-event-display to enhance user experience.

## My Work
I had two tasks:
1. Scaling
2. Navigation

### Scaling:
Users need to know the positions or relative locations of the particles, 3D distance between any two points, 3D coordinates of any point, dimensions of any subdetector, etc. For this, I did the following tasks:
1. Cartesian Grid: I introduced a 3D cartesian grid, that has various features. It has planes in XY, YZ and ZX directions, the number of planes in each direction can be changed, user can toggle the visibility of the planes of any direction, the sparsity of the gridlines can be changed, the grid can be translated - either by manually entering the value of the 3D coordinates of the new origin, or by clicking at any point to make it the new origin.

2. 3D Points: User can click at any point in the scene, and if there are visible meshes directly under the pointer, the 3D coordinates of the closest intersect will be displayed. A ray emits from the pointer towards the screen, and intersects with any mesh that falls under it. The coordinates of the closest intersect are extracted. Here is a catch, that, when the clipping is enabled, the ray cannot detect it, and intersect with the clipped region as well. So, the intersects that lie under the clipped region need to be manually discarded.

3. 3D Distance: Using this "3D Points" feature, user can find out the distance between any two points in three dimension.

Here are the PRs:
1. https://github.com/HSF/phoenix/pull/587
2. https://github.com/HSF/phoenix/pull/612
3. https://github.com/HSF/phoenix/pull/616

## Navigation:
Users need a feature in which he can navigate easily to any part of the detector, thereby reaching its subparts. For this, I added a menu, in which user can select the category of the subparts first. Now, in this category, all of the subparts will be listed. In front of each subpart, there are two buttons:
1. Move camera to object: This button will zoom the camera into the subpart's location, as well has highlight it.
2. Highlight object: This button will highlight or draw an outline around the subpart.

Here is the PR:
https://github.com/HSF/phoenix/pull/617
