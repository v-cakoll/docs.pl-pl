---
title: Wymagane argumenty i grupy metod przeciążonych
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 4eb62306f52b8ff890d5a5333c3789bd84ad7f60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142943"
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="30712-102">Wymagane argumenty i grupy metod przeciążonych</span><span class="sxs-lookup"><span data-stu-id="30712-102">Required Arguments and Overload Groups</span></span>
<span data-ttu-id="30712-103">Działania można skonfigurować tak, aby niektóre argumenty muszą być powiązane dla działania, które mają być prawidłowe do wykonania.</span><span class="sxs-lookup"><span data-stu-id="30712-103">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="30712-104">Atrybut `RequiredArgument` jest używany do wskazania, że niektóre argumenty `OverloadGroup` na działanie są wymagane i atrybut jest używany do grupowanie kategorii wymaganych argumentów razem.</span><span class="sxs-lookup"><span data-stu-id="30712-104">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="30712-105">Za pomocą atrybutów autorzy działań można zapewnić proste lub złożone konfiguracje sprawdzania poprawności działania.</span><span class="sxs-lookup"><span data-stu-id="30712-105">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="30712-106">Korzystanie z wymaganych argumentów</span><span class="sxs-lookup"><span data-stu-id="30712-106">Using Required Arguments</span></span>  
 <span data-ttu-id="30712-107">Aby użyć `RequiredArgument` atrybutu w działaniu, należy <xref:System.Activities.RequiredArgumentAttribute>wskazać żądane argumenty za pomocą programu .</span><span class="sxs-lookup"><span data-stu-id="30712-107">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="30712-108">W tym przykładzie zdefiniowano `Add` działanie, które ma dwa wymagane argumenty.</span><span class="sxs-lookup"><span data-stu-id="30712-108">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="30712-109">W języku XAML wymagane argumenty są <xref:System.Activities.RequiredArgumentAttribute>również wskazywane za pomocą programu .</span><span class="sxs-lookup"><span data-stu-id="30712-109">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="30712-110">W tym `Add` przykładzie działanie jest definiowane przy <xref:System.Activities.Statements.Assign%601> użyciu trzech argumentów i używa działania do wykonania operacji dodawania.</span><span class="sxs-lookup"><span data-stu-id="30712-110">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
```xaml  
<Activity x:Class="ValidationDemo.Add" ...>  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Result" Type="OutArgument(x:Int32)" />  
  </x:Members>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[Result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[Operand1 + Operand2]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Activity>  
```  
  
 <span data-ttu-id="30712-111">Jeśli działanie jest używane i jeden z wymaganych argumentów nie jest związany następujący błąd sprawdzania poprawności jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="30712-111">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="30712-112">**Wartość wymaganego argumentu działania "Operand1" nie została dostarczona.**</span><span class="sxs-lookup"><span data-stu-id="30712-112">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
> <span data-ttu-id="30712-113">Aby uzyskać więcej informacji na temat sprawdzania błędów i ostrzeżeń sprawdzania poprawności i obsługi ich, zobacz [Wywoływanie sprawdzania poprawności działania](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="30712-113">For more information about checking for and handling validation errors and warnings, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="30712-114">Korzystanie z grup przeciążenia</span><span class="sxs-lookup"><span data-stu-id="30712-114">Using Overload Groups</span></span>

<span data-ttu-id="30712-115">Grupy przeciążenia zapewniają metodę wskazującą, które kombinacje argumentów są prawidłowe w działaniu.</span><span class="sxs-lookup"><span data-stu-id="30712-115">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="30712-116">Argumenty są zgrupowane <xref:System.Activities.OverloadGroupAttribute>razem za pomocą programu .</span><span class="sxs-lookup"><span data-stu-id="30712-116">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="30712-117">Każdej grupie otrzymuje się nazwę określoną przez plik <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="30712-117">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="30712-118">Działanie jest prawidłowe, gdy tylko jeden zestaw argumentów w grupie przeciążenia są powiązane.</span><span class="sxs-lookup"><span data-stu-id="30712-118">The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="30712-119">W poniższym przykładzie zdefiniowano `CreateLocation` klasę.</span><span class="sxs-lookup"><span data-stu-id="30712-119">In the following example, a `CreateLocation` class is defined.</span></span>  
  
```csharp  
class CreateLocation: Activity  
{  
    [RequiredArgument]  
    public InArgument<string> Name { get; set; }  
  
    public InArgument<string> Description { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Latitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Longitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    [OverloadGroup("G3")]  
    public InArgument<string> Street { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> City { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> State { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G3")]  
    public InArgument<int> Zip { get; set; }
}  
```  
  
 <span data-ttu-id="30712-120">Celem tego działania jest określenie lokalizacji w STANACH Zjednoczonych.</span><span class="sxs-lookup"><span data-stu-id="30712-120">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="30712-121">Aby to zrobić, użytkownik działania można określić lokalizację przy użyciu jednej z trzech grup argumentów.</span><span class="sxs-lookup"><span data-stu-id="30712-121">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="30712-122">Aby określić prawidłowe kombinacje argumentów, zdefiniowane są trzy grupy przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="30712-122">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="30712-123">`G1`zawiera `Latitude` argumenty `Longitude` i argumenty.</span><span class="sxs-lookup"><span data-stu-id="30712-123">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="30712-124">`G2`zawiera `Street` `City`, `State`i .</span><span class="sxs-lookup"><span data-stu-id="30712-124">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="30712-125">`G3`zawiera `Street` `Zip`i .</span><span class="sxs-lookup"><span data-stu-id="30712-125">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="30712-126">`Name`jest również wymaganym argumentem, ale nie jest częścią grupy przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="30712-126">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="30712-127">Aby to działanie było `Name` prawidłowe, musiałoby być powiązane ze wszystkimi argumentami z jednej i tylko jednej grupy przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="30712-127">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="30712-128">W poniższym przykładzie pobranym z przykładu Działania dostępu do `ConnectionString` `ConfigFileSectionName` [bazy danych](./samples/database-access-activities.md) istnieją dwie grupy przeciążenia: i .</span><span class="sxs-lookup"><span data-stu-id="30712-128">In the following example, taken from the [Database Access Activities](./samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="30712-129">Aby to działanie było prawidłowe, argumenty `ProviderName` i `ConnectionString` muszą `ConfigName` być powiązane lub argument, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="30712-129">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
```csharp  
public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }
}  
```  
  
 <span data-ttu-id="30712-130">Podczas definiowania grupy przeciążenia:</span><span class="sxs-lookup"><span data-stu-id="30712-130">When defining an overload group:</span></span>  
  
- <span data-ttu-id="30712-131">Grupa przeciążenia nie może być podzbiorem ani równoważnym zestawem innej grupy przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="30712-131">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="30712-132">Istnieje jeden wyjątek od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="30712-132">There is one exception to this rule.</span></span> <span data-ttu-id="30712-133">Jeśli grupa przeciążenia jest podzbiorem innej grupy przeciążenia, `RequiredArgument` `false`a podzbiór zawiera tylko argumenty, gdzie jest , grupa przeciążenia jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="30712-133">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
- <span data-ttu-id="30712-134">Grupy przeciążenia mogą się nakładać, ale jest to błąd, jeśli przecięcie grup zawiera wszystkie wymagane argumenty jednej lub obu grup przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="30712-134">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="30712-135">W poprzednim `G2` przykładzie `G3` i przeciążenia grup nakładających się, ale ponieważ przecięcie nie zawiera wszystkie argumenty jednej lub obu grup to było prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="30712-135">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="30712-136">Podczas wiązania argumentów w grupie przeciążenia:</span><span class="sxs-lookup"><span data-stu-id="30712-136">When binding arguments in an overload group:</span></span>  
  
- <span data-ttu-id="30712-137">Grupa przeciążenia jest uważana `RequiredArgument` za powiązaną, jeśli wszystkie argumenty w grupie są powiązane.</span><span class="sxs-lookup"><span data-stu-id="30712-137">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
- <span data-ttu-id="30712-138">Jeśli grupa ma `RequiredArgument` zero argumentów i co najmniej jeden argument związany, a następnie grupa jest uważany za związany.</span><span class="sxs-lookup"><span data-stu-id="30712-138">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
- <span data-ttu-id="30712-139">Jest to błąd sprawdzania poprawności, jeśli nie grupy przeciążenia są powiązane, chyba że jedna grupa przeciążenia nie `RequiredArgument` ma argumentów w nim.</span><span class="sxs-lookup"><span data-stu-id="30712-139">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
- <span data-ttu-id="30712-140">Jest to błąd, aby mieć więcej niż jedną grupę przeciążenia związane, oznacza to, że wszystkie wymagane argumenty w jednej grupie przeciążenia są powiązane i każdy argument w innej grupie przeciążenia jest również powiązany.</span><span class="sxs-lookup"><span data-stu-id="30712-140">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
