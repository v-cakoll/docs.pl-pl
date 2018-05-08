---
title: mc:Ignorable — Atrybut
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: 7b8a2ef6e27bc6b25776157e59bef04b883fcb1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mcignorable-attribute"></a>mc:Ignorable — Atrybut
Określa, która [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] prefiksy przestrzeni nazw w pliku znaczników, może być ignorowane przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora. `mc:Ignorable` Atrybut obsługuje zgodności znaczników, zarówno w przypadku mapowania niestandardowej przestrzeni nazw, jak i dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przechowywania wersji.  
  
## <a name="xaml-attribute-usage-single-prefix"></a>Użycie atrybutu XAML (jeden przedrostek)  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a>Użycie atrybutu XAML (dwie prefiksy)  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|*ignorablePrefix ignorablePrefix1, itp.*|Dowolny ciąg prawidłowy prefiks, na Specyfikacja XML 1.0.|  
|*ignorableUri*|Wszelkie prawidłowy identyfikator URI przestrzeni nazw na Specyfikacja XML 1.0 wyznaczania.|  
|*ThisElementCanBeIgnored*|Element, który może być ignorowane przez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementacji procesora, jeśli nie można rozpoznać typu podstawowego.|  
  
## <a name="remarks"></a>Uwagi  
 `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Prefiks przestrzeni nazw jest Konwencji prefiks zalecaną do użycia podczas mapowania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nazw zgodności [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].  
  
 Elementów lub atrybutów, których część prefiks nazwy elementu są identyfikowane jako `mc:Ignorable` nie generuje błędy podczas przetwarzania przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora. Jeśli tego atrybutu nie można rozpoznać typu podstawowego lub konstrukcji programującej, że element zostanie zignorowany. Należy jednak pamiętać, że zignorowane elementy nadal może generować dodatkowe błędy analizy, dodatkowy element wymagania, które są efekty uboczne tego elementu nie są przetwarzane. Na przykład dany element modelu zawartości mogą wymagać dokładnie jeden element podrzędny, ale jeśli był element podrzędny określonego `mc:Ignorable` prefiks i element podrzędny określonego nie można rozpoznać typu, a następnie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora może Zgłoś błąd.  
  
 `mc:Ignorable` dotyczy tylko mapowania przestrzeni nazw na ciągi identyfikator. `mc:Ignorable` nie ma zastosowania do mapowania przestrzeni nazw w zestawy, które określają [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] przestrzeni nazw i zestawu (lub domyślne do bieżącego pliku wykonywalnego jako zestawu).  
  
 W przypadku wdrażania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora, implementacji procesor nie musi wygenerować, analizy lub przetwarzania błędów rozpoznawania typu element lub atrybut, który jest kwalifikowana przez prefiks, który jest identyfikowany jako `mc:Ignorable`. Ale implementacji procesora nadal może zgłaszać wyjątki, które są wynikiem dodatkowej elementu nie powiodło się załadowanie lub być przetwarzane, takich jak na przykład element podrzędny co podane wcześniej.  
  
 Domyślnie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora zignoruje zawartość elementu została zignorowana. Można jednak określić atrybut dodatkowe [mc:ProcessContent atrybutu](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), jest wymagane dalsze przetwarzanie zawartości w obrębie elementu zignorowane przez następnego elementu nadrzędnego dostępne.  
  
 Można określić wiele prefiksów w atrybucie przy użyciu co najmniej jeden znak odstępu jako separator, na przykład: `mc:Ignorable="ignore1 ignore2"`.  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Definiuje przestrzeń nazw innych elementów i atrybutów, które nie są opisane w tym obszarze [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]. Aby uzyskać więcej informacji, zobacz [specyfikacji zgodności znaczników XML](http://go.microsoft.com/fwlink/?LinkId=73824).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Markup.XamlReader>  
 [PresentationOptions:Freeze, atrybut](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
