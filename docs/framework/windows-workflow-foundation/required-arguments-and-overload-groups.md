---
title: Wymagane argumenty i grupy metod przeciążonych
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 5249cbb127064ffa5023074481a47decad279128
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964916"
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="4ed11-102">Wymagane argumenty i grupy metod przeciążonych</span><span class="sxs-lookup"><span data-stu-id="4ed11-102">Required Arguments and Overload Groups</span></span>
<span data-ttu-id="4ed11-103">Działania można skonfigurować tak, aby pewne argumenty były powiązane z prawidłowym działaniem do wykonania.</span><span class="sxs-lookup"><span data-stu-id="4ed11-103">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="4ed11-104">Ten `RequiredArgument` atrybut służy do wskazywania, że określone argumenty działania są wymagane `OverloadGroup` , a atrybut jest używany do grupowania kategorii wymaganych argumentów razem.</span><span class="sxs-lookup"><span data-stu-id="4ed11-104">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="4ed11-105">Przy użyciu atrybutów autorzy działań mogą zapewnić proste lub złożone konfiguracje weryfikacji działania.</span><span class="sxs-lookup"><span data-stu-id="4ed11-105">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="4ed11-106">Używanie wymaganych argumentów</span><span class="sxs-lookup"><span data-stu-id="4ed11-106">Using Required Arguments</span></span>  
 <span data-ttu-id="4ed11-107">Aby użyć `RequiredArgument` atrybutu w działaniu, należy wskazać odpowiednie argumenty przy użyciu <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4ed11-107">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="4ed11-108">W tym przykładzie `Add` zdefiniowano działanie, które ma dwa wymagane argumenty.</span><span class="sxs-lookup"><span data-stu-id="4ed11-108">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="4ed11-109">W języku XAML wymagane argumenty są również wskazywane przy <xref:System.Activities.RequiredArgumentAttribute>użyciu.</span><span class="sxs-lookup"><span data-stu-id="4ed11-109">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="4ed11-110">W tym przykładzie `Add` działanie jest zdefiniowane przy użyciu trzech argumentów i <xref:System.Activities.Statements.Assign%601> używa działania do wykonania operacji dodawania.</span><span class="sxs-lookup"><span data-stu-id="4ed11-110">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
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
  
 <span data-ttu-id="4ed11-111">Jeśli działanie jest używane i jeden z wymaganych argumentów nie jest powiązany, zwracany jest następujący błąd sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="4ed11-111">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="4ed11-112">**Nie podano wartości dla wymaganego argumentu działania "Operand1".**</span><span class="sxs-lookup"><span data-stu-id="4ed11-112">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
> <span data-ttu-id="4ed11-113">Aby uzyskać więcej informacji na temat sprawdzania i obsługi błędów i ostrzeżeń walidacji, zobacz [wywoływanie walidacji działania](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="4ed11-113">For more information about checking for and handling validation errors and warnings, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="4ed11-114">Korzystanie z grup przeciążeń</span><span class="sxs-lookup"><span data-stu-id="4ed11-114">Using Overload Groups</span></span>

<span data-ttu-id="4ed11-115">Grupy przeciążeń zapewniają metodę wskazującą, które kombinacje argumentów są prawidłowe w działaniu.</span><span class="sxs-lookup"><span data-stu-id="4ed11-115">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="4ed11-116">Argumenty są pogrupowane przy użyciu <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4ed11-116">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="4ed11-117">Każda grupa otrzymuje nazwę określoną przez <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4ed11-117">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="4ed11-118">Działanie jest prawidłowe, gdy są powiązane tylko jeden zestaw argumentów w grupie przeciążeń.</span><span class="sxs-lookup"><span data-stu-id="4ed11-118">The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="4ed11-119">W poniższym przykładzie `CreateLocation` zdefiniowano klasę.</span><span class="sxs-lookup"><span data-stu-id="4ed11-119">In the following example, a `CreateLocation` class is defined.</span></span>  
  
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
  
 <span data-ttu-id="4ed11-120">Celem tego działania jest określenie lokalizacji w Stanach Zjednoczonych.</span><span class="sxs-lookup"><span data-stu-id="4ed11-120">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="4ed11-121">W tym celu użytkownik działania może określić lokalizację przy użyciu jednej z trzech grup argumentów.</span><span class="sxs-lookup"><span data-stu-id="4ed11-121">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="4ed11-122">Aby określić prawidłowe kombinacje argumentów, definiowane są trzy grupy przeciążeń.</span><span class="sxs-lookup"><span data-stu-id="4ed11-122">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="4ed11-123">`G1`zawiera argumenty `Longitude`i. `Latitude`</span><span class="sxs-lookup"><span data-stu-id="4ed11-123">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="4ed11-124">`G2`zawiera `Street`, `City`i .`State`</span><span class="sxs-lookup"><span data-stu-id="4ed11-124">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="4ed11-125">`G3`zawiera `Street` i `Zip`.</span><span class="sxs-lookup"><span data-stu-id="4ed11-125">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="4ed11-126">`Name`jest również argumentem wymaganym, ale nie jest częścią grupy przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="4ed11-126">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="4ed11-127">Aby to działanie było prawidłowe, `Name` musi być powiązane ze wszystkimi argumentami z jednej i tylko jednej grupy przeciążeń.</span><span class="sxs-lookup"><span data-stu-id="4ed11-127">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="4ed11-128">W poniższym przykładzie z przykładu działania dotyczące [dostępu do bazy danych](./samples/database-access-activities.md) istnieją dwie grupy przeciążeń: `ConnectionString` i `ConfigFileSectionName`.</span><span class="sxs-lookup"><span data-stu-id="4ed11-128">In the following example, taken from the [Database Access Activities](./samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="4ed11-129">Aby to działanie było prawidłowe, `ProviderName` argumenty i `ConnectionString` muszą `ConfigName` być powiązane albo argument, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="4ed11-129">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
```  
Public class DbUpdate: AsyncCodeActivity  
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
  
 <span data-ttu-id="4ed11-130">Podczas definiowania grupy przeciążenia:</span><span class="sxs-lookup"><span data-stu-id="4ed11-130">When defining an overload group:</span></span>  
  
- <span data-ttu-id="4ed11-131">Grupa przeciążenia nie może być podzbiorem lub równoważnym zestawem innej grupy przeciążeń.</span><span class="sxs-lookup"><span data-stu-id="4ed11-131">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4ed11-132">Istnieje jeden wyjątek dla tej reguły.</span><span class="sxs-lookup"><span data-stu-id="4ed11-132">There is one exception to this rule.</span></span> <span data-ttu-id="4ed11-133">Jeśli grupa przeciążeń jest podzbiorem innej grupy przeciążeń, a podzestaw zawiera tylko `RequiredArgument` argumenty `false`, gdzie is, to grupa przeciążenia jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="4ed11-133">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
- <span data-ttu-id="4ed11-134">Grupy przeciążeń mogą się nakładać, ale jest to błąd, jeśli część wspólna grup zawiera wszystkie wymagane argumenty jednej lub obu grup przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="4ed11-134">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="4ed11-135">W poprzednim przykładzie `G2` grupy i `G3` przeciążania nakładają się na siebie, ale ponieważ część wspólna nie zawiera wszystkich argumentów jednej lub obu grup, które były prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="4ed11-135">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="4ed11-136">Podczas wiązania argumentów w grupie przeciążenia:</span><span class="sxs-lookup"><span data-stu-id="4ed11-136">When binding arguments in an overload group:</span></span>  
  
- <span data-ttu-id="4ed11-137">Grupa przeciążenia jest uznawana za powiązaną, `RequiredArgument` Jeśli wszystkie argumenty w grupie są powiązane.</span><span class="sxs-lookup"><span data-stu-id="4ed11-137">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
- <span data-ttu-id="4ed11-138">Jeśli grupa ma argumenty zero `RequiredArgument` i powiązana jest co najmniej jeden argument, Grupa jest uznawana za powiązaną.</span><span class="sxs-lookup"><span data-stu-id="4ed11-138">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
- <span data-ttu-id="4ed11-139">Jest to błąd walidacji, jeśli żadne grupy przeciążenia nie są powiązane, chyba że jedna `RequiredArgument` Grupa przeciążenia nie ma żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="4ed11-139">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
- <span data-ttu-id="4ed11-140">Występuje błąd z więcej niż jedną powiązaną grupą przeciążeń, to oznacza, że wszystkie wymagane argumenty w jednej grupie przeciążeń są powiązane i dowolny argument w innej grupie przeciążeń jest również powiązany.</span><span class="sxs-lookup"><span data-stu-id="4ed11-140">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
