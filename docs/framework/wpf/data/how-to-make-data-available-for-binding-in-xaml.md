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
ms.openlocfilehash: 2bfd9809a6ad487a7e706366dc6bce8fe951c940
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459763"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="9b7e2-102">Jak udostępnić dane do powiązania w XAML</span><span class="sxs-lookup"><span data-stu-id="9b7e2-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="9b7e2-103">W tym temacie omówiono różne sposoby udostępniania danych do powiązań w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], w zależności od potrzeb aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b7e2-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b7e2-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9b7e2-104">Example</span></span>  
 <span data-ttu-id="9b7e2-105">Jeśli masz obiekt środowiska uruchomieniowego języka wspólnego (CLR), z którym chcesz utworzyć powiązanie z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jednym ze sposobów udostępnienia obiektu do powiązania jest zdefiniowanie go jako zasobu i nadanie mu `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="9b7e2-105">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="9b7e2-106">W poniższym przykładzie masz `Person` obiekt z właściwością ciągu o nazwie `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="9b7e2-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="9b7e2-107">Obiekt `Person` (w wyróżnionym wierszu zawierającym element `<src>`) jest zdefiniowany w przestrzeni nazw o nazwie `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="9b7e2-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="9b7e2-108">Następnie można powiązać formant <xref:System.Windows.Controls.TextBlock> z obiektem w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jak wyróżniony wiersz zawiera element `<TextBlock>`.</span><span class="sxs-lookup"><span data-stu-id="9b7e2-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span> 
  
 <span data-ttu-id="9b7e2-109">Alternatywnie można użyć klasy <xref:System.Windows.Data.ObjectDataProvider>, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9b7e2-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="9b7e2-110">Powiązanie można zdefiniować w taki sam sposób, jak wyróżniony wiersz zawierający element `<TextBlock>`.</span><span class="sxs-lookup"><span data-stu-id="9b7e2-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="9b7e2-111">W tym konkretnym przykładzie wynik jest taki sam: masz <xref:System.Windows.Controls.TextBlock> z `Joe`zawartości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="9b7e2-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="9b7e2-112">Jednak Klasa <xref:System.Windows.Data.ObjectDataProvider> udostępnia funkcje, takie jak możliwość powiązania z wynikami metody.</span><span class="sxs-lookup"><span data-stu-id="9b7e2-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="9b7e2-113">Możesz użyć klasy <xref:System.Windows.Data.ObjectDataProvider>, jeśli potrzebujesz jej funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="9b7e2-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="9b7e2-114">Jeśli jednak tworzysz powiązanie z obiektem, który został już utworzony, musisz ustawić `DataContext` w kodzie, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9b7e2-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="9b7e2-115">Aby uzyskać dostęp do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych dla powiązania przy użyciu klasy <xref:System.Windows.Data.XmlDataProvider>, zobacz [Powiązywanie z danymi XML przy użyciu XmlDataProvider i zapytań XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="9b7e2-115">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="9b7e2-116">Aby uzyskać dostęp do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych dla powiązania przy użyciu klasy <xref:System.Windows.Data.ObjectDataProvider>, zobacz [bind to XElement lub LINQ for XML Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="9b7e2-116">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="9b7e2-117">Aby uzyskać informacje o wielu sposobach określania danych, do których są wiązane, zobacz [Określanie źródła powiązania](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="9b7e2-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="9b7e2-118">Aby uzyskać informacje o typach danych, z którymi można powiązać lub jak zaimplementować własne obiekty środowiska uruchomieniowego języka wspólnego (CLR) na potrzeby tworzenia powiązań, zobacz [Omówienie źródeł powiązań](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9b7e2-118">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b7e2-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b7e2-119">See also</span></span>

- [<span data-ttu-id="9b7e2-120">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="9b7e2-120">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="9b7e2-121">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="9b7e2-121">How-to Topics</span></span>](data-binding-how-to-topics.md)
