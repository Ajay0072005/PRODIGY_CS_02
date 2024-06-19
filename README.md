# PRODIGY_CS_02
A Simple image encryption tool using pixel manipulation
# impot 
   from PIL import Image
# Encrypt the image by applying a basic mathematical operation to each pixel
    
    def encrypt_image(image_path, key):
    try:
        img = Image.open(image_path)
        pixels = img.load()
        width, height = img.size
    for y in range(height):
            for x in range(width):
                r, g, b = pixels[x, y]
                r = (r + key) % 256
                g = (g + key) % 256
                b = (b + key) % 256
                pixels[x, y] = (r, g, b)

 # Save the encrypted image
        encrypted_image_path = "encrypted__img.png"
        img.save(encrypted_image_path)
        print(f"Image encrypted and saved as {encrypted_image_path}")
    except Exception as e:
        print(f"An error occurred: {e}")
# Decrypt the image by applying a basic mathematical operation to each pixel
    def decrypt_image(encrypted_image_path, key):
    try:
# Open the encrypted image
        img = Image.open(encrypted_image_path)
        pixels = img.load()
        width, height = img.size
        for y in range(height):
            for x in range(width):
                r, g, b = pixels[x, y]
                r = (r - key) % 256
                g = (g - key) % 256
                b = (b - key) % 256
                pixels[x, y] = (r, g, b)

# Save the decrypted image
        decrypted_image_path = "decrypted_img.png"
        img.save(decrypted_image_path)
        print(f"Image decrypted and saved as {decrypted_image_path}")
    except Exception as e:
        print(f"An error occurred: {e}")

# Example usage
    image_path = r"C:\Users\Ajaymohan\Downloads\300_ROG Zephyrus S17.jpg"  # Replace with the path to your image
    encryption_key = 42

# Encrypt the image
    encrypt_image(image_path, encryption_key)

# Decrypt the encrypted image
    decrypt_image("encrypted_image.png", encryption_key)
