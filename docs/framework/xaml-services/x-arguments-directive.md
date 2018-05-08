---
title: x:Arguments — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: e0e7f380ec176e80d2422878a2e676d64985d660
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xarguments-directive"></a>x:Arguments — dyrektywa
Argumenty konstrukcji pakietów z systemem innym niż domyślny konstruktor obiektu deklaracji elementu w języku XAML, lub fabryki metody obiektu.  
  
## <a name="xaml-element-usage-nondefault-constructor"></a>Użycie elementu XAML (inny niż domyślny konstruktor)  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>Użycie elementu XAML (metoda fabryki)  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|Co najmniej jeden element obiektu określających argumenty do przekazania do tworzenia kopii innych niż domyślne konstruktora lub metody fabryki.<br /><br /> Typowe jest używane do inicjowania tekstu w elementach obiektu umożliwia określenie wartości rzeczywistych argumentów. Zobacz sekcję dotyczącą przykłady.<br /><br /> Kolejność elementów jest znacząca. Typy XAML w kolejności musi pasują do typów, a następnie wpisz kolejność przeciążenie metody konstruktora lub fabryki zapasowego.|  
|`methodName`|Nazwa metody fabryki, która ma być przetwarzana żadnego `x:Arguments` argumentów.|  
  
## <a name="dependencies"></a>Zależności  
 `x:FactoryMethod` można zmodyfikować zakresu i zachowanie gdzie `x:Arguments` ma zastosowanie.  
  
 Jeśli nie `x:FactoryMethod` jest określony, `x:Arguments` dotyczy alternatywny podpisów (z systemem innym niż domyślny) konstruktorów zapasowego.  
  
 Jeśli `x:FactoryMethod` jest określony, `x:Arguments` dotyczy przeciążenia metody o nazwie.  
  
## <a name="remarks"></a>Uwagi  
 XAML 2006 może obsługiwać inicjowania inny niż domyślny za pomocą inicjowania tekstu. Praktyczne zastosowania technikę konstrukcji tekstu inicjowania jest jednak ograniczona. Inicjowanie tekst jest traktowany jako jeden ciąg tekstowy; w związku z tym tylko dodaje możliwość inicjowania pojedynczy parametr Jeśli konwerter typów nie jest zdefiniowany dla konstrukcji zachowanie można analizować elementy niestandardowe informacje i niestandardowych ograniczniki z ciągu. Ciąg tekstowy do obiektu logiki jest również potencjalnie konwerter typów natywnych domyślne danego analizatora XAML do obsługi podstawowych innego niż ciąg wartość true.  
  
 `x:Arguments` Użycie języka XAML nie jest użycie elementu właściwości w tym sensie, typowe, ponieważ znacznika dyrektywy nie odwołuje się do typu zawierającego element object. Jest więcej podobnie dyrektyw takich jak `x:Code` gdzie element demarks zakresu, w którym kod znaczników powinny być rozumiane jako inny niż domyślny dla podrzędnej zawartości. W takim przypadku typu XAML każdego elementu obiektu komunikuje się informacje o typy argumentów, co jest używany przez analizatory składni języka XAML w celu określenia podpisów metody fabryki określonego konstruktora `x:Arguments` użycia próbuje odwołać.  
  
 `x:Arguments` dla obiekt elementu budowany musi poprzedzać inne elementy właściwości, zawartość, tekst wewnętrzny ani ciągi inicjowanie obiektu elementu. Elementy obiektu wewnątrz `x:Arguments` mogą zawierać atrybuty i ciągi inicjowania dozwolonych przez tego typu XAML i jego zapasowy konstruktora lub metody fabryki. Dla obiekt lub argumentów można określić niestandardowych typów XAML lub XAML znajdujących się w przeciwnym razie poza domyślnej przestrzeni nazw XAML za pomocą odwołań do mapowania prefiksów ustalonych.  
  
 Procesory XAML, skorzystaj z poniższych wskazówek ustalenie sposobu określania argumentów w `x:Arguments` powinien zostać użyty do utworzenia obiektu. Jeśli `x:FactoryMethod` określono informacji jest porównywany do określonego `x:FactoryMethod` (należy pamiętać, że wartość `x:FactoryMethod` nazwę metody, a metodę o nazwie mogą mieć przeciążenia. Jeśli `x:FactoryMethod` nie zostanie określony, informacje są porównywane do zestawu wszystkich przeciążeń konstruktora publicznego obiektu. Logika przetwarzania XAML następnie porównuje liczbę parametrów i wybiera przeciążenia z dopasowania argumentów. Jeśli istnieje więcej niż jedno dopasowanie, procesor XAML należy porównać typów parametrów, na podstawie typów XAML elementów udostępnionego obiektu. W przypadku nadal więcej niż jedno dopasowanie XAML procesora jest niezdefiniowany. Jeśli `x:FactoryMethod` jest określony, ale nie można rozpoznać metody, procesor XAML powinien zgłosić wyjątek.  
  
 Użycie atrybutu XAML `<x:Arguments>string</x:Arguments>` jest technicznie możliwe. Zapewnia to nie możliwości poza co można zrobić w przeciwnym razie za pośrednictwem konwertery tekst i typ inicjowania i przy użyciu tej składni nie jest zamiar projektu XAML 2009 funkcji metody fabryki.  
  
## <a name="examples"></a>Przykłady  
 W poniższym przykładzie przedstawiono z systemem innym niż domyślny konstruktor podpisu, a następnie użycie XAML `x:Arguments` który uzyskuje dostęp do tego podpisu.  
  
```csharp  
public class Food {  
    private string _name;  
    private Int32 _calories;  
    public Food(string name, Int32 calories) {  
        _name=name;  
        _calories=calories;  
    }  
}  
```  
  
```xaml  
<my:Food>  
    <x:Arguments>  
        <x:String>Apple</x:String>  
        <x:Int32>150</x:Int32>  
    </x:Arguments>  
</my:Food>  
```  
  
 W poniższym przykładzie przedstawiono sygnatury metody fabryki docelowego, a następnie użycie XAML `x:Arguments` który uzyskuje dostęp do tego podpisu.  
  
```csharp  
public Food TryLookupFood(string name)  
{  
  switch (name) {  
    case "Apple": return new Food("Apple",150);  
    case "Chocolate": return new Food("Chocolate",200);  
    case "Cheese": return new Food("Cheese", 450);  
    default: {return new Food(name,0);  
  }  
}  
```  
  
```xaml  
<my:Food x:FactoryMethod="TryLookupFood">  
    <x:Arguments>  
        <x:String>Apple</x:String>  
    </x:Arguments>  
</my:Food>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie typów niestandardowych do użytku z usługami .NET Framework XAML](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)  
 [Przegląd XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
