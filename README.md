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


Import and use the SignupForm component in your React application:

jsx
Copy code
import SignupForm from './path/to/SignupForm';

function App() {
  return (
    <div className="App">
      <SignupForm />
    </div>
  );
}

export default App;
Component Code
jsx
Copy code
import React from 'react';
import { Formik, Form, Field, ErrorMessage } from 'formik';
import * as Yup from 'yup';
import '../pages/signUP.css'; // Import the CSS file for styling
import { useNavigate } from 'react-router-dom';
import { toast } from 'react-toastify';

const SignupForm = () => {
    const navigate = useNavigate();

    const validationSchema = Yup.object({
        name: Yup.string().required('Name is required'),
        email: Yup.string()
            .email('Invalid email format')
            .required('Email is required'),
        password: Yup.string()
            .matches(
                /^(?=.*[a-z])(?=.*[A-Z])(?=.*[0-9])(?=.*[!@#$%^&*])[a-zA-Z0-9!@#$%^&*]{8,}$/,
                'Password must start with a lowercase letter, contain an uppercase letter, a special character, and a number'
            )
            .required('Password is required'),
        confirmPassword: Yup.string()
            .oneOf([Yup.ref('password'), null], 'Passwords must match')
            .required('Confirm Password is required'),
    });

    const initialValues = {
        name: '',
        email: '',
        password: '',
        confirmPassword: '',
    };

    const handleSubmit = (values) => {
        console.log('Form submitted successfully:', values);
        toast.success("Submit Successfully !!!");
        setTimeout(() => {
            navigate('/home');
        }, 2000);
    };

    return (
        <div className="container">
            <div className="form-section">
                <h2>Welcome!</h2>
                <Formik
                    initialValues={initialValues}
                    validationSchema={validationSchema}
                    onSubmit={handleSubmit}
                >
                    {({ isSubmitting, isValid, dirty }) => (
                        <Form className="form">
                            <div className="form-group">
                                <label htmlFor="name">Name</label>
                                <Field name="name" type="text" placeholder="Name" />
                                <ErrorMessage name="name" component="div" className="error" />
                            </div>

                            <div className="form-group">
                                <label htmlFor="email">Email</label>
                                <Field name="email" type="email" placeholder="Email" />
                                <ErrorMessage name="email" component="div" className="error" />
                            </div>

                            <div className="form-group">
                                <label htmlFor="password">Password</label>
                                <Field name="password" type="password" placeholder="Password" />
                                <ErrorMessage name="password" component="div" className="error" />
                            </div>

                            <div className="form-group">
                                <label htmlFor="confirmPassword">Confirm Password</label>
                                <Field name="confirmPassword" type="password" placeholder="Confirm Password" />
                                <ErrorMessage name="confirmPassword" component="div" className="error" />
                            </div>

                            <button
                                type="submit"
                                className="submit-btn"
                                disabled={isSubmitting || !isValid || !dirty}
                            >
                                Sign Up
                            </button>
                        </Form>
                    )}
                </Formik>
            </div>
            <div className="image-section">
                <img src="https://images.pexels.com/photos/7974/pexels-photo.jpg?auto=compress&cs=tinysrgb&w=600" alt="form-img" />
            </div>
        </div>
    );
};

export default SignupForm;
CSS Styling
Create a file named signUP.css in the pages directory to style the form:

css
Copy code
/* signUP.css */
.container {
  display: flex;
  justify-content: space-between;
  padding: 20px;
}

.form-section {
  width: 50%;
}

.image-section {
  width: 50%;
}

.form-group {
  margin-bottom: 15px;
}

.error {
  color: red;
}

.submit-btn {
  background-color: #4CAF50;
  color: white;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
}
Usage
Name: A required field for the user's name.
Email: A required field for the user's email, validated for proper format.
Password: A required field with complex validation rules.
Confirm Password: A required field that must match the password.
Handling Form Submission
On successful form submission:

The form data is logged to the console.
A success message is displayed using react-toastify.
The user is redirected to the /home route after a 2-second delay.
License
This component is licensed under the MIT License. See LICENSE for more details.

Acknowledgments
Thanks to Pexels for providing the placeholder image.
Utilizes react-toastify for notifications and Formik with Yup for form handling and validation.





