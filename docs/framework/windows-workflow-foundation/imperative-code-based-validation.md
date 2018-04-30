---
title: Weryfikacja opartej na kodzie imperatywne
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5dde4c75d2cf9432c750a8988c2495cd72eb2770
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="imperative-code-based-validation"></a>Weryfikacja opartej na kodzie imperatywne
Konieczne weryfikacji opartych na kodzie zapewnia prosty sposób działania w celu udostępnienia weryfikacji o sobie samym i jest dostępny dla działań, które pochodzą z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, i <xref:System.Activities.NativeActivity>. Sprawdzanie poprawności kodu, który określa wszelkie błędy lub ostrzeżenia walidacji jest dodawany do działania.  
  
## <a name="using-code-based-validation"></a>Za pomocą opartej na kodzie sprawdzania poprawności  
 Oparte na kodzie sprawdzania poprawności jest obsługiwana przez działania, które pochodzą z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, i <xref:System.Activities.NativeActivity>. Sprawdzanie poprawności kodu można umieścić w <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienie, a błędy lub ostrzeżenia walidacji mogą być dodawane do argumentu metadanych. W poniższym przykładzie pobierana z [podstawowe sprawdzanie poprawności](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) przykładowe, jeśli `Cost` jest większa niż `Price`, błąd sprawdzania poprawności jest dodawany do metadanych.  
  
> [!NOTE]
>  Należy pamiętać, że `Cost` i `Price` nie są argumenty do działania, ale nie ma właściwości, które są ustawione w czasie projektowania. Oznacza to dlaczego ich wartości można zweryfikować w <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienia. Nie można zweryfikować wartości danych przepływających przez argument w czasie projektowania, ponieważ nie przepływ danych do czasu wykonywania, ale argumentów działania mogą być sprawdzone, aby upewnić się, że są one związane przy użyciu `RequiredArgument` atrybutu i przeciążenia grup. Ten przykładowy kod widzi `RequiredArgument` atrybutu dla `Description` argumentu i jeśli nie jest powiązany, zostanie wygenerowany błąd sprawdzania poprawności. Wymagane argumenty zostały omówione w [wymaganych argumentów i grup przeciążenia](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).  
  
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
  
 Domyślnie błąd sprawdzania poprawności jest dodawany do metadanych podczas <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> jest wywoływana. Aby dodać ostrzeżenie walidacji, użyj <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> przeciążenia, które przyjmuje <xref:System.Activities.Validation.ValidationError>i określić, że <xref:System.Activities.Validation.ValidationError> reprezentuje ostrzeżenie przez ustawienie <xref:System.Activities.Validation.ValidationError.IsWarning%2A> właściwości.  
  
 Sprawdzanie poprawności występuje, gdy przepływ pracy zostanie zmodyfikowany w Projektancie przepływów pracy i wszelkie błędy sprawdzania poprawności zostaną wyświetlone w Projektancie przepływów pracy. Sprawdzanie poprawności występuje także w czasie wykonywania po wywołaniu przepływu pracy i, jeśli wystąpią jakieś błędy sprawdzania poprawności, <xref:System.Activities.InvalidWorkflowException> jest generowany przez logikę sprawdzania poprawności domyślnej. Aby uzyskać więcej informacji na temat wywoływania sprawdzania poprawności i uzyskiwania dostępu do sprawdzania poprawności ostrzeżeń i błędów, zobacz [wywoływania sprawdzania poprawności działania](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).  
  
 Wszelkie wyjątki, które są generowane z <xref:System.Activities.CodeActivity.CacheMetadata%2A> nie są traktowane jako błędy sprawdzania poprawności. Te wyjątki zostaną wyjścia z wywołania <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> i muszą być obsługiwane przez obiekt wywołujący.  
  
 Oparte na kodzie sprawdzania poprawności jest przydatna do sprawdzania poprawności działania, który zawiera kod, ale nie ma wgląd w innych działań w przepływie pracy. Sprawdzanie poprawności ograniczenia deklaratywne pozwala, aby sprawdzić poprawność relacje między działania i innych działań w przepływie pracy i znajdują się w [deklaratywne ograniczenia](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md) tematu.
