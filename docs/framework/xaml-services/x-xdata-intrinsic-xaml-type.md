---
title: x:XData — Typ funkcji XAML
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: 3a16379fd6104342529723bf6d0bc9fb4762cf92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565366"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData — Typ funkcji XAML
Umożliwia umieszczanie Wysp danych XML w produkcji XAML. Elementy XML w `x:XData` nie powinny być traktowane przez procesory XAML, jak, jeśli są one częścią działania domyślnej przestrzeni nazw XAML lub innych nazw XAML. `x:XData` może zawierać dowolne poprawnie sformułowany plik XML.  
  
## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`elementDataRoot`|Element z jednym elementem głównym Wyspy danych zamknięte. Dla większości ostatecznego konsumentów XML, który nie ma jednym elementem głównym jest uznawane za nieprawidłowe. W szczególności jednym elementem głównym jest wymagany, jeśli `x:XData` ma pełnić rolę źródła danych XML dla WPF i wiele innych technologii używające źródła XML dla powiązania danych.|  
|`[elementData]`|Opcjonalna. Kod XML, który reprezentuje dane XML. Dowolna liczba elementów może być używany jako element danych i elementów zagnieżdżonych mogą być zawarte w innych elementach; Ogólne zasady XML się.|  
  
## <a name="remarks"></a>Uwagi  
 Elementy XML w `x:XData` obiekt można ponownie zadeklarować wszystkie możliwe obszary nazw i prefiksy zawierającego XMLDOM w danych.  
  
 Programowy dostęp do danych XML i `x:XData` wewnętrznego typu XAML jest możliwe w .NET Framework XAML Services za pośrednictwem <xref:System.Windows.Markup.XData> klasy.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 `x:XData` Obiekt przede wszystkim jest używany jako obiekt podrzędny <xref:System.Windows.Data.XmlDataProvider>, lub też obiektu podrzędnego <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> właściwości (w języku XAML, to jest zwykle wyrażony w składni elementu właściwości).  
  
 Dane zwykle powinny przedefiniować podstawowej przestrzeni nazw XML w Wyspy danych jako nowy domyślnej przestrzeni nazw XML (Ustaw ciąg pusty). Jest to najprostszy Wyspy proste danych, ponieważ <xref:System.Windows.Data.Binding.XPath%2A> wyrażeń, które są używane do odwołania i ich powiązania z danymi można uniknąć włączenia prefiksów. Bardziej złożone Wyspy danych może zdefiniować wiele prefiksów dla danych i używać określonego prefiksu dla przestrzeni nazw XML w katalogu głównym. W takim przypadku wszystkie <xref:System.Windows.Data.Binding.XPath%2A> odwołania do wyrażenia powinna zawierać prefiksu mapowane w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [omówienie powiązania danych](../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Z technicznego punktu widzenia `x:XData` mogą być używane jako zawartość żadnej właściwości typu <xref:System.Xml.Serialization.IXmlSerializable>. Jednak <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> tylko poświęcone implementacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Data.XmlDataProvider>  
 [Powiązanie danych — omówienie](../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Rozszerzenie znaczników powiązania](../../../docs/framework/wpf/advanced/binding-markup-extension.md)
