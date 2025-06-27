# project-qr
Making a QR code
import qrcode
from pathlib import Path

def save_to_downloads(filename='qr_code1.png'):
    downloads_path = Path.home() / "Downloads"
    return downloads_path / filename

# Get user input
data = input("Enter text or link to generate the QR Code: ")

# Generate the QR code image
qr = qrcode.QRCode(
    version=1,
    box_size=10,
    border=5
)
qr.add_data(data)
qr.make(fit=True)
img = qr.make_image(fill="black", back_color="white")

# Save the image
file_path = save_to_downloads()
img.save(file_path)

print(f"QR Code saved to: {file_path}")
