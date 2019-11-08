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
# <a name="how-to-use-xml-namespaces-in-data-binding"></a><span data-ttu-id="69051-102">Jak użyć przestrzeni nazw XML w powiązaniu danych</span><span class="sxs-lookup"><span data-stu-id="69051-102">How to: Use XML Namespaces in Data Binding</span></span>
## <a name="example"></a><span data-ttu-id="69051-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="69051-103">Example</span></span>
 <span data-ttu-id="69051-104">Ten przykład pokazuje, jak obsługiwać przestrzenie nazw określone w źródle powiązania XML.</span><span class="sxs-lookup"><span data-stu-id="69051-104">This example shows how to handle namespaces specified in your XML binding source.</span></span>

 <span data-ttu-id="69051-105">Jeśli dane XML mają następującą definicję przestrzeni nazw XML:</span><span class="sxs-lookup"><span data-stu-id="69051-105">If your XML data has the following XML namespace definition:</span></span>

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 <span data-ttu-id="69051-106">Można użyć elementu <xref:System.Windows.Data.XmlNamespaceMapping> do mapowania przestrzeni nazw na <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="69051-106">You can use the <xref:System.Windows.Data.XmlNamespaceMapping> element to map the namespace to a <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, as in the following example.</span></span> <span data-ttu-id="69051-107">Następnie można użyć <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, aby odwołać się do przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="69051-107">You can then use the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> to refer to the XML namespace.</span></span> <span data-ttu-id="69051-108"><xref:System.Windows.Controls.ListBox> w tym przykładzie wyświetla *tytuł* i *kontroler domeny: Data* każdego *elementu*.</span><span class="sxs-lookup"><span data-stu-id="69051-108">The <xref:System.Windows.Controls.ListBox> in this example displays the *title* and *dc:date* of each *item*.</span></span>

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 <span data-ttu-id="69051-109">Należy zauważyć, że określony <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> nie musi być zgodny z użytym w źródle XML; Jeśli prefiks zmieni się w źródle XML, Twoje mapowanie nadal działa.</span><span class="sxs-lookup"><span data-stu-id="69051-109">Note that the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> you specify does not have to match the one used in the XML source; if the prefix changes in the XML source your mapping still works.</span></span>

 <span data-ttu-id="69051-110">W tym konkretnym przykładzie dane XML pochodzą z usługi sieci Web, ale element <xref:System.Windows.Data.XmlNamespaceMapping> działa również z wbudowanymi danymi XML lub XML w osadzonym pliku.</span><span class="sxs-lookup"><span data-stu-id="69051-110">In this particular example, the XML data comes from a web service, but the <xref:System.Windows.Data.XmlNamespaceMapping> element also works with inline XML or XML data in an embedded file.</span></span>

## <a name="see-also"></a><span data-ttu-id="69051-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69051-111">See also</span></span>

- [<span data-ttu-id="69051-112">Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath</span><span class="sxs-lookup"><span data-stu-id="69051-112">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="69051-113">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="69051-113">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="69051-114">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="69051-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
