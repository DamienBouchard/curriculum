---
author: mihaiberq

levels:

  - beginner

  - basic

  - medium

  - advanced

type: normal

category: must-know



parent: prims-algorithm

---

# Prim's Algorithm Iteration

---
## Content

Consider the following *weighted, connected graph*:

![primsinit](%3Csvg%20width%3D%22100%25%22%20height%3D%22auto%22%20viewBox%3D%220%200%20500%20260%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Ctitle%3EArtboard%3C%2Ftitle%3E%3Cg%20fill%3D%22none%22%20fill-rule%3D%22evenodd%22%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%2260%22%20cy%3D%2260%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%2245.4975586%22%20y%3D%2279%22%3EA%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%2260%22%20cy%3D%22200%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%2245.4975586%22%20y%3D%22219%22%3ED%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%22250%22%20cy%3D%22200%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22235.497559%22%20y%3D%22219%22%3EE%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%22250%22%20cy%3D%2260%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22235.497559%22%20y%3D%2279%22%3EB%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%22440%22%20cy%3D%22126%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22425.497559%22%20y%3D%22145%22%3EC%3C%2Ftspan%3E%3C%2Ftext%3E%3Cpath%20d%3D%22M59%20105v51m47%2041h100.005M93%2092l129%2073M105%2062h101m90%200l117%2028M295%20201l115-41%22%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22146.498535%22%20y%3D%2255%22%3E1%3C%2Ftspan%3E%3C%2Ftext%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22156.498535%22%20y%3D%22123%22%3E3%3C%2Ftspan%3E%3C%2Ftext%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22355.498535%22%20y%3D%2273%22%3E5%3C%2Ftspan%3E%3C%2Ftext%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22355.498535%22%20y%3D%22202%22%3E3%3C%2Ftspan%3E%3C%2Ftext%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%2236.4985352%22%20y%3D%22139%22%3E2%3C%2Ftspan%3E%3C%2Ftext%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22146.498535%22%20y%3D%22225%22%3E1%3C%2Ftspan%3E%3C%2Ftext%3E%3C%2Fg%3E%3C%2Fsvg%3E)

The algorithm starts off by picking a random node, say *B*. It then adds edges incident to B to the sorted container of available edges:

![iter1](%3Csvg%20width%3D%22100%25%22%20height%3D%22auto%22%20viewBox%3D%220%200%20500%20260%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Ctitle%3EArtboard%3C%2Ftitle%3E%3Cg%20fill%3D%22none%22%20fill-rule%3D%22evenodd%22%3E%3Ccircle%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%20cx%3D%2260%22%20cy%3D%2260%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%2245.4975586%22%20y%3D%2279%22%3EA%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%22250%22%20cy%3D%2260%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22235.497559%22%20y%3D%2279%22%3EB%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%20cx%3D%22440%22%20cy%3D%22126%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22425.497559%22%20y%3D%22145%22%3EC%3C%2Ftspan%3E%3C%2Ftext%3E%3Cpath%20d%3D%22M105%2062h100m91%200l117%2028%22%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22146.498535%22%20y%3D%2255%22%3E1%3C%2Ftspan%3E%3C%2Ftext%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22355.498535%22%20y%3D%2273%22%3E5%3C%2Ftspan%3E%3C%2Ftext%3E%3C%2Fg%3E%3C%2Fsvg%3E)

Out of those edges, the cheapest one is *BA*. So it adds *A* to the tree and the new available edges to the sorted container:

![iter2](%3Csvg%20width%3D%22100%25%22%20height%3D%22auto%22%20viewBox%3D%220%200%20500%20260%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Ctitle%3EArtboard%3C%2Ftitle%3E%3Cg%20fill%3D%22none%22%20fill-rule%3D%22evenodd%22%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%2260%22%20cy%3D%2260%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%2245.4975586%22%20y%3D%2279%22%3EA%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%20cx%3D%2260%22%20cy%3D%22200%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%2245.4975586%22%20y%3D%22219%22%3ED%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%22250%22%20cy%3D%2260%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22235.497559%22%20y%3D%2279%22%3EB%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%20cx%3D%22440%22%20cy%3D%22126%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22425.497559%22%20y%3D%22145%22%3EC%3C%2Ftspan%3E%3C%2Ftext%3E%3Cpath%20d%3D%22M59%20105v51%22%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%2F%3E%3Cpath%20d%3D%22M105%2062h101%22%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%2F%3E%3Cpath%20d%3D%22M296%2062l117%2028%22%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22146.498535%22%20y%3D%2255%22%3E1%3C%2Ftspan%3E%3C%2Ftext%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22355.498535%22%20y%3D%2273%22%3E5%3C%2Ftspan%3E%3C%2Ftext%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%2236.4985352%22%20y%3D%22139%22%3E2%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%20cx%3D%22250%22%20cy%3D%22200%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22235.497559%22%20y%3D%22219%22%3EE%3C%2Ftspan%3E%3C%2Ftext%3E%3Cpath%20d%3D%22M93%2092l129%2073%22%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22156.498535%22%20y%3D%22123%22%3E3%3C%2Ftspan%3E%3C%2Ftext%3E%3C%2Fg%3E%3C%2Fsvg%3E)

*AD* is picked next:

![iter3](%3Csvg%20width%3D%22100%25%22%20height%3D%22auto%22%20viewBox%3D%220%200%20500%20260%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Ctitle%3EArtboard%3C%2Ftitle%3E%3Cg%20fill%3D%22none%22%20fill-rule%3D%22evenodd%22%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%2260%22%20cy%3D%2260%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%2245.4975586%22%20y%3D%2279%22%3EA%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%2260%22%20cy%3D%22200%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%2245.4975586%22%20y%3D%22219%22%3ED%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%22250%22%20cy%3D%2260%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22235.497559%22%20y%3D%2279%22%3EB%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%20cx%3D%22440%22%20cy%3D%22126%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22425.497559%22%20y%3D%22145%22%3EC%3C%2Ftspan%3E%3C%2Ftext%3E%3Cpath%20d%3D%22M59%20105v51m46-94h101%22%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%2F%3E%3Cpath%20d%3D%22M296%2062l117%2028%22%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22146.498535%22%20y%3D%2255%22%3E1%3C%2Ftspan%3E%3C%2Ftext%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22355.498535%22%20y%3D%2273%22%3E5%3C%2Ftspan%3E%3C%2Ftext%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%2236.4985352%22%20y%3D%22139%22%3E2%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%20cx%3D%22250%22%20cy%3D%22200%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22235.497559%22%20y%3D%22219%22%3EE%3C%2Ftspan%3E%3C%2Ftext%3E%3Cpath%20d%3D%22M93%2092l129%2073%22%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22156.498535%22%20y%3D%22123%22%3E3%3C%2Ftspan%3E%3C%2Ftext%3E%3Cpath%20d%3D%22M106%20197h100.005%22%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22146.498535%22%20y%3D%22225%22%3E1%3C%2Ftspan%3E%3C%2Ftext%3E%3C%2Fg%3E%3C%2Fsvg%3E)

The next cheapest edge is *DE*, so it adds *E* to the tree:

![alt description](%3Csvg%20width%3D%22100%25%22%20height%3D%22auto%22%20viewBox%3D%220%200%20500%20260%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Ctitle%3EArtboard%3C%2Ftitle%3E%3Cg%20fill%3D%22none%22%20fill-rule%3D%22evenodd%22%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%2260%22%20cy%3D%2260%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%2245.4975586%22%20y%3D%2279%22%3EA%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%2260%22%20cy%3D%22200%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%2245.4975586%22%20y%3D%22219%22%3ED%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%22250%22%20cy%3D%2260%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22235.497559%22%20y%3D%2279%22%3EB%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%20cx%3D%22440%22%20cy%3D%22126%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22425.497559%22%20y%3D%22145%22%3EC%3C%2Ftspan%3E%3C%2Ftext%3E%3Cpath%20d%3D%22M59%20105v51m46-94h101%22%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%2F%3E%3Cpath%20d%3D%22M296%2062l117%2028%22%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22146.498535%22%20y%3D%2255%22%3E1%3C%2Ftspan%3E%3C%2Ftext%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22355.498535%22%20y%3D%2273%22%3E5%3C%2Ftspan%3E%3C%2Ftext%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%2236.4985352%22%20y%3D%22139%22%3E2%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%22250%22%20cy%3D%22200%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22235.497559%22%20y%3D%22219%22%3EE%3C%2Ftspan%3E%3C%2Ftext%3E%3Cpath%20d%3D%22M93%2092l129%2073%22%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22156.498535%22%20y%3D%22123%22%3E3%3C%2Ftspan%3E%3C%2Ftext%3E%3Cpath%20d%3D%22M106%20197h100.005%22%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22146.498535%22%20y%3D%22225%22%3E1%3C%2Ftspan%3E%3C%2Ftext%3E%3Cpath%20d%3D%22M295%20201l115-41%22%20stroke%3D%22%23FFF%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22%23FFF%22%3E%3Ctspan%20x%3D%22355.498535%22%20y%3D%22202%22%3E3%3C%2Ftspan%3E%3C%2Ftext%3E%3C%2Fg%3E%3C%2Fsvg%3E)

Left with two edges that have the same weight to be picked next, the algorithm chooses the one for which the node at the other end is not already in the tree(or a random edge if neither node has been added). In the end, the minimum spanning tree will be:

![final](%3Csvg%20width%3D%22100%25%22%20height%3D%22auto%22%20viewBox%3D%220%200%20500%20260%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Ctitle%3EArtboard%3C%2Ftitle%3E%3Cg%20fill%3D%22none%22%20fill-rule%3D%22evenodd%22%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%2260%22%20cy%3D%2260%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%2245.4975586%22%20y%3D%2279%22%3EA%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%2260%22%20cy%3D%22200%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%2245.4975586%22%20y%3D%22219%22%3ED%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%22250%22%20cy%3D%2260%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22235.497559%22%20y%3D%2279%22%3EB%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%22440%22%20cy%3D%22126%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22425.497559%22%20y%3D%22145%22%3EC%3C%2Ftspan%3E%3C%2Ftext%3E%3Cpath%20d%3D%22M59%20105v51m46-94h101%22%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22146.498535%22%20y%3D%2255%22%3E1%3C%2Ftspan%3E%3C%2Ftext%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%2236.4985352%22%20y%3D%22139%22%3E2%3C%2Ftspan%3E%3C%2Ftext%3E%3Ccircle%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20cx%3D%22250%22%20cy%3D%22200%22%20r%3D%2245%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2250%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22235.497559%22%20y%3D%22219%22%3EE%3C%2Ftspan%3E%3C%2Ftext%3E%3Cpath%20d%3D%22M106%20197h100.005%22%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22146.498535%22%20y%3D%22225%22%3E1%3C%2Ftspan%3E%3C%2Ftext%3E%3Cpath%20d%3D%22M295%20201l115-41%22%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20font-family%3D%22RobotoMono-Light%2C%20Roboto%20Mono%22%20font-size%3D%2230%22%20font-weight%3D%22300%22%20fill%3D%22currentColor%22%3E%3Ctspan%20x%3D%22355.498535%22%20y%3D%22202%22%3E3%3C%2Ftspan%3E%3C%2Ftext%3E%3C%2Fg%3E%3C%2Fsvg%3E)

---
## Practice

If the sorted edge container looks like this:
```
[(AC, 5), (AB, 5), (CE, 5)]
```
And the current nodes in the tree are:
```
A, D, C, E
```
The next edge to be picked is:
```
???
```

* `AB`
* `AC`
* `CE`

---
## Revision

Prim's algorithm uses

???

* a greedy approach
* a dynamic approach
* a divide and conquer approach
* no particular approach
