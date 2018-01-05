---
title: "Jak powiązać z danymi XML przy użyciu XMLDataProvider i zapytań XPath"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92037be2280eaa248951ff9bad82b7a1581a4fd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Jak powiązać z danymi XML przy użyciu XMLDataProvider i zapytań XPath
W tym przykładzie przedstawiono sposób powiązania [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] danych przy użyciu <xref:System.Windows.Data.XmlDataProvider>.  
  
 Z <xref:System.Windows.Data.XmlDataProvider>, podstawowy danych, który jest możliwy za pośrednictwem powiązania danych w aplikacji może być dowolnym drzewa [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] węzłów. Innymi słowy <xref:System.Windows.Data.XmlDataProvider> oferują wygodny sposób używania dowolnego drzewa [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] węzłów jako źródło powiązania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie danych zostanie osadzony bezpośrednio [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] *Wyspy danych* w <xref:System.Windows.FrameworkElement.Resources%2A> sekcji. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Wyspy danych muszą być ujęte w `<x:XData>` tagów i na jednym węźle głównym, który jest ono mieć zawsze *spisu* w tym przykładzie.  
  
> [!NOTE]
>  Węzeł główny [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane mają **xmlns** atrybut, który ustawia [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] przestrzeni nazw na pusty ciąg. Jest to wymagane dla stosowania kwerendy XPath do wyspy danych, który jest wbudowany w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony. W tym przypadku wbudowanego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], i w związku z tym dziedziczy Wyspy danych <xref:System.Windows> przestrzeni nazw. W związku z tym musisz ustawić przestrzeń nazw puste, aby zapobiec kwerendy XPath jest kwalifikowana przez <xref:System.Windows> przestrzeni nazw, która będzie misdirect zapytania.  
  
 [!code-xaml[XMLDataSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Jak pokazano w tym przykładzie, do utworzenia tej samej deklaracji powiązania w składni atrybutu możesz musi escape znaki specjalne poprawnie. Aby uzyskać więcej informacji, zobacz [jednostki znaków XML i XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md).  
  
 <xref:System.Windows.Controls.ListBox> Pokaż następujące elementy, gdy zostanie uruchomione w tym przykładzie. Są to *tytuł*s wszystkie elementy w obszarze *książki* przy użyciu jednej *giełdowych* wartość "*limit*" lub *numer* wartość 3 lub większa niż lub równa 8. Zwróć uwagę, że nie *CD* elementy są zwracane, ponieważ <xref:System.Windows.Data.XmlDataProvider.XPath%2A> wartość zestawu na <xref:System.Windows.Data.XmlDataProvider> wskazuje, że tylko *książki* elementów powinny zostać ujawnione (zasadniczo ustawienie filtru).  
  
 ![Przykład XPath](../../../../docs/framework/wpf/data/media/xpathexample.PNG "XPathExample")  
  
 W tym przykładzie są wyświetlane tytułów książek, ponieważ <xref:System.Windows.Data.Binding.XPath%2A> z <xref:System.Windows.Controls.TextBlock> powiązanie w <xref:System.Windows.DataTemplate> ma ustawioną wartość "*tytuł*". Jeśli chcesz wyświetlić wartość atrybutu, takich jak *ISBN*, który ustawiał <xref:System.Windows.Data.Binding.XPath%2A> do wartości "`@ISBN`".  
  
 **XPath** właściwości w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są obsługiwane przez metodę XmlNode.SelectNodes. Można zmodyfikować **XPath** zapytania, aby uzyskać różne wyniki. Poniżej przedstawiono kilka przykładów <xref:System.Windows.Data.Binding.XPath%2A> zapytania na granicy <xref:System.Windows.Controls.ListBox> z poprzedniego przykładu:  
  
-   `XPath="Book[1]"`Zwraca pierwszy element książki ("XML w akcji"). Należy pamiętać, że **XPath** indeksy są oparte na 1, 0 nie.  
  
-   `XPath="Book[@*]"`Zwraca wszystkie elementy księgi z żadnych atrybutów.  
  
-   `XPath="Book[last()-1]"`zwróci drugi do ostatniego elementu książki ("wprowadzenie do programu Microsoft .NET").  
  
-   `XPath="*[position()>3]"`Zwraca wszystkie elementy księgi z wyjątkiem pierwszej 3.  
  
 Po uruchomieniu **XPath** zapytanie zwraca <xref:System.Xml.XmlNode> lub listę XmlNodes. <xref:System.Xml.XmlNode>jest [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektu, co oznacza, że można użyć <xref:System.Windows.Data.Binding.Path%2A> właściwości, aby powiązać [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwości. Należy wziąć pod uwagę poprzedni przykład ponownie. Jeśli pozostała część przykładzie pozostaje taki sam <xref:System.Windows.Controls.TextBlock> powiązanie z następujących czynności, zobaczysz nazwy zwrócony XmlNodes w <xref:System.Windows.Controls.ListBox>. W takim przypadku nazwa zwróconego węzłów jest "*książki*".  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 W niektórych aplikacjach osadzanie [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] jako wyspy danych w źródle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony może być niewygodne, ponieważ dokładną zawartość danych musi być znane w czasie kompilacji. W związku z tym uzyskanie danych z zewnętrznego [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] plik jest również obsługiwany, jak w poniższym przykładzie:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Jeśli [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane znajdują się w zdalnym [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] pliku, zostaną zdefiniowane dostępu do danych, przypisując odpowiednie [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] do <xref:System.Windows.Data.XmlDataProvider.Source%2A> atrybutu w następujący sposób:  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Data.ObjectDataProvider>  
 [Powiązywanie z dokumentem X, elementem X lub LINQ dla wyników zapytań XML](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)  
 [Używanie wzorca szczegółowego z danymi hierarchicznymi XML](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)  
 [Wiązanie źródeł — omówienie](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
