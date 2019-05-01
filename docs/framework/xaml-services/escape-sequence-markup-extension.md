---
title: '{} Znak ucieczki sekwencja — rozszerzenie znaczników'
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
ms.openlocfilehash: 9f6743dd8a82891ac2233978550e5679130de0be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855612"
---
# <a name="-escape-sequence--markup-extension"></a>{}, sekwencja ucieczki/rozszerzenie znaczników
Sekwencja unikowa XAML zawiera wartości atrybutów. Sekwencja unikowa umożliwia kolejnych wartości w atrybucie należy interpretować jako literał.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>Użycie elementu właściwości języka XAML  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|*literalValue*|Literał ciągu następujący sekwencji unikowej. Ten ciąg zawiera zazwyczaj otwierania lub zamykania nawias klamrowy ({lub}).|  
  
## <a name="remarks"></a>Uwagi  
 Sekwencja unikowa ({}) jest używany, tak aby otwierający nawias klamrowy ({}) może być używany jako znak literałowy, w XAML.  
  
 Czytelnicy XAML zazwyczaj używają otwierający nawias klamrowy ({}) do określenia punktu wejścia rozszerzenia znaczników; jednak najpierw sprawdzają następny znak w celu ustalenia, czy jest ono zamykającego nawiasu klamrowego (}). Tylko wtedy, gdy dwa nawiasów ({}) czy sąsiadujących, są one traktowane jako sekwencji unikowej.  
  
 Jeśli sekwencja unikowa czytnika XAML ma być przetwarzana w pozostałej części ciągu jako ciąg. Jednak jeśli sekwencja unikowa jest stosowany do składowej, która ma konwertera typów, ciąg może zostać poddane konwersji typu, gdy jest on interpretowany przez Edytor XAML.  
  
 Sekwencja unikowa nie jest rozszerzeniem znacznika i nie jest obsługiwane przez klasę. Jest jednak Konwencji, który należy przestrzegać czytelnicy XAML (w tym niestandardowych czytelnicy XAML).  
  
 Znak cudzysłowu (") nie może służyć jako sekwencja unikowa w ten sposób. Jeśli musisz ustawić znak cudzysłowu jako wartość właściwości dla właściwości noncontent, należy użyć składni elementu właściwości i umieścić znak cudzysłowu jako ciąg w elemencie właściwości lub Użyj jednostki znaków XML. Właściwość zawartości znaku cudzysłowu mogą być całej zawartości.  
  
 Sekwencja unikowa ({}) często jest wymagany podczas określania typu XML, który musi zawierać kwalifikator przestrzeni nazw w miejscu, gdzie mogą być wyświetlane jako rozszerzenie znacznika XAML. Dotyczy to również początku wartości atrybutu XAML oraz rozszerzeniem znacznika bezpośrednio po znaku równości (=). Poniższy przykład pokazuje sekwencji unikowych dla przestrzeni nazw XML, który pojawia się na początku wartości atrybutu XAML.  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>Zobacz także

- [Typy konwerterów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions-for-xaml.md)
- [Jednostki znaków XML i XAML](xml-character-entities-and-xaml.md)
