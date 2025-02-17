# PRODIGY_CS_02

from PIL import Image

def encrypt_image(image_path, output_path):
    # Open the image
    img = Image.open(image_path)
    pixels = img.load()

    # Get image dimensions
    width, height = img.size

    # Encrypt by swapping pixel values
    for y in range(height):
        for x in range(width):
            r, g, b = pixels[x, y]
            # Swap red and blue values
            pixels[x, y] = (b, g, r)

    # Save the encrypted image
    img.save(output_path)
    print(f"Image encrypted and saved to {output_path}")

def decrypt_image(image_path, output_path):
    # Open the encrypted image
    img = Image.open(image_path)
    pixels = img.load()

    # Get image dimensions
    width, height = img.size

    # Decrypt by swapping pixel values back
    for y in range(height):
        for x in range(width):
            r, g, b = pixels[x, y]
            # Swap red and blue values back
            pixels[x, y] = (b, g, r)

    # Save the decrypted image
    img.save(output_path)
    print(f"Image decrypted and saved to {output_path}")

# Example usage
encrypt_image('input_image.jpg', 'encrypted_image.jpg')
decrypt_image('encrypted_image.jpg', 'decrypted_image.jpg')