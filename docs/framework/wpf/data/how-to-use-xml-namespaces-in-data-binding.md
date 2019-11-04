---
title: Jak użyć przestrzeni nazw XML w powiązaniu danych
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 47ce0d951df39c7b60aa2a543baf845f5471de6c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460303"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Jak użyć przestrzeni nazw XML w powiązaniu danych
## <a name="example"></a>Przykład
 Ten przykład pokazuje, jak obsługiwać przestrzenie nazw określone w źródle powiązania [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].

 Jeśli dane [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] mają następującą [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] definicji przestrzeni nazw:

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 Można użyć elementu <xref:System.Windows.Data.XmlNamespaceMapping> do mapowania przestrzeni nazw na <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, jak w poniższym przykładzie. Następnie można użyć <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, aby odwołać się do przestrzeni nazw [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. <xref:System.Windows.Controls.ListBox> w tym przykładzie wyświetla *tytuł* i *kontroler domeny: Data* każdego *elementu*.

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 Należy zauważyć, że określony <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> nie musi być zgodny z użytym w źródle [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]; Jeśli prefiks zmieni się w źródle [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Twoje mapowanie nadal działa.

 W tym konkretnym przykładzie dane [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] pochodzą z usługi sieci Web, ale element <xref:System.Windows.Data.XmlNamespaceMapping> działa również z wbudowanymi [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] lub [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danymi w osadzonym pliku.

## <a name="see-also"></a>Zobacz także

- [Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
