SecureShare: A Secure File Sharing Platform (Educational Demo)

SecureShare is a foundational web application built with Flask that demonstrates core concepts of secure file sharing. It allows users to upload files, encrypt them at rest on the server, and generate unique, time-expiring, and download-limited shareable links.

Disclaimer: This project is intended for educational purposes only to illustrate concepts of web development, file handling, encryption, and access control. It is NOT production-ready and lacks many security features crucial for a real-world secure file sharing service. Do not use it for sensitive data in a production environment.
✨ Features

    User Authentication: Secure user registration and login with hashed passwords.

    File Upload: Users can upload any type of file.

    Server-Side Encryption: Files are encrypted using cryptography.fernet (AES-128 in CBC mode with HMAC) immediately upon upload and stored in an encrypted format.

    Unique Shareable Links: Generate unique UUID-based links for uploaded files.

    Expiring Links: Set a time limit for how long a share link remains active.

    Download Limits: Configure a maximum number of downloads for each link.

    File Management: Users can view their uploaded files and manage (generate/delete) their share links.

    File Deletion: Delete uploaded files and all associated share links.

    Responsive UI: Basic responsive design using Tailwind CSS.

🛠️ Technologies Used

    Backend: Python 3.9+

    Web Framework: Flask

    Database: SQLAlchemy (with SQLite for development, easily configurable for PostgreSQL)

    Encryption: cryptography library (Fernet symmetric encryption)

    Password Hashing: Werkzeug's generate_password_hash

    Frontend: HTML, Tailwind CSS

    Project Management: pip for dependencies

🚀 Getting Started

Follow these steps to set up and run the SecureShare platform on your local machine.
Prerequisites

    Python 3.9 or higher installed.

    pip (Python package installer).

1. Clone the Repository

First, clone this GitHub repository to your local machine:

git clone https://github.com/your-username/secure-share-platform.git
cd secure-share-platform

(Note: Replace your-username/secure-share-platform with the actual path to your repository if you fork it.)
2. Create and Activate a Virtual Environment

It's highly recommended to use a virtual environment to manage project dependencies.

# Create a virtual environment
python3 -m venv venv

# Activate the virtual environment
# On macOS/Linux:
source venv/bin/activate

# On Windows:
.\venv\Scripts\activate

3. Install Dependencies

With your virtual environment activated, install the required Python packages:

pip install -r requirements.txt

4. Run the Flask Application

Now, you can run the Flask development server:

python app.py

You will see output in your terminal indicating that the Flask server is running, usually on http://127.0.0.1:5000/ or http://localhost:5000/.

Important Notes on First Run:

    A master_key.key file will be generated in your project root. This key is crucial for encrypting/decrypting file-specific keys. Keep this file secure!

    An uploads/ directory will be created to store your encrypted files.

    A secure_share.db SQLite database file will be created to store user and file metadata.

5. Access the Platform

Open your web browser and navigate to:

http://localhost:5000/

You should now see the SecureShare platform's home page.
6. Basic Usage

    Register: Create a new user account.

    Login: Log in with your new account.

    Upload File: Go to "Upload File", choose a file, and upload it. It will be encrypted.

    My Files: Visit "My Files" to see your uploaded files.

    Generate Link: For any file, click "Generate New Link." Configure expiration and download limits.

    Share & Download: Copy the generated public URL and share it. Recipients can use this link to download the file.

    Delete: You can delete files (which removes all associated links) or individual share links from the "My Files" page.

7. Stopping the Application

To stop the Flask development server, press Ctrl+C in the terminal where app.py is running.

To deactivate your virtual environment:

# On macOS/Linux:
deactivate
# On Windows:
deactivate

⚠️ Security Considerations and Limitations

This project is a simplified demonstration. For a production-grade secure file sharing platform, the following would be critical:

    No True End-to-End Encryption (E2E): Files are encrypted on the server. The server holds the master key and can technically access unencrypted data. True E2E requires client-side encryption where only the client holds the decryption key.

    Master Key Management: The master_key.key is stored directly on the server's filesystem. In production, this key must be managed securely using a Key Management Service (KMS) or Hardware Security Module (HSM).

    No HTTPS: The development server runs on HTTP. All production deployments must use HTTPS to encrypt data in transit.

    No Robust Input Validation/Sanitization: While basic checks are in place, a production app needs comprehensive input validation to prevent XSS, SQL injection, etc.

    No Rate Limiting: Vulnerable to brute-force attacks on login or share links.

    File Size Limits: No explicit file size limits implemented.

    Scalability: Local file storage and SQLite are not suitable for large-scale deployments. Cloud storage (AWS S3, GCS) and a robust database (PostgreSQL, MySQL) would be needed.

    Error Handling: More comprehensive and user-friendly error handling.

    Logging and Monitoring: Essential for security auditing and incident response.

💡 Future Enhancements

    Implement client-side (browser-based) encryption for true end-to-end security.

    Integrate with cloud storage providers (e.g., AWS S3, Google Cloud Storage) for scalable and durable file storage.

    Add multi-factor authentication (MFA) for user accounts.

    Implement robust logging and monitoring.

    Add an administrative interface for managing users and files.

    Implement file versioning.

    Allow users to set passwords for share links.


