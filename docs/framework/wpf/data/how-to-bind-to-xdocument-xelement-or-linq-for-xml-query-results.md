---
title: Jak powiązać z dokumentem X, elementem X lub LINQ dla wyników zapytań XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: 7e4f9cc2f5e6815a35b4911f5b4a480161d66ef3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a>Jak powiązać z dokumentem X, elementem X lub LINQ dla wyników zapytań XML
W tym przykładzie pokazano, jak można powiązać danych XML do <xref:System.Windows.Controls.ItemsControl> przy użyciu <xref:System.Xml.Linq.XDocument>.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XAML definiuje <xref:System.Windows.Controls.ItemsControl> i zawiera szablon danych danych typu `Planet` w `http://planetsNS` przestrzeni nazw XML. Typ danych XML, który zajmie przestrzeni nazw musi zawierać przestrzeni nazw w nawiasach klamrowych, a jeśli wygląda na to, gdzie może być rozszerzenie znaczników w XAML, musi poprzedzać przestrzeni nazw w sekwencji ucieczki nawiasu klamrowego. Ten kod jest powiązany z właściwości dynamiczne, które odpowiadają <xref:System.Xml.Linq.XContainer.Element%2A> i <xref:System.Xml.Linq.XElement.Attribute%2A> metody <xref:System.Xml.Linq.XElement> klasy. Właściwości dynamiczne Włączanie XAML powiązać właściwości dynamiczne, które mają nazwy metody. Aby dowiedzieć się więcej, zobacz [LINQ do XML właściwości dynamicznych](/visualstudio/designers/linq-to-xml-dynamic-properties). Zwróć uwagę, jak deklarację domyślnej przestrzeni nazw XML, nie ma zastosowania do nazw atrybutów.  
  
 [!code-xaml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 Następujące wywołania kodu C# <xref:System.Xml.Linq.XDocument.Load%2A> i ustawia kontekst danych panelu stosu wszystkie podelementy elementu o nazwie `SolarSystemPlanets` w `http://planetsNS` przestrzeni nazw XML.  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 Dane XML mogą być przechowywane jako przy użyciu zasobów XAML <xref:System.Windows.Data.ObjectDataProvider>. Pełny przykład, zobacz [kod źródłowy L2DBForm.xaml](http://msdn.microsoft.com/library/624e96d4-6d27-4195-8ac2-2f3835f6c57e). Poniższy przykład pokazuje, jak kod można ustawić kontekstu danych zasobów obiektów.  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 Właściwości dynamiczne, które mapują <xref:System.Xml.Linq.XContainer.Element%2A> i <xref:System.Xml.Linq.XElement.Attribute%2A> zapewniają elastyczność w języku XAML. Kod może także powiązać wyniki LINQ dla zapytania XML. W tym przykładzie wiąże się z wynikami zapytania uporządkowanych według wartości elementu.  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie źródeł — omówienie](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [Powiązanie danych WPF za pomocą LINQ to XML — omówienie](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)  
 [Powiązanie danych WPF za pomocą LINQ to XML — przykład](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)  
 [Właściwości dynamiczne LINQ to XML](/visualstudio/designers/linq-to-xml-dynamic-properties)
