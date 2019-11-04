---
title: x:Arguments — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 338286b417c78b7cceeb30188e888928a15607cd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458653"
---
# <a name="xarguments-directive"></a>x:Arguments — dyrektywa
Argumenty konstrukcji pakietów dla deklaracji elementu obiektu konstruktora bez parametrów w języku XAML lub dla deklaracji obiektu metody fabryki.  
  
## <a name="xaml-element-usage-nonparameterless-constructor"></a>Użycie elementu XAML (Konstruktor bez parametrów)  
  
```xaml  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>Użycie elementu XAML (Metoda Factory)  
  
```xaml  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|Co najmniej jeden element obiektu, który określa argumenty, które mają być przekazane do tworzenia kopii zapasowej konstruktora bez parametrów lub metody fabryki.<br /><br /> Typowym zastosowaniem jest użycie tekstu inicjującego wewnątrz elementów obiektów w celu określenia rzeczywistych wartości argumentów. Zobacz sekcję przykłady.<br /><br /> Kolejność elementów jest istotna. Typy XAML w kolejności muszą być zgodne z typami i kolejnością typu w konstruktorze zapasowym lub przeciążenia metody fabryki.|  
|`methodName`|Nazwa metody fabryki, która powinna przetwarzać dowolne `x:Arguments` argumenty.|  
  
## <a name="dependencies"></a>Zależności  
 `x:FactoryMethod` może zmodyfikować zakres i zachowanie, w których `x:Arguments` ma zastosowanie.  
  
 Jeśli `x:FactoryMethod` nie zostanie określona, `x:Arguments` ma zastosowanie do alternatywnych podpisów (innych niż domyślne) konstruktorów zapasowych.  
  
 Jeśli `x:FactoryMethod` jest określony, `x:Arguments` ma zastosowanie do przeciążenia nazwanej metody.  
  
## <a name="remarks"></a>Uwagi  
 KOD XAML 2006 może obsługiwać inicjalizację niedomyślną za pomocą tekstu inicjującego. Jednak praktyczne zastosowania techniki tworzenia tekstu inicjującego są ograniczone. Tekst inicjujący jest traktowany jako pojedynczy ciąg tekstowy. w związku z tym tylko dodaje możliwość inicjowania jednego parametru, chyba że konwerter typu jest zdefiniowany dla zachowania konstrukcji, które może analizować niestandardowe elementy informacji i niestandardowe ograniczniki z ciągu. Ponadto ciąg tekstowy do logiki obiektu jest potencjalnie oddzielnym domyślnym konwerterem typu analizatora XAML do obsługi elementów pierwotnych innych niż ciąg prawdziwy.  
  
 Użycie języka XAML `x:Arguments` nie jest użycie elementu właściwości w typowym sensie, ponieważ znacznik dyrektywy nie odwołuje się do typu zawierającego element obiektu. Więcej zbliżone do innych dyrektyw, takich jak `x:Code`, gdzie element demarkuje zakres, w którym Adiustacja powinna być interpretowana jako inna niż domyślna dla zawartości podrzędnej. W takim przypadku typ XAML każdego elementu obiektu komunikuje informacje o typach argumentów, które są używane przez analizatory języka XAML do określenia, który określony Konstruktor metody fabryki ma `x:Arguments` użycie próbuje się odwołać.  
  
 `x:Arguments` dla konstruowanego elementu obiektu musi poprzedzać wszystkie inne elementy właściwości, zawartość, tekst wewnętrzny lub ciągi inicjujące elementu Object. Elementy obiektu w `x:Arguments` mogą zawierać atrybuty i ciągi inicjujące, zgodnie z dozwolonymi przez ten typ XAML i jego konstruktorem zapasowym lub metodą fabryki. Dla obiektu lub argumentów można określić niestandardowe typy XAML lub typy XAML, które w przeciwnym wypadku poza domyślną przestrzenią nazw XAML przez odwołanie się do ustanowionych mapowań prefiksów.  
  
 Procesory XAML wykorzystują następujące wytyczne, aby określić, jak argumenty określone w `x:Arguments` powinny być używane do konstruowania obiektu. Jeśli `x:FactoryMethod` jest określony, informacje są porównywane z określoną `x:FactoryMethod` (należy zauważyć, że wartość `x:FactoryMethod` jest nazwą metody, a nazwana Metoda może mieć przeciążenia. Jeśli nie określono `x:FactoryMethod`, informacje są porównywane z zestawem wszystkich przeciążeń konstruktora publicznego obiektu. Logika przetwarzania XAML następnie porównuje liczbę parametrów i wybiera przeciążenia z pasującymi liczbami argumentów. Jeśli istnieje więcej niż jedno dopasowanie, procesor XAML powinien porównać typy parametrów na podstawie typów XAML podanych elementów obiektu. Jeśli nadal istnieje więcej niż jedno dopasowanie, zachowanie procesora XAML jest niezdefiniowane. Jeśli określono `x:FactoryMethod` ale nie można rozpoznać metody, procesor XAML powinien zgłosić wyjątek.  
  
 Użycie atrybutu XAML `<x:Arguments>string</x:Arguments>` jest technicznie możliwe. Nie ma jednak możliwości wykraczających poza to, co można zrobić za pomocą tekstu inicjującego i konwerterów typów, a korzystanie z tej składni nie jest zamiarem projektu dla funkcji metody fabryki języka XAML 2009.  
  
## <a name="examples"></a>Przykłady  
 Poniższy przykład przedstawia sygnaturę konstruktora bez parametrów, a następnie użycie kodu XAML `x:Arguments`, który uzyskuje dostęp do tej sygnatury.  
  
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
  
 Poniższy przykład przedstawia sygnaturę docelowej metody fabryki, a następnie użycie kodu XAML `x:Arguments`, który uzyskuje dostęp do tej sygnatury.  
  
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
- [Przegląd XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
