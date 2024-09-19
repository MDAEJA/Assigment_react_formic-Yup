# SignupForm Component

## Overview

The `SignupForm` component is a React functional component that uses Formik for form management and Yup for validation. It provides a user-friendly form for user registration with fields for name, email, password, and confirm password.

## Features

- **Formik Integration**: Handles form state management and validation.
- **Yup Validation Schema**: Ensures user inputs are correctly formatted and meet requirements.
- **User Feedback**: Displays success messages using `react-toastify`.
- **Navigation**: Redirects users to a different route upon successful form submission.
- **Responsive Design**: Styled with a CSS file for a clean and professional appearance.

## Dependencies

- `react`
- `formik`
- `yup`
- `react-router-dom`
- `react-toastify`

## Installation

1. Ensure you have Node.js and npm installed on your machine.
2. Clone the repository or copy the component files into your project.
3. Install the required dependencies:

   ```bash
   npm install formik yup react-router-dom react-toastify

## Usage

1. Name: A required field for the user's name.
2. Email: A required field for the user's email, validated for proper format.
3. Password: A required field with complex validation rules.
4. Confirm Password: A required field that must match the password.

## Handling Form Submission
`On successful form submission:`
The form data is logged to the console.
A success message is displayed using react-toastify.
The user is redirected to the /home route after a 2-second delay.

## License
This component is licensed under the MIT License. See LICENSE for more details.

## Acknowledgments
Thanks to Pexels for providing the placeholder image.
Utilizes react-toastify for notifications and Formik with Yup for form handling and validation.





