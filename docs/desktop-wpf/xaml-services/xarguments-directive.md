---
title: x:Arguments — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5ec6e192688e1065ea847db6c175ad9da0e743fe
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071592"
---
# <a name="xarguments-directive"></a>x:Arguments — dyrektywa

Pakiety argumenty konstrukcyjne dla nieswęzowej deklaracji elementu obiektu konstruktora w XAML lub dla deklaracji obiektu metody fabrycznej.

## <a name="xaml-element-usage-nonparameterless-constructor"></a>Użycie elementu XAML (konstruktor bezparametrowy)

```xaml
<object ...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-element-usage-factory-method"></a>Użycie elementu XAML (metoda fabryczna)

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
|`oneOrMoreObjectElements`|Jeden lub więcej elementów obiektu, które określają argumenty, które mają być przekazywane do kopii nieparzemetryczne konstruktora lub metody fabrycznej.<br /><br /> Typowym zastosowaniem jest użycie tekstu inicjowania w elementach obiektu w celu określenia rzeczywistych wartości argumentów. Zobacz przykłady sekcji.<br /><br /> Kolejność elementów jest znacząca. Typy XAML w kolejności musi odpowiadać typy i kolejność typów konstruktora kopii zapasowej lub przeciążenie metody fabrycznej.|
|`methodName`|Nazwa metody fabrycznej, która `x:Arguments` powinna przetwarzać wszystkie argumenty.|

## <a name="dependencies"></a>Zależności

`x:FactoryMethod`można zmodyfikować zakres `x:Arguments` i zachowanie, gdzie ma zastosowanie.

Jeśli `x:FactoryMethod` nie jest `x:Arguments` określony, stosuje się do alternatywnych (nie domyślne) podpisy konstruktorów kopii zapasowej.

Jeśli `x:FactoryMethod` jest `x:Arguments` określony, stosuje się do przeciążenia nazwanej metody.

## <a name="remarks"></a>Uwagi

XAML 2006 może obsługiwać inicjowanie inne niż domyślne za pomocą tekstu inicjowania. Jednak praktyczne zastosowanie techniki budowy tekstu inicjowania jest ograniczone. Tekst inicjowania jest traktowany jako pojedynczy ciąg tekstowy; w związku z tym tylko dodaje możliwości inicjowania pojedynczego parametru, chyba że konwerter typu jest zdefiniowany dla zachowania konstrukcji, które można przeanalizować elementy informacji niestandardowych i niestandardowe ograniczniki z ciągu. Ponadto ciąg tekstowy do logiki obiektu jest potencjalnie natywnego konwertera typu domyślnego analizatora analizatora XAML do obsługi podstawowego niż ciąg rzeczywisty.

Użycie `x:Arguments` XAML nie jest użycie elementu właściwości w typowym sensie, ponieważ znaczników dyrektywy nie odwołuje się do typu elementu zawierającego obiekt. Jest bardziej zbliżona do innych `x:Code` dyrektyw, takich jak gdzie element demarks zakres, w którym znaczników powinny być interpretowane jako inne niż domyślne dla zawartości podrzędnej. W takim przypadku typ XAML każdego elementu obiektu komunikuje informacje o typach argumentów, który jest używany przez `x:Arguments` analizatory XAML do określenia, który podpis metody fabrycznej konstruktora próbuje odwołać.

`x:Arguments`dla elementu obiektu konstruowany musi poprzedzać inne elementy właściwości, zawartość, tekst wewnętrzny lub ciągi inicjowania elementu obiektu. Elementy obiektu `x:Arguments` wewnątrz mogą zawierać atrybuty i ciągi inicjowania, zgodnie z tym typem XAML i jego konstruktorem zapasowym lub metodą fabryczną. Dla obiektu lub argumentów można określić niestandardowe typy XAML lub typy XAML, które w przeciwnym razie znajdują się poza domyślnym obszarem nazw XAML, odwołując się do ustalonych mapowań prefiksów.

Procesory XAML używają następujących wskazówek, aby `x:Arguments` określić, w jaki sposób argumenty określone w powinny być używane do konstruowania obiektu. Jeśli `x:FactoryMethod` jest określony, informacje są `x:FactoryMethod` porównywane z `x:FactoryMethod` określonym (należy zauważyć, że wartość jest nazwą metody, a nazwana metoda może mieć przeciążenia. Jeśli `x:FactoryMethod` nie jest określony, informacje są porównywane z zestawem wszystkich przeciążeń konstruktora publicznego obiektu. Logika przetwarzania XAML następnie porównuje liczbę parametrów i wybiera przeciążenie z pasującymi arity. Jeśli istnieje więcej niż jedno dopasowanie, procesor XAML należy porównać typy parametrów na podstawie typów XAML podanych elementów obiektu. Jeśli nadal istnieje więcej niż jedno dopasowanie, zachowanie procesora XAML jest niezdefiniowane. Jeśli `x:FactoryMethod` a jest określony, ale nie można rozpoznać metody, procesor XAML powinien zgłosić wyjątek.

Użycie `<x:Arguments>string</x:Arguments>` atrybutu XAML jest technicznie możliwe. Zapewnia to jednak żadnych możliwości poza to, co można zrobić w przeciwnym razie za pomocą konwerterów tekstu inicjowania i typu, a użycie tej składni nie jest intencją projektu funkcji metody fabrycznej XAML 2009.

## <a name="examples"></a>Przykłady

W poniższym przykładzie przedstawiono podpis konstruktora bez `x:Arguments` parametrów, a następnie użycie XAML, który uzyskuje dostęp do tego podpisu.

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

W poniższym przykładzie pokazano podpis docelowej metody `x:Arguments` fabryki, a następnie użycie XAML, który uzyskuje dostęp do tego podpisu.

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

- [Definiowanie typów niestandardowych do użytku z usługami .NET XAML](define-custom-types.md)
- [Omówienie XAML (WPF)](../fundamentals/xaml.md)
