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
# <a name="required-arguments-and-overload-groups"></a>Wymagane argumenty i grupy metod przeciążonych
Działania można skonfigurować tak, aby niektóre argumenty muszą być powiązane dla działania, które mają być prawidłowe do wykonania. Atrybut `RequiredArgument` jest używany do wskazania, że niektóre argumenty `OverloadGroup` na działanie są wymagane i atrybut jest używany do grupowanie kategorii wymaganych argumentów razem. Za pomocą atrybutów autorzy działań można zapewnić proste lub złożone konfiguracje sprawdzania poprawności działania.  
  
## <a name="using-required-arguments"></a>Korzystanie z wymaganych argumentów  
 Aby użyć `RequiredArgument` atrybutu w działaniu, należy <xref:System.Activities.RequiredArgumentAttribute>wskazać żądane argumenty za pomocą programu . W tym przykładzie zdefiniowano `Add` działanie, które ma dwa wymagane argumenty.  
  
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
  
 W języku XAML wymagane argumenty są <xref:System.Activities.RequiredArgumentAttribute>również wskazywane za pomocą programu . W tym `Add` przykładzie działanie jest definiowane przy <xref:System.Activities.Statements.Assign%601> użyciu trzech argumentów i używa działania do wykonania operacji dodawania.  
  
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
  
 Jeśli działanie jest używane i jeden z wymaganych argumentów nie jest związany następujący błąd sprawdzania poprawności jest zwracany.  
  
 **Wartość wymaganego argumentu działania "Operand1" nie została dostarczona.**  
> [!NOTE]
> Aby uzyskać więcej informacji na temat sprawdzania błędów i ostrzeżeń sprawdzania poprawności i obsługi ich, zobacz [Wywoływanie sprawdzania poprawności działania](invoking-activity-validation.md).  
  
## <a name="using-overload-groups"></a>Korzystanie z grup przeciążenia

Grupy przeciążenia zapewniają metodę wskazującą, które kombinacje argumentów są prawidłowe w działaniu. Argumenty są zgrupowane <xref:System.Activities.OverloadGroupAttribute>razem za pomocą programu . Każdej grupie otrzymuje się nazwę określoną przez plik <xref:System.Activities.OverloadGroupAttribute>. Działanie jest prawidłowe, gdy tylko jeden zestaw argumentów w grupie przeciążenia są powiązane. W poniższym przykładzie zdefiniowano `CreateLocation` klasę.  
  
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
  
 Celem tego działania jest określenie lokalizacji w STANACH Zjednoczonych. Aby to zrobić, użytkownik działania można określić lokalizację przy użyciu jednej z trzech grup argumentów. Aby określić prawidłowe kombinacje argumentów, zdefiniowane są trzy grupy przeciążenia. `G1`zawiera `Latitude` argumenty `Longitude` i argumenty. `G2`zawiera `Street` `City`, `State`i . `G3`zawiera `Street` `Zip`i . `Name`jest również wymaganym argumentem, ale nie jest częścią grupy przeciążenia. Aby to działanie było `Name` prawidłowe, musiałoby być powiązane ze wszystkimi argumentami z jednej i tylko jednej grupy przeciążenia.  
  
 W poniższym przykładzie pobranym z przykładu Działania dostępu do `ConnectionString` `ConfigFileSectionName` [bazy danych](./samples/database-access-activities.md) istnieją dwie grupy przeciążenia: i . Aby to działanie było prawidłowe, argumenty `ProviderName` i `ConnectionString` muszą `ConfigName` być powiązane lub argument, ale nie oba.  
  
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
  
- Grupa przeciążenia nie może być podzbiorem ani równoważnym zestawem innej grupy przeciążenia.  
  
    > [!NOTE]
    > Istnieje jeden wyjątek od tej reguły. Jeśli grupa przeciążenia jest podzbiorem innej grupy przeciążenia, `RequiredArgument` `false`a podzbiór zawiera tylko argumenty, gdzie jest , grupa przeciążenia jest prawidłowa.  
  
- Grupy przeciążenia mogą się nakładać, ale jest to błąd, jeśli przecięcie grup zawiera wszystkie wymagane argumenty jednej lub obu grup przeciążenia. W poprzednim `G2` przykładzie `G3` i przeciążenia grup nakładających się, ale ponieważ przecięcie nie zawiera wszystkie argumenty jednej lub obu grup to było prawidłowe.  
  
 Podczas wiązania argumentów w grupie przeciążenia:  
  
- Grupa przeciążenia jest uważana `RequiredArgument` za powiązaną, jeśli wszystkie argumenty w grupie są powiązane.  
  
- Jeśli grupa ma `RequiredArgument` zero argumentów i co najmniej jeden argument związany, a następnie grupa jest uważany za związany.  
  
- Jest to błąd sprawdzania poprawności, jeśli nie grupy przeciążenia są powiązane, chyba że jedna grupa przeciążenia nie `RequiredArgument` ma argumentów w nim.  
  
- Jest to błąd, aby mieć więcej niż jedną grupę przeciążenia związane, oznacza to, że wszystkie wymagane argumenty w jednej grupie przeciążenia są powiązane i każdy argument w innej grupie przeciążenia jest również powiązany.
