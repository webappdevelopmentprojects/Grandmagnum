<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Employee Data Form</title>
    <style>
            
        .hidden { display: none; }
        .center { text-align: center; }
        .next-button, .prev-button {
            position: fixed;
            bottom: 20px;
        }
        .next-button {
            right: 20px;
        }
        .prev-button {
            left: 20px;
        }
        #photo_preview {
            display: block;
            margin: 10px auto;
            max-width: 150px;
            max-height: 150px;
        }



        /* Adding colors and font styles */
        body { 
            font-family: 'Arial', sans-serif; 
            color: #333; 
            background-color: #f4f4f4; /* Light grey background for the body */
        }
        h1 { color: #004080; } /* Dark blue for headers */
        table { 
            width: 100%; 
            border-collapse: collapse; 
            background-color: #ffffff; /* White background for the table */
        }
        th {
            background-color: #004080; /* Dark blue background for table headers */
            color: white; /* White text for table headers */
            font-weight: bold; /* Bold text for table headers */
            padding: 10px;
        }
        td, th { 
            padding: 10px; 
            border: 1px solid #ddd; 
        }
        tr:nth-child(even) { background-color: #f9f9f9; } /* Alternating row colors */
        input[type="text"], input[type="date"], input[type="email"], input[type="tel"], textarea, select {
            border: 1px solid #ddd; 
            padding: 8px; 
            width: 100%;
            box-sizing: border-box;
        }
        .button {
            background-color: #004080; /* Dark blue background */
            color: white; /* White text */
            border: none;
            padding: 10px 20px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 16px;
            margin: 4px 2px;
            cursor: pointer;
        }
        .button:hover { background-color: #003366; } /* Darker blue on hover */


        
    </style>
    <script>
        function copyAddress() {
            if (document.getElementById('same_address').checked) {
                document.getElementById('permanent_address').value = document.getElementById('present_address').value;
            } else {
                document.getElementById('permanent_address').value = '';
            }
        }

        function showSection(sectionId) {
            const sections = document.querySelectorAll('.section');
            sections.forEach(section => section.classList.add('hidden'));
            document.getElementById(sectionId).classList.remove('hidden');
        }

        function toggleRelativesSection() {
            const relativesSection = document.getElementById('relative_section');
            relativesSection.classList.toggle('hidden');
        }

        function toggleCourtSection() {
            const courtSection = document.getElementById('court_section');
            courtSection.classList.toggle('hidden');
        }

        function togglePendingcaseSection() {
            const pendingcaseSection = document.getElementById('pendingcase_section');
            pendingcaseSection.classList.toggle('hidden');
        }

        function toggleMedicalillnessSection() {
            const medicalIllnessSection = document.getElementById('medical_illness_section');
            medicalIllnessSection.classList.toggle('hidden');
        }  

        function previewPhoto() {
            const fileInput = document.getElementById('photo_upload');
            const preview = document.getElementById('photo_preview');
            const file = fileInput.files[0];
            const reader = new FileReader();

            reader.onloadend = function() {
                preview.src = reader.result;
            }

            if (file) {
                reader.readAsDataURL(file);
            } else {
                preview.src = "";
            }
        }

        function updateDesignation() {
            const department = document.getElementById('department').value;
            const designationDropdown = document.getElementById('designation');
            let designation = [];

            switch (department) {
                case 'Legal':
                    designation = ['Legal Head', 'Advocate', 'Executive', 'Sr.Executive', 'Assistant', 'Asst.Manager'];
                    break;
                case 'Accounts':
                    designation = ['Asst Manager', 'CFO', 'Manager', 'Executive', 'Sr.Executive', 'Manager'];
                    break;
                case 'HR':
                    designation = ['HR Manager', 'Recruiter', 'HR Executive'];
                    break;
                case 'Admin':
                    designation = ['OA', 'Executive'];
                    break;
                case 'B2B Operations':
                    designation = ['Executive', 'Sr.Executive'];
                    break;
                case 'CADD':
                    designation = ['Draftsman'];
                    break;
                case 'CRM':
                    designation = ['Asst.Manager', 'Manager'];
                    break;
                case 'Digital Marketing':
                    designation = ['Manager', 'Sr.Manager', 'Content Writer'];
                    break;
                case 'Executive Management':
                    designation = ['Chief Strategic Officer'];
                    break;
                case 'Graphics Designer':
                    designation = ['Designer'];
                    break;
                case 'B2B Sales':
                    designation =['Manager','Sr.Manager','Executive','Sr.Executive'];
                    break;
                case 'B2B Operation':
                    designation=['Manager','Sr.Manager',"Executive',Sr.Executive"];
                    break;
                case 'IT':
                    designation = ['System Administrator'];
                    break;
                case 'Marketing':
                    designation = ['Executive', 'Sr.Executive', 'Manager', 'Sr.Manager'];
                    break;
                case 'Operations':
                    designation = ['VP', 'Manager', 'Graphic Designer', 'Executive', 'Lead-MIS', 'Sales Coordinator'];
                    break;
                case 'Presales':
                    designation = ['Executive', 'Sr.Executive', 'Team Leader'];
                    break;
                case 'R&D':
                    designation = ['Data Analyst', 'Sr.Data Analyst'];
                    break;
                case 'Sales':
                    designation = ['Executive', 'Sr.Executive', 'Asst.Manager', 'Manager', 'General Manager'];
                    break;
                case 'Secretariat':
                    designation = ['Executive Assistant', 'Sr.Executive', 'Manager', 'Sr.Manager'];
                    break;
            }

            designationDropdown.innerHTML = ''; // Clear previous options
            designation.forEach(function(designation) {
                const option = document.createElement('option');
                option.value = designation;
                option.text = designation;
                designationDropdown.add(option);
            });
        }
    </script>
</head>
<body>
    <form action="https://script.google.com/macros/s/AKfycbxjTZinXoDb5HvWNfQ_Bihq6aJpSO6cV347Vr6pICXdIIcJ8lkuYvKf0HflaxSuNwuO/exec" method="post" enctype="multipart/form-data">
        <!-- Section 1: Personal Details -->
        <div id="section1" class="section">
            <h1 class="center">GRAND MAGNUM HOUSING PVT LTD</h1>
            <table border="1">
                <tr>
                    <td>Emp ID:</td>
                    <td><input type="text" name="emp_id"></td>
                    <td>Date of Joining:</td>
                    <td><input type="date" name="date_of_joining"></td>
                    <td rowspan="3">
                        <input type="file" id="photo_upload" name="photo_upload" accept="image/*" onchange="previewPhoto()" >
                        <img id="photo_preview" src="#" alt="Photo Preview" />
                    </td>
                </tr>
                <tr>
                    <td>Department:</td>
                    <td>
                        <select id="department" name="department" required onchange="updateDesignation()">
                            <option value="">Select</option>
                            <option value="HR">HR</option>
                            <option value="Accounts">Accounts</option>
                            <option value="Graphics Designer">Graphics Designer</option>
                            <option value="Marketing">Marketing</option>
                            <option value="Legal">Legal</option>
                            <option value="B2B Sales">B2B Sales</option>
                            <option value="B2B Operation">B2B Operation</option>
                            <option value="Presales">Presales</option>
                            <option value="Sales">Sales</option>
                            <option value="CADD">CADD</option>
                            <option value="Admin">Admin</option>
                            <option value="Operations">Operations</option>
                            <option value="CRM">CRM</option>
                            <option value="EA">EA</option>
                            <option value="R&D">R&D</option>
                            <option value="IT">IT</option>
                            <option value="Secretariat">Secretariat</option>
                            <option value="Executive Management">Executive Management</option>
                            <option value="Digital Marketing">Digital Marketing</option>
                        </select>
                    </td>
                    <<td>Designation:</td>
                    <td>
                        <select id="designation" name="designation" required>
                            <option value="">Select</option>
                            <!-- Options will be dynamically populated based on the department -->
                        </select>
                    </td>

                </tr>

                <tr>
                    <td>Location:</td>
                    <td colspan="1">
                        <select name="location" required>
                            <option value="">Select</option>
                            <option value="Chennai Anna Nagar">Chennai Anna Nagar</option>
                            <option value="Chennai Egmore">Chennai Egmore</option>
                        </select>
                    </td>
                    <td>Employment Type:</td>
                    <td col="2",row="3">
                        <select name="employment_type" required>
                            <option value="">Select</option>
                            <option value="Full_Time">Full_Time</option>
                            <option value="Contracted">Contracted</option>
                            <option value="Consultancy">Consultancy</option>
                        </select>
                    </td>
                </tr>
            </table>
            <br><br>


            <table border="1" style="width: 100%;">
                <tr>
                    <th colspan="4" style="text-align: center;">PERSONAL DETAILS</th>
                </tr>
                <tr>
                   <td>Name:</td>
                   <td><input type="text" name="name" maxlength="30" required></td>
                   <td>Mobile Number:</td>
                   <td><input type="tel" name="mobile_number" maxlength="10" required></td>
                </tr>
                <tr>
                   <td>Gender:</td>
                   <td><input type="radio" name="gender" value="Female" required> Female</td>
                   <td><input type="radio" name="gender" value="Male" required> Male</td>
                   <td><input type="radio" name="gender" value="Others" required> Others</td>    
                </tr>
                <tr>
                    <td>Date of Birth:</td>
                    <td><input type="date" name="date_of_birth" required></td>
                    <td>Email:</td>
                   <td><input type="email" name="email_id" required></td>
                   
                </tr>
                <tr>
                    <td>Marital Status:</td>
                   <td><input type="radio" name="marital_status" value="Married" required>Married</td>
                   <td><input type="radio" name="marital_status" value="Unmarried" required>Unmarried</td>
                   <td><input type="radio" name="marital_status" value="Single" required>Single</td>
                   
                </tr>
                   
                <tr>
                   <td>Blood Group:</td>
                   <td>
                       <select name="blood_group" required>
                           <option value="">Select</option>
                           <option value="A+">A+</option>
                           <option value="A-">A-</option>
                           <option value="B+">B+</option>
                           <option value="B-">B-</option>
                           <option value="O+">O+</option>
                           <option value="O-">O-</option>
                           <option value="AB+">AB+</option>
                           <option value="AB-">AB-</option>
                       </select>
                   </td>
                   <td>Religion:</td>
                   <td>
                        <select name="religion" maxlength="10" required>
                            <option value="">Select</option>
                            <option value="Hinduism">Hinduism</option>
                            <option value="Islam">Islam</option>
                            <option value="Christianity">Christianity</option>
                            <option value="Sikhism">Sikhism</option>
                            <option value="Buddhism">Buddhism</option>
                            <option value="Jainism">Jainism</option>
                            <option value="Other">Other</option>
                        </select>
                    </td>
                </tr>

                <tr>
                   <td>Height:</td>
                   <td><input type="text" name="height" maxlength="3"></td>
                   <td>Weight:</td>
                   <td><input type="text" name="weight" maxlength="3"></td>
                   
                </tr>
                <tr>
                   <td>Identification Mark:</td>
                   <td colspan="3"><textarea name="identification_mark" id="identification_mark" rows="4" cols="50"></textarea></td>
                </tr>
                <tr>
                   <td>Present Address:</td>
                   <td colspan="3"><textarea name="present_address" id="present_address" rows="4" cols="50" required></textarea></td>
                </tr>
                <tr>
                   <td><input type="checkbox" id="same_address" onclick="copyAddress()"> Same as Present Address</td>
                </tr>
                <tr>
                   <td>Permanent Address:</td>
                   <td colspan="3"><textarea name="permanent_address" id="permanent_address" rows="4" cols="50"></textarea></td>
                </tr>
                <tr>
                    <td>State:</td>
                    <td>
                        <select name="state" required>
                            <option value="">Select</option>
                            <option value="Andra Pradesh">Andra Pradesh
                            <option value="Arunachal Pradesh">Arunachal Pradesh
                            <option value="Assam">Assam
                            <option value="Bihar">Bihar
                            <option value="Chhattisgarh">Chhattisgarh
                            <option value="Delhi">Delhi
                            <option value="Goa">Goa
                            <option value="Gujarat">Gujarat
                            <option value="Haryana">Haryana
                            <option value="Himachal Pradesh">Himachal Pradesh
                            <option value="Jammu and Kashmir">Jammu and Kashmir
                            <option value="Jharkhand">Jharkhand
                            <option value="Karnataka">Karnataka
                            <option value="Kerala">Kerala
                            <option value="Maharashtra">Maharashtra
                            <option value="Madhya Pradesh">Madhya Pradesh
                            <option value="Manipur">Manipur
                            <option value="Meghalaya">Meghalaya
                            <option value="Mizoram">Mizoram
                            <option value="Nagalan">Nagaland
                            <option value="Odisha">Odisha
                            <option value="Punjab">Punjab
                            <option value="Rajasthan">Rajasthan
                            <option value="Sikkim">Sikkim
                            <option value="Tamil Nadu">Tamil Nadu
                            <option value="Tripura">Tripura
                            <option value="Telangana">Telangana
                            <option value="Uttar Pradesh">Uttar Pradesh
                            <option value="Uttarkhand">Uttrakhand
                            <option value="West Bengal">West Bengal
                        </select>
                    </td>
                    <td>Pincode:</td>
                    <td><input type="text" name="pincode" maxlength="6"required></td>
                </tr>        
            </table>
            <br><br>
            <table border="1" style="width: 100%;">
                <tr>
                    <th colspan="4" style="text-align: center;">EMERGENCY DETAILS</th>
                </tr>
                <tr>
                    <th>Name</th>
                    <th>Relationship</th>
                    <th>Contact Number</th>
                    <th>Address</th>
                </tr>
                
                <tr>
                    <td><input type="text" name="emergency_name_1" required></td>
                    <td><input type="text" name="emergency_relationship_1" maxlength="15" required></td>
                    <td><input type="tel" name="emergency_contact_1" maxlength="10" required></td>
                    <td><input type="text" name="emergency_address_1"></td>
                </tr>
		<tr>
                    <td><input type="text" name="emergency_name_2" required></td>
                    <td><input type="text" name="emergency_relationship_2" maxlength="15" required></td>
                    <td><input type="tel" name="emergency_contact_2" maxlength="10" required></td>
                    <td><input type="text" name="emergency_address_2"></td>
                </tr>
                
            </table>
            <br><br>
            <table border="1" style="width: 100%;">
                <tr>
                    <th colspan="5" style="text-align: center;">FAMILY DETAILS</th>
                </tr>
                <tr>
                    <th>Name</th>
                    <th>Date of Birth</th>
                    <th>Relationship</th>
                    <th>Occupation</th>
                    <th>Monthly Income</th>
                </tr>
                
                <tr>
                    <td><input type="text" name="family_name_1" maxlength="30" required></td>
                    <td><input type="date" name="family_dob_1"></td>
                    <td>
                        <select name="family_relationship_1" required>
                           <option value="">Select</option>
                           <option value="Father">Father</option>
                           <option value="Mother">Mother</option>
                           <option value="Spouse">Spouse</option>
                           <option value="Sister">Sister</option>
                           <option value="Brother">Brother</option>
                           <option value="Daughter">Daughter</option>
                           <option value="Son">Son</option>
                        </select>
                    </td>
                    <td>
                       <select name="family_occupation_1" required>
                           <option value="">Select</option>
                           <option value="Private">Private</option>
                           <option value="Government">Government</option>
                           <option value="Self Employed">Self Government</option>
                           <option value="Business">Business</option>
                           <option value="Homemaker">Homemaker</option>
                        </select>
                    </td>
                           
                    <td><input type="number" name="family_income_1"></td>
                </tr>
                


		<tr>
                    <td><input type="text" name="family_name_2" maxlength="30" required></td>
                    <td><input type="date" name="family_dob_2"></td>
                    <td>
                        <select name="family_relationship_2" required>
                           <option value="">Select</option>
                           <option value="Father">Father</option>
                           <option value="Mother">Mother</option>
                           <option value="Spouse">Spouse</option>
                           <option value="Sister">Sister</option>
                           <option value="Brother">Brother</option>
                           <option value="Daughter">Daughter</option>
                           <option value="Son">Son</option>
                        </select>
                    </td>
                    <td>
                       <select name="family_occupation_2" required>
                           <option value="">Select</option>
                           <option value="Private">Private</option>
                           <option value="Government">Government</option>
                           <option value="Self Employed">Self Government</option>
                           <option value="Business">Business</option>
                           <option value="Homemaker">Homemaker</option>
                        </select>
                    </td>
                           
                    <td><input type="number" name="family_income_2"></td>
                </tr>


		<tr>
                    <td><input type="text" name="family_name_3" maxlength="30"></td>
                    <td><input type="date" name="family_dob_3"></td>
                    <td>
                        <select name="family_relationship_3" >
                           <option value="">Select</option>
                           <option value="Father">Father</option>
                           <option value="Mother">Mother</option>
                           <option value="Spouse">Spouse</option>
                           <option value="Sister">Sister</option>
                           <option value="Brother">Brother</option>
                           <option value="Daughter">Daughter</option>
                           <option value="Son">Son</option>
                        </select>
                    </td>
                    <td>
                       <select name="family_occupation_3" >
                           <option value="">Select</option>
                           <option value="Private">Private</option>
                           <option value="Government">Government</option>
                           <option value="Self Employed">Self Government</option>
                           <option value="Business">Business</option>
                           <option value="Homemaker">Homemaker</option>
                        </select>
                    </td>
                           
                    <td><input type="number" name="family_income_3"></td>
                </tr>
		<tr>
                    <td><input type="text" name="family_name_4" maxlength="30"></td>
                    <td><input type="date" name="family_dob_4"></td>
                    <td>
                        <select name="family_relationship_4" >
                           <option value="">Select</option>
                           <option value="Father">Father</option>
                           <option value="Mother">Mother</option>
                           <option value="Spouse">Spouse</option>
                           <option value="Sister">Sister</option>
                           <option value="Brother">Brother</option>
                           <option value="Daughter">Daughter</option>
                           <option value="Son">Son</option>
                        </select>
                    </td>
                    <td>
                       <select name="family_occupation_4" >
                           <option value="">Select</option>
                           <option value="Private">Private</option>
                           <option value="Government">Government</option>
                           <option value="Self Employed">Self Government</option>
                           <option value="Business">Business</option>
                           <option value="Homemaker">Homemaker</option>
                        </select>
                    </td>
                           
                    <td><input type="number" name="family_income_4"></td>
                </tr>


		<tr>
                    <td><input type="text" name="family_name_5" maxlength="30"></td>
                    <td><input type="date" name="family_dob_5"></td>
                    <td>
                        <select name="family_relationship_5" >
                           <option value="">Select</option>
                           <option value="Father">Father</option>
                           <option value="Mother">Mother</option>
                           <option value="Spouse">Spouse</option>
                           <option value="Sister">Sister</option>
                           <option value="Brother">Brother</option>
                           <option value="Daughter">Daughter</option>
                           <option value="Son">Son</option>
                        </select>
                    </td>
                    <td>
                       <select name="family_occupation_5" >
                           <option value="">Select</option>
                           <option value="Private">Private</option>
                           <option value="Government">Government</option>
                           <option value="Self Employed">Self Government</option>
                           <option value="Business">Business</option>
                           <option value="Homemaker">Homemaker</option>
                        </select>
                    </td>
                           
                    <td><input type="number" name="family_income_5"></td>
                </tr>
		<tr>
                    <td><input type="text" name="family_name_6" maxlength="30"></td>
                    <td><input type="date" name="family_dob_6"></td>
                    <td>
                        <select name="family_relationship_6" >
                           <option value="">Select</option>
                           <option value="Father">Father</option>
                           <option value="Mother">Mother</option>
                           <option value="Spouse">Spouse</option>
                           <option value="Sister">Sister</option>
                           <option value="Brother">Brother</option>
                           <option value="Daughter">Daughter</option>
                           <option value="Son">Son</option>
                        </select>
                    </td>
                    <td>
                       <select name="family_occupation_6" >
                           <option value="">Select</option>
                           <option value="Private">Private</option>
                           <option value="Government">Government</option>
                           <option value="Self Employed">Self Government</option>
                           <option value="Business">Business</option>
                           <option value="Homemaker">Homemaker</option>
                        </select>
                    </td>
                           
                    <td><input type="number" name="family_income_6"></td>
                </tr>
		
            </table>
            <br><br>
            <table border="1" style="width: 100%;">
                <tr>
                    <th colspan="7" style="text-align: center;">EDUCATION DETAILS</th>
                </tr>
                <tr>
                    <th>Details</th>
                    <th>Std.X</th>
                    <th>Std.XII_Diploma</th>
                    <th>Graduation</th>
                    <th>Post Graduation</th>
                </tr>
                <tr>
                    <th>Degree</th>
                    <td><input type="text" name="degree_x"></td>
                    <td><input type="text" name="degree_xii_diploma"></td>
                    <td><input type="text" name="degree_grad"></td>
                    <td><input type="text" name="degree_pg"></td>
                </tr>
                <tr>
                    <th>Specialization</th>
                    <td><input type="text" name="specialization_x"></td>
                    <td><input type="text" name="specialization_xii_diploma"></td>
                    <td><input type="text" name="specialization_grad"></td>
                    <td><input type="text" name="specialization_pg"></td>
                </tr>
                <tr>
                    <th>Name of Institution</th>
                    <td><input type="text" name="institution_x" required></td>
                    <td><input type="text" name="institution_xii_diploma" ></td>
                    <td><input type="text" name="institution_grad"></td>
                    <td><input type="text" name="institution_pg"></td>
                </tr>
                <tr>
                    <th>Board/University</th>
                    <td><input type="text" name="board_x" required></td>
                    <td><input type="text" name="board_xii_diploma" ></td>
                    <td><input type="text" name="board_grad"></td>
                    <td><input type="text" name="board_pg"></td>
                </tr>
                <tr>
                    <th>Year of Passing</th>
                    <td><input type="date" name="year_x" required</td>
                    <td><input type="date" name="year_xii_diploma"</td>
                    <td><input type="date" name="year_grad" </td>
                    <td><input type="date" name="year_pg" </td>
                </tr>
                <tr>
                    <th>Percentage</th>
                    <td><input type="text" name="percentage_x" maxlength="3" required></td>
                    <td><input type="text" name="percentage_xii_diploma" maxlength="3" ></td>
                    <td><input type="text" name="percentage_grad" maxlength="3"></td>
                    <td><input type="text" name="percentage_pg" maxlength="3"></td>
                </tr>
            </table>
            <br><br>
            

       
            <table border="1" style="width: 100%;">
                <tr>
                    <th colspan="6" style="text-align: center;">EMPLOYMENT DETAILS</th>
                </tr>
                <tr>
                    <th>Organization Name</th>
                    <th>From</th>
                    <th>To</th>
                    <th>Designation</th>
                    <th>Last Salary Drawn per month</th>
                    <th>Reason for Leaving</th>
                </tr>
                
                <tr>
                    <td><input type="text" name="org_name_1"></td>
                    <td><input type="date" name="from_date_1"></td>
                    <td><input type="date" name="to_date_1"></td>
                    <td><input type="text" name="designation_1" maxlength="30"></td>
                    <td><input type="text" name="last_salary_1" maxlength="10"></td>
                    <td><textarea name="reason_leaving_1" rows="2" cols="20"></textarea></td>
                </tr>
		<tr>
                    <td><input type="text" name="org_name_2"></td>
                    <td><input type="date" name="from_date_2"></td>
                    <td><input type="date" name="to_date_2"></td>
                    <td><input type="text" name="designation_2" maxlength="30"></td>
                    <td><input type="text" name="last_salary_2" maxlength="10"></td>
                    <td><textarea name="reason_leaving_2" rows="2" cols="20"></textarea></td>
                </tr>
		<tr>
                    <td><input type="text" name="org_name_3"></td>
                    <td><input type="date" name="from_date_3"></td>
                    <td><input type="date" name="to_date_3"></td>
                    <td><input type="text" name="designation_3" maxlength="30"></td>
                    <td><input type="text" name="last_salary_3" maxlength="10"></td>
                    <td><textarea name="reason_leaving_3" rows="2" cols="20"></textarea></td>
                </tr>
		<tr>
                    <td><input type="text" name="org_name_4"></td>
                    <td><input type="date" name="from_date_4"></td>
                    <td><input type="date" name="to_date_4"></td>
                    <td><input type="text" name="designation_4" maxlength="30"></td>
                    <td><input type="text" name="last_salary_4" maxlength="10"></td>
                    <td><textarea name="reason_leaving_4" rows="2" cols="20"></textarea></td>
                </tr>
		<tr>
                    <td><input type="text" name="org_name_5"></td>
                    <td><input type="date" name="from_date_5"></td>
                    <td><input type="date" name="to_date_5"></td>
                    <td><input type="text" name="designation_5" maxlength="30"></td>
                    <td><input type="text" name="last_salary_5" maxlength="10"></td>
                    <td><textarea name="reason_leaving_5" rows="2" cols="20"></textarea></td>
                </tr>

                
            </table>
            <br><br>
            <div class="center">
                <button type="button" class="next-button" onclick="showSection('section2')">Next</button>
            </div>
        </div>

       

        <!-- Section 2: Other Details -->
        <div id="section2" class="section hidden">
            <h1 class="center">GRAND MAGNUM HOUSING PVT LTD</h1>
            <table border="1" style="width: 100%;">
                <tr>
                    <th colspan="4" style="text-align: center;">OTHER DETAILS</th>
                </tr>
            <table border="1" style="width: 100%;">
                <tr>
                    <td>Is any of your relative working in our organization?</td>
                    <td>
                        <input type="radio" name="relative_working" value="yes" onclick="toggleRelativesSection()"> Yes
                        <input type="radio" name="relative_working" value="no" onclick="toggleRelativesSection()"> No
                    </td>
                </tr>
                <tr id="relative_section" class="hidden">
                    <td>If Yes, give details:</td>
                    <td><textarea name="relative_details" rows="4" cols="50"></textarea></td>
                </tr>
                <tr>
                    <td>Were you ever involved in any criminal proceedings?</td>
                    <td>
                        <input type="radio" name="criminal_proceedings" value="yes" onclick="toggleCourtSection()"> Yes
                        <input type="radio" name="criminal_proceedings" value="no" onclick="toggleCourtSection()"> No
                    </td>
                </tr>
                <tr id="court_section" class="hidden">
                    <td>If Yes, give details:</td>
                    <td><textarea name="criminal_details" rows="4" cols="50"></textarea></td>
                </tr>
                <tr>
                    <td>Is any case pending against you in any court of law?</td>
                    <td>
                        <input type="radio" name="pending_case" value="yes" onclick="togglePendingcaseSection()"> Yes
                        <input type="radio" name="pending_case" value="no" onclick="togglePendingcaseSection()"> No
                    </td>
                </tr>
                <tr id="pendingcase_section" class="hidden">
                    <td>If Yes, give details:</td>
                    <td><textarea name="pending_case_details" rows="4" cols="50"></textarea></td>
                </tr>
                <tr>
                    <td>Any major illness in the past?</td>
                    <td>
                        <input type="radio" name="major_illness" value="yes" onclick="toggleMedicalillnessSection()"> Yes
                        <input type="radio" name="major_illness" value="no" onclick="toggleMedicalillnessSection()"> No
                    </td>
                </tr>
                <tr id="medical_illness_section" class="hidden">
                    <td>If Yes, give details:</td>
                    <td><textarea name="major_illness_details" rows="4" cols="50"></textarea></td>
                </tr>
                <tr>
                    <td>Languages Known:</td>
                    <td>
                        <input type="checkbox" name="language_known_t" value="tamil"> Tamil
                        <input type="checkbox" name="language_known_e" value="english"> English
                        <input type="checkbox" name="language_known_h" value="hindi"> Hindi
                        <input type="checkbox" name="language_known_o" value="other"> Others
                    </td>
                </tr>
                
            </table>
            <br><br>
            <table border="1" style="width: 100%;">
                <tr>
                    <th colspan="4" style="text-align: center;">REFERENCES</th>
                </tr>
                <tr>
                    <th>Name</th>
                    <th>Organisation Name & Address</th>
                    <th>Designation</th>
                    <th>Contact Details</th>
                </tr>
                
                <tr>
                    <td><input type="text" name="reference_name_1" required></td>
                    <td><input type="text" name="reference_organisation_1"></td>
                    <td><input type="text" name="reference_designation_1"></td>
                    <td><input type="number" name="reference_contact_1" required></td>
                </tr>
		<tr>
                    <td><input type="text" name="reference_name_2" required></td>
                    <td><input type="text" name="reference_organisation_2"></td>
                    <td><input type="text" name="reference_designation_2"></td>
                    <td><input type="number" name="reference_contact_2" required></td>
                </tr>
                
            </table>
            <br><br>
            
            
            <table border="1" style="width: 100%;">
                <tr>
                    <th colspan="4" style="text-align:center:">STATUTORY DETAILS</th>
                </tr>
                <tr>
                    <th>PAN No.</th>
                    <th>Aadhar No.</th>
                    <th>ESIC No.</th>
                    <th>UAN No.</th>
                    
                </tr>
                
                <tr>
                    <td><input type="text" name="pan_no" required></td>
                    <td><input type="text" name="aadhar_no" required></td>
                    <td><input type="text" name="esic_no"></td>
                    <td><input type="text" name="uan_no"></td>
                    
                </tr>
                
            </table>
            <br><br>

            
            <table border="1" style="width: 100%;">
                <tr>
                    <th colspan="5" style="text-align: center;">BANK DETAILS</th>
                </tr>
                <tr>
                    <th>Bank Account No.</th>
                    <th>Bank Name</th>
                    <th>Bank Account HolderName</th>
                    <th>Branch</th>
                    <th>IFSC code</th>
                    
                </tr>
                
                <tr>
                    <td><input type="number" name="account_number" required></td>
                    <td><input type="text" name="bank_name" required></td>
                    <td><input type="text" name="bankaccount_holder_name" required></td>
                    <td><input type="text" name="branch" required></td>
                    <td><input type="text" name="ifsc_code" required></td>
                </tr>
                
            </table>
            <br><br>
            <table border="1" style="width: 100%;">
                <tr>
                    <th colspan="5" style="text-align: center;">DECLARATION</th>
                </tr>
                <tr>
                    <td colspan="5">
                        <p>I declare that all the information provided in this form is true and correct to the best of my knowledge and belief. I understand that any false information or misrepresentation will disqualify me from employment and may result in legal action against me.</p>
                    </td>
                </tr>
            </table>
            <br><br>
            <table border="1" style="width: 100%;">
                <tr>
                    <td>Signature:</td>
                    <td><input type="text" name="signature" required></td>
                    <td>Date:</td>
                    <td><input type="date" name="date" required></td>
                </tr>
            </table>
            <br><br>
            <div class="center">
                <button type="button" class="prev-button" onclick="showSection('section1')">Previous</button>
                <button type="submit">Submit</button>
            </div>   
        </div>
            

        
    </form>
</body>
</html>
