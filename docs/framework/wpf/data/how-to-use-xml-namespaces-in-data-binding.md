---
title: Jak użyć przestrzeni nazw XML w powiązaniu danych
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: f6e6e042fa5583fcf91bd15c524537490fb6670c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740575"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Jak użyć przestrzeni nazw XML w powiązaniu danych
## <a name="example"></a>Przykład
 Ten przykład pokazuje, jak obsługiwać przestrzenie nazw określone w źródle powiązania XML.

 Jeśli dane XML mają następującą definicję przestrzeni nazw XML:

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 Można użyć elementu <xref:System.Windows.Data.XmlNamespaceMapping> do mapowania przestrzeni nazw na <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, jak w poniższym przykładzie. Następnie można użyć <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, aby odwołać się do przestrzeni nazw XML. <xref:System.Windows.Controls.ListBox> w tym przykładzie wyświetla *tytuł* i *kontroler domeny: Data* każdego *elementu*.

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 Należy zauważyć, że określony <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> nie musi być zgodny z użytym w źródle XML; Jeśli prefiks zmieni się w źródle XML, Twoje mapowanie nadal działa.

 W tym konkretnym przykładzie dane XML pochodzą z usługi sieci Web, ale element <xref:System.Windows.Data.XmlNamespaceMapping> działa również z wbudowanymi danymi XML lub XML w osadzonym pliku.

## <a name="see-also"></a>Zobacz także

- [Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
