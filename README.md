### Full Stack Task Description

#### Overview
You will be tasked with creating a full stack solution for managing anamnesis forms within the ClinicOS system. This involves both backend and frontend development. The backend will involve setting up MedusaJS with PostgreSQL and developing a custom plugin. The frontend will integrate with the Medusa Admin to provide an interface for managing the anamnesis forms.

#### Technologies and Libraries
- **Backend**: MedusaJS, PostgreSQL
- **Frontend**: Vite, React, TailwindCSS, TypeScript, DndKit, React-Table

#### Backend Task Requirements
1. **Set Up MedusaJS Locally**
   - Follow the official MedusaJS documentation to install MedusaJS locally with a PostgreSQL database.
   - Documentation: [MedusaJS Installation](https://docs.medusajs.com/development/backend/install)

2. **Develop `medusa-plugin-anamnesis`**
   - Follow the MedusaJS plugin creation guide to scaffold a new plugin named `medusa-plugin-anamnesis`.
   - Documentation: [Creating Plugins in MedusaJS](https://docs.medusajs.com/development/plugins/create)

3. **Plugin Requirements**
   - Allow creation of digital anamnesis forms.
   - An anamnesis form will have multiple sections (`anamnesis_sections`), and each section will have multiple questions (`anamnesis_questions`).

4. **Data Models and Relationships**
   - **AnamnesisForm**
     - `id`
     - `title`
     - `description`
     - `created_at`
     - `updated_at`
   - **AnamnesisSection**
     - `id`
     - `form_id` (foreign key to AnamnesisForm)
     - `title`
     - `description`
     - `order` (integer to maintain section order)
     - `created_at`
     - `updated_at`
   - **AnamnesisQuestion**
     - `id`
     - `section_id` (foreign key to AnamnesisSection)
     - `question_text`
     - `question_type` (enum: short_answer, long_answer, date, date_time, time, multiple_choice, select)
     - `options` (JSONB, used for multiple_choice and select types)
     - `created_at`
     - `updated_at`

5. **Handling Responses**
   - Create a model to store patient responses with the following fields:
     - **AnamnesisResponse**
       - `id`
       - `customer_id`
       - `order_id`
       - `form_id` (foreign key to AnamnesisForm)
       - `responses` (JSONB: [{question_id, answer}, ...])
       - `created_at`
       - `updated_at`

6. **API Endpoints**
   - Create both `/admin` and `/store` endpoints for managing and retrieving forms.
     - `/admin` Endpoints:
       - Create a new anamnesis form
       - Add sections to a form
       - Add questions to a section
       - Retrieve a form template for management
       - Delete forms, sections, and questions
     - `/store` Endpoints:
       - Retrieve a form template for patient use
       - Submit patient responses

#### Frontend Task Requirements
1. **Integrate with Medusa Admin**
   - Follow the MedusaJS documentation to add your own modules to the existing Medusa Admin.
   - Documentation: [Medusa Admin Quickstart](https://docs.medusajs.com/admin/quickstart)

2. **Pages and Functionality**
   - Create the following pages with the specified functionalities within the Medusa Admin:

   **1. List of All Anamnesis Forms**
   - Use `react-table` to display a list of all anamnesis forms.
   - Include columns for form title, description, creation date, and actions (view, edit, delete).
   - Implement pagination, sorting, and searching functionalities.
   - For searching, add debounce functionality and simulate an async search.

   **2. Anamnesis Form Detail Page**
   - Display the details of a selected anamnesis form.
   - Show the sections and questions within the form.
   - Use `DndKit` to allow drag-and-drop reordering of sections and questions.

   **3. Create Anamnesis Form Page**
   - Provide a form to create a new anamnesis form with fields for the title and description.
   - Allow adding multiple sections, and within each section, allow adding multiple questions.
   - Use `DndKit` for drag-and-drop functionality to reorder sections and questions.

   **4. Update Anamnesis Form Page**
   - Similar to the create page, but pre-populate the form with the existing data of the selected anamnesis form.
   - Allow updating the form, sections, and questions.
   - Use `DndKit` for drag-and-drop functionality to reorder sections and questions.

3. **Deletion Functionality**
   - Implement the ability to delete an anamnesis form from the list page.
   - Implement the ability to delete a section from a form or a question from a section on the detail and update pages.


#### Additional Requirements
- Use TypeScript for all components and ensure type safety.
- Ensure the UI is responsive and user-friendly.
- Provide clear and concise documentation for setting up and running the project.

#### Submission
- Provide a GitHub repository link with your MedusaJS project and integrated Medusa Admin.
- Include a README.md with instructions on how to set up and run your project.
- Document your design decisions, especially for the data flow and state management approach.

### Evaluation Criteria
- **Functionality**: The solution works as intended, with proper CRUD operations for forms, sections, and questions.
- **Code Quality**: Clean, readable, and maintainable code.
- **Design**: User-friendly and responsive UI design.
- **Usage of Libraries**: Effective use of `react-table` and `DndKit`.
- **TypeScript Usage**: Proper use of TypeScript for type safety.
- **Documentation**: Clear instructions and well-documented code.

Good luck, and we look forward to reviewing your submission!
