---
title: 'Instrukcje: Powiąż z dokumentem X, elementem X lub LINQ dla wyników zapytań XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: 67d81c02ca7a207a48190a3bf09b6ab5dbec17de
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746406"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a><span data-ttu-id="7bdf8-102">Instrukcje: Powiąż z dokumentem X, elementem X lub LINQ dla wyników zapytań XML</span><span class="sxs-lookup"><span data-stu-id="7bdf8-102">How to: Bind to XDocument, XElement, or LINQ for XML Query Results</span></span>
<span data-ttu-id="7bdf8-103">W tym przykładzie pokazano, jak powiązać dane XML do <xref:System.Windows.Controls.ItemsControl> przy użyciu <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="7bdf8-103">This example demonstrates how to bind XML data to an <xref:System.Windows.Controls.ItemsControl> using <xref:System.Xml.Linq.XDocument>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bdf8-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7bdf8-104">Example</span></span>  
 <span data-ttu-id="7bdf8-105">Poniższy kod XAML definiuje <xref:System.Windows.Controls.ItemsControl> i zawiera szablon danych dla danych typu `Planet` w `http://planetsNS` przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="7bdf8-105">The following XAML code defines an <xref:System.Windows.Controls.ItemsControl> and includes a data template for data of type `Planet` in the `http://planetsNS` XML namespace.</span></span> <span data-ttu-id="7bdf8-106">Typu danych XML, który zajmuje przestrzeni nazw musi zawierać przestrzeń nazw w nawiasach klamrowych, a jeśli wygląda na to, gdzie rozszerzenie znaczników XAML może się pojawić, musi poprzedzać przestrzeni nazw przy użyciu sekwencji unikowej nawiasu klamrowego.</span><span class="sxs-lookup"><span data-stu-id="7bdf8-106">An XML data type that occupies a namespace must include the namespace in braces, and if it appears where a XAML markup extension could appear, it must precede the namespace with a brace escape sequence.</span></span> <span data-ttu-id="7bdf8-107">Ten kod wiąże właściwości dynamicznych, które odpowiadają <xref:System.Xml.Linq.XContainer.Element%2A> i <xref:System.Xml.Linq.XElement.Attribute%2A> metody <xref:System.Xml.Linq.XElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="7bdf8-107">This code binds to dynamic properties that correspond to the <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> methods of the <xref:System.Xml.Linq.XElement> class.</span></span> <span data-ttu-id="7bdf8-108">Właściwości dynamiczne Włączanie XAML powiązać właściwości dynamicznych, które mają nazwy metody.</span><span class="sxs-lookup"><span data-stu-id="7bdf8-108">Dynamic properties enable XAML to bind to dynamic properties that share the names of methods.</span></span> <span data-ttu-id="7bdf8-109">Aby dowiedzieć się więcej, zobacz [XML właściwości dynamiczne LINQ to](/visualstudio/designers/linq-to-xml-dynamic-properties).</span><span class="sxs-lookup"><span data-stu-id="7bdf8-109">To learn more, see [LINQ to XML Dynamic Properties](/visualstudio/designers/linq-to-xml-dynamic-properties).</span></span> <span data-ttu-id="7bdf8-110">Zwróć uwagę, jak deklarację domyślnej przestrzeni nazw XML, nie ma zastosowania do nazwy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7bdf8-110">Notice how the default namespace declaration for the XML does not apply to attribute names.</span></span>  
  
 [!code-xaml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 <span data-ttu-id="7bdf8-111">Następujące wywołania kodu C# <xref:System.Xml.Linq.XDocument.Load%2A> i ustawia kontekst danych panelu stosu wszystkie dozwolone podelementy elementu o nazwie `SolarSystemPlanets` w `http://planetsNS` przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="7bdf8-111">The following C# code calls <xref:System.Xml.Linq.XDocument.Load%2A> and sets the stack panel data context to all subelements of the element named `SolarSystemPlanets` in the `http://planetsNS` XML namespace.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 <span data-ttu-id="7bdf8-112">Dane XML mogą być przechowywane jako zasobów XAML przy użyciu <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="7bdf8-112">XML data can be stored as a XAML resource using <xref:System.Windows.Data.ObjectDataProvider>.</span></span> <span data-ttu-id="7bdf8-113">Aby uzyskać kompletny przykład, zobacz [kod źródłowy L2DBForm.xaml](/visualstudio/designers/l2dbform-xaml-source-code).</span><span class="sxs-lookup"><span data-stu-id="7bdf8-113">For a complete example, see  [L2DBForm.xaml source code](/visualstudio/designers/l2dbform-xaml-source-code).</span></span> <span data-ttu-id="7bdf8-114">Poniższy przykład pokazuje, jak kod można ustawić kontekstu danych z zasobem obiektu.</span><span class="sxs-lookup"><span data-stu-id="7bdf8-114">The following sample shows how code can set the data context to an object resource.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 <span data-ttu-id="7bdf8-115">Właściwości dynamicznych, które mapują <xref:System.Xml.Linq.XContainer.Element%2A> i <xref:System.Xml.Linq.XElement.Attribute%2A> zapewniają elastyczność w XAML.</span><span class="sxs-lookup"><span data-stu-id="7bdf8-115">The dynamic properties that map to <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> provide flexibility within XAML.</span></span> <span data-ttu-id="7bdf8-116">Twój kod może także powiązać z wynikami LINQ do kwerendy XML.</span><span class="sxs-lookup"><span data-stu-id="7bdf8-116">Your code can also bind to the results of a LINQ for XML query.</span></span> <span data-ttu-id="7bdf8-117">W tym przykładzie wiąże wyniki zapytania uporządkowane według wartości elementu.</span><span class="sxs-lookup"><span data-stu-id="7bdf8-117">This example binds to query results ordered by an element value.</span></span>  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a><span data-ttu-id="7bdf8-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7bdf8-118">See also</span></span>
- [<span data-ttu-id="7bdf8-119">Wiązanie źródeł — omówienie</span><span class="sxs-lookup"><span data-stu-id="7bdf8-119">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)
- [<span data-ttu-id="7bdf8-120">Powiązanie danych WPF za pomocą LINQ to XML — omówienie</span><span class="sxs-lookup"><span data-stu-id="7bdf8-120">WPF Data Binding with LINQ to XML Overview</span></span>](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)
- [<span data-ttu-id="7bdf8-121">Powiązanie danych WPF za pomocą LINQ to XML — przykład</span><span class="sxs-lookup"><span data-stu-id="7bdf8-121">WPF Data Binding Using LINQ to XML Example</span></span>](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)
- [<span data-ttu-id="7bdf8-122">Właściwości dynamiczne LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="7bdf8-122">LINQ to XML Dynamic Properties</span></span>](/visualstudio/designers/linq-to-xml-dynamic-properties)
