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
ms.openlocfilehash: 91e89dbf36024c31f4afcd9b6d956944baf13576
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174189"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="485df-102">Jak udostępnić dane do powiązania w XAML</span><span class="sxs-lookup"><span data-stu-id="485df-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="485df-103">W tym temacie omówiono różne sposoby [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]udostępniania danych do powiązania w programie , w zależności od potrzeb aplikacji.</span><span class="sxs-lookup"><span data-stu-id="485df-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="485df-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="485df-104">Example</span></span>  
 <span data-ttu-id="485df-105">Jeśli masz wspólny obiekt środowiska uruchomieniowego języka (CLR), [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]z którego chcesz powiązać, jednym ze sposobów udostępnienia obiektu `x:Key`do powiązania jest zdefiniowanie go jako zasobu i nadanie mu .</span><span class="sxs-lookup"><span data-stu-id="485df-105">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="485df-106">W poniższym przykładzie `Person` masz obiekt o `PersonName`nazwie .</span><span class="sxs-lookup"><span data-stu-id="485df-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="485df-107">Obiekt `Person` (w wyświetlonym wierszu wyróżnionym, `<src>` który zawiera element) `SDKSample`jest zdefiniowany w obszarze nazw o nazwie .</span><span class="sxs-lookup"><span data-stu-id="485df-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="485df-108">Następnie można powiązać <xref:System.Windows.Controls.TextBlock> formant [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]z obiektem w , `<TextBlock>` jak podświetlony wiersz, który zawiera element.</span><span class="sxs-lookup"><span data-stu-id="485df-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span>
  
 <span data-ttu-id="485df-109">Alternatywnie można użyć <xref:System.Windows.Data.ObjectDataProvider> klasy, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="485df-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="485df-110">Wiązania można zdefiniować w taki sam sposób, `<TextBlock>` jak wyróżniony wiersz, który zawiera element pokazuje.</span><span class="sxs-lookup"><span data-stu-id="485df-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="485df-111">W tym konkretnym przykładzie wynik jest <xref:System.Windows.Controls.TextBlock> taki sam: `Joe`masz z zawartością tekstową .</span><span class="sxs-lookup"><span data-stu-id="485df-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="485df-112">Jednak <xref:System.Windows.Data.ObjectDataProvider> klasa zapewnia funkcje, takie jak możliwość powiązania z wynikiem metody.</span><span class="sxs-lookup"><span data-stu-id="485df-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="485df-113">Można użyć klasy, <xref:System.Windows.Data.ObjectDataProvider> jeśli potrzebujesz funkcji, które zapewnia.</span><span class="sxs-lookup"><span data-stu-id="485df-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="485df-114">Jednak jeśli są wiążące dla obiektu, który został już `DataContext` utworzony, należy ustawić w kodzie, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="485df-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="485df-115">Aby uzyskać dostęp do danych <xref:System.Windows.Data.XmlDataProvider> XML do powiązania przy użyciu klasy, zobacz [Powiązanie danych XML przy użyciu aplikacji XMLDataProvider i XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="485df-115">To access XML data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="485df-116">Aby uzyskać dostęp do danych <xref:System.Windows.Data.ObjectDataProvider> XML do powiązania przy użyciu klasy, zobacz [Bind to XDocument, XElement lub LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="485df-116">To access XML data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="485df-117">Aby uzyskać informacje o wielu sposobach określania danych, z których użytkownik jest powiązany, zobacz [Określanie źródła wiązania](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="485df-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="485df-118">Aby uzyskać informacje o typach danych, z jakimi można powiązać lub jak zaimplementować własne obiekty środowiska wykonawczego języka wspólnego (CLR) do wiązania, zobacz [Omówienie źródeł powiązania.](binding-sources-overview.md)</span><span class="sxs-lookup"><span data-stu-id="485df-118">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="485df-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="485df-119">See also</span></span>

- [<span data-ttu-id="485df-120">Przegląd Wiązanie danych</span><span class="sxs-lookup"><span data-stu-id="485df-120">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="485df-121">Tematy in jakże</span><span class="sxs-lookup"><span data-stu-id="485df-121">How-to Topics</span></span>](data-binding-how-to-topics.md)
