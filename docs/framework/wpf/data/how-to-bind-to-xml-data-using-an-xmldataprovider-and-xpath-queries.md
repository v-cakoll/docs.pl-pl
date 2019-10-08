---
title: Jak powiązać z danymi XML przy użyciu XMLDataProvider i zapytań XPath
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: d92b01c453a9e07a5d4a6d1900d54e8c86210041
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005685"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Jak powiązać z danymi XML przy użyciu XMLDataProvider i zapytań XPath
Ten przykład pokazuje, jak utworzyć powiązanie z danymi [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] przy użyciu <xref:System.Windows.Data.XmlDataProvider>.  
  
 W przypadku <xref:System.Windows.Data.XmlDataProvider> dane bazowe, do których można uzyskać dostęp za pomocą powiązania danych w aplikacji mogą być dowolnym drzewem węzłów [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Innymi słowy, <xref:System.Windows.Data.XmlDataProvider> zapewnia wygodny sposób używania dowolnego drzewa węzłów [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] jako źródła powiązania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie dane są osadzone bezpośrednio jako *wyspa danych* [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] w sekcji <xref:System.Windows.FrameworkElement.Resources%2A>. Wyspa danych [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] musi być opakowana w Tagi `<x:XData>` i zawsze mieć pojedynczy węzeł główny, który jest *spisem* w tym przykładzie.  
  
> [!NOTE]
> Węzeł główny danych [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ma atrybut **xmlns** , który ustawia przestrzeń nazw [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] na pusty ciąg. Jest to wymagane do zastosowania zapytań XPath do Wyspy danych, która jest wbudowana w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony. W tym przypadku, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a tym samym wyspa danych, dziedziczy przestrzeń nazw <xref:System.Windows>. Z tego względu należy ustawić pustą przestrzeń nazw, aby kwerendy XPath były kwalifikowane przez przestrzeń nazw <xref:System.Windows>, co spowodowałoby nieregularne kierowanie zapytań.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Jak pokazano w tym przykładzie, aby utworzyć tę samą deklarację powiązania w składni atrybutów, należy odpowiednio wprowadzić znaki specjalne. Aby uzyskać więcej informacji, zobacz [jednostki znaków XML i XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 W przypadku uruchomienia tego przykładu <xref:System.Windows.Controls.ListBox> będzie zawierać następujące elementy. Są to *tytuły*wszystkich elementów w ramach *książek* z wartością *giełdową* "*out*" lub *liczbą* 3 lub większą lub równą 8. Należy zauważyć, że nie są zwracane żadne elementy z *dysku CD* , ponieważ wartość <xref:System.Windows.Data.XmlDataProvider.XPath%2A> ustawiona na <xref:System.Windows.Data.XmlDataProvider> wskazuje, że tylko elementy *książek* powinny być uwidocznione (zasadniczo ustawienie filtru).  
  
 ![Zrzut ekranu przedstawiający przykład wyrażenia XPath z tytułem czterech książek.](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 W tym przykładzie tytuły książek są wyświetlane, ponieważ <xref:System.Windows.Data.Binding.XPath%2A> dla powiązania <xref:System.Windows.Controls.TextBlock> w <xref:System.Windows.DataTemplate> ma wartość "*title*". Jeśli chcesz wyświetlić wartość atrybutu, na przykład *ISBN*, należy ustawić tę wartość <xref:System.Windows.Data.Binding.XPath%2A> na "`@ISBN`".  
  
 Właściwości **XPath** w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są obsługiwane przez metodę XmlNode. SelectNodes. Zapytania **XPath** można modyfikować, aby uzyskać różne wyniki. Poniżej przedstawiono kilka przykładów zapytania <xref:System.Windows.Data.Binding.XPath%2A> w powiązanym <xref:System.Windows.Controls.ListBox> z poprzedniego przykładu:  
  
- `XPath="Book[1]"` zwróci pierwszy element książki ("XML w akcji"). Należy zauważyć, że indeksy **XPath** bazują na 1, nie wartości 0.  
  
- `XPath="Book[@*]"` zwróci wszystkie elementy książki z dowolnymi atrybutami.  
  
- `XPath="Book[last()-1]"` zwróci sekundę do ostatniego elementu książki ("wprowadzając Microsoft .NET").  
  
- `XPath="*[position()>3]"` zwróci wszystkie elementy książki z wyjątkiem pierwszego 3.  
  
 Po uruchomieniu zapytania **XPath** zwraca <xref:System.Xml.XmlNode> lub listę elementów XmlNode. <xref:System.Xml.XmlNode> to obiekt środowiska uruchomieniowego języka wspólnego (CLR), co oznacza, że można użyć właściwości <xref:System.Windows.Data.Binding.Path%2A> do powiązania z właściwościami środowiska uruchomieniowego języka wspólnego (CLR). Rozważmy ponownie poprzedni przykład. Jeśli pozostała część przykładu pozostanie taka sama i zmienisz powiązanie <xref:System.Windows.Controls.TextBlock> na następujące, zobaczysz nazwy zwróconych elementów XmlNode w <xref:System.Windows.Controls.ListBox>. W takim przypadku nazwą wszystkich zwracanych węzłów jest "*książka*".  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 W niektórych aplikacjach osadzenie [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] jako Wyspy danych w źródle strony [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] może być niewygodne, ponieważ dokładna zawartość danych musi być znana w czasie kompilacji. W związku z tym, uzyskiwanie danych z zewnętrznego pliku [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] jest również obsługiwane, jak w poniższym przykładzie:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Jeśli dane [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] znajdują się w zdalnym pliku [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], należy zdefiniować dostęp do danych przez przypisanie odpowiedniego adresu URL do atrybutu <xref:System.Windows.Data.XmlDataProvider.Source%2A> w następujący sposób:  
  
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
