---
title: xml:lang — Obsługa w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 98bfabba96e5805b96c63eb02233b15eae233cc0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740563"
---
# <a name="xmllang-handling-in-xaml"></a>xml:lang — Obsługa w XAML
Atrybut `xml:lang` jest atrybutem zdefiniowanym przez XML, który deklaruje informacje o języku i kulturze dla elementu w formacie XML. Takie samo znaczenie atrybutu utrzymuje się w języku XAML; Niektóre dodatkowe zagadnienia są jednak stosowane.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|*rfc3066lang*|Ciąg pochodzący ze standardu [RFC 3066](https://go.microsoft.com/fwlink/?LinkId=132454) i identyfikujący język lub region języka. Gdy jest to ostatni, język i region są rozdzielone pojedynczym łącznikiem. Aby uzyskać więcej informacji na temat wartości i formatu, zobacz <xref:System.Windows.Markup.XmlLanguage>.|  
  
## <a name="remarks"></a>Uwagi  
 Definicja atrybutu `xml:lang` w [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pochodzi od `xml:lang`, jak określono jako "atrybut specjalny" przez organizacja World Wide Web Consortium (W3C) dla XML. Informacje o języku i kulturze mogą być przetwarzane na różne sposoby według elementów, w zależności od ich implementacji; nie ma jednak domyślnego przetwarzania [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] atrybutu `xml:lang`.  
  
 Wartość domyślna atrybutu `xml:lang` jest ciągiem pustym na poziomie atrybutu.  
  
 `xml:lang` efekty atrybutu i wartość atrybutu są zwykle perpetuated do elementów podrzędnych, gdy są interpretowane przez systemy, które działają na wartościach `xml:lang`.  
  
 W przypadku interpretowania przez autorów XAML .NET Framework usług XAML, `xml:lang` wartość może tworzyć obiekty <xref:System.Windows.Markup.XmlLanguage> lub <xref:System.Globalization.CultureInfo> w reprezentacji bazowego obiektu; jednak takie zachowanie zależy od tego, czy wartość określona dla `xml:lang` jest prawidłową konstrukcją dla tych klas.  
  
 Struktury programu mogą tworzyć skojarzenia między właściwościami zdefiniowanymi przez platformę i znaczenie `xml:lang` w kodzie XML przez zastosowanie <xref:System.Windows.Markup.XmlLangPropertyAttribute> do właściwości.  
  
## <a name="wpf-usage-nodes"></a>Węzły użycia WPF  
 Dla elementów, które są klasami pochodnymi <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>, można użyć równoważnej właściwości zależności <xref:System.Windows.FrameworkElement.Language%2A> zamiast atrybutu `xml:lang`. Domyślnie właściwość <xref:System.Windows.FrameworkElement.Language%2A> używa wartości "pl-US", jeśli nie została ustawiona inaczej, przez właściwość lub poprzez przetwarzanie atrybutu `xml:lang`.  
  
## <a name="see-also"></a>Zobacz także

- [Globalizacja dla WPF](../wpf/advanced/globalization-for-wpf.md)
