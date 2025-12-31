from flask import Flask, render_template_string

app = Flask(__name__)

# 100 Diseases with prescriptions
DISEASES = {
    "Fever": "Paracetamol, rest, fluids",
    "Common Cold": "Antihistamines, steam inhalation",
    "Flu": "Oseltamivir, rest",
    "COVID-19": "Isolation, paracetamol, fluids",
    "Diabetes": "Metformin, diet control",
    "Hypertension": "Amlodipine, low salt diet",
    "Asthma": "Salbutamol inhaler",
    "Migraine": "Sumatriptan",
    "Gastritis": "Omeprazole",
    "Acidity": "Pantoprazole",
    "Tuberculosis": "DOTS therapy",
    "Pneumonia": "Antibiotics",
    "Malaria": "Artemisinin therapy",
    "Dengue": "Fluids, platelet monitoring",
    "Typhoid": "Ceftriaxone",
    "Anemia": "Iron supplements",
    "Arthritis": "NSAIDs",
    "Back Pain": "Pain relievers, physiotherapy",
    "UTI": "Nitrofurantoin",
    "Kidney Stones": "Hydration, pain relief",
    "Appendicitis": "Surgical consultation",
    "Jaundice": "Liver supportive care",
    "Hepatitis A": "Rest, hydration",
    "Hepatitis B": "Antiviral therapy",
    "Hepatitis C": "DAA therapy",
    "Heart Disease": "Aspirin, statins",
    "Stroke": "Emergency thrombolysis",
    "Epilepsy": "Levetiracetam",
    "Insomnia": "Melatonin, sleep hygiene",
    "Depression": "SSRIs, counseling",
    "Anxiety": "CBT, anxiolytics",
    "Obesity": "Diet and exercise",
    "PCOS": "Lifestyle changes, metformin",
    "Thyroid Disorder": "Levothyroxine",
    "Skin Allergy": "Antihistamines",
    "Psoriasis": "Topical steroids",
    "Eczema": "Moisturizers",
    "Acne": "Benzoyl peroxide",
    "Hair Loss": "Minoxidil",
    "Constipation": "Fiber, laxatives",
    "Diarrhea": "ORS, probiotics",
    "Hemorrhoids": "Topical ointments",
    "Eye Infection": "Antibiotic drops",
    "Ear Infection": "Amoxicillin",
    "Sinusitis": "Steam, antibiotics",
    "Tonsillitis": "Antibiotics",
    "Dental Pain": "Analgesics, dental care",
    "Osteoporosis": "Calcium, Vitamin D",
    "Vitamin D Deficiency": "Vitamin D supplements",
    "Vitamin B12 Deficiency": "B12 injections",
    "Scabies": "Permethrin cream",
    "Worm Infection": "Albendazole",
    "Cholera": "IV fluids",
    "Rabies": "Post-exposure vaccination",
    "Chickenpox": "Calamine lotion",
    "Measles": "Supportive care",
    "Mumps": "Pain relievers",
    "Whooping Cough": "Antibiotics",
    "Leprosy": "MDT therapy",
    "Glaucoma": "Eye drops",
    "Cataract": "Surgery",
    "Prostate Enlargement": "Alpha blockers",
    "Menstrual Pain": "NSAIDs",
    "Infertility": "Hormonal therapy",
    "Low Blood Pressure": "Fluids, salt",
    "High Cholesterol": "Statins",
    "Gout": "Allopurinol",
    "Rheumatic Fever": "Penicillin",
    "Sickle Cell Disease": "Hydroxyurea",
    "Thalassemia": "Blood transfusions",
    "Liver Cirrhosis": "Supportive care",
    "Pancreatitis": "Hospital treatment",
    "Food Poisoning": "ORS, antibiotics",
    "Motion Sickness": "Antiemetics",
    "Vertigo": "Betahistine",
    "Nausea": "Ondansetron",
    "Vomiting": "Antiemetics",
    "Bronchitis": "Bronchodilators",
    "COPD": "Inhaled bronchodilators",
    "Sleep Apnea": "CPAP therapy",
    "Burns": "Wound care",
    "Fracture": "Immobilization",
    "Sprain": "RICE therapy",
    "Heat Stroke": "Cooling, fluids",
    "Hypothermia": "Warming",
    "Sepsis": "IV antibiotics",
    "Cancer": "Oncology referral",
    "HIV": "ART therapy"
}

HTML = """
<!DOCTYPE html>
<html>
<head>
    <title>Healthcare Prescription System</title>
    <style>
        body { font-family: Arial; background: #f2f2f2; }
        .container {
            width: 80%;
            margin: auto;
            background: white;
            padding: 20px;
        }
        h1 { text-align: center; }
        .disease {
            padding: 10px;
            border-bottom: 1px solid #ddd;
        }
        .name { font-weight: bold; color: #0072ff; }
    </style>
</head>
<body>

<div class="container">
    <h1>Healthcare Prescription Website</h1>

    {% for disease, prescription in diseases.items() %}
        <div class="disease">
            <span class="name">{{ disease }}</span><br>
            Prescription: {{ prescription }}
        </div>
    {% endfor %}
</div>

</body>
</html>
"""

@app.route("/")
def home():
    return render_template_string(HTML, diseases=DISEASES)

if __name__ == "__main__":
    app.run(debug=True)
