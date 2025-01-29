# Interactive Editable Mind Map

This is a **dynamic mind map** created using **D3.js**. You can **edit the JSON structure** in the text box below to customize the nodes and relationships.

### 📌 How to Use:
1. Modify the JSON structure in the **text area** below.
2. Click **"Update Map"** to apply the changes.
3. The mind map updates dynamically.

---

## **Edit Mind Map JSON**
<textarea id="jsonInput" rows="10" cols="80">
{
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
}
</textarea>
<br>
<button onclick="updateMap()">Update Map</button>

---

## **Live Mind Map**
<svg></svg>

<script src="https://d3js.org/d3.v7.min.js"></script>
<script>
    let svg = d3.select("svg").attr("width", 800).attr("height", 500);
    let g = svg.append("g").attr("transform", "translate(50,50)");
    let treeLayout = d3.tree().size([700, 400]);

    function drawMindMap(jsonData) {
        g.selectAll("*").remove(); // Clear previous map

        const root = d3.hierarchy(jsonData);
        treeLayout(root);

        // Draw links
        g.selectAll(".link")
            .data(root.links())
            .enter().append("line")
            .attr("stroke", "#999")
            .attr("stroke-width", "2px")
            .attr("x1", d => d.source.x)
            .attr("y1", d => d.source.y)
            .attr("x2", d => d.target.x)
            .attr("y2", d => d.target.y);

        // Draw nodes
        const nodes = g.selectAll(".node")
            .data(root.descendants())
            .enter().append("g")
            .attr("transform", d => `translate(${d.x},${d.y})`);

        nodes.append("circle")
            .attr("r", 8)
            .attr("fill", "steelblue")
            .attr("stroke", "black")
            .attr("stroke-width", "1.5px");

        nodes.append("text")
            .attr("dy", -10)
            .attr("font-size", "12px")
            .attr("text-anchor", "middle")
            .text(d => d.data.name);
    }

    function updateMap() {
        try {
            const jsonData = JSON.parse(document.getElementById("jsonInput").value);
            drawMindMap(jsonData);
        } catch (error) {
            alert("Invalid JSON format. Please check your syntax.");
        }
    }

    // Initialize with default map
    updateMap();
</script>

---

### 🚀 Features:
✔ **Editable Mind Map** – Modify the JSON structure to add/remove nodes.  
✔ **Live Updates** – Click **"Update Map"** to apply changes instantly.  
✔ **Error Handling** – Alerts if the JSON format is incorrect.  
✔ **GitHub Pages Compatible** – Runs directly on `github.io`.  

---

Would you like **expand/collapse nodes**, **better styling**, or **export options**? Let me know! 🚀