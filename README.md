from reportlab.lib.pagesizes import letter
from reportlab.platypus import SimpleDocTemplate, Paragraph, Spacer, Image
from reportlab.lib.styles import getSampleStyleSheet
from reportlab.lib.units import inch

def create_brochure(filename="Aqua_Inc_Brochure.pdf"):
    # Document setup
    doc = SimpleDocTemplate(filename, pagesize=letter)
    styles = getSampleStyleSheet()
    story = []

    # Title
    title = Paragraph("<b><font size=24>Aqua Inc</font></b>", styles["Title"])
    story.append(title)
    story.append(Spacer(1, 0.5 * inch))

    # Subtitle
    subtitle = Paragraph(
        "<font size=14>Premium Water Treatment Supplies & Solutions</font>",
        styles["Heading2"]
    )
    story.append(subtitle)
    story.append(Spacer(1, 0.2 * inch))

    # About Section
    about_text = """
        Aqua Inc is a trusted provider of high-quality water treatment supplies designed
        for residential, commercial, and industrial systems. We offer cutting-edge
        filtration technologies, eco-friendly purification products, and reliable
        equipment to ensure clean, safe, and great-tasting water.
    """
    story.append(Paragraph(about_text, styles["BodyText"]))
    story.append(Spacer(1, 0.3 * inch))

    # Products Section
    products_title = Paragraph("<b><font size=16>Our Products</font></b>", styles["Heading2"])
    story.append(products_title)
    story.append(Spacer(1, 0.1 * inch))

    products_list = """
        • Sediment Filters<br/>
        • Activated Carbon Cartridges<br/>
        • Reverse Osmosis Membranes<br/>
        • UV Water Purification Systems<br/>
        • Industrial Filtration Media<br/>
        • Water Testing Kits<br/>
        • Chemical Treatment Solutions
    """
    story.append(Paragraph(products_list, styles["BodyText"]))
    story.append(Spacer(1, 0.3 * inch))

    # Contact Section
    contact_title = Paragraph("<b><font size=16>Contact Us</font></b>", styles["Heading2"])
    story.append(contact_title)
    story.append(Spacer(1, 0.1 * inch))

    contact_info = """
        Aqua Inc<br/>
        Email: info@aquainc.com<br/>
        Phone: (555) 123-4567<br/>
        Website: www.aquainc.com<br/>
        Address: 123 Bluewater Drive, Clearwater, FL
    """
    story.append(Paragraph(contact_info, styles["BodyText"]))

    # Build the PDF
    doc.build(story)
    print(f"Brochure successfully created: {filename}")

# Run the function
create_brochure()
