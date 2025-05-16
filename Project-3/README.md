# Project 3 – Procedural WebGL Shapes

This project contains 5 WebGL applications that progressively build toward rendering a rotating star shape procedurally.

## Demo Pages

| Demo                    | Description                         |
|-------------------------|-------------------------------------|
| [Triangle](https://blue.cs.sonoma.edu/~kmaldonado/CS-351/Project-3/triangle.html) | Wireframe triangle using `gl.LINE_LOOP` |
| [Polygon](https://blue.cs.sonoma.edu/~kmaldonado/CS-351/Project-3/polygon.html)   | Filled 10-sided polygon using `gl.TRIANGLE_FAN` |
| [Star](https://blue.cs.sonoma.edu/~kmaldonado/CS-351/Project-3/star.html)         | Five-pointed star with alternating vertex radii |
| [Rotating Star](https://blue.cs.sonoma.edu/~kmaldonado/CS-351/Project-3/rotating-star.html) | Same star but spinning using a time-based uniform |
| [Colorful Rotating Star](https://blue.cs.sonoma.edu/~kmaldonado/CS-351/Project-3/colorful-rotating-star.html) | **(Extra Credit)** A rotating star with color gradient — optional! |

## Notes

- All shapes are generated procedurally in the vertex shader.
- Vertex count is controlled by a uniform `N` sent from JavaScript.
- `gl_VertexID` is used to calculate each vertex’s angle.
- Rotation is applied via a time uniform `t`.

---

Let me know if you want to double-check that everything’s live on Blue or if you want help committing/pushing to GitHub again!

