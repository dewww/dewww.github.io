# Interactive Mind Map

This is a simple **interactive mind map** created using **D3.js**. It organizes concepts into a tree structure where each node represents an idea, and lines represent relationships.

### 📌 How to Use:
- The **"Root Idea"** connects to **Concepts** (A, B, C).
- Each **Concept** has **Details** attached to it.
- You can customize the mind map by editing the JSON structure in the embedded script.

---

## Live Mind Map

<svg></svg>

<script src="https://d3js.org/d3.v7.min.js"></script>
<script>
    const data = {
        "name": "Root Idea",
        "children": [
            { "name": "Concept A", "children": [
                { "name": "Detail A1" },
                { "name": "Detail A2" }
            ]},
            { "name": "Concept B", "children": [
                { "name": "Detail B1" },
                { "name": "Detail B2" }
            ]},
            { "name": "Concept C", "children": [
                { "name": "Detail C1" },
                { "name": "Detail C2" }
            ]}
        ]
    };

    const width = 800, height = 500;
    const svg = d3.select("svg").attr("width", width).attr("height", height);
    const g = svg.append("g").attr("transform", "translate(50,50)");

    const treeLayout = d3.tree().size([width - 100, height - 100]);
    const root = d3.hierarchy(data);
    treeLayout(root);

    // Links
    g.selectAll(".link")
        .data(root.links())
        .enter().append("line")
        .style("stroke", "#999")
        .style("stroke-width", "2px")
        .attr("x1", d => d.source.x)
        .attr("y1", d => d.source.y)
        .attr("x2", d => d.target.x)
        .attr("y2", d => d.target.y);

    // Nodes
    const nodes = g.selectAll(".node")
        .data(root.descendants())
        .enter().append("g")
        .attr("transform", d => `translate(${d.x},${d.y})`);

    nodes.append("circle")
        .attr("r", 8)
        .style("fill", "steelblue")
        .style("stroke", "black")
        .style("stroke-width", "1.5px");

    nodes.append("text")
        .attr("dy", -10)
        .style("font-size", "12px")
        .style("text-anchor", "middle")
        .text(d => d.data.name);
</script>

---

### 🚀 Features:
✔ **Graphical Mind Map** – Visualizes relationships between ideas.  
✔ **Customizable** – Modify the JSON structure in the script to add new nodes.  
✔ **Fully GitHub Pages Compatible** – Runs directly on `github.io`.  

---

Would you like **expand/collapse functionality** or **more interactivity**? Let me know! 🚀