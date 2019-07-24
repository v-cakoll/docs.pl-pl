---
title: 'Instrukcje: Udostępnianie danych do powiązania w XAML'
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 3487a160cc49ab6b779a20157668915c2da33900
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401491"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="10cff-102">Instrukcje: Udostępnianie danych do powiązania w XAML</span><span class="sxs-lookup"><span data-stu-id="10cff-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="10cff-103">W tym temacie omówiono różne sposoby tworzenia danych do powiązania w programie, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]w zależności od potrzeb aplikacji.</span><span class="sxs-lookup"><span data-stu-id="10cff-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10cff-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="10cff-104">Example</span></span>  
 <span data-ttu-id="10cff-105">Jeśli masz obiekt środowiska uruchomieniowego języka wspólnego (CLR), z którym chcesz utworzyć powiązanie, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]jednym ze sposobów, aby można było uzyskać dostęp do obiektu dla powiązania, jest definiowanie go jako zasobu i nadanie `x:Key`mu.</span><span class="sxs-lookup"><span data-stu-id="10cff-105">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="10cff-106">W poniższym przykładzie masz `Person` obiekt z właściwością ciągu o nazwie. `PersonName`</span><span class="sxs-lookup"><span data-stu-id="10cff-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="10cff-107">Obiekt (w wyświetlonym wierszu wyróżniony, który `<src>` zawiera element) jest zdefiniowany w przestrzeni nazw o `SDKSample`nazwie. `Person`</span><span class="sxs-lookup"><span data-stu-id="10cff-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="10cff-108">Następnie można powiązać <xref:System.Windows.Controls.TextBlock> formant z obiektem w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jako `<TextBlock>` wyróżniony wiersz, który zawiera element.</span><span class="sxs-lookup"><span data-stu-id="10cff-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span> 
  
 <span data-ttu-id="10cff-109">Alternatywnie można użyć <xref:System.Windows.Data.ObjectDataProvider> klasy, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="10cff-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="10cff-110">Powiązanie można zdefiniować w taki sam sposób, jak wyróżniony wiersz zawierający `<TextBlock>` element.</span><span class="sxs-lookup"><span data-stu-id="10cff-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="10cff-111">W tym konkretnym przykładzie wynik jest taki sam, jak <xref:System.Windows.Controls.TextBlock> w przypadku zawartości `Joe`tekstowej.</span><span class="sxs-lookup"><span data-stu-id="10cff-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="10cff-112"><xref:System.Windows.Data.ObjectDataProvider> Jednak Klasa zawiera funkcje, takie jak możliwość powiązania z wynikami metody.</span><span class="sxs-lookup"><span data-stu-id="10cff-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="10cff-113">Możesz wybrać użycie klasy, <xref:System.Windows.Data.ObjectDataProvider> Jeśli potrzebujesz jej funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="10cff-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="10cff-114">Jeśli jednak tworzysz powiązanie z obiektem, który został już utworzony, musisz ustawić `DataContext` kod w kodzie, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="10cff-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="10cff-115">Aby uzyskać [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dostęp do danych dla powiązania <xref:System.Windows.Data.XmlDataProvider> przy użyciu klasy, zobacz [Powiązywanie z danymi XML przy użyciu XmlDataProvider i zapytań XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="10cff-115">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="10cff-116">Aby uzyskać [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dostęp do danych dla powiązania <xref:System.Windows.Data.ObjectDataProvider> przy użyciu klasy, zobacz [bind to XDocuments, XElement lub LINQ for XML Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="10cff-116">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="10cff-117">Aby uzyskać informacje o wielu sposobach określania danych, do których są wiązane, zobacz [Określanie źródła powiązania](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="10cff-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="10cff-118">Aby uzyskać informacje o typach danych, z którymi można powiązać lub jak zaimplementować własne obiekty środowiska uruchomieniowego języka wspólnego (CLR) na potrzeby tworzenia powiązań, zobacz [Omówienie źródeł powiązań](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="10cff-118">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10cff-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10cff-119">See also</span></span>

- [<span data-ttu-id="10cff-120">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="10cff-120">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="10cff-121">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="10cff-121">How-to Topics</span></span>](data-binding-how-to-topics.md)
