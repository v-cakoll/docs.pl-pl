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
# <a name="forms-and-validation"></a>Formularze i walidacja

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Struktura formularzy sieci Web ASP.NET zawiera zestaw kontrolek serwera weryfikacji, które obsługują sprawdzanie poprawności danych wprowadzonych przez użytkownika do formularza (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator`itd.). Struktura formularzy sieci Web ASP.NET obsługuje również powiązanie modelu i sprawdzanie poprawności modelu na podstawie adnotacji danych (`[Required]`, `[StringLength]`, `[Range]`itd.). Logikę walidacji można wymusić zarówno na serwerze, jak i na kliencie przy użyciu niezauważalnej weryfikacji opartej na języku JavaScript. Formant serwera `ValidationSummary` służy do wyświetlania podsumowania błędów walidacji dla użytkownika.

Blazor obsługuje udostępnianie logiki walidacji między klientem a serwerem. ASP.NET zapewnia wstępnie skompilowane implementacje języka JavaScript wielu typowych walidacji serwera. W wielu przypadkach deweloper nadal musi napisać kod JavaScript w celu pełnego zaimplementowania logiki walidacji specyficznej dla aplikacji. Te same typy modeli, adnotacje danych i logikę walidacji mogą być używane zarówno na serwerze, jak i na komputerze klienckim.

Blazor zawiera zestaw składników wejściowych. Składniki wejściowe obsługują dane pól powiązań z modelem i sprawdzają poprawność danych wejściowych użytkownika podczas przesyłania formularza.

|Składnik wejściowy|Renderowany element HTML    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

Składnik `EditForm` otacza te składniki wejściowe i organizuje proces sprawdzania poprawności przez `EditContext`. Podczas tworzenia `EditForm`należy określić, jakie wystąpienie modelu ma być powiązane z użyciem `Model` parametru. Sprawdzanie poprawności jest zwykle wykonywane przy użyciu adnotacji danych i rozszerzalne. Aby włączyć weryfikację opartą na adnotacji danych, Dodaj składnik `DataAnnotationsValidator` jako element podrzędny `EditForm`. Składnik `EditForm` zapewnia wygodne zdarzenie do obsługi prawidłowych (`OnValidSubmit`) i nieprawidłowych (`OnInvalidSubmit`) przesłania. Istnieje również bardziej ogólne zdarzenie `OnSubmit`, które pozwala na samodzielne wyzwalanie i obsługę walidacji.

Aby wyświetlić podsumowanie błędu walidacji, użyj składnika `ValidationSummary`. Aby wyświetlić komunikaty o walidacji dla określonego pola wejściowego, należy użyć składnika `ValidationMessage`, określając wyrażenie lambda dla parametru `For`, który wskazuje odpowiedni element członkowski modelu.

Następujący typ modelu definiuje kilka reguł walidacji przy użyciu adnotacji danych:

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

Poniższy składnik ilustruje Kompilowanie formularza w Blazor na podstawie typu modelu `Starship`:

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

Po przesłaniu formularza dane powiązane z modelem nie zostały zapisane w żadnym magazynie danych, takim jak baza danych. W aplikacji Blazor webassembly dane muszą być wysyłane do serwera. Na przykład za pomocą żądania HTTP POST. W aplikacji serwera Blazor dane są już na serwerze, ale muszą być utrwalone. Obsługa dostępu do danych w aplikacjach Blazor jest przedmiotem sekcji dotyczącej [danych](data.md) .

## <a name="additional-resources"></a>Dodatkowe zasoby

Aby uzyskać więcej informacji na temat [formularzy i walidacji](/aspnet/core/blazor/forms-validation) w aplikacjach Blazor, zobacz dokumentację Blazor.

>[!div class="step-by-step"]
>[Poprzedni](state-management.md)
>[Następny](data.md)
