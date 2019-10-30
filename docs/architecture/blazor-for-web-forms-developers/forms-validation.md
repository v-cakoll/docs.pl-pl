---
title: Formularze i walidacja
description: Dowiedz się, jak tworzyć formularze z walidacją po stronie klienta w Blazor.
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: c30db5e06d36a6d15301835fe782b21058a80592
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088084"
---
# <a name="forms-and-validation"></a><span data-ttu-id="e2290-103">Formularze i walidacja</span><span class="sxs-lookup"><span data-stu-id="e2290-103">Forms and validation</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="e2290-104">Struktura formularzy sieci Web ASP.NET zawiera zestaw kontrolek serwera weryfikacji, które obsługują sprawdzanie poprawności danych wprowadzonych przez użytkownika do formularza (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator`itd.).</span><span class="sxs-lookup"><span data-stu-id="e2290-104">The ASP.NET Web Forms framework includes a set of validation server controls that handle validating user input entered into a form (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator`, and so on).</span></span> <span data-ttu-id="e2290-105">Struktura formularzy sieci Web ASP.NET obsługuje również powiązanie modelu i sprawdzanie poprawności modelu na podstawie adnotacji danych (`[Required]`, `[StringLength]`, `[Range]`itd.).</span><span class="sxs-lookup"><span data-stu-id="e2290-105">The ASP.NET Web Forms framework also supports model binding and validating the model based on data annotations (`[Required]`, `[StringLength]`, `[Range]`, and so on).</span></span> <span data-ttu-id="e2290-106">Logikę walidacji można wymusić zarówno na serwerze, jak i na kliencie przy użyciu niezauważalnej weryfikacji opartej na języku JavaScript.</span><span class="sxs-lookup"><span data-stu-id="e2290-106">The validation logic can be enforced both on the server and on the client using unobtrusive JavaScript-based validation.</span></span> <span data-ttu-id="e2290-107">Formant serwera `ValidationSummary` służy do wyświetlania podsumowania błędów walidacji dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e2290-107">The `ValidationSummary` server control is used to display a summary of the validation errors to the user.</span></span>

<span data-ttu-id="e2290-108">Blazor obsługuje udostępnianie logiki walidacji między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="e2290-108">Blazor supports the sharing of validation logic between both the client and the server.</span></span> <span data-ttu-id="e2290-109">ASP.NET zapewnia wstępnie skompilowane implementacje języka JavaScript wielu typowych walidacji serwera.</span><span class="sxs-lookup"><span data-stu-id="e2290-109">ASP.NET provides pre-built JavaScript implementations of many common server validations.</span></span> <span data-ttu-id="e2290-110">W wielu przypadkach deweloper nadal musi napisać kod JavaScript w celu pełnego zaimplementowania logiki walidacji specyficznej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2290-110">In many cases, the developer still has to write JavaScript to fully implement their app-specific validation logic.</span></span> <span data-ttu-id="e2290-111">Te same typy modeli, adnotacje danych i logikę walidacji mogą być używane zarówno na serwerze, jak i na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="e2290-111">The same model types, data annotations, and validation logic can be used on both the server and client.</span></span>

<span data-ttu-id="e2290-112">Blazor zawiera zestaw składników wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e2290-112">Blazor provides a set of input components.</span></span> <span data-ttu-id="e2290-113">Składniki wejściowe obsługują dane pól powiązań z modelem i sprawdzają poprawność danych wejściowych użytkownika podczas przesyłania formularza.</span><span class="sxs-lookup"><span data-stu-id="e2290-113">The input components handle binding field data to a model and validating the user input when the form is submitted.</span></span>

|<span data-ttu-id="e2290-114">Składnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="e2290-114">Input component</span></span>|<span data-ttu-id="e2290-115">Renderowany element HTML</span><span class="sxs-lookup"><span data-stu-id="e2290-115">Rendered HTML element</span></span>    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

<span data-ttu-id="e2290-116">Składnik `EditForm` otacza te składniki wejściowe i organizuje proces sprawdzania poprawności przez `EditContext`.</span><span class="sxs-lookup"><span data-stu-id="e2290-116">The `EditForm` component wraps these input components and orchestrates the validation process through an `EditContext`.</span></span> <span data-ttu-id="e2290-117">Podczas tworzenia `EditForm`należy określić, jakie wystąpienie modelu ma być powiązane z użyciem `Model` parametru.</span><span class="sxs-lookup"><span data-stu-id="e2290-117">When creating an `EditForm`, you specify what model instance to bind to using the `Model` parameter.</span></span> <span data-ttu-id="e2290-118">Sprawdzanie poprawności jest zwykle wykonywane przy użyciu adnotacji danych i rozszerzalne.</span><span class="sxs-lookup"><span data-stu-id="e2290-118">Validation is typically done using data annotations, and it's extensible.</span></span> <span data-ttu-id="e2290-119">Aby włączyć weryfikację opartą na adnotacji danych, Dodaj składnik `DataAnnotationsValidator` jako element podrzędny `EditForm`.</span><span class="sxs-lookup"><span data-stu-id="e2290-119">To enable data annotation-based validation, add the `DataAnnotationsValidator` component as a child of the `EditForm`.</span></span> <span data-ttu-id="e2290-120">Składnik `EditForm` zapewnia wygodne zdarzenie do obsługi prawidłowych (`OnValidSubmit`) i nieprawidłowych (`OnInvalidSubmit`) przesłania.</span><span class="sxs-lookup"><span data-stu-id="e2290-120">The `EditForm` component provides a convenient event for handling valid (`OnValidSubmit`) and invalid (`OnInvalidSubmit`) submissions.</span></span> <span data-ttu-id="e2290-121">Istnieje również bardziej ogólne zdarzenie `OnSubmit`, które pozwala na samodzielne wyzwalanie i obsługę walidacji.</span><span class="sxs-lookup"><span data-stu-id="e2290-121">There's also a more generic `OnSubmit` event that lets you trigger and handle the validation yourself.</span></span>

<span data-ttu-id="e2290-122">Aby wyświetlić podsumowanie błędu walidacji, użyj składnika `ValidationSummary`.</span><span class="sxs-lookup"><span data-stu-id="e2290-122">To display a validation error summary, use the `ValidationSummary` component.</span></span> <span data-ttu-id="e2290-123">Aby wyświetlić komunikaty o walidacji dla określonego pola wejściowego, należy użyć składnika `ValidationMessage`, określając wyrażenie lambda dla parametru `For`, który wskazuje odpowiedni element członkowski modelu.</span><span class="sxs-lookup"><span data-stu-id="e2290-123">To display validation messages for a specific input field, use the `ValidationMessage` component, specifying a lambda expression for the `For` parameter that points to the appropriate model member.</span></span>

<span data-ttu-id="e2290-124">Następujący typ modelu definiuje kilka reguł walidacji przy użyciu adnotacji danych:</span><span class="sxs-lookup"><span data-stu-id="e2290-124">The following model type defines several validation rules using data annotations:</span></span>

```csharp
using System;
using System.ComponentModel.DataAnnotations;

public class Starship
{
    [Required]
    [StringLength(16,
        ErrorMessage = "Identifier too long (16 character limit).")]
    public string Identifier { get; set; }

    public string Description { get; set; }

    [Required]
    public string Classification { get; set; }

    [Range(1, 100000,
        ErrorMessage = "Accommodation invalid (1-100000).")]
    public int MaximumAccommodation { get; set; }

    [Required]
    [Range(typeof(bool), "true", "true",
        ErrorMessage = "This form disallows unapproved ships.")]
    public bool IsValidatedDesign { get; set; }

    [Required]
    public DateTime ProductionDate { get; set; }
}
```

<span data-ttu-id="e2290-125">Poniższy składnik ilustruje Kompilowanie formularza w Blazor na podstawie typu modelu `Starship`:</span><span class="sxs-lookup"><span data-stu-id="e2290-125">The following component demonstrates building a form in Blazor based on the `Starship` model type:</span></span>

```razor
<h1>New Ship Entry Form</h1>

<EditForm Model="@starship" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <p>
        <label for="identifier">Identifier: </label>
        <InputText id="identifier" @bind-Value="starship.Identifier" />
        <ValidationMessage For="() => starship.Identifier" />
    </p>
    <p>
        <label for="description">Description (optional): </label>
        <InputTextArea id="description" @bind-Value="starship.Description" />
    </p>
    <p>
        <label for="classification">Primary Classification: </label>
        <InputSelect id="classification" @bind-Value="starship.Classification">
            <option value="">Select classification ...</option>
            <option value="Exploration">Exploration</option>
            <option value="Diplomacy">Diplomacy</option>
            <option value="Defense">Defense</option>
        </InputSelect>
        <ValidationMessage For="() => starship.Classification" />
    </p>
    <p>
        <label for="accommodation">Maximum Accommodation: </label>
        <InputNumber id="accommodation" @bind-Value="starship.MaximumAccommodation" />
        <ValidationMessage For="() => starship.MaximumAccommodation" />
    </p>
    <p>
        <label for="valid">Engineering Approval: </label>
        <InputCheckbox id="valid" @bind-Value="starship.IsValidatedDesign" />
        <ValidationMessage For="() => starship.IsValidatedDesign" />
    </p>
    <p>
        <label for="productionDate">Production Date: </label>
        <InputDate id="productionDate" @bind-Value="starship.ProductionDate" />
        <ValidationMessage For="() => starship.ProductionDate" />
    </p>

    <button type="submit">Submit</button>
</EditForm>

@code {
    private Starship starship = new Starship();

    private void HandleValidSubmit()
    {
        // Save the data
    }
}
```

<span data-ttu-id="e2290-126">Po przesłaniu formularza dane powiązane z modelem nie zostały zapisane w żadnym magazynie danych, takim jak baza danych.</span><span class="sxs-lookup"><span data-stu-id="e2290-126">After the form submission, the model-bound data hasn't been saved to any data store, like a database.</span></span> <span data-ttu-id="e2290-127">W aplikacji Blazor webassembly dane muszą być wysyłane do serwera.</span><span class="sxs-lookup"><span data-stu-id="e2290-127">In a Blazor WebAssembly app, the data must be sent to the server.</span></span> <span data-ttu-id="e2290-128">Na przykład za pomocą żądania HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="e2290-128">For example, using an HTTP POST request.</span></span> <span data-ttu-id="e2290-129">W aplikacji serwera Blazor dane są już na serwerze, ale muszą być utrwalone.</span><span class="sxs-lookup"><span data-stu-id="e2290-129">In a Blazor Server app, the data is already on the server, but it must be persisted.</span></span> <span data-ttu-id="e2290-130">Obsługa dostępu do danych w aplikacjach Blazor jest przedmiotem sekcji dotyczącej [danych](data.md) .</span><span class="sxs-lookup"><span data-stu-id="e2290-130">Handling data access in Blazor apps is the subject of the [Dealing with data](data.md) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e2290-131">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="e2290-131">Additional resources</span></span>

<span data-ttu-id="e2290-132">Aby uzyskać więcej informacji na temat [formularzy i walidacji](/aspnet/core/blazor/forms-validation) w aplikacjach Blazor, zobacz dokumentację Blazor.</span><span class="sxs-lookup"><span data-stu-id="e2290-132">For more information on [forms and validation](/aspnet/core/blazor/forms-validation) in Blazor apps, see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e2290-133">[Poprzedni](state-management.md)
>[Następny](data.md)</span><span class="sxs-lookup"><span data-stu-id="e2290-133">[Previous](state-management.md)
[Next](data.md)</span></span>
