---
title: '{}Sekwencja unikowa — rozszerzenie znaczników'
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
ms.openlocfilehash: b0646c62a1342eb160d1967e86ac286429013f3c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053875"
---
# <a name="-escape-sequence--markup-extension"></a>{}, sekwencja ucieczki/rozszerzenie znaczników
Udostępnia sekwencję ucieczki XAML dla wartości atrybutów. Sekwencja ucieczki pozwala, aby kolejne wartości w atrybucie były interpretowane jako literał.  
  
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
|*literalValue*|Ciąg literału, który następuje po sekwencji ucieczki. Zazwyczaj ten ciąg zawiera otwarty lub zamykający nawias klamrowy ({lub}).|  
  
## <a name="remarks"></a>Uwagi  
 Sekwencja ucieczki ({}) jest używana, aby w języku XAML można było użyć otwierającego nawiasu klamrowego ({) jako znaku literału.  
  
 Czytelnicy XAML zazwyczaj używają nawiasu otwierającego ({) do określenia punktu wejścia rozszerzenia znaczników, jednak najpierw sprawdzają następny znak, aby określić, czy jest to zamykający nawias klamrowy (}). Tylko wtedy, gdy dwa nawiasy{}klamrowe () są przyległe, są traktowane jako sekwencje ucieczki.  
  
 Jeśli zostanie wykryta sekwencja ucieczki, czytnik XAML powinien przetworzyć pozostałą część ciągu jako ciąg. Jeśli jednak sekwencja ucieczki zostanie zastosowana do elementu członkowskiego, który ma konwerter typu, ciąg może zostać przekształcony na konwersję typu, gdy jest interpretowany przez moduł zapisujący XAML.  
  
 Sekwencja ucieczki nie jest rozszerzeniem znaczników i nie jest obsługiwana przez klasę. Jednak jest to Konwencja, którą powinni przestrzegać czytelnicy XAML (w tym niestandardowe czytniki XAML).  
  
 W ten sposób nie można użyć znaku cudzysłowu (") jako sekwencji unikowej. Jeśli musisz ustawić znak cudzysłowu jako wartość właściwości dla właściwości niezawartości, użyj składni elementu właściwości i umieść znak cudzysłowu jako ciąg wewnątrz elementu Property lub Użyj jednostki znaku XML. W przypadku właściwości content cudzysłowem może być cała zawartość.  
  
 Sekwencja ucieczki ({}) jest często wymagana podczas określania typu XML, który musi zawierać kwalifikator przestrzeni nazw w lokalizacji, w której może się pojawić rozszerzenie XAML markup. Obejmuje to początek wartości atrybutu XAML i w rozszerzeniu znacznika bezpośrednio po znaku równości (=). Poniższy przykład pokazuje sekwencje ucieczki dla przestrzeni nazw XML, która pojawia się na początku wartości atrybutu XAML.  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>Zobacz także

- [Typy konwerterów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions-for-xaml.md)
- [Jednostki znaków XML i XAML](xml-character-entities-and-xaml.md)
