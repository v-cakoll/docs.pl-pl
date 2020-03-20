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
# <a name="imperative-code-based-validation"></a><span data-ttu-id="8820f-102">Walidacja oparta na kodzie imperatywnym</span><span class="sxs-lookup"><span data-stu-id="8820f-102">Imperative Code-Based Validation</span></span>

<span data-ttu-id="8820f-103">Trwać w testapikonietce opartej na kodzie imperatywnym zapewnia <xref:System.Activities.CodeActivity>prosty <xref:System.Activities.AsyncCodeActivity>sposób <xref:System.Activities.NativeActivity>działania w celu zapewnienia sprawdzania poprawności o sobie i jest dostępna dla działań, które wynikają z , i .</span><span class="sxs-lookup"><span data-stu-id="8820f-103">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="8820f-104">Kod sprawdzania poprawności, który określa wszelkie błędy sprawdzania poprawności lub ostrzeżenia jest dodawany do działania.</span><span class="sxs-lookup"><span data-stu-id="8820f-104">Validation code that determines any validation errors or warnings is added to the activity.</span></span>  
  
## <a name="using-code-based-validation"></a><span data-ttu-id="8820f-105">Korzystanie z sprawdzania poprawności opartej na kodzie</span><span class="sxs-lookup"><span data-stu-id="8820f-105">Using Code-Based Validation</span></span>

<span data-ttu-id="8820f-106">Sprawdzanie poprawności oparte na kodzie jest obsługiwane <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity>przez <xref:System.Activities.NativeActivity>działania, które wynikają z , i .</span><span class="sxs-lookup"><span data-stu-id="8820f-106">Code-based validation is supported by activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="8820f-107">Kod sprawdzania poprawności można <xref:System.Activities.CodeActivity.CacheMetadata%2A> umieścić w zastąpienia i błędy sprawdzania poprawności lub ostrzeżenia mogą być dodawane do argumentu metadanych.</span><span class="sxs-lookup"><span data-stu-id="8820f-107">Validation code can be placed in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override, and validation errors or warnings can be added to the metadata argument.</span></span> <span data-ttu-id="8820f-108">W poniższym przykładzie, jeśli `Cost` `Price`jest większa niż , błąd sprawdzania poprawności jest dodawany do metadanych.</span><span class="sxs-lookup"><span data-stu-id="8820f-108">In the following example, if the `Cost` is greater than the `Price`, a validation error is added to the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8820f-109">Należy `Cost` zauważyć, że i `Price` nie są argumentami działania, ale są właściwości, które są ustawione w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="8820f-109">Note that `Cost` and `Price` are not arguments to the activity, but are properties that are set at design time.</span></span> <span data-ttu-id="8820f-110">Dlatego ich wartości mogą być sprawdzane w <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="8820f-110">That is why their values can be validated in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="8820f-111">Wartość danych przepływających przez argument nie może być zweryfikowana w czasie projektowania, ponieważ dane nie przepływają do czasu wykonywania, ale argumenty działania można sprawdzić, aby upewnić się, że są one powiązane przy użyciu grup `RequiredArgument` atrybutów i przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="8820f-111">The value of the data flowing through an argument cannot be validated at design time because the data does not flow until run time, but activity arguments can be validated to ensure that they are bound by using the `RequiredArgument` attribute and overload groups.</span></span> <span data-ttu-id="8820f-112">Ten przykładowy `RequiredArgument` kod widzi `Description` atrybut dla argumentu, a jeśli nie jest związany, a następnie generowany jest błąd sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="8820f-112">This example code sees the `RequiredArgument` attribute for the `Description` argument, and if it is not bound then a validation error is generated.</span></span> <span data-ttu-id="8820f-113">Wymagane argumenty są opisane w [Required Arguments i Overload Groups](required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="8820f-113">Required arguments are covered in [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>  
  
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
  
 <span data-ttu-id="8820f-114">Domyślnie błąd sprawdzania poprawności jest dodawany <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> do metadanych, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="8820f-114">By default, a validation error is added to the metadata when <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> is called.</span></span> <span data-ttu-id="8820f-115">Aby dodać ostrzeżenie sprawdzania <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> poprawności, należy <xref:System.Activities.Validation.ValidationError>użyć przeciążenia, które ma , i określić, że <xref:System.Activities.Validation.ValidationError> reprezentuje ostrzeżenie, ustawiając <xref:System.Activities.Validation.ValidationError.IsWarning%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="8820f-115">To add a validation warning, use the <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> overload that takes a <xref:System.Activities.Validation.ValidationError>, and specify that the <xref:System.Activities.Validation.ValidationError> represents a warning by setting the <xref:System.Activities.Validation.ValidationError.IsWarning%2A> property.</span></span>  
  
 <span data-ttu-id="8820f-116">Sprawdzanie poprawności występuje, gdy przepływ pracy jest modyfikowany w projektancie przepływu pracy i wszelkie błędy sprawdzania poprawności lub ostrzeżenia są wyświetlane w projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8820f-116">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="8820f-117">Sprawdzanie poprawności występuje również w czasie wykonywania, gdy jest wywoływany <xref:System.Activities.InvalidWorkflowException> przepływ pracy i jeśli wystąpią błędy sprawdzania poprawności, jest generowany przez domyślną logikę sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="8820f-117">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="8820f-118">Aby uzyskać więcej informacji na temat wywoływania sprawdzania poprawności i uzyskiwania dostępu do ostrzeżeń lub błędów sprawdzania poprawności, zobacz [Wywoływanie sprawdzania poprawności działania](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="8820f-118">For more information about invoking validation and accessing any validation warnings or errors, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
 <span data-ttu-id="8820f-119">Wszelkie wyjątki, które <xref:System.Activities.CodeActivity.CacheMetadata%2A> są generowane z nie są traktowane jako błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="8820f-119">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="8820f-120">Te wyjątki uciekną <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> od wywołania i muszą być obsługiwane przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8820f-120">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
 <span data-ttu-id="8820f-121">Sprawdzanie poprawności oparte na kodzie jest przydatne do sprawdzania poprawności działania, które zawiera kod, ale nie ma wglądu w inne działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="8820f-121">Code-based validation is useful for validating the activity that contains the code, but it does not have visibility into the other activities in the workflow.</span></span> <span data-ttu-id="8820f-122">Sprawdzanie poprawności ograniczeń deklaratywnych zapewnia możliwość sprawdzania poprawności relacji między działaniem a innymi działaniami w przepływie pracy i jest omówione w temacie [Ograniczenia deklaratywne.](declarative-constraints.md)</span><span class="sxs-lookup"><span data-stu-id="8820f-122">Declarative constraints validation provides the ability to validate the relationships between an activity and other activities in the workflow, and is covered in the [Declarative Constraints](declarative-constraints.md) topic.</span></span>
