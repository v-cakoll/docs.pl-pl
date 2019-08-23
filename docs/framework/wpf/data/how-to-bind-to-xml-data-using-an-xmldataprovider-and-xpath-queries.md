---
title: 'Instrukcje: Wiązanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: 4833e024fcd352094a2163f11df8572aa4c241f8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944649"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Instrukcje: Wiązanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath
Ten przykład pokazuje, jak utworzyć powiązanie [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] z danymi <xref:System.Windows.Data.XmlDataProvider>przy użyciu.  
  
 Dane podstawowe [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] , do których można uzyskać dostęp za pomocą powiązania danych w aplikacji, mogą być dowolnym drzewem węzłów. <xref:System.Windows.Data.XmlDataProvider> Innymi słowy, <xref:System.Windows.Data.XmlDataProvider> zapewnia wygodny sposób użycia dowolnego [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] drzewa węzłów jako źródła powiązań.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie dane są osadzone bezpośrednio jako [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] <xref:System.Windows.FrameworkElement.Resources%2A> *wyspa danych* w sekcji. Wyspa danych musi być opakowana w `<x:XData>` Tagi i zawsze mieć jeden węzeł główny, który jest spisem w tym przykładzie. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]  
  
> [!NOTE]
> Węzeł [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] główny danych ma [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] atrybut **xmlns** , który ustawia przestrzeń nazw na pusty ciąg. Jest to wymagane do zastosowania zapytań XPath do Wyspy danych, która jest wbudowana [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] na stronie. W tym przypadku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]wbudowanym, a tym samym wyspa danych, <xref:System.Windows> dziedziczy przestrzeń nazw. Z tego względu należy ustawić pustą przestrzeń nazw, aby kwerendy XPath były kwalifikowane przez <xref:System.Windows> przestrzeń nazw, co spowodowałoby nieregularne kierowanie zapytań.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Jak pokazano w tym przykładzie, aby utworzyć tę samą deklarację powiązania w składni atrybutów, należy odpowiednio wprowadzić znaki specjalne. Aby uzyskać więcej informacji, zobacz [jednostki znaków XML i XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 Po uruchomieniu tego przykładu zostanąwyświetlonenastępująceelementy.<xref:System.Windows.Controls.ListBox> Są to *tytuły*wszystkich elementów w ramach *książek* z wartością giełdową "*out*" lub *liczbą* 3 lub większą lub równą 8. Należy zauważyć, że nie są zwracane żadne elementy <xref:System.Windows.Data.XmlDataProvider.XPath%2A> z *dysku CD* , <xref:System.Windows.Data.XmlDataProvider> ponieważ wartość ustawiona na wskazuje, że tylko elementy *książek* powinny być uwidocznione (zasadniczo ustawienie filtru).  
  
 ![Zrzut ekranu przedstawiający przykład wyrażenia XPath z tytułem czterech książek.](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 W tym przykładzie tytuły książek są wyświetlane <xref:System.Windows.Data.Binding.XPath%2A> , ponieważ <xref:System.Windows.Controls.TextBlock> dla powiązania w <xref:System.Windows.DataTemplate> elemencie jest ustawiona wartość "*title*". Jeśli chcesz wyświetlić wartość atrybutu, na przykład *ISBN*, ustaw tę <xref:System.Windows.Data.Binding.XPath%2A> wartość na "`@ISBN`".  
  
 Właściwości **XPath** w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są obsługiwane przez metodę XmlNode. SelectNodes. Zapytania **XPath** można modyfikować, aby uzyskać różne wyniki. Oto kilka przykładów <xref:System.Windows.Data.Binding.XPath%2A> zapytania względem powiązania <xref:System.Windows.Controls.ListBox> z poprzedniego przykładu:  
  
- `XPath="Book[1]"`zwróci pierwszy element książki ("XML w akcji"). Należy zauważyć, że indeksy **XPath** bazują na 1, nie wartości 0.  
  
- `XPath="Book[@*]"`zwróci wszystkie elementy książki z dowolnymi atrybutami.  
  
- `XPath="Book[last()-1]"`zwróci drugi do ostatniego elementu książki ("wprowadzenie Microsoft .NET").  
  
- `XPath="*[position()>3]"`zwróci wszystkie elementy książki z wyjątkiem pierwszego 3.  
  
 Po uruchomieniu kwerendy **XPath** zwraca <xref:System.Xml.XmlNode> ona lub listę elementów XmlNode. <xref:System.Xml.XmlNode>jest obiektem środowiska uruchomieniowego języka wspólnego (CLR), co oznacza, że <xref:System.Windows.Data.Binding.Path%2A> można użyć właściwości do powiązania z właściwościami środowiska uruchomieniowego języka wspólnego (CLR). Rozważmy ponownie poprzedni przykład. Jeśli pozostała część tego przykładu pozostanie taka sama i <xref:System.Windows.Controls.TextBlock> zmienisz powiązanie na następujące, zobaczysz nazwy zwróconych elementów XmlNode <xref:System.Windows.Controls.ListBox>w. W takim przypadku nazwą wszystkich zwracanych węzłów jest "*książka*".  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 W niektórych aplikacjach osadzenie [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] jako Wyspy danych w źródle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony może być niewygodne, ponieważ dokładna zawartość danych musi być znana w czasie kompilacji. W związku z tym, uzyskiwanie danych [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] z pliku zewnętrznego jest również obsługiwane, jak w poniższym przykładzie:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Jeśli dane znajdują się w pliku zdalnym [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] , należy zdefiniować dostęp do danych, <xref:System.Windows.Data.XmlDataProvider.Source%2A> przypisując odpowiednie [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] do atrybutu w następujący sposób: [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]  
  
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
