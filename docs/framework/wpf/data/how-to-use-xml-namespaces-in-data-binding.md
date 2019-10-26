---
title: Jak użyć przestrzeni nazw XML w powiązaniu danych
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 9d8ddc5445bac28c68cd6cc99acf3313613a8c7f
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919667"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a><span data-ttu-id="f68f1-102">Jak użyć przestrzeni nazw XML w powiązaniu danych</span><span class="sxs-lookup"><span data-stu-id="f68f1-102">How to: Use XML Namespaces in Data Binding</span></span>
## <a name="example"></a><span data-ttu-id="f68f1-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="f68f1-103">Example</span></span>
 <span data-ttu-id="f68f1-104">Ten przykład pokazuje, jak obsługiwać przestrzenie nazw określone w źródle powiązania [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f68f1-104">This example shows how to handle namespaces specified in your [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] binding source.</span></span>

 <span data-ttu-id="f68f1-105">Jeśli dane [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] mają następującą [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] definicji przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="f68f1-105">If your [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data has the following [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace definition:</span></span>

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 <span data-ttu-id="f68f1-106">Można użyć elementu <xref:System.Windows.Data.XmlNamespaceMapping> do mapowania przestrzeni nazw na <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f68f1-106">You can use the <xref:System.Windows.Data.XmlNamespaceMapping> element to map the namespace to a <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, as in the following example.</span></span> <span data-ttu-id="f68f1-107">Następnie można użyć <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, aby odwołać się do przestrzeni nazw [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f68f1-107">You can then use the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> to refer to the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace.</span></span> <span data-ttu-id="f68f1-108"><xref:System.Windows.Controls.ListBox> w tym przykładzie wyświetla *tytuł* i *kontroler domeny: Data* każdego *elementu*.</span><span class="sxs-lookup"><span data-stu-id="f68f1-108">The <xref:System.Windows.Controls.ListBox> in this example displays the *title* and *dc:date* of each *item*.</span></span>

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 <span data-ttu-id="f68f1-109">Należy zauważyć, że określony <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> nie musi być zgodny z użytym w źródle [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]; Jeśli prefiks zmieni się w źródle [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Twoje mapowanie nadal działa.</span><span class="sxs-lookup"><span data-stu-id="f68f1-109">Note that the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> you specify does not have to match the one used in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source; if the prefix changes in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source your mapping still works.</span></span>

 <span data-ttu-id="f68f1-110">W tym konkretnym przykładzie dane [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] pochodzą z usługi sieci Web, ale element <xref:System.Windows.Data.XmlNamespaceMapping> działa również z wbudowanymi [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] lub [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danymi w osadzonym pliku.</span><span class="sxs-lookup"><span data-stu-id="f68f1-110">In this particular example, the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data comes from a web service, but the <xref:System.Windows.Data.XmlNamespaceMapping> element also works with inline [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] or [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data in an embedded file.</span></span>

## <a name="see-also"></a><span data-ttu-id="f68f1-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f68f1-111">See also</span></span>

- [<span data-ttu-id="f68f1-112">Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath</span><span class="sxs-lookup"><span data-stu-id="f68f1-112">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="f68f1-113">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="f68f1-113">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="f68f1-114">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="f68f1-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
