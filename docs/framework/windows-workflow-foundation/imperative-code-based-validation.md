---
title: Walidacja oparta na kodzie imperatywnym
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: f3b07d0ab06b3753286c929b90e713a6941684ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143099"
---
# <a name="imperative-code-based-validation"></a>Walidacja oparta na kodzie imperatywnym

Trwać w testapikonietce opartej na kodzie imperatywnym zapewnia <xref:System.Activities.CodeActivity>prosty <xref:System.Activities.AsyncCodeActivity>sposób <xref:System.Activities.NativeActivity>działania w celu zapewnienia sprawdzania poprawności o sobie i jest dostępna dla działań, które wynikają z , i . Kod sprawdzania poprawności, który określa wszelkie błędy sprawdzania poprawności lub ostrzeżenia jest dodawany do działania.  
  
## <a name="using-code-based-validation"></a>Korzystanie z sprawdzania poprawności opartej na kodzie

Sprawdzanie poprawności oparte na kodzie jest obsługiwane <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity>przez <xref:System.Activities.NativeActivity>działania, które wynikają z , i . Kod sprawdzania poprawności można <xref:System.Activities.CodeActivity.CacheMetadata%2A> umieścić w zastąpienia i błędy sprawdzania poprawności lub ostrzeżenia mogą być dodawane do argumentu metadanych. W poniższym przykładzie, jeśli `Cost` `Price`jest większa niż , błąd sprawdzania poprawności jest dodawany do metadanych.  
  
> [!NOTE]
> Należy `Cost` zauważyć, że i `Price` nie są argumentami działania, ale są właściwości, które są ustawione w czasie projektowania. Dlatego ich wartości mogą być sprawdzane w <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienia. Wartość danych przepływających przez argument nie może być zweryfikowana w czasie projektowania, ponieważ dane nie przepływają do czasu wykonywania, ale argumenty działania można sprawdzić, aby upewnić się, że są one powiązane przy użyciu grup `RequiredArgument` atrybutów i przeciążenia. Ten przykładowy `RequiredArgument` kod widzi `Description` atrybut dla argumentu, a jeśli nie jest związany, a następnie generowany jest błąd sprawdzania poprawności. Wymagane argumenty są opisane w [Required Arguments i Overload Groups](required-arguments-and-overload-groups.md).  
  
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
  
 Domyślnie błąd sprawdzania poprawności jest dodawany <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> do metadanych, gdy jest wywoływana. Aby dodać ostrzeżenie sprawdzania <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> poprawności, należy <xref:System.Activities.Validation.ValidationError>użyć przeciążenia, które ma , i określić, że <xref:System.Activities.Validation.ValidationError> reprezentuje ostrzeżenie, ustawiając <xref:System.Activities.Validation.ValidationError.IsWarning%2A> właściwość.  
  
 Sprawdzanie poprawności występuje, gdy przepływ pracy jest modyfikowany w projektancie przepływu pracy i wszelkie błędy sprawdzania poprawności lub ostrzeżenia są wyświetlane w projektancie przepływu pracy. Sprawdzanie poprawności występuje również w czasie wykonywania, gdy jest wywoływany <xref:System.Activities.InvalidWorkflowException> przepływ pracy i jeśli wystąpią błędy sprawdzania poprawności, jest generowany przez domyślną logikę sprawdzania poprawności. Aby uzyskać więcej informacji na temat wywoływania sprawdzania poprawności i uzyskiwania dostępu do ostrzeżeń lub błędów sprawdzania poprawności, zobacz [Wywoływanie sprawdzania poprawności działania](invoking-activity-validation.md).  
  
 Wszelkie wyjątki, które <xref:System.Activities.CodeActivity.CacheMetadata%2A> są generowane z nie są traktowane jako błędy sprawdzania poprawności. Te wyjątki uciekną <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> od wywołania i muszą być obsługiwane przez wywołującego.  
  
 Sprawdzanie poprawności oparte na kodzie jest przydatne do sprawdzania poprawności działania, które zawiera kod, ale nie ma wglądu w inne działania w przepływie pracy. Sprawdzanie poprawności ograniczeń deklaratywnych zapewnia możliwość sprawdzania poprawności relacji między działaniem a innymi działaniami w przepływie pracy i jest omówione w temacie [Ograniczenia deklaratywne.](declarative-constraints.md)
