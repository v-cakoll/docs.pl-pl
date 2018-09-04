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
ms.openlocfilehash: 83254bcb0b2aef53a53874a67e8ae169ad242d57
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499942"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a>Jak powiązać z dokumentem X, elementem X lub LINQ dla wyników zapytań XML
W tym przykładzie pokazano, jak powiązać dane XML do <xref:System.Windows.Controls.ItemsControl> przy użyciu <xref:System.Xml.Linq.XDocument>.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XAML definiuje <xref:System.Windows.Controls.ItemsControl> i zawiera szablon danych dla danych typu `Planet` w `http://planetsNS` przestrzeni nazw XML. Typu danych XML, który zajmuje przestrzeni nazw musi zawierać przestrzeń nazw w nawiasach klamrowych, a jeśli wygląda na to, gdzie rozszerzenie znaczników XAML może się pojawić, musi poprzedzać przestrzeni nazw przy użyciu sekwencji unikowej nawiasu klamrowego. Ten kod wiąże właściwości dynamicznych, które odpowiadają <xref:System.Xml.Linq.XContainer.Element%2A> i <xref:System.Xml.Linq.XElement.Attribute%2A> metody <xref:System.Xml.Linq.XElement> klasy. Właściwości dynamiczne Włączanie XAML powiązać właściwości dynamicznych, które mają nazwy metody. Aby dowiedzieć się więcej, zobacz [XML właściwości dynamiczne LINQ to](/visualstudio/designers/linq-to-xml-dynamic-properties). Zwróć uwagę, jak deklarację domyślnej przestrzeni nazw XML, nie ma zastosowania do nazwy atrybutu.  
  
 [!code-xaml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 Następujące wywołania kodu C# <xref:System.Xml.Linq.XDocument.Load%2A> i ustawia kontekst danych panelu stosu wszystkie dozwolone podelementy elementu o nazwie `SolarSystemPlanets` w `http://planetsNS` przestrzeni nazw XML.  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 Dane XML mogą być przechowywane jako zasobów XAML przy użyciu <xref:System.Windows.Data.ObjectDataProvider>. Aby uzyskać kompletny przykład, zobacz [kod źródłowy L2DBForm.xaml](https://msdn.microsoft.com/library/624e96d4-6d27-4195-8ac2-2f3835f6c57e). Poniższy przykład pokazuje, jak kod można ustawić kontekstu danych z zasobem obiektu.  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 Właściwości dynamicznych, które mapują <xref:System.Xml.Linq.XContainer.Element%2A> i <xref:System.Xml.Linq.XElement.Attribute%2A> zapewniają elastyczność w XAML. Twój kod może także powiązać z wynikami LINQ do kwerendy XML. W tym przykładzie wiąże wyniki zapytania uporządkowane według wartości elementu.  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie źródeł — omówienie](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [Powiązanie danych WPF za pomocą LINQ to XML — omówienie](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)  
 [Powiązanie danych WPF za pomocą LINQ to XML — przykład](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)  
 [Właściwości dynamiczne LINQ to XML](/visualstudio/designers/linq-to-xml-dynamic-properties)
