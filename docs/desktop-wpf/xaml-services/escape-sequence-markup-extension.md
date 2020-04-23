---
title: '{}Sekwencja ucieczki — rozszerzenie znaczników'
ms.date: 03/30/2017
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
ms.openlocfilehash: f84243994557d76fa52d72b060a1ba35460e98b0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071746"
---
# <a name="-escape-sequence--markup-extension"></a>{}Rozszerzenie sekwencji ucieczki / znaczników

Udostępnia sekwencję unikową XAML dla wartości atrybutów. Sekwencja ucieczki umożliwia kolejne wartości w atrybucie, które mają być interpretowane jako literał.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<object property="{} literalValue" .../>
```

## <a name="xaml-property-element-usage"></a>Użycie elementu właściwości języka XAML

```xaml
<object>
  <object.property>
    {} literalValue
  </object.property>
</object>
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|*literałValue*|Ciąg literał, który następuje sekwencji ucieczki. Zazwyczaj ten ciąg zawiera nawias klamrowy otwarty lub zamknięty ({ lub }).|

## <a name="remarks"></a>Uwagi

Sekwencja ucieczki ({}) jest używana tak, aby otwarty nawias klamrowy ({) mógł być używany jako znak literału w języku XAML.

Czytniki XAML zazwyczaj używają otwartego nawiasu klamrowego ({) do oznaczania punktu wejścia rozszerzenia znaczników; najpierw sprawdzają następny znak, aby ustalić, czy jest to nawias zamykający (}). Tylko wtedy, gdy{}dwie nawiasy klamrowe ( ) sąsiadują, są one uważane za sekwencję ucieczki.

Jeśli zostanie napotkana sekwencja ucieczki, czytnik XAML powinien przetworzyć pozostałą część ciągu jako ciąg. Jeśli jednak sekwencja unikowa jest stosowana do elementu członkowskiego, który ma konwerter typów, ciąg może zostać poddany konwersji typu, gdy jest interpretowany przez moduł zapisujący XAML.

Sekwencja ucieczki nie jest rozszerzeniem znaczników i nie jest wspierana przez klasę. Jest to jednak konwencja, którą czytelnicy XAML (w tym niestandardowe czytniki XAML) powinni przestrzegać.

Cudzysłów (") nie może być używany jako sekwencja ucieczki w ten sposób. Jeśli chcesz ustawić cudzysłów jako wartość właściwości dla właściwości niezgodnej, użyj składni elementu właściwości i umieść cudzysłów jako ciąg wewnątrz elementu właściwości lub użyj encji znaku XML. Dla właściwości zawartości cudzysłow może być całą zawartością.

Sekwencja ucieczki ({}) jest często wymagana przy określaniu typu XML, który musi zawierać kwalifikator obszaru nazw w lokalizacji, w której może pojawić się rozszerzenie znaczników XAML. Ta lokalizacja obejmuje początek wartości atrybutu XAML i w rozszerzeniu znaczników bezpośrednio po znaku równości (=). Poniższy przykład przedstawia sekwencje usztywnienia dla obszaru nazw XML, który pojawia się na początku wartości atrybutu XAML.

[!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]

## <a name="see-also"></a>Zobacz też

- [Typy konwerterów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions.md)
- [Jednostki znaków XML i XAML](xml-character-entities.md)
