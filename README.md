using System.Windows;
using System.Windows. Controls;
using System.Windows. Media;
namespace RecipeApp
{
public partial class MainWindow: Window
{
private List<Recipe> recipes; // List of
recipes (replace with your own data structure)
private List<string> foodGroups; // List
of food groups (replace with your own data structure)
public Mainwindow ()
InitializeComponent ( );
InitializeData ( );
LoadRecipes ( ) ;
LoadFoodGroups ( );
private void InitializeData ( )
// Initialize recipes and foodGroups
with sample data (replace with your own data)
recipes = new List<Recipe>
{
new Recipe { Name = "Recipe 1"
Ingredients = new List<string>
• {
"Ingredient A'
"Ingredient B' ], FoodGroup =
"Group 1", Calories
= 100 },
new Recipe { Name = "Recipe 2",
Ingredients = new List<string> { "Ingredient B"
"Ingredient C" †, FoodGroup =
"Group 2", Calories
= 200 },
new Recipe { Name = "Recipe 3"
Ingredients = new List<string> {
"Ingredient A"
"Ingredient C' †, FoodGroup =
"Group 1", Calories
= 150 },
new Recipe { Name = "Recipe 4"
Ingredients = new List<string> { "Ingredient D'
}, FoodGroup = "Group 3", Calories = 300 },
};
"Group 1"
foodGroups = new List<string> {
"Group 2",
"Group 3" 1;
private void LoadRecipes ( )
{
recipeListBox.ItemsSource = recipes
}
private void LoadFoodGroups ( )
{
foodGroupComboBox. ItemsSource =
foodGroups;
}
private void
FilterByIngredient_Click(object sender,
RoutedEventArgs e)
{
string ingredient
ingredientTextBox.Text;
List<Recipe> filteredRecipes =
recipes.Where(recipe => recipe. Ingredients.Contains (ingredient)).ToList recipeListBox. ItemsSource
=
filteredRecipes;
private void
FilterByFoodGroup_Click(object sender,
RoutedEventArgs e)
{
string foodGroup = foodGroupComboBox.SelectedItem as string;
List<Recipe> filteredRecipes
recipes.Where(recipe => recipe.FoodGroup == foodGroup) • ToList ( ) ;
recipeListBox.ItemsSource =
filteredRecipes:
}
private void
FilterByMaxCalories_Click(object sender,
RoutedEventArgs e)
if
(int. TryParse (maxCaloriesTextBox.Text, out int maxCalories) )
List<Recipe> filteredRecipes =
recipes.Where(recipe => recipe.Calories <= maxCalories) .ToList ( );
recipeListBox.ItemsSource =
filteredRecipes;
}
else
{
MessageBox. Show ("Invalid maximum
calories input.");
set; }
public class Recipe
public string Name { get; set; } public List<string> Ingredients { get;
public string FoodGroup { get; set; } public int Calories { get; set;
}
