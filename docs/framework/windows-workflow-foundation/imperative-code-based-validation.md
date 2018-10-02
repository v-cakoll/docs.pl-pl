---
title: Imperatywne sprawdzanie poprawności, które są oparte na kodzie
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: ac77132e3469bdffa6f88f8c6d617c6faa1c9323
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47862423"
---
# <a name="imperative-code-based-validation"></a>Imperatywne sprawdzanie poprawności, które są oparte na kodzie

Imperatywne sprawdzanie poprawności, które są oparte na kodzie zapewnia prostą metodę dla działania w celu udostępnienia weryfikacji o sobie i jest dostępny dla działań, które wynikają z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, i <xref:System.Activities.NativeActivity>. Kod sprawdzania poprawności, który określa żadnych ostrzeżeń ani błędów sprawdzania poprawności jest dodawany do działania.  
  
## <a name="using-code-based-validation"></a>Za pomocą kodu sprawdzania poprawności

W oparciu o kod sprawdzania poprawności jest obsługiwana przez działania, które wynikają z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, i <xref:System.Activities.NativeActivity>. Kod sprawdzania poprawności można umieścić w <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienia, a błędy sprawdzania poprawności lub ostrzeżenia, które mogą być dodawane do argumentu metadanych. W poniższym przykładzie Jeśli `Cost` jest większa niż `Price`, błąd sprawdzania poprawności jest dodawany do metadanych.  
  
> [!NOTE]
> Należy pamiętać, że `Cost` i `Price` nie są argumenty do działania, ale są właściwościami, które są ustawiane w czasie projektowania. Oznacza to dlaczego ich wartości mogą być sprawdzone w <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienia. Nie można zweryfikować wartości danych przepływających przez argument w czasie projektowania, ponieważ nie przepływu danych do czasu wykonywania, ale działanie argumenty mogą być sprawdzone aby upewnić się, że są powiązane za pomocą `RequiredArgument` atrybutu i przeciążenia grup. Ten przykładowy kod będzie widział `RequiredArgument` atrybutu dla `Description` argument, a jeśli nie jest powiązany, to generowany jest błąd sprawdzania poprawności. Wymagane argumenty są objęte [wymagane argumenty i grupy przeciążenia](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).  
  
```csharp  
public sealed class CreateProduct : CodeActivity  
{  
    public double Price { get; set; }  
    public double Cost { get; set; }  
  
    // [RequiredArgument] attribute will generate a validation error   
    // if the Description argument is not set.  
    [RequiredArgument]  
    public InArgument<string> Description { get; set; }  
  
    protected override void CacheMetadata(CodeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        // Determine when the activity has been configured in an invalid way.  
        if (this.Cost > this.Price)  
        {  
            // Add a validation error with a custom message.  
            metadata.AddValidationError("The Cost must be less than or equal to the Price.");  
        }  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // Not needed for the sample.  
    }  
}  
```  
  
 Domyślnie, błąd sprawdzania poprawności jest dodawana do metadanych podczas <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> jest wywoływana. Aby dodać ostrzeżeń dotyczących weryfikacji, należy użyć <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> przeciążenia przyjmującego <xref:System.Activities.Validation.ValidationError>i określić, że <xref:System.Activities.Validation.ValidationError> reprezentuje ostrzeżenie, ustawiając <xref:System.Activities.Validation.ValidationError.IsWarning%2A> właściwości.  
  
 Sprawdzanie poprawności występuje, gdy przepływ pracy zostanie zmodyfikowany w Projektancie przepływów pracy i żadnych ostrzeżeń ani błędów sprawdzania poprawności, które są wyświetlane w Projektancie przepływu pracy. Sprawdzanie poprawności występuje także w czasie wykonywania po wywołaniu przepływu pracy i, jeśli wystąpią błędy sprawdzania poprawności, <xref:System.Activities.InvalidWorkflowException> jest generowany przez domyślną logikę weryfikacji. Aby uzyskać więcej informacji na temat wywoływania sprawdzania poprawności i uzyskiwania dostępu do żadnych Walidacja ostrzeżeń ani błędów, zobacz [wywoływanie walidacji działania](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).  
  
 Wszelkie wyjątki, które są generowane przez <xref:System.Activities.CodeActivity.CacheMetadata%2A> nie są traktowane jako błędy sprawdzania poprawności. Wyjątki te będą uciekały z wywołania <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> i muszą być obsługiwane przez obiekt wywołujący.  
  
 W oparciu o kod sprawdzania poprawności jest przydatne w przypadku sprawdzania poprawności działania, który zawiera kod, ale nie ma wglądu w innych działań w przepływie pracy. Ograniczenia deklaratywne sprawdzanie poprawności zapewnia możliwość zweryfikowania relacji między działania i inne działania w przepływie pracy i został omówiony w [ograniczenia deklaratywne](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md) tematu.
