---
title: x:Arguments — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: a87542513ffeeec7efc526d4218f921d1b7579a1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184850"
---
# <a name="xarguments-directive"></a>x:Arguments — dyrektywa
Pakiety argumentów deklaracji elementu innego niż domyślny konstruktor obiektu w XAML lub dla deklaracji obiektu metody fabryki.  
  
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
|`oneOrMoreObjectElements`|Co najmniej jeden element obiektu, które określają argumenty, które mają być przekazane do metody konstruktora lub fabryki innych niż domyślne tworzenie kopii.<br /><br /> Typowy jest Użyj tekstu inicjowanie elementów obiektu, aby określić wartości rzeczywistych argumentów. Zobacz sekcję przykłady.<br /><br /> Kolejność elementów jest znaczący. Typy XAML w kolejności musi pasują do typów, a następnie wpisz kolejność przeciążenia metody konstruktora lub fabryki zapasowy.|  
|`methodName`|Nazwa metody fabryka, która ma być przetwarzana dowolne `x:Arguments` argumentów.|  
  
## <a name="dependencies"></a>Zależności  
 `x:FactoryMethod` można zmodyfikować zakres i zachowanie gdzie `x:Arguments` ma zastosowanie.  
  
 Jeśli nie `x:FactoryMethod` jest określony, `x:Arguments` stosuje się do alternatywnego podpisy (innych niż domyślne) konstruktorów zapasowy.  
  
 Jeśli `x:FactoryMethod` jest określony, `x:Arguments` ma zastosowanie do przeciążenia metody o nazwie.  
  
## <a name="remarks"></a>Uwagi  
 XAML 2006 może obsługiwać inicjowania inny niż domyślny za pomocą inicjowania tekstu. Praktyczne zastosowanie technikę konstrukcji tekstu inicjowania jest jednak ograniczona. Inicjowanie tekst jest traktowany jako jeden ciąg tekstowy; w związku z tym tylko dodaje możliwość inicjowania jeden parametr, chyba że konwertera typów jest zdefiniowany dla zachowanie konstrukcji, które mogą przeanalizować elementów niestandardowych informacji oraz niestandardowego ograniczników z ciągu. Ciąg tekstowy do logiki obiektu jest również potencjalnie konwertera typów natywnych domyślną danego analizatora XAML do obsługi podstawowych innych niż ciąg wartość true.  
  
 `x:Arguments` Użycia XAML nie jest użycie elementu właściwości w sensie typowe, ponieważ znaczników dyrektywy nie odwołuje się do typu elementu obiektu nadrzędnego. Więcej podobnie inne dyrektywy to taki jak `x:Code` gdzie element demarks zakresu, w którym znaczniki powinny być interpretowane jako inny niż domyślny dla podrzędnej zawartości. W tym przypadku typ XAML każdego elementu obiektu komunikuje się informacji na temat typów argumentu, używany przez analizatory składni XAML, aby określić, które podpis metody fabryka konstruktora określonego `x:Arguments` próbuje odwoływać się do użycia.  
  
 `x:Arguments` elementu obiektu budowany musi poprzedzać wszystkie inne elementy właściwości, zawartości, tekst wewnętrzny lub inicjowania ciągi elementu obiektu. Elementy obiektu w ramach `x:Arguments` mogą one obejmować atrybuty i parametry inicjowania dozwolonym przez tego typu XAML oraz sposób jej zapasowy konstruktora lub fabryki. Dla obiektu lub argumenty można określić niestandardowe typy XAML lub XAML znajdujących się w przeciwnym razie poza domyślna przestrzeń nazw XAML, odwołując się do mapowania prefiksów ustalonych.  
  
 Procesory XAML skorzystaj z poniższych wskazówek, aby określić, jak argumenty określone w `x:Arguments` powinien zostać użyty do utworzenia obiektu. Jeśli `x:FactoryMethod` jest określony, są porównywane do określonego `x:FactoryMethod` (należy pamiętać, że wartość `x:FactoryMethod` jest nazwa metody, a metody nazwanej, mogą mieć przeciążenia. Jeśli `x:FactoryMethod` nie zostanie określony, są porównywane do zestawu wszystkich przeciążeń konstruktora publicznego obiektu. Logika przetwarzania XAML następnie porównuje liczbę parametrów i wybiera przeciążenia za pomocą dopasowywania argumentów. Jeśli istnieje więcej niż jedno dopasowanie, procesor XAML należy porównać typy parametrów na podstawie typów XAML elementów udostępnionego obiektu. W przypadku nadal więcej niż jedno dopasowanie zachowanie procesora XAML jest niezdefiniowane. Jeśli `x:FactoryMethod` jest określony, ale metoda nie można rozwiązać, procesor XAML powinien zgłosić wyjątek.  
  
 Użycie atrybutu XAML `<x:Arguments>string</x:Arguments>` jest technicznie możliwa. Zapewnia to nie możliwości poza co można zrobić w przeciwnym razie za pomocą inicjowania tekst i wpisać konwerterów i przy użyciu tej składni nie jest zamiar projektu funkcji metoda fabryki XAML 2009.  
  
## <a name="examples"></a>Przykłady  
 W poniższym przykładzie pokazano bez domyślnego konstruktora podpisu, a następnie użycie XAML `x:Arguments` , uzyskuje dostęp ten podpis.  
  
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
  
 W poniższym przykładzie pokazano podpis metody fabryki docelowego, a następnie użycie XAML `x:Arguments` , uzyskuje dostęp ten podpis.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Definiowanie typów niestandardowych do użytku z usługami .NET Framework XAML](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [Omówienie XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
