---
title: xml:lang — Obsługa w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 886f4063fa8c793fdce93431a29219cf86078593
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xmllang-handling-in-xaml"></a>xml:lang — Obsługa w XAML
`xml:lang` Atrybutu [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-zdefiniowany atrybut deklarujący informacje języku i kulturze dla elementu w pliku XML. To samo znaczenie atrybut będzie nadal występował w XAML; jednak pewne dodatkowe kwestie.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|*rfc3066lang*|Ciąg, który jest pochodną [RFC 3066](http://go.microsoft.com/fwlink/?LinkId=132454) standardowe i identyfikuje języka lub obszarem języka. Po drugie, region i język są rozdzielone przez pojedynczy łącznik. Zobacz <xref:System.Windows.Markup.XmlLanguage> uzyskać więcej informacji o wartości i formatu.|  
  
## <a name="remarks"></a>Uwagi  
 Definicja `xml:lang` atrybutu w [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] jest pochodną `xml:lang` zgodnie z definicją jako "specjalne atrybutu" [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] dla [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]. Informacje o języku i kulturze potencjalnie są przetwarzane na różne sposoby przez elementy, w zależności od ich implementacji; jednak nie ma domyślnych [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] przetwarzanie `xml:lang` atrybutu.  
  
 Wartość domyślna `xml:lang` atrybut jest pusty ciąg na poziomie atrybutu.  
  
 `xml:lang` Efekty atrybutu, a wartość atrybutu zazwyczaj są perpetuated do elementów podrzędnych, gdy interpretowany przez systemy, które działają w `xml:lang` wartości.  
  
 Kiedy interpretowane przez autorów XAML .NET Framework XAML usług, `xml:lang` można utworzyć wartości <xref:System.Windows.Markup.XmlLanguage> lub <xref:System.Globalization.CultureInfo> obiektów w odpowiadającego obiektu reprezentacja; jednak to zachowanie jest zależny od tego, czy wartość określona dla `xml:lang`jest nieprawidłowa konstrukcja dla tych klas.  
  
 Platformy można utworzyć skojarzenia między zdefiniowanych w ramach właściwości oraz na znaczenie właściwości `xml:lang` w formacie XML, stosując <xref:System.Windows.Markup.XmlLangPropertyAttribute> do właściwości.  
  
## <a name="wpf-usage-nodes"></a>Węzły użycia WPF  
 Dla klas pochodnych elementy, które są <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>, można użyć odpowiednikiem <xref:System.Windows.FrameworkElement.Language%2A> właściwości zależności zamiast `xml:lang` atrybutu. Domyślnie <xref:System.Windows.FrameworkElement.Language%2A> właściwość używa "pl pl", jeśli go nie jest w przeciwnym razie ustawiony, za pośrednictwem właściwości lub przetwarzania `xml:lang` atrybutu.  
  
## <a name="see-also"></a>Zobacz też  
 [Globalizacja dla WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
