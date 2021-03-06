# InsuranceQuestionnaireAnalysis

Among the various available insurance type I have selected **Employee Compensation** in order to carry this analysis. Employee compensation refers to the benefits (cash, vacation, etc.) that an employee receives in exchange for the service they provide to their employer.

I have selected two real carriers and went through their questions to get a quote. For the ease of discussion we call then **Carrier A** and **Carrier B**

## Assumptions

Following assumptions has been made when collecting questions for carrier and analyzing them.

1. 'Software Development' is the business that needs Employee Compensation product.

2. The data types for the questions are same or at least can be converted to similar representation.
   eg: Business Start date takes Datetime in one case and Drop down menu with values started last year, started 2 years ago, started 3 years ago, started 4 years ago, started 5 or more years ago. In both case we can get a count for total number of years.

3. Any question should fall into a category, eg: Business Information, Contact Information, Operations etc.

## Methodology

1. Choosing 'Software Development' as the business that needs Employee Compensation, went through all the questions asked by the carrier to receive a suitable quote for my assumed business. (see sheet 'Collected Questions' in assignment.xlsx)

2. After collecting questions from the two carriers, manually went through the questions to find those questions with difference in phrasings, but similarity in implication of info being assessed. (see sheet 'Question Analysis' in assignment.xlsx)

3. Categorized the questions into the given categories (see sheet 'Question Analysis' in assignment.xlsx)
   -Company Information
   -Business Details
   -Location
   -Contact Information
   -Operations

4. Collected the choice type for the similar questions.
5. Created Embeded json to represent the similar questions.

## Findings

1. For a few sample questions and a number of carriers, manual intervention seems effective
   since it results in the least number of false positives.
2. In case of huge number of questions and similar number of carrier, a manual approach does
   not seem feasible. A probable solution would be rueducing the manual work by using Machine Learning for string comparison.

## Embeded JSON

This has also been provided as a file as embededJson.json.

```json
{
  "Q-001": {
    "question_id": "IndustryType",
    "category": "Company Information",
    "question_description": "the kind of the business you want to insure.",
    "carriers": [
      {
        "carrier_id": "CID-001",
        "carrier_name": "Carrier A",
        "carrier_query": "What's your industry?",
        "choice_type": "DropDown",
        "conditions_remarks": []
      },
      {
        "carrier_id": "CID-002",
        "carrier_name": "Carrier B",
        "carrier_query": "What kind of work do you do?",
        "choice_type": "DropDown",
        "conditions_remarks": []
      }
    ]
  },
  "Q-002": {
    "question_id": "EmployeeCount",
    "category": "Business Details",
    "question_description": "number of employees that needs to be insured.",
    "carriers": [
      {
        "carrier_id": "CID-001",
        "carrier_name": "Carrier A",
        "carrier_query": "How many employees do you have?",
        "choice_type": "Integer",
        "conditions_remarks": [
          "Include both part-time and full-time employees in your response. Exclude business owners and officers."
        ]
      },
      {
        "carrier_id": "CID-002",
        "carrier_name": "Carrier B",
        "carrier_query": "Number of employees?",
        "choice_type": "Integer",
        "conditions_remarks": ["Not including owners and officers."]
      }
    ]
  },
  "Q-003": {
    "question_id": "IndustryLocation",
    "category": "Location",
    "question_description": "the location of your business/Industry.",
    "carriers": [
      {
        "carrier_id": "CID-001",
        "carrier_name": "Carrier A",
        "carrier_query": "Where is your business located?",
        "choice_type": "string",
        "conditions_remarks": []
      },
      {
        "carrier_id": "CID-002",
        "carrier_name": "Carrier B",
        "carrier_query": "Business Location: City, State?",
        "choice_type": "DropDown",
        "conditions_remarks": ["choices based on zip code provided"]
      }
    ]
  },
  "Q-004": {
    "question_id": "BusinessStructure",
    "category": "Business Details",
    "question_description": "the structure of your business/Industry.",
    "carriers": [
      {
        "carrier_id": "CID-001",
        "carrier_name": "Carrier A",
        "carrier_query": "How is your business structured?",
        "choice_type": "DropDown",
        "conditions_remarks": [
          "Corporation, Partnership, Individual/Sole Proprietor, Sub-Chapter Corp"
        ]
      },
      {
        "carrier_id": "CID-002",
        "carrier_name": "Carrier B",
        "carrier_query": "How is your business registered?",
        "choice_type": "DropDown",
        "conditions_remarks": [
          "Corporation, Individual, Joint Venture, LLC, Partnership, Limited Partnership, S Corporation"
        ]
      }
    ]
  },
  "Q-005": {
    "question_id": "FirstName",
    "category": "Contact Information",
    "question_description": "the first name of company owner insured.",
    "carriers": [
      {
        "carrier_id": "CID-001",
        "carrier_name": "Carrier A",
        "carrier_query": "Insured first name",
        "choice_type": "String",
        "conditions_remarks": []
      },
      {
        "carrier_id": "CID-002",
        "carrier_name": "Carrier B",
        "carrier_query": "Owner's first name",
        "choice_type": "String",
        "conditions_remarks": []
      }
    ]
  },
  "Q-006": {
    "question_id": "LastName",
    "category": "Contact Information",
    "question_description": "the last name of company owner insured.",
    "carriers": [
      {
        "carrier_id": "CID-001",
        "carrier_name": "Carrier A",
        "carrier_query": "Insured last name",
        "choice_type": "String",
        "conditions_remarks": []
      },
      {
        "carrier_id": "CID-002",
        "carrier_name": "Carrier B",
        "carrier_query": "Owner's last name",
        "choice_type": "String",
        "conditions_remarks": []
      }
    ]
  },
  "Q-007": {
    "question_id": "CompanyName",
    "category": "Company Information",
    "question_description": "name of company.",
    "carriers": [
      {
        "carrier_id": "CID-001",
        "carrier_name": "Carrier A",
        "carrier_query": "Doing business as",
        "choice_type": "String",
        "conditions_remarks": []
      },
      {
        "carrier_id": "CID-002",
        "carrier_name": "Carrier B",
        "carrier_query": "What is the name of your business? ",
        "choice_type": "String",
        "conditions_remarks": ["Include DBA if present"]
      }
    ]
  },
  "Q-008": {
    "question_id": "Email",
    "category": "Contact Information",
    "question_description": "the email of company owner insured.",
    "carriers": [
      {
        "carrier_id": "CID-001",
        "carrier_name": "Carrier A",
        "carrier_query": "Contact email",
        "choice_type": "String",
        "conditions_remarks": []
      },
      {
        "carrier_id": "CID-002",
        "carrier_name": "Carrier B",
        "carrier_query": "Email",
        "choice_type": "String",
        "conditions_remarks": []
      }
    ]
  },
  "Q-009": {
    "question_id": "ContactNumber",
    "category": "Contact Information",
    "question_description": "the email of company owner insured.",
    "carriers": [
      {
        "carrier_id": "CID-001",
        "carrier_name": "Carrier A",
        "carrier_query": "Contact phone",
        "choice_type": "String",
        "conditions_remarks": []
      },
      {
        "carrier_id": "CID-002",
        "carrier_name": "Carrier B",
        "carrier_query": "Phone number",
        "choice_type": "String",
        "conditions_remarks": []
      }
    ]
  },
  "Q-010": {
    "question_id": "BusinessRunTime",
    "category": "Business Details",
    "question_description": "the number of years business has been running.",
    "carriers": [
      {
        "carrier_id": "CID-001",
        "carrier_name": "Carrier A",
        "carrier_query": "When did you start your business?",
        "choice_type": "DatePicker",
        "conditions_remarks": []
      },
      {
        "carrier_id": "CID-002",
        "carrier_name": "Carrier B",
        "carrier_query": "What date did your business begin under current ownership?",
        "choice_type": "DropDown",
        "conditions_remarks": [
          "Started last year, Started 2 years ago, started 3 years ago, started 4 years ago, started 5 years ago, started 6 years ago, started 7 years ago, started 8 years ago, started 9 years ago, started 10 or more years ago"
        ]
      }
    ]
  },
  "Q-011": {
    "question_id": "ClaimsMade",
    "category": "Operations",
    "question_description": "if any claims have been made.",
    "carriers": [
      {
        "carrier_id": "CID-001",
        "carrier_name": "Carrier A",
        "carrier_query": "In the past 3 years were any Workers' Compensation claims reported?",
        "choice_type": "Yes/No",
        "conditions_remarks": []
      },
      {
        "carrier_id": "CID-002",
        "carrier_name": "Carrier B",
        "carrier_query": "Has your company had any claims in the past 5 years?",
        "choice_type": "Yes/No",
        "conditions_remarks": []
      }
    ]
  },
  "Q-012": {
    "question_id": "HiredEmployee",
    "category": "Operations",
    "question_description": "if any temporary employees are hired",
    "carriers": [
      {
        "carrier_id": "CID-001",
        "carrier_name": "Carrier A",
        "carrier_query": "Do you use any volunteers or donated labor?",
        "choice_type": "Yes/No",
        "conditions_remarks": []
      },
      {
        "carrier_id": "CID-002",
        "carrier_name": "Carrier B",
        "carrier_query": "Do you hire other labor beside your employee?",
        "choice_type": "Yes/No",
        "conditions_remarks": []
      }
    ]
  },
  "Q-013": {
    "question_id": "HaveBranches",
    "category": "Operations",
    "question_description": "if any branches are affiliated",
    "carriers": [
      {
        "carrier_id": "CID-001",
        "carrier_name": "Carrier A",
        "carrier_query": "Do you have multiple locations in more than one state?",
        "choice_type": "Yes/No",
        "conditions_remarks": []
      },
      {
        "carrier_id": "CID-002",
        "carrier_name": "Carrier B",
        "carrier_query": "Do you have 2 or more branches?",
        "choice_type": "Yes/No",
        "conditions_remarks": []
      }
    ]
  }
}
```
