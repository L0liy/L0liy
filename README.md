# إعداد ملف PDF بالإنجليزية
from fpdf import FPDF

class PDF(FPDF):
    def header(self):
        self.set_font('Arial', 'B', 12)
        self.cell(0, 10, 'Bulking Meal Recipes', align='C', ln=True)
        self.ln(10)

    def add_recipe(self, title, ingredients, method, protein):
        self.set_font('Arial', 'B', 12)
        self.cell(0, 10, title, ln=True)
        self.set_font('Arial', '', 11)
        self.ln(5)
        self.cell(0, 10, 'Ingredients:', ln=True)
        self.set_font('Arial', '', 10)
        for ingredient in ingredients:
            self.cell(0, 10, f"- {ingredient}", ln=True)
        self.ln(5)
        self.set_font('Arial', '', 11)
        self.cell(0, 10, 'Method:', ln=True)
        self.set_font('Arial', '', 10)
        self.multi_cell(0, 10, method)
        self.ln(5)
        self.set_font('Arial', 'I', 10)
        self.cell(0, 10, f"* Protein Content: {protein} grams", ln=True)
        self.ln(10)


# English recipes
recipes = [
    {
        "title": "Grilled Chicken with Potatoes and Veggies",
        "ingredients": [
            "200g chicken breast",
            "200g potatoes (boiled or roasted)",
            "1 cup mixed veggies (broccoli, carrots, zucchini)",
            "1 tbsp olive oil",
            "Salt, pepper, and spices to taste"
        ],
        "method": "1. Season the chicken with salt, pepper, and spices.\n"
                  "2. Grill the chicken on a grill or in the oven for 20-25 minutes.\n"
                  "3. Slice the potatoes and add olive oil and salt, then roast or boil them.\n"
                  "4. Steam the veggies or sauté them with a little oil.\n"
                  "5. Serve everything together and enjoy.",
        "protein": 45,
    },
    {
        "title": "Chicken and Veggie Rice Bowl",
        "ingredients": [
            "150g chicken breast, cubed",
            "1 cup cooked white or brown rice",
            "1/2 cup bell peppers, onions, and carrots",
            "1 tbsp olive oil",
            "Salt, pepper, and curry spices"
        ],
        "method": "1. Heat the oil in a pan and add the chicken cubes until browned.\n"
                  "2. Add the veggies and stir for 5 minutes.\n"
                  "3. Add the cooked rice and curry spices, mixing well.\n"
                  "4. Serve hot.",
        "protein": 35,
    },
    {
        "title": "Broccoli and Cheese Egg Omelette",
        "ingredients": [
            "3 eggs",
            "1/2 cup chopped broccoli",
            "30g low-fat cheese",
            "1 tbsp olive oil",
            "Salt and pepper"
        ],
        "method": "1. Heat the oil in a pan.\n"
                  "2. Whisk the eggs with salt and pepper.\n"
                  "3. Add the broccoli to the pan and sauté for a minute.\n"
                  "4. Pour the eggs over the broccoli and cook until set.\n"
                  "5. Sprinkle cheese on top and let it melt.\n"
                  "6. Serve warm.",
        "protein": 28,
    },
    {
        "title": "Protein Banana Smoothie (Snack)",
        "ingredients": [
            "1 scoop protein powder (30g)",
            "1 banana",
            "1 cup low-fat milk",
            "1 tbsp peanut butter (optional)",
            "Ice cubes"
        ],
        "method": "1. Place all ingredients in a blender.\n"
                  "2. Blend until smooth.\n"
                  "3. Pour into a glass and enjoy.",
        "protein": 35,
    }
]

# Generate PDF
pdf = PDF()
pdf.add_page()
pdf.set_auto_page_break(auto=True, margin=15)

for recipe in recipes:
    pdf.add_recipe(recipe["title"], recipe["ingredients"], recipe["method"], recipe["protein"])

# Save the file
file_path = "/mnt/data/Bulking_Meal_Recipes.pdf"
pdf.output(file_path)
file_path
