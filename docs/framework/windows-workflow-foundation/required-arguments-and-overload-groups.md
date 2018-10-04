---
title: Wymagane Argumenty i Grupy metod Przeciążonych
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: d25702e573acd9a0815c232cdf6935d6e9651631
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2018
ms.locfileid: "48244870"
---
# <a name="required-arguments-and-overload-groups"></a>Wymagane Argumenty i Grupy metod Przeciążonych
Działania można skonfigurować tak, aby niektóre argumenty są wymagane powiązać na ważne potrzeby wykonywania działania. `RequiredArgument` Atrybut jest używany do wskazania, że niektórych argumentów w ramach działania są wymagane i `OverloadGroup` atrybut służy do grupowania kategorii wymaganych argumentów. Za pomocą atrybutów, autorzy działanie może zapewnić proste lub złożone działanie sprawdzania poprawności konfiguracji.  
  
## <a name="using-required-arguments"></a>Przy użyciu wymaganych argumentów  
 Aby użyć `RequiredArgument` atrybutu w działaniu, określ żądany argumentów, za pomocą <xref:System.Activities.RequiredArgumentAttribute>. W tym przykładzie `Add` działania jest zdefiniowana, że ma dwa wymagane argumenty.  
  
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
  
 W XAML, wymagane argumenty są również oznaczane przy użyciu <xref:System.Activities.RequiredArgumentAttribute>. W tym przykładzie `Add` działania jest definiowana za pomocą trzech argumentów i zastosowania <xref:System.Activities.Statements.Assign%601> działania do wykonania operacji dodawania.  
  
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
  
 Jeśli działanie jest używane, a jeden z wymaganych argumentów nie jest powiązany jest zwracany następujący błąd sprawdzania poprawności.  
  
 **Nieprawidłowa wartość argumentu wymagane działania "Operand1".**  
> [!NOTE]
> Aby uzyskać informacje dotyczące sprawdzania i obsługa błędy i ostrzeżenia walidacji, zobacz [wywoływanie walidacji działania](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).  
  
## <a name="using-overload-groups"></a>Za pomocą Grupy metod Przeciążonych

Grupy metod przeciążonych udostępnia metody wskazujące, które kombinacje argumenty są prawidłowe w działaniu. Argumenty są zgrupowane za pomocą <xref:System.Activities.OverloadGroupAttribute>. Każda grupa otrzymuje nazwę, która jest określona przez <xref:System.Activities.OverloadGroupAttribute>. Działanie jest prawidłowa, gdy tylko jeden zestaw argumentów w grupie przeciążenia są powiązane. W poniższym przykładzie `CreateLocation` klasa jest zdefiniowana.  
  
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
  
 Celem tego działania jest aby określić lokalizację, w stanach Zjednoczonych. Aby to zrobić, użytkownik działania można określić lokalizacji przy użyciu jednej z trzech grup argumentów. Aby określić prawidłową kombinacji argumentów, trzy grupy metod przeciążonych są zdefiniowane. `G1` zawiera `Latitude` i `Longitude` argumentów. `G2` zawiera `Street`, `City`, i `State`. `G3` zawiera `Street` i `Zip`. `Name` Ponadto argument jest wymagany, ale nie jest częścią grupy przeciążenia. Dla tego działania był prawidłowy `Name` musi powiązać razem z wszystkie argumenty z grupy przeciążenia jeden i tylko jeden.  
  
 W poniższym przykładzie pobierana z [działań w bazie danych programu Access](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) próbki, istnieją dwa przeciążenia grup: `ConnectionString` i `ConfigFileSectionName`. Dla tego działania był prawidłowy, albo `ProviderName` i `ConnectionString` argumentów musi być powiązana, lub `ConfigName` argumentów, ale nie oba.  
  
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
  
 Podczas definiowania grupę przeciążenia:  
  
-   Grupę przeciążenia nie może być podzbiór lub zbiór równoważny, innej grupy przeciążenia.  
  
    > [!NOTE]
    >  Istnieje jeden wyjątek od tej reguły. Jeśli grupa przeciążenie jest podzbiorem innej grupy przeciążenia i podzbiór zawiera tylko argumenty gdzie `RequiredArgument` jest `false`, grupy przeciążenie jest nieprawidłowy.  
  
-   Grupy metod przeciążonych może pokrywać się, ale jest to błąd, jeśli na przecięciu grupy zawiera wszystkie wymagane argumenty z jedną lub obie grupy metod przeciążonych. W poprzednim przykładzie `G2` i `G3` przeciążać nakładających się grup, ale ponieważ wspólną nie zawierała wszystkie argumenty jednego lub dwóch grup była nieprawidłowa.  
  
 Podczas tworzenia powiązania argumentów w grupie przeciążenia:  
  
-   Grupę przeciążenie jest uznawany za powiązane z, jeśli wszystkie `RequiredArgument` argumentów w grupie są powiązane.  
  
-   Jeśli grupa zawiera zero `RequiredArgument` argumentów i co najmniej jednego argumentu powiązania, a następnie grupy jest uznawany za granicę.  
  
-   Jeśli nie grupy metod przeciążonych są powiązane, chyba że nie ma jednej grupy przeciążenia, występuje błąd sprawdzania poprawności `RequiredArgument` argumentów w nim.  
  
-   Jest błędem do więcej niż jedna grupa przeciążenia, powiązana, będącego, wszystkie wymagane argumenty z kilkoma przeciążeniami grupy są powiązane i wszystkich argumentów w innej grupie przeciążenie jest również powiązane.
