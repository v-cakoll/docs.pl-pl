---
title: "{} Sekwencja unikowa — rozszerzenie znaczników"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8419a1e89d5e94b9868b0fd1fb81540253efca5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="-escape-sequence--markup-extension"></a>{} Sekwencja unikowa / rozszerzenie znaczników
Udostępnia sekwencji unikowej XAML dla wartości atrybutu. Sekwencja specjalna umożliwia kolejnych wartości w atrybucie interpretowane jako literału.  
  
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
|*literalValue*|Literał znajdujący się sekwencji ucieczki. Zazwyczaj ten ciąg zawiera otwierania lub zamykania nawiasu klamrowego ({lub}).|  
  
## <a name="remarks"></a>Uwagi  
 Sekwencja specjalna ({}) jest używany, aby otwierający nawias klamrowy ({}) może być używany jako znak w języku XAML.  
  
 Czytniki XAML zwykle otwierający nawias klamrowy ({}) do określenia punktu wejścia rozszerzenia znacznika; jednak najpierw sprawdzają następny znak w celu ustalenia, czy jest ono zamykający nawias klamrowy (}). Tylko wtedy, gdy dwa nawiasy klamrowe ({}) znajdują się obok siebie, są one traktowane jako sekwencja ucieczki.  
  
 W przypadku sekwencji ucieczki czytnika XAML ma być przetwarzane w pozostałej części ciągu jako ciąg. Jednak jeśli sekwencja specjalna jest stosowany do elementu członkowskiego, który ma konwertera typów, ciąg mogą być konwersji typu, gdy jest interpretowany przez moduł zapisujący XAML.  
  
 Sekwencja specjalna nie jest rozszerzeniem znacznika i nie jest ona obsługiwana przez klasę. Jest jednak Konwencji, która powinna być zgodna czytników XAML (w tym niestandardowe czytników XAML).  
  
 Znak cudzysłowu (") nie można użyć jako sekwencję ucieczki w ten sposób. Należy ustawić znak cudzysłowu jako wartość właściwości dla właściwości noncontent, należy użyć składni elementu właściwości i umieścić cudzysłów jako ciąg w elemencie właściwości lub Użyj jednostki znaków XML. Dla właściwości content znaku cudzysłowu można całej zawartości.  
  
 Sekwencja specjalna ({}) jest często wymagana podczas określania typu XML, który musi zawierać kwalifikatora przestrzeni nazw w lokalizacji, gdzie mogą być wyświetlane rozszerzenie znaczników w XAML. Początek wartości atrybutu XAML, a w rozszerzeniu znacznika, w tym bezpośrednio po znaku równości (=). W poniższym przykładzie przedstawiono sekwencji ucieczki dla przestrzeni nazw XML, który pojawia się na początku wartości atrybutu XAML.  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>Zobacz też  
 [Typy konwerterów i rozszerzenia znaczników dla XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [Jednostki znaków XML i XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
