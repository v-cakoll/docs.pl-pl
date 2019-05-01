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
ms.openlocfilehash: 03439a2c4a1a4de375e90d0e5121e690541e2f0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61805148"
---
# <a name="mcignorable-attribute"></a>mc:Ignorable — Atrybut
Określa, która [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] prefiksy przestrzeni nazw w pliku znaczników mogą być ignorowane przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora. `mc:Ignorable` Atrybut obsługuje zgodność znaczników, zarówno dla mapowania niestandardowej przestrzeni nazw i [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przechowywania wersji.  
  
## <a name="xaml-attribute-usage-single-prefix"></a>Użycie atrybutu XAML (prefiks jednego)  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a>Użycie atrybutu XAML (dwóch prefiksy)  
  
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
|*ignorableUri*|Wszelkie prawidłowy identyfikator URI do wyznaczania obszaru nazw, na Specyfikacja XML 1.0.|  
|*ThisElementCanBeIgnored*|Element, który może być ignorowane przez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementacji procesora, jeśli nie można rozpoznać typu bazowego.|  
  
## <a name="remarks"></a>Uwagi  
 `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Prefiks przestrzeni nazw jest do Konwencja prefiks zalecane do użycia podczas mapowania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przestrzeni nazw zgodności [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].  
  
 Elementy lub atrybuty, których część prefiks nazwy elementu są identyfikowane jako `mc:Ignorable` nie będą powodowały błędy podczas przetwarzania przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora. Jeśli ten atrybut nie można rozpoznać typu podstawowego lub konstrukcji programowania, ten element jest ignorowany. Należy jednak pamiętać, że zignorowane elementy nadal może generować dodatkowe błędy analizy dla wymagania dotyczące dodatkowych elementów, które są efekty uboczne tego elementu nie są przetwarzane. Na przykład konkretnego elementu modelu zawartości mogą wymagać dokładnie jeden element podrzędny, ale jeśli element podrzędny określonego była w `mc:Ignorable` prefiksu i element podrzędny określonego nie można rozpoznać do typu, a następnie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora może Zgłoś błąd.  
  
 `mc:Ignorable` ma zastosowanie tylko do mapowania przestrzeni nazw na ciągi znaków identyfikatora. `mc:Ignorable` nie ma zastosowania do mapowania przestrzeni nazw do zestawów, które określają [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] przestrzeni nazw i zestawu (lub domyślne do bieżącego pliku wykonywalnego jako zestawu).  
  
 W przypadku wdrażania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora, implementacji procesora nie trzeba zwiększyć, analizowania lub przetwarzania błędów na rozpoznawanie typu do celów dowolny element lub atrybut, który jest kwalifikowana za prefiks, który jest identyfikowany jako `mc:Ignorable`. Ale implementacji procesora nadal może zgłaszać wyjątki, które są wynikiem dodatkowej elementu nie można załadować lub być przetworzone, takich jak w przykładzie element podrzędny jednego z podanych wcześniej.  
  
 Domyślnie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora zignoruje zawartości w obrębie elementu zignorowane. Można jednak określić atrybut dodatkowe [MC: processcontent — atrybut](mc-processcontent-attribute.md), jest wymagane dalsze przetwarzanie zawartości w obrębie elementu ignorowane przez następnego elementu nadrzędnego dostępne.  
  
 W atrybucie, przy użyciu co najmniej jeden znak spacji jako separator, na przykład można określić wiele prefiksów: `mc:Ignorable="ignore1 ignore2"`.  

 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Nazw definiuje innych elementów i atrybutów, które nie zostały zamieszczone w tym obszarze [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]. Aby uzyskać więcej informacji, zobacz [specyfikacji zgodności znaczników XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Markup.XamlReader>
- [PresentationOptions:Freeze, atrybut](presentationoptions-freeze-attribute.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Dokumenty w WPF](documents-in-wpf.md)
