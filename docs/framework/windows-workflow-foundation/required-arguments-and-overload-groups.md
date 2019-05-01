---
title: Wymagane argumenty i grupy metod przeciążonych
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: b5006a201ce5db68e925bd5764fadde308bbccb4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937790"
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="8ffa2-102">Wymagane argumenty i grupy metod przeciążonych</span><span class="sxs-lookup"><span data-stu-id="8ffa2-102">Required Arguments and Overload Groups</span></span>
<span data-ttu-id="8ffa2-103">Działania można skonfigurować tak, aby niektóre argumenty są wymagane powiązać na ważne potrzeby wykonywania działania.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-103">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="8ffa2-104">`RequiredArgument` Atrybut jest używany do wskazania, że niektórych argumentów w ramach działania są wymagane i `OverloadGroup` atrybut służy do grupowania kategorii wymaganych argumentów.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-104">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="8ffa2-105">Za pomocą atrybutów, autorzy działanie może zapewnić proste lub złożone działanie sprawdzania poprawności konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-105">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="8ffa2-106">Przy użyciu wymaganych argumentów</span><span class="sxs-lookup"><span data-stu-id="8ffa2-106">Using Required Arguments</span></span>  
 <span data-ttu-id="8ffa2-107">Aby użyć `RequiredArgument` atrybutu w działaniu, określ żądany argumentów, za pomocą <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-107">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="8ffa2-108">W tym przykładzie `Add` działania jest zdefiniowana, że ma dwa wymagane argumenty.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-108">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="8ffa2-109">W XAML, wymagane argumenty są również oznaczane przy użyciu <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-109">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="8ffa2-110">W tym przykładzie `Add` działania jest definiowana za pomocą trzech argumentów i zastosowania <xref:System.Activities.Statements.Assign%601> działania do wykonania operacji dodawania.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-110">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
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
  
 <span data-ttu-id="8ffa2-111">Jeśli działanie jest używane, a jeden z wymaganych argumentów nie jest powiązany jest zwracany następujący błąd sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-111">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="8ffa2-112">**Nieprawidłowa wartość argumentu wymagane działania "Operand1".**</span><span class="sxs-lookup"><span data-stu-id="8ffa2-112">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
> <span data-ttu-id="8ffa2-113">Aby uzyskać więcej informacji dotyczących sprawdzania i obsługa błędy i ostrzeżenia walidacji, zobacz [wywoływanie walidacji działania](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="8ffa2-113">For more information about checking for and handling validation errors and warnings, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="8ffa2-114">Za pomocą Grupy metod Przeciążonych</span><span class="sxs-lookup"><span data-stu-id="8ffa2-114">Using Overload Groups</span></span>

<span data-ttu-id="8ffa2-115">Grupy metod przeciążonych udostępnia metody wskazujące, które kombinacje argumenty są prawidłowe w działaniu.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-115">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="8ffa2-116">Argumenty są zgrupowane za pomocą <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-116">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="8ffa2-117">Każda grupa otrzymuje nazwę, która jest określona przez <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-117">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="8ffa2-118">Działanie jest prawidłowa, gdy tylko jeden zestaw argumentów w grupie przeciążenia są powiązane.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-118">The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="8ffa2-119">W poniższym przykładzie `CreateLocation` klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-119">In the following example, a `CreateLocation` class is defined.</span></span>  
  
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
  
 <span data-ttu-id="8ffa2-120">Celem tego działania jest aby określić lokalizację, w stanach Zjednoczonych.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-120">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="8ffa2-121">Aby to zrobić, użytkownik działania można określić lokalizacji przy użyciu jednej z trzech grup argumentów.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-121">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="8ffa2-122">Aby określić prawidłową kombinacji argumentów, trzy grupy metod przeciążonych są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-122">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="8ffa2-123">`G1` zawiera `Latitude` i `Longitude` argumentów.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-123">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="8ffa2-124">`G2` zawiera `Street`, `City`, i `State`.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-124">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="8ffa2-125">`G3` zawiera `Street` i `Zip`.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-125">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="8ffa2-126">`Name` Ponadto argument jest wymagany, ale nie jest częścią grupy przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-126">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="8ffa2-127">Dla tego działania był prawidłowy `Name` musi powiązać razem z wszystkie argumenty z grupy przeciążenia jeden i tylko jeden.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-127">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="8ffa2-128">W poniższym przykładzie pobierana z [działań w bazie danych programu Access](./samples/database-access-activities.md) próbki, istnieją dwa przeciążenia grup: `ConnectionString` i `ConfigFileSectionName`.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-128">In the following example, taken from the [Database Access Activities](./samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="8ffa2-129">Dla tego działania był prawidłowy, albo `ProviderName` i `ConnectionString` argumentów musi być powiązana, lub `ConfigName` argumentów, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-129">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
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
  
 <span data-ttu-id="8ffa2-130">Podczas definiowania grupę przeciążenia:</span><span class="sxs-lookup"><span data-stu-id="8ffa2-130">When defining an overload group:</span></span>  
  
- <span data-ttu-id="8ffa2-131">Grupę przeciążenia nie może być podzbiór lub zbiór równoważny, innej grupy przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-131">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8ffa2-132">Istnieje jeden wyjątek od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-132">There is one exception to this rule.</span></span> <span data-ttu-id="8ffa2-133">Jeśli grupa przeciążenie jest podzbiorem innej grupy przeciążenia i podzbiór zawiera tylko argumenty gdzie `RequiredArgument` jest `false`, grupy przeciążenie jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-133">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
- <span data-ttu-id="8ffa2-134">Grupy metod przeciążonych może pokrywać się, ale jest to błąd, jeśli na przecięciu grupy zawiera wszystkie wymagane argumenty z jedną lub obie grupy metod przeciążonych.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-134">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="8ffa2-135">W poprzednim przykładzie `G2` i `G3` przeciążać nakładających się grup, ale ponieważ wspólną nie zawierała wszystkie argumenty jednego lub dwóch grup była nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-135">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="8ffa2-136">Podczas tworzenia powiązania argumentów w grupie przeciążenia:</span><span class="sxs-lookup"><span data-stu-id="8ffa2-136">When binding arguments in an overload group:</span></span>  
  
- <span data-ttu-id="8ffa2-137">Grupę przeciążenie jest uznawany za powiązane z, jeśli wszystkie `RequiredArgument` argumentów w grupie są powiązane.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-137">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
- <span data-ttu-id="8ffa2-138">Jeśli grupa zawiera zero `RequiredArgument` argumentów i co najmniej jednego argumentu powiązania, a następnie grupy jest uznawany za granicę.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-138">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
- <span data-ttu-id="8ffa2-139">Jeśli nie grupy metod przeciążonych są powiązane, chyba że nie ma jednej grupy przeciążenia, występuje błąd sprawdzania poprawności `RequiredArgument` argumentów w nim.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-139">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
- <span data-ttu-id="8ffa2-140">Jest błędem do więcej niż jedna grupa przeciążenia, powiązana, będącego, wszystkie wymagane argumenty z kilkoma przeciążeniami grupy są powiązane i wszystkich argumentów w innej grupie przeciążenie jest również powiązane.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-140">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
