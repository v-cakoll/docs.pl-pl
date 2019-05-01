---
title: 'Instrukcje: Wiązanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: 3a3df65f0c20cff49f9bd2a8790e8d9ae0032391
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63809572"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Instrukcje: Wiązanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath
W tym przykładzie pokazano, jak powiązać [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] danych przy użyciu <xref:System.Windows.Data.XmlDataProvider>.  
  
 Za pomocą <xref:System.Windows.Data.XmlDataProvider>, bazowych danych, który jest możliwy za pośrednictwem powiązania danych w aplikacji może być dowolnym drzewo [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] węzłów. Innymi słowy <xref:System.Windows.Data.XmlDataProvider> oferuje wygodny sposób, aby użyć dowolnego drzewo [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] węzłów jako źródło wiążące.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie danych zostanie osadzony bezpośrednio [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] *Wyspy danych* w ramach <xref:System.Windows.FrameworkElement.Resources%2A> sekcji. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Wyspy danych muszą być ujęte w `<x:XData>` tagów i na jednym węźle głównym, który jest ono mieć zawsze *spisu* w tym przykładzie.  
  
> [!NOTE]
>  Węzeł główny [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych **xmlns** atrybut, który ustawia [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] przestrzeni nazw na pusty ciąg. Jest to wymagane dla stosowania kwerendy XPath do wyspy danych, która jest wbudowana w ramach [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony. W tym przypadku wbudowane [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], i w związku z tym dziedziczy Wyspy danych <xref:System.Windows> przestrzeni nazw. W związku z tym należy ustawić pustą wartość, aby zapobiec kwerendy XPath jest kwalifikowana przez obszar nazw <xref:System.Windows> przestrzeń nazw, która będzie misdirect zapytania.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Jak pokazano w tym przykładzie, do tworzenia tej samej deklaracji powiązania w składni atrybutów należy przed nimi znak ucieczki znaków specjalnych prawidłowo. Aby uzyskać więcej informacji, zobacz [jednostki znaków XML i XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 <xref:System.Windows.Controls.ListBox> Pokaże następujące elementy, po uruchomieniu tego przykładu. Są to *tytuł*s wszystkich elementów w obszarze *książki* z oboma *Stock* wartość "*się*" lub *numer* wartość 3 lub większa niż lub równa 8. Należy zauważyć, że nie *CD* elementy są zwracane, ponieważ <xref:System.Windows.Data.XmlDataProvider.XPath%2A> wartość zestawu <xref:System.Windows.Data.XmlDataProvider> wskazuje, że tylko *książki* elementy powinny zostać ujawnione (zasadniczo ustawienie filtru).  
  
 ![Zrzut ekranu przykładu XPath, przedstawiający tytuł cztery książki.](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 W tym przykładzie są wyświetlane tytułów książek, ponieważ <xref:System.Windows.Data.Binding.XPath%2A> z <xref:System.Windows.Controls.TextBlock> powiązanie w <xref:System.Windows.DataTemplate> jest ustawiona na "*tytuł*". Jeśli chcesz wyświetlić wartość atrybutu, takich jak *ISBN*, który ustawi <xref:System.Windows.Data.Binding.XPath%2A> wartość "`@ISBN`".  
  
 **XPath** właściwości w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są obsługiwane przez metodę XmlNode.SelectNodes. Możesz zmodyfikować **XPath** zapytania, aby uzyskać różne wyniki. Poniżej przedstawiono kilka przykładów <xref:System.Windows.Data.Binding.XPath%2A> zapytania to granica <xref:System.Windows.Controls.ListBox> z poprzedniego przykładu:  
  
- `XPath="Book[1]"` Zwraca pierwszy element książki ("XML w akcji"). Należy pamiętać, że **XPath** indeksy są oparte na 1, 0 nie.  
  
- `XPath="Book[@*]"` będzie zwracać wszystkie elementy księgi żadnych atrybutów.  
  
- `XPath="Book[last()-1]"` Zwraca drugi do ostatniego elementu książki ("Przedstawiamy .NET firmy Microsoft").  
  
- `XPath="*[position()>3]"` zwrócone zostaną wszystkie książki elementy, z wyjątkiem pierwszej 3.  
  
 Po uruchomieniu **XPath** zapytania i zwraca <xref:System.Xml.XmlNode> lub Podaj listę XmlNodes. <xref:System.Xml.XmlNode> jest [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektu, co oznacza, że można użyć <xref:System.Windows.Data.Binding.Path%2A> właściwość można powiązać [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwości. Należy wziąć pod uwagę poprzedni przykład ponownie. Jeśli pozostałą część przykładu pozostaje taka sama, a następnie zmienisz <xref:System.Windows.Controls.TextBlock> powiązania do poniższego, zobaczysz nazwy zwrócone XmlNodes w <xref:System.Windows.Controls.ListBox>. W takim przypadku nazwa zwracany węzłów jest "*książki*".  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 W niektórych aplikacjach osadzania [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] jako wyspy danych w źródle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strona może być niewygodne, ponieważ dokładną zawartość danych musi być znane w czasie kompilacji. Dlatego uzyskanie danych z zewnętrznej [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] pliku obsługiwana jest również, jak w poniższym przykładzie:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Jeśli [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane znajdują się w lokalizacji zdalnej [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] pliku, należy zdefiniować dostęp do danych, przypisując odpowiednie [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] do <xref:System.Windows.Data.XmlDataProvider.Source%2A> atrybutu w następujący sposób:  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.ObjectDataProvider>
- [Powiązywanie z dokumentem X, elementem X lub LINQ dla wyników zapytań XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)
- [Używanie wzorca szczegółowego z danymi hierarchicznymi XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Wiązanie źródeł — omówienie](binding-sources-overview.md)
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
