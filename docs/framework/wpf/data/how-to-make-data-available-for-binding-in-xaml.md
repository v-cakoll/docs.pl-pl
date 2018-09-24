---
title: Jak udostępnić dane do powiązania w XAML
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 09a6fca48c06efca6f06b9e0617de9095197bd17
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703492"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="261bb-102">Jak udostępnić dane do powiązania w XAML</span><span class="sxs-lookup"><span data-stu-id="261bb-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="261bb-103">W tym temacie omówiono różne sposoby, które można udostępnić dane do powiązania w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], w zależności od potrzeb aplikacji.</span><span class="sxs-lookup"><span data-stu-id="261bb-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="261bb-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="261bb-104">Example</span></span>  
 <span data-ttu-id="261bb-105">Jeśli masz [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektów, które chcesz powiązać z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jeden ze sposobów, które można udostępnić obiektu dla powiązania jest do definiowania go jako zasób i nadaj mu `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="261bb-105">If you have a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="261bb-106">W poniższym przykładzie użytkownik ma `Person` obiektu z właściwością ciągu o nazwie `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="261bb-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="261bb-107">`Person` Obiektu (w wierszu wyświetlane wyróżnione zawierający `<src>` elementu) jest zdefiniowany w przestrzeni nazw o nazwie `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="261bb-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="261bb-108">Następnie możesz powiązać <xref:System.Windows.Controls.TextBlock> formantu do obiektu w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jak wyróżniony wiersz zawiera `<TextBlock>` pokazuje element.</span><span class="sxs-lookup"><span data-stu-id="261bb-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span> 
  
 <span data-ttu-id="261bb-109">Alternatywnie, można użyć <xref:System.Windows.Data.ObjectDataProvider> klasy, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="261bb-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="261bb-110">Zdefiniuj powiązanie taki sam sposób, jak wyróżniony wiersz, który zawiera `<TextBlock>` pokazuje element.</span><span class="sxs-lookup"><span data-stu-id="261bb-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="261bb-111">W tym przykładzie, wynik jest taki sam: masz <xref:System.Windows.Controls.TextBlock> z zawartością tekstową `Joe`.</span><span class="sxs-lookup"><span data-stu-id="261bb-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="261bb-112">Jednak <xref:System.Windows.Data.ObjectDataProvider> klasa oferuje funkcje, takie jak możliwość powiązania do wyniku metody.</span><span class="sxs-lookup"><span data-stu-id="261bb-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="261bb-113">Możesz użyć <xref:System.Windows.Data.ObjectDataProvider> klasy, jeśli potrzebujesz funkcji zapewnia.</span><span class="sxs-lookup"><span data-stu-id="261bb-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="261bb-114">Jednak jeśli dokonywane jest wiązanie obiektu, który został już utworzony, musisz ustawić `DataContext` w kodzie, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="261bb-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="261bb-115">Aby uzyskać dostęp do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane dotyczące korzystania z wiązania <xref:System.Windows.Data.XmlDataProvider> klasy, zobacz [powiązania danych XML przy użyciu XMLDataProvider i zapytań XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="261bb-115">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="261bb-116">Aby uzyskać dostęp do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane dotyczące korzystania z wiązania <xref:System.Windows.Data.ObjectDataProvider> klasy, zobacz [Powiąż z dokumentem, elementem x lub LINQ dla wyników zapytań XML](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="261bb-116">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="261bb-117">Aby uzyskać informacje o wiele sposobów, można określić dane, w której dokonywane jest wiązanie, zobacz [określić źródło wiążące](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="261bb-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="261bb-118">Więcej informacji o jakie typy danych można powiązać i jak implementować własne [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektów dla powiązania, zobacz [wiązanie źródeł — omówienie](../../../../docs/framework/wpf/data/binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="261bb-118">For information about what types of data you can bind to or how to implement your own [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objects for binding, see [Binding Sources Overview](../../../../docs/framework/wpf/data/binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="261bb-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="261bb-119">See Also</span></span>  
 [<span data-ttu-id="261bb-120">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="261bb-120">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="261bb-121">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="261bb-121">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
