---
title: Jak powiązać z dokumentem X, elementem X lub LINQ dla wyników zapytań XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: 070f67f30613d4522a48e08fd1c208fbe5887525
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920123"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a><span data-ttu-id="5d066-102">Jak powiązać z dokumentem X, elementem X lub LINQ dla wyników zapytań XML</span><span class="sxs-lookup"><span data-stu-id="5d066-102">How to: Bind to XDocument, XElement, or LINQ for XML Query Results</span></span>

<span data-ttu-id="5d066-103">W tym przykładzie pokazano, jak powiązać dane XML z <xref:System.Windows.Controls.ItemsControl> przy użyciu <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="5d066-103">This example demonstrates how to bind XML data to an <xref:System.Windows.Controls.ItemsControl> using <xref:System.Xml.Linq.XDocument>.</span></span>

## <a name="example"></a><span data-ttu-id="5d066-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d066-104">Example</span></span>

<span data-ttu-id="5d066-105">Poniższy kod XAML definiuje <xref:System.Windows.Controls.ItemsControl> i zawiera szablon danych dla danych typu `Planet` w przestrzeni nazw `http://planetsNS` XML.</span><span class="sxs-lookup"><span data-stu-id="5d066-105">The following XAML code defines an <xref:System.Windows.Controls.ItemsControl> and includes a data template for data of type `Planet` in the `http://planetsNS` XML namespace.</span></span> <span data-ttu-id="5d066-106">Typ danych XML, który zajmuje przestrzeń nazw, musi zawierać przestrzeń nazw w nawiasach klamrowych, a jeśli pojawia się, gdzie może się pojawić rozszerzenie XAML markup, musi poprzedzać przestrzeń nazw z sekwencją ucieczki w nawiasach klamrowych.</span><span class="sxs-lookup"><span data-stu-id="5d066-106">An XML data type that occupies a namespace must include the namespace in braces, and if it appears where a XAML markup extension could appear, it must precede the namespace with a brace escape sequence.</span></span> <span data-ttu-id="5d066-107">Ten kod wiąże się z właściwościami dynamicznymi odpowiadającymi metodom <xref:System.Xml.Linq.XContainer.Element%2A> i <xref:System.Xml.Linq.XElement.Attribute%2A> klasy <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5d066-107">This code binds to dynamic properties that correspond to the <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> methods of the <xref:System.Xml.Linq.XElement> class.</span></span> <span data-ttu-id="5d066-108">Właściwości dynamiczne umożliwiają XAML powiązanie z właściwościami dynamicznymi, które współużytkują nazwy metod.</span><span class="sxs-lookup"><span data-stu-id="5d066-108">Dynamic properties enable XAML to bind to dynamic properties that share the names of methods.</span></span> <span data-ttu-id="5d066-109">Aby dowiedzieć się więcej, zobacz [LINQ to XML właściwości dynamiczne](linq-to-xml-dynamic-properties.md).</span><span class="sxs-lookup"><span data-stu-id="5d066-109">To learn more, see [LINQ to XML dynamic properties](linq-to-xml-dynamic-properties.md).</span></span> <span data-ttu-id="5d066-110">Zwróć uwagę, jak domyślna Deklaracja przestrzeni nazw dla XML nie ma zastosowania do nazw atrybutów.</span><span class="sxs-lookup"><span data-stu-id="5d066-110">Notice how the default namespace declaration for the XML does not apply to attribute names.</span></span>

[!code-xaml[XLinqExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]
[!code-xaml[XLinqExample#ItemsControl](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]

<span data-ttu-id="5d066-111">Poniższy C# kod wywołuje<xref:System.Xml.Linq.XDocument.Load%2A>i ustawia kontekst danych w panelu stosu na wszystkie podelementy elementu o nazwie`SolarSystemPlanets`w przestrzeni nazw`http://planetsNS`XML.</span><span class="sxs-lookup"><span data-stu-id="5d066-111">The following C# code calls <xref:System.Xml.Linq.XDocument.Load%2A> and sets the stack panel data context to all subelements of the element named `SolarSystemPlanets` in the `http://planetsNS` XML namespace.</span></span>

[!code-csharp[XLinqExample#LoadDCFromFile](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
[!code-vb[XLinqExample#LoadDCFromFile](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]

<span data-ttu-id="5d066-112">Dane XML mogą być przechowywane jako zasób XAML przy użyciu <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="5d066-112">XML data can be stored as a XAML resource using <xref:System.Windows.Data.ObjectDataProvider>.</span></span> <span data-ttu-id="5d066-113">Pełny przykład można znaleźć w temacie [kod źródłowy kod źródłowy L2DBForm. XAML](l2dbform-xaml-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="5d066-113">For a complete example, see  [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span> <span data-ttu-id="5d066-114">Poniższy przykład pokazuje, jak kod może ustawić kontekst danych dla zasobu obiektu.</span><span class="sxs-lookup"><span data-stu-id="5d066-114">The following sample shows how code can set the data context to an object resource.</span></span>

[!code-csharp[XLinqExample#LoadDCFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
[!code-vb[XLinqExample#LoadDCFromXAML](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]

<span data-ttu-id="5d066-115">Właściwości dynamiczne, które są mapowane na <xref:System.Xml.Linq.XContainer.Element%2A> i <xref:System.Xml.Linq.XElement.Attribute%2A> zapewniają elastyczność w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="5d066-115">The dynamic properties that map to <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> provide flexibility within XAML.</span></span> <span data-ttu-id="5d066-116">Kod można także powiązać z wynikami zapytania LINQ for XML.</span><span class="sxs-lookup"><span data-stu-id="5d066-116">Your code can also bind to the results of a LINQ for XML query.</span></span> <span data-ttu-id="5d066-117">Ten przykład wiąże się z wynikami zapytania uporządkowanymi według wartości elementu.</span><span class="sxs-lookup"><span data-stu-id="5d066-117">This example binds to query results ordered by an element value.</span></span>

[!code-csharp[XLinqExample#BindToResults](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
[!code-vb[XLinqExample#BindToResults](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]

## <a name="see-also"></a><span data-ttu-id="5d066-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d066-118">See also</span></span>

- [<span data-ttu-id="5d066-119">Wiązanie źródeł — omówienie</span><span class="sxs-lookup"><span data-stu-id="5d066-119">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="5d066-120">Powiązanie danych WPF za pomocą LINQ to XML — omówienie</span><span class="sxs-lookup"><span data-stu-id="5d066-120">WPF Data Binding with LINQ to XML Overview</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="5d066-121">Powiązanie danych WPF za pomocą LINQ to XML — przykład</span><span class="sxs-lookup"><span data-stu-id="5d066-121">WPF Data Binding Using LINQ to XML Example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="5d066-122">Właściwości dynamiczne LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="5d066-122">LINQ to XML Dynamic Properties</span></span>](linq-to-xml-dynamic-properties.md)
