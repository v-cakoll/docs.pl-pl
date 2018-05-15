---
title: Wymagane argumenty i grupy metod przeciążonych
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 794a0a531fbd26d9e4242d40be5147ab41547192
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="86ed2-102">Wymagane argumenty i grupy metod przeciążonych</span><span class="sxs-lookup"><span data-stu-id="86ed2-102">Required Arguments and Overload Groups</span></span>
<span data-ttu-id="86ed2-103">Można skonfigurować tak, aby niektóre argumenty są wymagane może być powiązane działania jest nieprawidłowy do wykonania działań.</span><span class="sxs-lookup"><span data-stu-id="86ed2-103">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="86ed2-104">`RequiredArgument` Atrybut służy do wskazania, że niektóre argumenty w działaniu wymagane i `OverloadGroup` atrybutów jest używane do grupowania kategorii wymaganych argumentów.</span><span class="sxs-lookup"><span data-stu-id="86ed2-104">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="86ed2-105">Przy użyciu atrybutów, autorzy działania zapewniają prostymi lub złożonymi działanie sprawdzania poprawności konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="86ed2-105">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="86ed2-106">Przy użyciu wymaganych argumentów</span><span class="sxs-lookup"><span data-stu-id="86ed2-106">Using Required Arguments</span></span>  
 <span data-ttu-id="86ed2-107">Aby użyć `RequiredArgument` atrybutu w działaniu, określ żądany argumentów, za pomocą <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="86ed2-107">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="86ed2-108">W tym przykładzie `Add` działania jest zdefiniowany, że dwa wymaga argumentów.</span><span class="sxs-lookup"><span data-stu-id="86ed2-108">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="86ed2-109">W języku XAML, wymagane argumenty są również oznaczone za pomocą <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="86ed2-109">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="86ed2-110">W tym przykładzie `Add` działania jest definiowana za pomocą trzech argumentów i używa <xref:System.Activities.Statements.Assign%601> działanie do wykonania operacji dodawania.</span><span class="sxs-lookup"><span data-stu-id="86ed2-110">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
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
  
 <span data-ttu-id="86ed2-111">Jeśli jest używane działanie i jeden z wymaganych argumentów nie jest powiązany jest zwracany następujący błąd sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="86ed2-111">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="86ed2-112">**Nie podano wartości dla wymaganego argumentu działania "Operand1".**</span><span class="sxs-lookup"><span data-stu-id="86ed2-112">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
>  <span data-ttu-id="86ed2-113">Aby uzyskać informacje dotyczące sprawdzania i obsługi sprawdzania poprawności błędy i ostrzeżenia, zobacz [wywoływania sprawdzania poprawności działania](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="86ed2-113">For more information about about checking for and handling validation errors and warnings, see [Invoking Activity Validation](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="86ed2-114">Za pomocą grupy metod przeciążonych</span><span class="sxs-lookup"><span data-stu-id="86ed2-114">Using Overload Groups</span></span>  
 <span data-ttu-id="86ed2-115">Grupy metod przeciążonych udostępnia metody wskazujący, które kombinacje argumenty są prawidłowe w działaniu.</span><span class="sxs-lookup"><span data-stu-id="86ed2-115">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="86ed2-116">Argumenty są zgrupowane za pomocą <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="86ed2-116">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="86ed2-117">Każda grupa ma nadane nazwy, która jest określona przez <xref:System.Activities.OverloadGroupAttribute>, działanie jest prawidłowa, gdy tylko jeden zestaw argumentów w grupie metod przeciążonych są powiązane.</span><span class="sxs-lookup"><span data-stu-id="86ed2-117">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>, The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="86ed2-118">W poniższym przykładzie pobierana z [OverloadGroups](../../../docs/framework/windows-workflow-foundation/samples/overloadgroups.md) próbki, `CreateLocation` klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="86ed2-118">In the following example, taken from the [OverloadGroups](../../../docs/framework/windows-workflow-foundation/samples/overloadgroups.md) sample, a `CreateLocation` class is defined.</span></span>  
  
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
  
 <span data-ttu-id="86ed2-119">Celem tego działania jest do określenia lokalizacji w Stanach Zjednoczonych.</span><span class="sxs-lookup"><span data-stu-id="86ed2-119">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="86ed2-120">Aby to zrobić, użytkownik działania można określić lokalizacji przy użyciu jednej z trzech grup argumentów.</span><span class="sxs-lookup"><span data-stu-id="86ed2-120">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="86ed2-121">Aby określić prawidłową kombinację argumenty, trzy grupy metod przeciążonych są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="86ed2-121">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="86ed2-122">`G1` zawiera `Latitude` i `Longitude` argumentów.</span><span class="sxs-lookup"><span data-stu-id="86ed2-122">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="86ed2-123">`G2` zawiera `Street`, `City`, i `State`.</span><span class="sxs-lookup"><span data-stu-id="86ed2-123">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="86ed2-124">`G3` zawiera `Street` i `Zip`.</span><span class="sxs-lookup"><span data-stu-id="86ed2-124">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="86ed2-125">`Name` jest również wymagany argument, ale nie jest częścią grupy przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="86ed2-125">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="86ed2-126">Dla tego działania identyfikator był prawidłowy `Name` musi być powiązane razem wszystkie argumenty z grupy metod przeciążonych jeden i tylko jeden.</span><span class="sxs-lookup"><span data-stu-id="86ed2-126">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="86ed2-127">W poniższym przykładzie pobierana z [działania dostępu do bazy danych](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) przykładowa występują dwa przeciążenia grup: `ConnectionString` i `ConfigFileSectionName`.</span><span class="sxs-lookup"><span data-stu-id="86ed2-127">In the following example, taken from the [Database Access Activities](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="86ed2-128">Dla tego działania identyfikator był prawidłowy, albo `ProviderName` i `ConnectionString` argumentów musi być powiązana, lub `ConfigName` argumentu, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="86ed2-128">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
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
  
 <span data-ttu-id="86ed2-129">Podczas definiowania grupa metod przeciążonych:</span><span class="sxs-lookup"><span data-stu-id="86ed2-129">When defining an overload group:</span></span>  
  
-   <span data-ttu-id="86ed2-130">Grupa metod przeciążonych nie może być podzbiór lub równoważne zbiór innej grupy przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="86ed2-130">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="86ed2-131">Istnieje jeden wyjątek od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="86ed2-131">There is one exception to this rule.</span></span> <span data-ttu-id="86ed2-132">Jeśli grupa metod przeciążonych są podzestawem innej grupy metod przeciążonych i podzbiór zawiera tylko argumenty, gdzie `RequiredArgument` jest `false`, to grupa metod przeciążonych jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="86ed2-132">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
-   <span data-ttu-id="86ed2-133">Grupy metod przeciążonych mogą nakładać się na, ale jeśli przecięciu grupy zawiera wszystkie wymagane argumenty jedną lub obie grupy metod przeciążonych, występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="86ed2-133">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="86ed2-134">W poprzednim przykładzie `G2` i `G3` przeciążenia grup pokrywający się, ale ponieważ przecięcie nie zawierał wszystkie argumenty jednego lub dwóch grup jest to prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="86ed2-134">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="86ed2-135">Podczas tworzenia wiązania argumenty w grupie metod przeciążonych:</span><span class="sxs-lookup"><span data-stu-id="86ed2-135">When binding arguments in an overload group:</span></span>  
  
-   <span data-ttu-id="86ed2-136">Grupa metod przeciążonych jest uznawany za granica, jeśli wszystkie `RequiredArgument` argumentów w grupie są powiązane.</span><span class="sxs-lookup"><span data-stu-id="86ed2-136">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
-   <span data-ttu-id="86ed2-137">Jeśli grupa ma wartość zero `RequiredArgument` argumentów i co najmniej jednego argumentu powiązany, a następnie grupy jest uznawany za powiązane z.</span><span class="sxs-lookup"><span data-stu-id="86ed2-137">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
-   <span data-ttu-id="86ed2-138">Jeśli nie grupy metod przeciążonych są powiązane chyba, że jedna grupa metod przeciążonych nie jest błąd sprawdzania poprawności `RequiredArgument` argumenty w nim.</span><span class="sxs-lookup"><span data-stu-id="86ed2-138">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
-   <span data-ttu-id="86ed2-139">Występuje błąd ma więcej niż jedną grupę metod przeciążonych powiązana, który jest, wszystkie wymagane argumenty w jedna grupa metod przeciążonych są powiązane i wszystkich argumentów w innej grupie przeciążenia jest także powiązany.</span><span class="sxs-lookup"><span data-stu-id="86ed2-139">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
