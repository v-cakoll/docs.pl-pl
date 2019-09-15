---
title: Wymagane argumenty i grupy metod przeciążonych
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 84384e90be0036036477d9b4249832f544e17d08
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989307"
---
# <a name="required-arguments-and-overload-groups"></a>Wymagane argumenty i grupy metod przeciążonych
Działania można skonfigurować tak, aby pewne argumenty były powiązane z prawidłowym działaniem do wykonania. Ten `RequiredArgument` atrybut służy do wskazywania, że określone argumenty działania są wymagane `OverloadGroup` , a atrybut jest używany do grupowania kategorii wymaganych argumentów razem. Przy użyciu atrybutów autorzy działań mogą zapewnić proste lub złożone konfiguracje weryfikacji działania.  
  
## <a name="using-required-arguments"></a>Używanie wymaganych argumentów  
 Aby użyć `RequiredArgument` atrybutu w działaniu, należy wskazać odpowiednie argumenty przy użyciu <xref:System.Activities.RequiredArgumentAttribute>. W tym przykładzie `Add` zdefiniowano działanie, które ma dwa wymagane argumenty.  
  
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
  
 W języku XAML wymagane argumenty są również wskazywane przy <xref:System.Activities.RequiredArgumentAttribute>użyciu. W tym przykładzie `Add` działanie jest zdefiniowane przy użyciu trzech argumentów i <xref:System.Activities.Statements.Assign%601> używa działania do wykonania operacji dodawania.  
  
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
  
 Jeśli działanie jest używane i jeden z wymaganych argumentów nie jest powiązany, zwracany jest następujący błąd sprawdzania poprawności.  
  
 **Nie podano wartości dla wymaganego argumentu działania "Operand1".**  
> [!NOTE]
> Aby uzyskać więcej informacji na temat sprawdzania i obsługi błędów i ostrzeżeń walidacji, zobacz [wywoływanie walidacji działania](invoking-activity-validation.md).  
  
## <a name="using-overload-groups"></a>Korzystanie z grup przeciążeń

Grupy przeciążeń zapewniają metodę wskazującą, które kombinacje argumentów są prawidłowe w działaniu. Argumenty są pogrupowane przy użyciu <xref:System.Activities.OverloadGroupAttribute>. Każda grupa otrzymuje nazwę określoną przez <xref:System.Activities.OverloadGroupAttribute>. Działanie jest prawidłowe, gdy są powiązane tylko jeden zestaw argumentów w grupie przeciążeń. W poniższym przykładzie `CreateLocation` zdefiniowano klasę.  
  
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
  
 Celem tego działania jest określenie lokalizacji w Stanach Zjednoczonych. W tym celu użytkownik działania może określić lokalizację przy użyciu jednej z trzech grup argumentów. Aby określić prawidłowe kombinacje argumentów, definiowane są trzy grupy przeciążeń. `G1`zawiera argumenty `Longitude`i. `Latitude` `G2`zawiera `Street`, `City`i .`State` `G3`zawiera `Street` i `Zip`. `Name`jest również argumentem wymaganym, ale nie jest częścią grupy przeciążenia. Aby to działanie było prawidłowe, `Name` musi być powiązane ze wszystkimi argumentami z jednej i tylko jednej grupy przeciążeń.  
  
 W poniższym przykładzie z przykładu działania dotyczące [dostępu do bazy danych](./samples/database-access-activities.md) istnieją dwie grupy przeciążeń: `ConnectionString` i `ConfigFileSectionName`. Aby to działanie było prawidłowe, `ProviderName` argumenty i `ConnectionString` muszą `ConfigName` być powiązane albo argument, ale nie oba.  
  
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
  
 Podczas definiowania grupy przeciążenia:  
  
- Grupa przeciążenia nie może być podzbiorem lub równoważnym zestawem innej grupy przeciążeń.  
  
    > [!NOTE]
    > Istnieje jeden wyjątek dla tej reguły. Jeśli grupa przeciążeń jest podzbiorem innej grupy przeciążeń, a podzestaw zawiera tylko `RequiredArgument` argumenty `false`, gdzie is, to grupa przeciążenia jest prawidłowa.  
  
- Grupy przeciążeń mogą się nakładać, ale jest to błąd, jeśli część wspólna grup zawiera wszystkie wymagane argumenty jednej lub obu grup przeciążenia. W poprzednim przykładzie `G2` grupy i `G3` przeciążania nakładają się na siebie, ale ponieważ część wspólna nie zawiera wszystkich argumentów jednej lub obu grup, które były prawidłowe.  
  
 Podczas wiązania argumentów w grupie przeciążenia:  
  
- Grupa przeciążenia jest uznawana za powiązaną, `RequiredArgument` Jeśli wszystkie argumenty w grupie są powiązane.  
  
- Jeśli grupa ma argumenty zero `RequiredArgument` i powiązana jest co najmniej jeden argument, Grupa jest uznawana za powiązaną.  
  
- Jest to błąd walidacji, jeśli żadne grupy przeciążenia nie są powiązane, chyba że jedna `RequiredArgument` Grupa przeciążenia nie ma żadnych argumentów.  
  
- Występuje błąd z więcej niż jedną powiązaną grupą przeciążeń, to oznacza, że wszystkie wymagane argumenty w jednej grupie przeciążeń są powiązane i dowolny argument w innej grupie przeciążeń jest również powiązany.
