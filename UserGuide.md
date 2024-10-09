# How to Use the New Features

#BELOW IS A TEMPLATE PLS DELETE BEFORE SUBMISSION.

## User Story #:

### 1. Feature Overview
- **Feature Name**: [Name of the feature]
- **Purpose**: Brief description of what the feature does and why it's useful.
- **Coder**: Name of coder

### 2. Steps to Use the Feature
1. **Step 1**: Describe the first step the user needs to take.
2. **Step 2**: Detail the next step in using the feature.
3. **Step 3**: Continue explaining until the user can fully utilize the feature.
4. **Expected Result**: Describe what the user should see or experience after using the feature.

### Automated Tests

### 1. Location of Automated Tests
- **Location**: Provide a link or description of where the automated tests can be found (e.g., repository path or test suite).

### 2. What is Being Tested
- **Tested Features**: List the specific features or functionalities covered by the tests.
- **Test Type**: Mention if these are unit tests, integration tests, etc.

### 3. Why the Tests Are Sufficient
- **Coverage Justification**: Explain why these tests are sufficient, covering important workflows, edge cases, and error handling.

---

## User Story 1: As a student, I want to be able to create topics anonymously, so that I feel comfortable asking questions without judgment.

### 1. Feature Overview
- **Feature Name**: Anonymous Checkbox for Topic Creation
- **Purpose**: This feature allows students to create topics anonymously, which encourages participation by providing a safe space for users who may feel hesitant or intimidated to ask questions openly. It fosters an inclusive environment within the Q&A system, enhancing student comfort and participation
- **Coder**: Shanting Hou

### 2. Steps to Use the Feature
1. **Step 1**: Navigate to the categories page and click on the Q&A category.
2. **Step 2**: Once in the Q&A category page, click the button to create a new topic.
3. **Step 3**: In the topic creation interface, locate the "Post Anonymously" checkbox.
4. **Step 4**: If you wish to post anonymously, check the "Post Anonymously" checkbox before submitting your topic.
5. **Step 5**: Submit the topic.
<img width="309" alt="Screenshot 2024-09-23 at 3 53 11 PM" src="https://github.com/user-attachments/assets/d9e6f989-b5f2-43f2-9542-acef73ad03f0">
<img width="900" alt="Screenshot 2024-09-17 at 6 31 47 PM" src="https://github.com/user-attachments/assets/ced374cd-8c57-4a50-8d84-380ceab66be2">

7. **Expected Result**:
- The "Post Anonymously" checkbox will appear as an option in the topic creation interface. By default, it will be unchecked.
- If the user chooses to post anonymously by checking the box, the topic will be published without associating the user's profile or icon. Instead, it will display an anonymous user icon.
- Internally, the topic will still be tied to the user, allowing the system to send notifications about responses or interactions with the post, even though it appears anonymous to other users.

### Automated Tests

### 1. Location of Automated Tests
**Location**: Test/topics.js, lines 80-107

### 2. What is Being Tested
- **Tested Features**: The functionality of the "Post Anonymously" checkbox and the behavior of the isAnonymous field in topic creation.
- **Test Type**: Unit tests and back-end tests were implemented to ensure the feature works as intended.

### 3. Why the Tests Are Sufficient
- **Coverage Justification**:
The tests provide comprehensive coverage of the anonymous posting feature, focusing on both typical and edge-case scenarios. The default behavior test ensures that when the "Post Anonymously" checkbox is not selected, the isAnonymous field defaults to false, confirming non-anonymous posting works correctly. The anonymous checkbox test verifies that selecting the checkbox sets isAnonymous to true, ensuring anonymous posts are handled correctly in the back end while maintaining user anonymity in the interface. Additionally, tests ensure back-end data integrity, confirming anonymous posts are linked to users for notifications without revealing their identity publicly. Edge cases like rapidly toggling the checkbox and ensuring consistency across browsers are also covered. Front-end tests were excluded because the focus was on back-end logic and data integrity, with UI behavior verified through manual testing. Since the critical functionality involves handling anonymity in the back end, server-side validation was prioritized.

---

## User Story 2: 

### 1. Feature Overview
- **Feature Name**: 'Mark As Resolved' button in dropdown menu
- **Purpose**: This feature allows users to mark a topic as resolved. Once a topic is resolved, it updates the topic's status both in the backend and the frontend, displaying a "Resolved" badge. This feature improves forum organization by clearly indicating which topics have been addressed, helping users easily identify open issues or questions.
- **Coder**: Amanda Lu

### 2. Steps to Use the Feature
1. **Step 1**: Navigate to the forum topic you want to mark as resolved.
2. **Step 2**: Click on the dropdown menu to reveal additional options.
<img width="235" alt="Screen Shot 2024-10-03 at 17 09 02" src="https://github.com/user-attachments/assets/ab2fb858-0b88-4bd2-859b-f3ae271c0d27">

3. **Step 3**: Click on the "Mark As Resolved" button from the dropdown menu.
4. **Step 4**: Then a card displaying resolve confirmation will appear, user should click on "Yes, Mark As Resolved" button.
<img width="315" alt="Screen Shot 2024-10-03 at 17 14 52" src="https://github.com/user-attachments/assets/be5c8438-8a87-4e63-9677-035bd67f9704">

5. **Expected Result**: The topic will be marked as resolved, and a "Resolved" badge will appear next to the topic title, indicating its status. Additionally, the status will be updated in the backend, and the change will be reflected in the forum interface.
<img width="758" alt="Screen Shot 2024-10-03 at 17 13 24" src="https://github.com/user-attachments/assets/0948218e-d4e4-478a-9b9f-29462c718907">

### Automated Tests

### 1. Location of Automated Tests
- **Location**: File: test/topics.js, Lines: 241-276, 910-932

### 2. What is Being Tested
- **Tested Features**:
   - Default topic as unresolved.
   - Admin(instructor) should be able to mark topic as resolved.
   - Verifies that the topic can be marked as resolved using apiTopics.resolve().
- **Test Type**: Unit tests and backend tests

### 3. Why the Tests Are Sufficient
- **Coverage Justification**:
I believe the tests are sufficient for covering the changes because they address the key behaviors related to the "resolved" field:
- The first test checks that when a topic is initially created, the "resolved" field is undefined. This ensures that no unintended default values are assigned to the field during topic creation, which aligns with the expected functionality.
- The second test verifies that the system correctly allows marking a topic as resolved by setting the "resolved" field to 1. It ensures that the update mechanism works as intended and that the field can be retrieved with the correct value after the change is made.
- The tests in line 910-932 cover both the creation of a new topic and updating its "resolved" status. They validate the core functionality of marking topics as resolved and ensure the changes work end-to-end. The state is checked after the update, confirming correct behavior.

---

## User Story 3:

### 1. Feature Overview
- **Feature Name**: Privacy Toggle for Topic Creation
- **Purpose**: This feature allows students to privately communicate sensitive or personal information to their instructors without exposing it to their peers or the public. It also enhances the purpose of the Q&A forum as it allows students to ask more personalized questions (eg, questions involving code for example, or performance in the course), without it being shown to other students. Without this feature, students would be limited in scope to what kind of questions they can ask and what details they can provide in their posts.
- **Coder**: Guanjie Cheng

### 2. Steps to Use the Feature
1. **Step 1**: Register Two New Users, User A and  User B (these are regular users, not admins)
2. **Step 2**: Login as  User A.
3. **Step 3**: Go to the Q&A category.
4. **Step 4**: Click New Topic.
5. **Step 5**: Fill in Topic title and Topic body
6. **Step 6**: In the top right, next to "Post Anonymously" click the button that is currently an open lock and says "Public". This should toggle the button to be a closed lock icon and say "Private"
   **Expected Result**:
   ![Screenshot 2024-10-09 at 6 11 54 PM](https://github.com/user-attachments/assets/a42866e5-0e09-41d1-bf72-07792a6e6bfa)
8. **Step 7**: Click Submit
9. **Step 8**: Go back to Q&A section and see that the topic is successfully created by User A
   **Expected Result**:
   ![Screenshot 2024-10-09 at 6 13 15 PM](https://github.com/user-attachments/assets/19f97100-3e91-4959-bd44-d71f15358903)
11. **Step 9**: Log out and Log in as User B
12. **Step 10**: Go to the Q&A section and see that there are no topics created, as user B does not have administrative privileges thus unable to see User A's private topic
    **Expected Result**:
    ![Screenshot 2024-10-09 at 6 15 06 PM](https://github.com/user-attachments/assets/2034a618-3579-4d1c-b2ae-6f24365b6879)
13. **Step 11**: Create a Public topic and a Private topic as User B and go back to the Q&A to see both topics.
    **Expected Result**:
    ![Screenshot 2024-10-09 at 6 20 42 PM](https://github.com/user-attachments/assets/112f636b-1614-4819-9387-bed478ba9643)
14. **Step 12**: Log out and Log in as User A and go to the Q&A category. See how User A can only see its own Private topic and User B's public topic and not User B's private topic.
    **Expected Result**:
    ![Screenshot 2024-10-09 at 6 22 28 PM](https://github.com/user-attachments/assets/afde2e49-1669-4dc2-a668-d2f87eddd493)
15. **Step 13**: Log out and log in as an Administrator and go to the Q&A category. See how the administrator can see all topics created. 
    **Expected Result**:
    ![Screenshot 2024-10-09 at 6 23 36 PM](https://github.com/user-attachments/assets/b546ac41-9d31-4898-8101-d923c15fa730)


### Automated Tests

### 1. Location of Automated Tests
- **Location**: The tests can [be found in test/topics.js here](https://github.com/CMU-313/nodebb-f24-the-turtles/blob/838f17a0a9009a5c6f7147dcf44132451641263e/test/topics.js#L269-L332)

### 2. What is Being Tested
- **Tested Features**:
  - Information on if a topic was created as public is accurately reflected in the backend
  - Information on if a topic was created as private is accurately reflected in the backend
  - Filtering of topics based on user privileges.
- **Test Type**: Unit tests. 

### 3. Why the Tests Are Sufficient
- **Coverage Justification**: These tests are ultimately sufficient because they comprehensively cover the core functionality of privacy labeling in topic creation, and privilege-based filtering, which are the features that I included. First, by testing both the default public behavior and the explicit marking of topics as private, I ensure that the system correctly handles all possible paths for topic creation. Also, by validating that the correct privacy information is included in the database, it guarantees that subsequent operations based on this data, such as filtering, will have the correct information passed to them for further operations. The filtering test, which differentiates between admin and non-admin users, ensures that only authorized users can view private topics, verifying that the privilege-based access control works as intended. 


# Author(s)
- **Names**: Shanting Hou, Sofia Reyes Franco, Guanjie Cheng, Amanda Lu
