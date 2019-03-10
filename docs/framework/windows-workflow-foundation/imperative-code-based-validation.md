---
title: Imperatywne sprawdzanie poprawności, które są oparte na kodzie
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: 333e1e200825dd1fc8ed750abbecbb309da66663
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707836"
---
# <a name="imperative-code-based-validation"></a><span data-ttu-id="467e8-102">Imperatywne sprawdzanie poprawności, które są oparte na kodzie</span><span class="sxs-lookup"><span data-stu-id="467e8-102">Imperative Code-Based Validation</span></span>

<span data-ttu-id="467e8-103">Imperatywne sprawdzanie poprawności, które są oparte na kodzie zapewnia prostą metodę dla działania w celu udostępnienia weryfikacji o sobie i jest dostępny dla działań, które wynikają z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, i <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="467e8-103">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="467e8-104">Kod sprawdzania poprawności, który określa żadnych ostrzeżeń ani błędów sprawdzania poprawności jest dodawany do działania.</span><span class="sxs-lookup"><span data-stu-id="467e8-104">Validation code that determines any validation errors or warnings is added to the activity.</span></span>  
  
## <a name="using-code-based-validation"></a><span data-ttu-id="467e8-105">Za pomocą kodu sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="467e8-105">Using Code-Based Validation</span></span>

<span data-ttu-id="467e8-106">W oparciu o kod sprawdzania poprawności jest obsługiwana przez działania, które wynikają z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, i <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="467e8-106">Code-based validation is supported by activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="467e8-107">Kod sprawdzania poprawności można umieścić w <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienia, a błędy sprawdzania poprawności lub ostrzeżenia, które mogą być dodawane do argumentu metadanych.</span><span class="sxs-lookup"><span data-stu-id="467e8-107">Validation code can be placed in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override, and validation errors or warnings can be added to the metadata argument.</span></span> <span data-ttu-id="467e8-108">W poniższym przykładzie Jeśli `Cost` jest większa niż `Price`, błąd sprawdzania poprawności jest dodawany do metadanych.</span><span class="sxs-lookup"><span data-stu-id="467e8-108">In the following example, if the `Cost` is greater than the `Price`, a validation error is added to the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="467e8-109">Należy pamiętać, że `Cost` i `Price` nie są argumenty do działania, ale są właściwościami, które są ustawiane w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="467e8-109">Note that `Cost` and `Price` are not arguments to the activity, but are properties that are set at design time.</span></span> <span data-ttu-id="467e8-110">Oznacza to dlaczego ich wartości mogą być sprawdzone w <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="467e8-110">That is why their values can be validated in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="467e8-111">Nie można zweryfikować wartości danych przepływających przez argument w czasie projektowania, ponieważ nie przepływu danych do czasu wykonywania, ale działanie argumenty mogą być sprawdzone aby upewnić się, że są powiązane za pomocą `RequiredArgument` atrybutu i przeciążenia grup.</span><span class="sxs-lookup"><span data-stu-id="467e8-111">The value of the data flowing through an argument cannot be validated at design time because the data does not flow until run time, but activity arguments can be validated to ensure that they are bound by using the `RequiredArgument` attribute and overload groups.</span></span> <span data-ttu-id="467e8-112">Ten przykładowy kod będzie widział `RequiredArgument` atrybutu dla `Description` argument, a jeśli nie jest powiązany, to generowany jest błąd sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="467e8-112">This example code sees the `RequiredArgument` attribute for the `Description` argument, and if it is not bound then a validation error is generated.</span></span> <span data-ttu-id="467e8-113">Wymagane argumenty są objęte [wymagane argumenty i grupy przeciążenia](required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="467e8-113">Required arguments are covered in [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>  
  
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
  
 <span data-ttu-id="467e8-114">Domyślnie, błąd sprawdzania poprawności jest dodawana do metadanych podczas <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="467e8-114">By default, a validation error is added to the metadata when <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> is called.</span></span> <span data-ttu-id="467e8-115">Aby dodać ostrzeżeń dotyczących weryfikacji, należy użyć <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> przeciążenia przyjmującego <xref:System.Activities.Validation.ValidationError>i określić, że <xref:System.Activities.Validation.ValidationError> reprezentuje ostrzeżenie, ustawiając <xref:System.Activities.Validation.ValidationError.IsWarning%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="467e8-115">To add a validation warning, use the <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> overload that takes a <xref:System.Activities.Validation.ValidationError>, and specify that the <xref:System.Activities.Validation.ValidationError> represents a warning by setting the <xref:System.Activities.Validation.ValidationError.IsWarning%2A> property.</span></span>  
  
 <span data-ttu-id="467e8-116">Sprawdzanie poprawności występuje, gdy przepływ pracy zostanie zmodyfikowany w Projektancie przepływów pracy i żadnych ostrzeżeń ani błędów sprawdzania poprawności, które są wyświetlane w Projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="467e8-116">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="467e8-117">Sprawdzanie poprawności występuje także w czasie wykonywania po wywołaniu przepływu pracy i, jeśli wystąpią błędy sprawdzania poprawności, <xref:System.Activities.InvalidWorkflowException> jest generowany przez domyślną logikę weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="467e8-117">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="467e8-118">Aby uzyskać więcej informacji na temat wywoływania sprawdzania poprawności i uzyskiwania dostępu do żadnych Walidacja ostrzeżeń ani błędów, zobacz [wywoływanie walidacji działania](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="467e8-118">For more information about invoking validation and accessing any validation warnings or errors, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
 <span data-ttu-id="467e8-119">Wszelkie wyjątki, które są generowane przez <xref:System.Activities.CodeActivity.CacheMetadata%2A> nie są traktowane jako błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="467e8-119">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="467e8-120">Wyjątki te będą uciekały z wywołania <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> i muszą być obsługiwane przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="467e8-120">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
 <span data-ttu-id="467e8-121">W oparciu o kod sprawdzania poprawności jest przydatne w przypadku sprawdzania poprawności działania, który zawiera kod, ale nie ma wglądu w innych działań w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="467e8-121">Code-based validation is useful for validating the activity that contains the code, but it does not have visibility into the other activities in the workflow.</span></span> <span data-ttu-id="467e8-122">Ograniczenia deklaratywne sprawdzanie poprawności zapewnia możliwość zweryfikowania relacji między działania i inne działania w przepływie pracy i został omówiony w [ograniczenia deklaratywne](declarative-constraints.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="467e8-122">Declarative constraints validation provides the ability to validate the relationships between an activity and other activities in the workflow, and is covered in the [Declarative Constraints](declarative-constraints.md) topic.</span></span>
