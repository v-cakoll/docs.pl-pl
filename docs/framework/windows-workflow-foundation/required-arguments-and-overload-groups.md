---
title: Wymagane argumenty i grupy metod przeciążonych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 47e94c65ff722d3b4f98b026d69ecd31bc02b934
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="required-arguments-and-overload-groups"></a>Wymagane argumenty i grupy metod przeciążonych
Można skonfigurować tak, aby niektóre argumenty są wymagane może być powiązane działania jest nieprawidłowy do wykonania działań. `RequiredArgument` Atrybut służy do wskazania, że niektóre argumenty w działaniu wymagane i `OverloadGroup` atrybutów jest używane do grupowania kategorii wymaganych argumentów. Przy użyciu atrybutów, autorzy działania zapewniają prostymi lub złożonymi działanie sprawdzania poprawności konfiguracji.  
  
## <a name="using-required-arguments"></a>Przy użyciu wymaganych argumentów  
 Aby użyć `RequiredArgument` atrybutu w działaniu, określ żądany argumentów, za pomocą <xref:System.Activities.RequiredArgumentAttribute>. W tym przykładzie `Add` działania jest zdefiniowany, że dwa wymaga argumentów.  
  
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
  
 W języku XAML, wymagane argumenty są również oznaczone za pomocą <xref:System.Activities.RequiredArgumentAttribute>. W tym przykładzie `Add` działania jest definiowana za pomocą trzech argumentów i używa <xref:System.Activities.Statements.Assign%601> działanie do wykonania operacji dodawania.  
  
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
  
 Jeśli jest używane działanie i jeden z wymaganych argumentów nie jest powiązany jest zwracany następujący błąd sprawdzania poprawności.  
  
 **Nie podano wartości dla wymaganego argumentu działania "Operand1".**  
> [!NOTE]
>  Aby uzyskać informacje dotyczące sprawdzania i obsługi sprawdzania poprawności błędy i ostrzeżenia, zobacz [wywoływania sprawdzania poprawności działania](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).  
  
## <a name="using-overload-groups"></a>Za pomocą grupy metod przeciążonych  
 Grupy metod przeciążonych udostępnia metody wskazujący, które kombinacje argumenty są prawidłowe w działaniu. Argumenty są zgrupowane za pomocą <xref:System.Activities.OverloadGroupAttribute>. Każda grupa ma nadane nazwy, która jest określona przez <xref:System.Activities.OverloadGroupAttribute>, działanie jest prawidłowa, gdy tylko jeden zestaw argumentów w grupie metod przeciążonych są powiązane. W poniższym przykładzie pobierana z [OverloadGroups](../../../docs/framework/windows-workflow-foundation/samples/overloadgroups.md) próbki, `CreateLocation` klasa jest zdefiniowana.  
  
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
  
 Celem tego działania jest do określenia lokalizacji w Stanach Zjednoczonych. Aby to zrobić, użytkownik działania można określić lokalizacji przy użyciu jednej z trzech grup argumentów. Aby określić prawidłową kombinację argumenty, trzy grupy metod przeciążonych są zdefiniowane. `G1` zawiera `Latitude` i `Longitude` argumentów. `G2` zawiera `Street`, `City`, i `State`. `G3` zawiera `Street` i `Zip`. `Name` jest również wymagany argument, ale nie jest częścią grupy przeciążenia. Dla tego działania identyfikator był prawidłowy `Name` musi być powiązane razem wszystkie argumenty z grupy metod przeciążonych jeden i tylko jeden.  
  
 W poniższym przykładzie pobierana z [działania dostępu do bazy danych](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) przykładowa występują dwa przeciążenia grup: `ConnectionString` i `ConfigFileSectionName`. Dla tego działania identyfikator był prawidłowy, albo `ProviderName` i `ConnectionString` argumentów musi być powiązana, lub `ConfigName` argumentu, ale nie oba.  
  
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
  
 Podczas definiowania grupa metod przeciążonych:  
  
-   Grupa metod przeciążonych nie może być podzbiór lub równoważne zbiór innej grupy przeciążenia.  
  
    > [!NOTE]
    >  Istnieje jeden wyjątek od tej reguły. Jeśli grupa metod przeciążonych są podzestawem innej grupy metod przeciążonych i podzbiór zawiera tylko argumenty, gdzie `RequiredArgument` jest `false`, to grupa metod przeciążonych jest nieprawidłowy.  
  
-   Grupy metod przeciążonych mogą nakładać się na, ale jeśli przecięciu grupy zawiera wszystkie wymagane argumenty jedną lub obie grupy metod przeciążonych, występuje błąd. W poprzednim przykładzie `G2` i `G3` przeciążenia grup pokrywający się, ale ponieważ przecięcie nie zawierał wszystkie argumenty jednego lub dwóch grup jest to prawidłowa.  
  
 Podczas tworzenia wiązania argumenty w grupie metod przeciążonych:  
  
-   Grupa metod przeciążonych jest uznawany za granica, jeśli wszystkie `RequiredArgument` argumentów w grupie są powiązane.  
  
-   Jeśli grupa ma wartość zero `RequiredArgument` argumentów i co najmniej jednego argumentu powiązany, a następnie grupy jest uznawany za powiązane z.  
  
-   Jeśli nie grupy metod przeciążonych są powiązane chyba, że jedna grupa metod przeciążonych nie jest błąd sprawdzania poprawności `RequiredArgument` argumenty w nim.  
  
-   Występuje błąd ma więcej niż jedną grupę metod przeciążonych powiązana, który jest, wszystkie wymagane argumenty w jedna grupa metod przeciążonych są powiązane i wszystkich argumentów w innej grupie przeciążenia jest także powiązany.
