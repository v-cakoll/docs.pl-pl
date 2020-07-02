---
title: Jak udostępnić dane do powiązania w XAML
description: Poznaj różne sposoby udostępniania danych zgodnie z potrzebami aplikacji w Windows Presentation Foundation (WPF).
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 16618ce8b19f5dd5854c4d126e7fc455f0428a28
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620797"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="97b64-103">Jak udostępnić dane do powiązania w XAML</span><span class="sxs-lookup"><span data-stu-id="97b64-103">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="97b64-104">W tym temacie omówiono różne sposoby tworzenia danych do powiązania w programie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , w zależności od potrzeb aplikacji.</span><span class="sxs-lookup"><span data-stu-id="97b64-104">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97b64-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="97b64-105">Example</span></span>  
 <span data-ttu-id="97b64-106">Jeśli masz obiekt środowiska uruchomieniowego języka wspólnego (CLR), z którym chcesz utworzyć powiązanie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , jednym ze sposobów, aby można było uzyskać dostęp do obiektu dla powiązania, jest definiowanie go jako zasobu i nadanie mu `x:Key` .</span><span class="sxs-lookup"><span data-stu-id="97b64-106">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="97b64-107">W poniższym przykładzie masz `Person` obiekt z właściwością ciągu o nazwie `PersonName` .</span><span class="sxs-lookup"><span data-stu-id="97b64-107">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="97b64-108">`Person`Obiekt (w wyświetlonym wierszu wyróżniony, który zawiera `<src>` element) jest zdefiniowany w przestrzeni nazw o nazwie `SDKSample` .</span><span class="sxs-lookup"><span data-stu-id="97b64-108">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="97b64-109">Następnie można powiązać <xref:System.Windows.Controls.TextBlock> formant z obiektem w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , jako wyróżniony wiersz, który zawiera `<TextBlock>` element.</span><span class="sxs-lookup"><span data-stu-id="97b64-109">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span>
  
 <span data-ttu-id="97b64-110">Alternatywnie można użyć <xref:System.Windows.Data.ObjectDataProvider> klasy, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="97b64-110">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="97b64-111">Powiązanie można zdefiniować w taki sam sposób, jak wyróżniony wiersz zawierający `<TextBlock>` element.</span><span class="sxs-lookup"><span data-stu-id="97b64-111">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="97b64-112">W tym konkretnym przykładzie wynik jest taki sam, jak w przypadku <xref:System.Windows.Controls.TextBlock> zawartości tekstowej `Joe` .</span><span class="sxs-lookup"><span data-stu-id="97b64-112">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="97b64-113">Jednak <xref:System.Windows.Data.ObjectDataProvider> Klasa zawiera funkcje, takie jak możliwość powiązania z wynikami metody.</span><span class="sxs-lookup"><span data-stu-id="97b64-113">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="97b64-114">Możesz wybrać użycie <xref:System.Windows.Data.ObjectDataProvider> klasy, jeśli potrzebujesz jej funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="97b64-114">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="97b64-115">Jeśli jednak tworzysz powiązanie z obiektem, który został już utworzony, musisz ustawić `DataContext` kod w kodzie, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="97b64-115">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="97b64-116">Aby uzyskać dostęp do danych XML na potrzeby wiązania przy użyciu <xref:System.Windows.Data.XmlDataProvider> klasy, zobacz [Powiązywanie z danymi XML przy użyciu XmlDataProvider i zapytań XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="97b64-116">To access XML data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="97b64-117">Aby uzyskać dostęp do danych XML dla powiązania przy użyciu <xref:System.Windows.Data.ObjectDataProvider> klasy, zobacz [bind to XDocument, XELEMENT lub LINQ for XML Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="97b64-117">To access XML data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="97b64-118">Aby uzyskać informacje o wielu sposobach określania danych, do których są wiązane, zobacz [Określanie źródła powiązania](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="97b64-118">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="97b64-119">Aby uzyskać informacje o typach danych, z którymi można powiązać lub jak zaimplementować własne obiekty środowiska uruchomieniowego języka wspólnego (CLR) na potrzeby tworzenia powiązań, zobacz [Omówienie źródeł powiązań](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="97b64-119">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97b64-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97b64-120">See also</span></span>

- [<span data-ttu-id="97b64-121">Przegląd powiązań danych</span><span class="sxs-lookup"><span data-stu-id="97b64-121">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="97b64-122">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="97b64-122">How-to Topics</span></span>](data-binding-how-to-topics.md)
