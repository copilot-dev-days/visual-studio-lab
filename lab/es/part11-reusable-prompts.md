<!-- l10n-sync: source-file="part11-reusable-prompts.md" -->

Los archivos de prompt son una forma poderosa de crear prompts estandarizados y reutilizables que se pueden compartir con tu equipo. Ayudan a garantizar la consistencia en cómo interactúas con GitHub Copilot y pueden codificar las mejores prácticas para tareas comunes como generación de código, pruebas y documentación.

En esta parte, crearás un archivo de prompt reutilizable para generar pruebas unitarias y lo usarás para agregar pruebas al proyecto existente TinyShop.Tests.

## Entendiendo los Archivos de Prompt

Los archivos de prompt son archivos markdown almacenados en la carpeta `.github/prompts` de tu repositorio. Estos:
- Pueden ser invocados por nombre en Copilot Chat
- Se comparten con todo tu equipo a través del control de código fuente
- Pueden incluir marcadores de posición para contenido dinámico
- Ayudan a estandarizar tareas comunes de desarrollo

## Explorando el Proyecto de Pruebas

La solución ya incluye un proyecto **TinyShop.Tests** con MSTest configurado. Echemos un vistazo a lo que hay.

1. [] En el **Solution Explorer**, expande el proyecto **TinyShop.Tests**.
1. [] Abre **ProductTests.cs** para ver la prueba de referencia existente.
1. [] Observa que la prueba sigue el patrón Arrange-Act-Assert y verifica los valores predeterminados para una nueva instancia de Product.

## Creando un Archivo de Prompt para Pruebas Unitarias

Ahora creemos un archivo de prompt que ayude a generar pruebas unitarias adicionales usando MSTest.

1. [] En el **Solution Explorer** veremos el nodo **GitHub** de la extensión para agregarlo fácilmente:
   - Haz clic derecho en el icono/extensión del nodo **GitHub** en Visual Studio.
   - Elige **Add Copilot File...**.
   - Selecciona **Prompt file...** del diálogo.
   - Cambia el nombre del archivo a `unit-test.prompt.md` y haz clic en **OK**.
   - El nuevo archivo se abrirá en el editor; pega el contenido que se muestra a continuación en el archivo y guárdalo.

1. [] Si puedes crear el archivo manualmente en el explorador de archivos, agrega un nuevo archivo llamado `unit-test.prompt.md` en `.github/prompts` y pega el contenido a continuación.

1. [] Actualiza el archivo de prompt con el siguiente contenido:

   ```markdown
   ---
   mode: agent
   description: Generate comprehensive unit tests using MSTest
   ---

   # Unit Test Generator

   Generate unit tests for the selected code using the MSTest framework.

   ## Requirements

   - Use MSTest attributes ([TestClass], [TestMethod], [DataRow])
   - Follow the Arrange-Act-Assert pattern
   - Include both positive and negative test cases
   - Test edge cases and boundary conditions
   - Use descriptive test method names that explain what is being tested
   - Mock dependencies where appropriate

   ## Test Structure

   Each test should:
   1. Have a clear name following the pattern: `MethodName_Scenario_ExpectedBehavior`
   2. Include a brief comment explaining the test purpose
   3. Use proper assertions with meaningful failure messages

   ## Context

   Generate tests for: ${input:Describe what you want to test}
   ```

1. [] Guarda el archivo.

## Usando el Prompt Reutilizable

Ahora usemos nuestro nuevo archivo de prompt para generar pruebas unitarias adicionales para la clase Product.

1. [] En Copilot Chat, escribe `/` para ver los archivos de prompt disponibles.
1. [] Selecciona `unit-test` de la lista de prompts disponibles.
1. [] Cuando se te solicite la entrada, escribe: `the Product class in DataEntities, including tests for setting and getting each property, and tests using DataRow for multiple values`

   ![Usando un archivo de prompt](./images/11-prompt-file.png)

1. [] Revisa las pruebas generadas. Deberían incluir:
   - Pruebas para cada propiedad (Name, Description, Price, ImageUrl)
   - Pruebas usando DataRow para pruebas parametrizadas
   - Nombres de métodos de prueba apropiados siguiendo el patrón
   - Comentarios explicando el propósito de las pruebas

## Ejemplo de Pruebas Generadas

Las pruebas generadas deberían verse similares a:

```csharp
[TestMethod]
public void Name_SetValue_ReturnsExpectedValue()
{
    // Arrange
    var product = new Product();
    var expectedName = "Test Product";

    // Act
    product.Name = expectedName;

    // Assert
    Assert.AreEqual(expectedName, product.Name);
}

[TestMethod]
[DataRow(19.99)]
[DataRow(0)]
[DataRow(999.99)]
public void Price_SetValue_ReturnsExpectedValue(double price)
{
    // Arrange
    var product = new Product();
    var expectedPrice = (decimal)price;

    // Act
    product.Price = expectedPrice;

    // Assert
    Assert.AreEqual(expectedPrice, product.Price);
}

[TestMethod]
[DataRow("product1.png")]
[DataRow("product2.png")]
[DataRow("")]
public void ImageUrl_SetValue_ReturnsExpectedValue(string imageUrl)
{
    // Arrange
    var product = new Product();

    // Act
    product.ImageUrl = imageUrl;

    // Assert
    Assert.AreEqual(imageUrl, product.ImageUrl);
}
```

## Ejecutando las Pruebas

1. [] Abre el **Test Explorer** desde **Test -> Test Explorer**.
1. [] Compila la solución para descubrir las pruebas.
1. [] Haz clic en **Run All** para ejecutar todas las pruebas incluyendo las nuevas pruebas generadas.
1. [] Verifica que todas las pruebas pasen.

**Punto clave**: Los archivos de prompt reutilizables ayudan a estandarizar cómo tu equipo usa GitHub Copilot. Al crear prompts para tareas comunes como pruebas unitarias, aseguras consistencia y codificas las mejores prácticas de las que todo el equipo puede beneficiarse.

---

[Atrás: Parte 10 - Planning Mode en Agent](./part10-planning-mode.md) ← | [Siguiente: Parte 12 - Delegar a la Nube](./part12-delegate-to-cloud.md) →
