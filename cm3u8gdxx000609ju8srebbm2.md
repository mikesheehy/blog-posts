---
title: "Building a Web Application Using Amazon Q"
seoTitle: "Building a Web Application Using Amazon Q"
datePublished: Sat Nov 23 2024 13:55:43 GMT+0000 (Coordinated Universal Time)
cuid: cm3u8gdxx000609ju8srebbm2
slug: building-a-web-application-using-amazon-q
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1732370017487/cf4b33d3-db60-4a03-a5eb-54ed3422e1e5.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1732370042202/255b2b2f-248b-443e-8b09-923564c691f9.png
tags: aws

---

It's difficult to read the news and not come across a headline involving AI. Our search engines, messaging apps, and more have embraced the new technology, and while some have embraced it, some developers may wonder where their place is in an AI-infused world. Is it here to replace us, or is it merely a tool to help speed up the development process? I gave Amazon Q a try to figure out how it can help my coding journey.

Amazon Q debuted in November 2023 and later appeared as a VS Code extension in April 2024. The chatbot can give you detailed steps to create a project, explain code in your project, and give suggestions on how to fix code in your project. At the end of the day, Amazon Q is acting more as a helpful tool and not as a developer replacement since it will be up to you to actually put the pieces together and decide best practices.

To get started, open the marketplace on visual studio code and search for Amazon Q.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1732325248458/fcb6be91-f3a3-43e8-be4a-b53a56a1f4ed.png align="center")

Select the Amazon Q tab to start writing the prompt for the web application. In my example, I used the prompt “Create a Spring web application that adds and edits recipes stored in MongoDB”. It's important to be as specific as possible for these prompts to make sure the right dependencies are included with Spring Initializr (you can always add dependencies later to your pom file).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1732365483556/aedb6be1-628f-4b81-86b9-850a9c5d12c2.png align="center")

The steps provided by Amazon Q are exactly how I would start creating this app (the Spring Web dependency to build a web application, the Thymeleaf dependency to inject our data to the front end, and Mongo DB to connect to our database). I Included all of the generated steps below.

```plaintext
Certainly! I'll guide you through creating a Spring Boot web application that uses MongoDB Atlas for storing recipes and Bootstrap for the frontend. Here's a step-by-step approach to build this application:
	1. Set up the project: Create a new Spring Boot project using Spring Initializer (  https://start.spring.io/) with the following dependencies:
		○ Spring Web
		○ Spring Data MongoDB
		○ Thymeleaf (for server-side templating)
	2. Configure MongoDB Atlas: Add the MongoDB Atlas connection string to your 
application.properties
 file: [1]
spring.data.mongodb.uri=${MONGODB_URI}

CopyInsert at cursorproperties
Make sure to set the 
MONGODB_URI
 environment variable with your actual MongoDB Atlas connection string.
	3. Create the Recipe model:
import org.springframework.data.annotation.Id;
import org.springframework.data.mongodb.core.mapping.Document;
@Document(collection = "recipes")
public class Recipe {
    @Id
    private String id;
    private String name;
    private String ingredients;
    private String instructions;
// Constructors, getters, and setters
}
CopyInsert at cursorjava
	1. Create a MongoDB repository:
import org.springframework.data.mongodb.repository.MongoRepository;
public interface RecipeRepository extends MongoRepository<Recipe, String> {
}
CopyInsert at cursorjava
	1. Create a controller to handle recipe operations:
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.*;
@Controller
@RequestMapping("/recipes")
public class RecipeController {
@Autowired
    private RecipeRepository recipeRepository;
@GetMapping
    public String listRecipes(Model model) {
        model.addAttribute("recipes", recipeRepository.findAll());
        return "recipes/list";
    }
@GetMapping("/add")
    public String addRecipeForm(Model model) {
        model.addAttribute("recipe", new Recipe());
        return "recipes/form";
    }
@PostMapping("/add")
    public String addRecipe(@ModelAttribute Recipe recipe) {
        recipeRepository.save(recipe);
        return "redirect:/recipes";
    }
@GetMapping("/edit/{id}")
    public String editRecipeForm(@PathVariable String id, Model model) {
        model.addAttribute("recipe", recipeRepository.findById(id).orElseThrow());
        return "recipes/form";
    }
@PostMapping("/edit/{id}")
    public String editRecipe(@PathVariable String id, @ModelAttribute Recipe recipe) {
        recipe.setId(id);
        recipeRepository.save(recipe);
        return "redirect:/recipes";
    }
@GetMapping("/delete/{id}")
    public String deleteRecipe(@PathVariable String id) {
        recipeRepository.deleteById(id);
        return "redirect:/recipes";
    }
}
CopyInsert at cursorjava
	1. Create Thymeleaf templates for the views:Create a 
templates/recipes
 folder and add the following files: 
list.html
:
<!DOCTYPE html>
<html xmlns:th="<a href="http://www.thymeleaf.org"&gt">http://www.thymeleaf.org"&gt</a>;
<head>
    <meta charset="UTF-8">
    <title>Recipe List</title>
    <link href="<a href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css">https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css</a>" rel="stylesheet">
</head>
<body>
    <div class="container mt-5">
        <h1>Recipe List</h1>
        <a href="/recipes/add" class="btn btn-primary mb-3">Add New Recipe</a>
        <table class="table">
            <thead>
                <tr>
                    <th>Name</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody>
                <tr th:each="recipe : ${recipes}">
                    <td th:text="${recipe.name}"></td>
                    <td>
                        <a th:href="@{/recipes/edit/{id}(id=${recipe.id})}" class="btn btn-sm btn-warning">Edit</a>
                        <a th:href="@{/recipes/delete/{id}(id=${recipe.id})}" class="btn btn-sm btn-danger" onclick="return confirm('Are you sure?')">Delete</a>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
    <script src="<a href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script&gt">https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script&gt</a>;
</body>
</html>

CopyInsert at cursorhtml
form.html
:
<!DOCTYPE html>
<html xmlns:th="<a href="http://www.thymeleaf.org"&gt">http://www.thymeleaf.org"&gt</a>;
<head>
    <meta charset="UTF-8">
    <title>Recipe Form</title>
    <link href="<a href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css">https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css</a>" rel="stylesheet">
</head>
<body>
    <div class="container mt-5">
        <h1 th:text="${recipe.id} ? 'Edit Recipe' : 'Add New Recipe'"></h1>
        <form th:action="${recipe.id} ? @{/recipes/edit/{id}(id=${recipe.id})} : @{/recipes/add}" th:object="${recipe}" method="post">
            <div class="mb-3">
                <label for="name" class="form-label">Name</label>
                <input type="text" class="form-control" id="name" th:field="<em>{name}" required>
            </div>
            <div class="mb-3">
                <label for="ingredients" class="form-label">Ingredients</label>
                <textarea class="form-control" id="ingredients" th:field="</em>{ingredients}" rows="3" required></textarea>
            </div>
            <div class="mb-3">
                <label for="instructions" class="form-label">Instructions</label>
                <textarea class="form-control" id="instructions" th:field="*{instructions}" rows="5" required></textarea>
            </div>
            <button type="submit" class="btn btn-primary">Save</button>
            <a href="/recipes" class="btn btn-secondary">Cancel</a>
        </form>
    </div>
    <script src="<a href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script&gt">https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script&gt</a>;
</body>
</html>

CopyInsert at cursorhtml
	2. Run the application: Make sure you have set the 
MONGODB_URI
 environment variable with your MongoDB Atlas connection string, then run your Spring Boot application.
This setup creates a basic Spring Boot web application that allows users to add, edit, and delete recipes stored in MongoDB Atlas. The frontend uses Bootstrap for styling and responsiveness. Users can navigate to 
http://localhost:8080/recipes
 to see the list of recipes and perform CRUD operations.
Remember to handle exceptions, add input validation, and implement user authentication for a production-ready application. You may also want to add more features like search functionality or categorization of recipes.
Sources
[1] SpringPortal #3 - MongoDB Atlas with Spring Boot
24naman.hashnode.devspringportal-3-mongodb-atlas-with-spring-boot
create a spring boot web application to add and edit recipes stored in mongodb atlas and uses bootstrap
Hi, I'm Amazon Q. I can answer your software development questions.
Ask me to explain, debug, or optimize your code.
You can enter 
/
 to see a list of quick actions. Add @workspace to beginning of your message to include your entire workspace as context.
 
4000/4000
Amazon Q Developer uses generative AI. You may need to verify responses. See the AWS Responsible AI Policy.
```

As you can see, Amazon Q can do more than give us just the steps needed to get through Spring Initializr. It also generated necessary classes and a Thymeleaf template to help display the list of recipes, as well as adding, editing, and deletion options. Beyond that, it’s up to the developer to add styling, data, and extra functionality.

In conclusion, Amazon Q is an excellent resource that goes beyond a simple Stack Overflow answer, but still provides room for the developer to demonstrate their value. For more information on Amazon Q, visit [https://aws.amazon.com/q/](https://aws.amazon.com/q/) .