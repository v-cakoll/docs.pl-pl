---
title: xml:lang — Obsługa w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 025e4b2865fe3938e5f1454f87e90bae7a85bcfd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399666"
---
# <a name="xmllang-handling-in-xaml"></a>xml:lang — Obsługa w XAML
`xml:lang` Atrybut jest [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-zdefiniowany atrybut deklarujący informacje języka i kultury dla elementu w pliku XML. To takie samo znaczenie atrybut będzie nadal występował w XAML; jednak dodatkowe zagadnienia do rozważenia.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|*rfc3066lang*|Ciąg, który jest tworzony na podstawie [RFC 3066](https://go.microsoft.com/fwlink/?LinkId=132454) standardowe i identyfikuje języka lub obszarem języka. Gdy jest to ten ostatni, język i region są oddzielone pojedynczy łącznik. Zobacz <xref:System.Windows.Markup.XmlLanguage> Aby uzyskać więcej informacji na temat wartości i formatu.|  
  
## <a name="remarks"></a>Uwagi  
 Definicja `xml:lang` atrybutu w [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] jest tworzony na podstawie `xml:lang` zgodnie z definicją jako "specjalne atrybutu" [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] dla [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]. Informacje o języku i kulturze potencjalnie jest przetwarzany na różne sposoby przez elementy, w zależności od ich implementacji; jednak nie jest domyślnie [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] przetwarzanie `xml:lang` atrybutu.  
  
 Wartość domyślna `xml:lang` atrybut jest pusty ciąg na poziomie atrybutu.  
  
 `xml:lang` Efekty atrybutu i wartość atrybutu zazwyczaj są perpetuated do elementów podrzędnych, kiedy interpretowane przez systemy, które działają w `xml:lang` wartości.  
  
 Kiedy interpretowane przez autorów XAML usług .NET Framework XAML, `xml:lang` można utworzyć wartości <xref:System.Windows.Markup.XmlLanguage> lub <xref:System.Globalization.CultureInfo> obiektów w źródłowym obiekcie reprezentacji; jednak to zachowanie zależy od tego, czy wartość określona dla `xml:lang`składa się z prawidłową dla tych klas.  
  
 Platformy można utworzyć skojarzenia między właściwościami zdefiniowanych i znaczenie `xml:lang` w formacie XML, stosując <xref:System.Windows.Markup.XmlLangPropertyAttribute> do właściwości.  
  
## <a name="wpf-usage-nodes"></a>Węzły użycia WPF  
 Dla elementów, które są pochodne klasy <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>, można użyć odpowiednik <xref:System.Windows.FrameworkElement.Language%2A> właściwość zależności zamiast `xml:lang` atrybutu. Domyślnie <xref:System.Windows.FrameworkElement.Language%2A> właściwość używa "en US", jeśli nie jest w przeciwnym razie ustawiona, za pomocą właściwości lub za pośrednictwem przetwarzania `xml:lang` atrybutu.  
  
## <a name="see-also"></a>Zobacz też  
 [Globalizacja dla WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
