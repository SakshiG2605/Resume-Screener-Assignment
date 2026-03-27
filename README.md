# Resume-Screener-Assignment

pip install PyPDF2
from PyPDF2 import PdfReader

# step 1: Read Resume PDF
def read_resume(file_path):
    reader = PdfReader(file_path)               
    text = ""

    for page in reader.pages:
        text += page.extract_text()

    return text

# step 2: Extract Skills from Resume
def extract_skills(text):
    skills_list = ["Python", "SQL", "Excel", "Tableau", "Power BI", "Machine Learning"]

    found_skills = []

    for skill in skills_list:
        if skill.lower() in text.lower():
            found_skills.append(skill)

    return found_skills

# step 3: Job description Skills

jd_skills = ["Python", "SQL", "Excel"]

# step 4: Calculate Match Percentage

def calculate_match(resume_skills, jd_skills):
    matched = 0

    for skill in jd_skills:
        if skill in resume_skills:
            matched += 1

    percentage = (matched / len(jd_skills)) * 100
    return percentage

# step 5: Read Resume

resume_text = read_resume("C:/Users/goyal_p1qhzjn/Downloads/Sakshi_Goyal_Resume_DS.pdf")

# step 6: Extract Resume Skills

resume_skills = extract_skills(resume_text)

# step 7: Calculate Percentage

score = calculate_match(resume_skills, jd_skills)

# step 8: Output

print("Resume Skills Found:", resume_skills)
print("Match Percentage:", score, "%")
