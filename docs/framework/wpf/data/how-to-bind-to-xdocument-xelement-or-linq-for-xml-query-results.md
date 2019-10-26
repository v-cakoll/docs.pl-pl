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
ms.openlocfilehash: 070f67f30613d4522a48e08fd1c208fbe5887525
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920123"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a>Jak powiązać z dokumentem X, elementem X lub LINQ dla wyników zapytań XML

W tym przykładzie pokazano, jak powiązać dane XML z <xref:System.Windows.Controls.ItemsControl> przy użyciu <xref:System.Xml.Linq.XDocument>.

## <a name="example"></a>Przykład

Poniższy kod XAML definiuje <xref:System.Windows.Controls.ItemsControl> i zawiera szablon danych dla danych typu `Planet` w przestrzeni nazw `http://planetsNS` XML. Typ danych XML, który zajmuje przestrzeń nazw, musi zawierać przestrzeń nazw w nawiasach klamrowych, a jeśli pojawia się, gdzie może się pojawić rozszerzenie XAML markup, musi poprzedzać przestrzeń nazw z sekwencją ucieczki w nawiasach klamrowych. Ten kod wiąże się z właściwościami dynamicznymi odpowiadającymi metodom <xref:System.Xml.Linq.XContainer.Element%2A> i <xref:System.Xml.Linq.XElement.Attribute%2A> klasy <xref:System.Xml.Linq.XElement>. Właściwości dynamiczne umożliwiają XAML powiązanie z właściwościami dynamicznymi, które współużytkują nazwy metod. Aby dowiedzieć się więcej, zobacz [LINQ to XML właściwości dynamiczne](linq-to-xml-dynamic-properties.md). Zwróć uwagę, jak domyślna Deklaracja przestrzeni nazw dla XML nie ma zastosowania do nazw atrybutów.

[!code-xaml[XLinqExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]
[!code-xaml[XLinqExample#ItemsControl](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]

Poniższy C# kod wywołuje<xref:System.Xml.Linq.XDocument.Load%2A>i ustawia kontekst danych w panelu stosu na wszystkie podelementy elementu o nazwie`SolarSystemPlanets`w przestrzeni nazw`http://planetsNS`XML.

[!code-csharp[XLinqExample#LoadDCFromFile](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
[!code-vb[XLinqExample#LoadDCFromFile](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]

Dane XML mogą być przechowywane jako zasób XAML przy użyciu <xref:System.Windows.Data.ObjectDataProvider>. Pełny przykład można znaleźć w temacie [kod źródłowy kod źródłowy L2DBForm. XAML](l2dbform-xaml-source-code.md). Poniższy przykład pokazuje, jak kod może ustawić kontekst danych dla zasobu obiektu.

[!code-csharp[XLinqExample#LoadDCFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
[!code-vb[XLinqExample#LoadDCFromXAML](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]

Właściwości dynamiczne, które są mapowane na <xref:System.Xml.Linq.XContainer.Element%2A> i <xref:System.Xml.Linq.XElement.Attribute%2A> zapewniają elastyczność w języku XAML. Kod można także powiązać z wynikami zapytania LINQ for XML. Ten przykład wiąże się z wynikami zapytania uporządkowanymi według wartości elementu.

[!code-csharp[XLinqExample#BindToResults](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
[!code-vb[XLinqExample#BindToResults](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]

## <a name="see-also"></a>Zobacz także

- [Wiązanie źródeł — omówienie](binding-sources-overview.md)
- [Powiązanie danych WPF za pomocą LINQ to XML — omówienie](wpf-data-binding-with-linq-to-xml-overview.md)
- [Powiązanie danych WPF za pomocą LINQ to XML — przykład](linq-to-xml-data-binding-sample.md)
- [Właściwości dynamiczne LINQ to XML](linq-to-xml-dynamic-properties.md)
