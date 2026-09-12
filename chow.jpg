from PIL import Image, ImageDraw, ImageFont
 
# Canvas setup
width, height = 600, 300
bg_color = (20, 20, 20)          # near-black background
border_color = (0, 0, 0)         # black outer border
panel_color = (250, 240, 190)    # pale yellow inner panel
bulb_color = (255, 240, 130)     # glowing yellow bulbs
text_color = (30, 30, 30)        # dark text
 
img = Image.new("RGB", (width, height), border_color)
draw = ImageDraw.Draw(img)
 
# Inner cream panel
panel_margin = 30
draw.rectangle(
    [panel_margin, panel_margin, width - panel_margin, height - panel_margin],
    fill=panel_color
)
 
# Draw rows of "light bulbs" around the border
bulb_radius = 8
spacing = 30
 
def draw_bulb(x, y):
    draw.ellipse(
        [x - bulb_radius, y - bulb_radius, x + bulb_radius, y + bulb_radius],
        fill=bulb_color,
        outline=(120, 100, 20)
    )
 
# Top and bottom rows
for x in range(spacing, width - spacing // 2, spacing):
    draw_bulb(x, 15)
    draw_bulb(x, height - 15)
 
# Left and right columns
for y in range(spacing, height - spacing // 2, spacing):
    draw_bulb(15, y)
    draw_bulb(width - 15, y)
 
# Text: "COMING SOON!"
try:
    font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf", 48)
except IOError:
    font = ImageFont.load_default()
 
text = "COMING SOON!"
bbox = draw.textbbox((0, 0), text, font=font)
text_w = bbox[2] - bbox[0]
text_h = bbox[3] - bbox[1]
text_x = (width - text_w) / 2
text_y = (height - text_h) / 2 - bbox[1]
 
draw.text((text_x, text_y), text, fill=text_color, font=font)
 
img.save("coming_soon_sign.png")
print("Saved coming_soon_sign.png")
