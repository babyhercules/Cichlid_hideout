---
layout: default
title: Fish Room
permalink: /fishroom/
---

<div class="single-post">
  <h2>Fish Room Tank Inventory</h2>
  <p>Tracking tank status, needed equipment, and current stock.</p>

  {% for tank in site.data.tanks %}
    <section style="border:1px solid var(--border); border-radius:6px; padding:1rem 1.25rem; margin:1.25rem 0; background:#fafbfc;">
      <h3 style="margin:0; color:var(--navy);">{{ tank.name }} — {{ tank.status }}</h3>
      <p style="margin:0.35rem 0 0.85rem; color:var(--muted); font-size:0.9rem;"><strong>Tank Size:</strong> {{ tank.size }}</p>

      <h4 style="margin:0.5rem 0 0.25rem; font-size:0.95rem;">Equipment Needed</h4>
      {% if tank.needed_equipment and tank.needed_equipment.size > 0 %}
        <ul style="margin:0.25rem 0 0.9rem;">
          {% for item in tank.needed_equipment %}
            <li>{{ item }}</li>
          {% endfor %}
        </ul>
      {% else %}
        <p style="margin:0.25rem 0 0.9rem; color:var(--muted); font-size:0.9rem;">None</p>
      {% endif %}

      <h4 style="margin:0.5rem 0 0.25rem; font-size:0.95rem;">Stock List</h4>
      {% if tank.stock and tank.stock.size > 0 %}
        <ul style="margin:0.25rem 0 0;">
          {% for fish in tank.stock %}
            <li><strong>{{ fish.species }}</strong> — {{ fish.size }} (Qty: {{ fish.qty }})</li>
          {% endfor %}
        </ul>
      {% else %}
        <p style="margin:0.25rem 0 0; color:var(--muted); font-size:0.9rem;">No fish currently stocked.</p>
      {% endif %}
    </section>
  {% endfor %}
</div>
