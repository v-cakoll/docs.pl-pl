---
title: Jak powiązać z danymi XML przy użyciu XMLDataProvider i zapytań XPath
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: a5ad7d8bce9bc0a760868e483278d1836f9472af
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559706"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Jak powiązać z danymi XML przy użyciu XMLDataProvider i zapytań XPath
Ten przykład pokazuje, jak utworzyć powiązanie z danymi XML przy użyciu <xref:System.Windows.Data.XmlDataProvider>.  
  
 Za pomocą <xref:System.Windows.Data.XmlDataProvider>dane bazowe, do których można uzyskać dostęp za pomocą powiązania danych w aplikacji, mogą być dowolnym drzewem węzłów XML. Innymi słowy, <xref:System.Windows.Data.XmlDataProvider> zapewnia wygodny sposób używania dowolnych drzew węzłów XML jako źródła powiązań.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie dane są osadzone bezpośrednio jako *wyspa danych* XML w sekcji <xref:System.Windows.FrameworkElement.Resources%2A>. Wyspa danych XML musi być opakowana w Tagi `<x:XData>` i zawsze mieć pojedynczy węzeł główny, który jest *spisem* w tym przykładzie.  
  
> [!NOTE]
> Węzeł główny danych XML ma atrybut **xmlns** , który ustawia przestrzeń nazw XML na pusty ciąg. Jest to wymagane do zastosowania zapytań XPath do Wyspy danych, która jest wbudowana na stronie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. W tym przypadku, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a tym samym wyspa danych, dziedziczy <xref:System.Windows> przestrzeni nazw. Z tego względu należy ustawić pustą przestrzeń nazw, aby kwerendy XPath były kwalifikowane przez przestrzeń nazw <xref:System.Windows>, co spowodowałoby nieregularne kierowanie zapytań.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Jak pokazano w tym przykładzie, aby utworzyć tę samą deklarację powiązania w składni atrybutów, należy odpowiednio wprowadzić znaki specjalne. Aby uzyskać więcej informacji, zobacz [jednostki znaków XML i XAML](../../../desktop-wpf/xaml-services/xml-character-entities.md).  
  
 Podczas uruchamiania tego przykładu <xref:System.Windows.Controls.ListBox> będą widoczne następujące elementy. Są to *tytuły*wszystkich elementów w ramach *książek* z wartością *giełdową* "*out*" lub *liczbą* 3 lub większą lub równą 8. Należy zauważyć, że nie są zwracane żadne elementy z *dysku CD* , ponieważ wartość <xref:System.Windows.Data.XmlDataProvider.XPath%2A> ustawiona na <xref:System.Windows.Data.XmlDataProvider> wskazuje, że tylko elementy *książek* powinny być uwidocznione (zasadniczo ustawienie filtru).  
  
 ![Zrzut ekranu przedstawiający przykład wyrażenia XPath z tytułem czterech książek.](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 W tym przykładzie tytuły książek są wyświetlane, ponieważ <xref:System.Windows.Data.Binding.XPath%2A> powiązania <xref:System.Windows.Controls.TextBlock> w <xref:System.Windows.DataTemplate> jest ustawiony na "*title*". Jeśli chcesz wyświetlić wartość atrybutu, na przykład *ISBN*, ustaw tę <xref:System.Windows.Data.Binding.XPath%2A> wartość na "`@ISBN`".  
  
 Właściwości **XPath** w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są obsługiwane przez metodę XmlNode. SelectNodes. Zapytania **XPath** można modyfikować, aby uzyskać różne wyniki. Poniżej przedstawiono kilka przykładów zapytania <xref:System.Windows.Data.Binding.XPath%2A> na powiązanej <xref:System.Windows.Controls.ListBox> z poprzedniego przykładu:  
  
- `XPath="Book[1]"` zwróci pierwszy element książki ("XML w akcji"). Należy zauważyć, że indeksy **XPath** bazują na 1, nie wartości 0.  
  
- `XPath="Book[@*]"` zwróci wszystkie elementy książki z dowolnymi atrybutami.  
  
- `XPath="Book[last()-1]"` zwróci drugi do ostatniego elementu książki ("wprowadzenie Microsoft .NET").  
  
- `XPath="*[position()>3]"` zwróci wszystkie elementy książki z wyjątkiem pierwszego 3.  
  
 Po uruchomieniu zapytania **XPath** zwraca <xref:System.Xml.XmlNode> lub listę elementów XmlNode. <xref:System.Xml.XmlNode> to obiekt środowiska uruchomieniowego języka wspólnego (CLR), co oznacza, że można użyć właściwości <xref:System.Windows.Data.Binding.Path%2A> do powiązania z właściwościami środowiska uruchomieniowego języka wspólnego (CLR). Rozważmy ponownie poprzedni przykład. Jeśli pozostała część tego przykładu pozostanie taka sama i zmienisz powiązanie <xref:System.Windows.Controls.TextBlock> na następujące, zobaczysz nazwy zwróconych elementów XmlNode w <xref:System.Windows.Controls.ListBox>. W takim przypadku nazwą wszystkich zwracanych węzłów jest "*książka*".  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 W niektórych aplikacjach osadzenie kodu XML jako Wyspy danych w źródle strony [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] może być niewygodne, ponieważ dokładna zawartość danych musi być znana w czasie kompilacji. W związku z tym, uzyskiwanie danych z zewnętrznego pliku XML jest również obsługiwane, jak w poniższym przykładzie:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Jeśli dane XML znajdują się w zdalnym pliku XML, należy zdefiniować dostęp do danych przez przypisanie odpowiedniego adresu URL do atrybutu <xref:System.Windows.Data.XmlDataProvider.Source%2A> w następujący sposób:  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.ObjectDataProvider>
- [Powiązywanie z dokumentem X, elementem X lub LINQ dla wyników zapytań XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)
- [Używanie wzorca szczegółowego z danymi hierarchicznymi XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Wiązanie źródeł — omówienie](binding-sources-overview.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
