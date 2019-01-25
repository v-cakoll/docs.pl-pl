---
title: 'Instrukcje: Utwórz dekorację tekstu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
ms.openlocfilehash: b85bbaed13d9406f85c62a9a5bc5ca220d90b0b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607949"
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="7520a-102">Instrukcje: Utwórz dekorację tekstu</span><span class="sxs-lookup"><span data-stu-id="7520a-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="7520a-103">A <xref:System.Windows.TextDecoration> obiekt jest ornamentacji visual, można dodać do tekstu.</span><span class="sxs-lookup"><span data-stu-id="7520a-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="7520a-104">Istnieją cztery typy dekoracje tekstu: podkreślenie, linii bazowej, przekreślenia i nadkreślenia.</span><span class="sxs-lookup"><span data-stu-id="7520a-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="7520a-105">Poniższy przykład przedstawia lokalizacje dekoracje tekstu względem tekstu.</span><span class="sxs-lookup"><span data-stu-id="7520a-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 <span data-ttu-id="7520a-106">![Diagram lokalizacji dekoracji tekstu](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span><span class="sxs-lookup"><span data-stu-id="7520a-106">![Diagram of text decoration locations](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span></span>  
<span data-ttu-id="7520a-107">Przykład typów dekoracji tekstu</span><span class="sxs-lookup"><span data-stu-id="7520a-107">Example of text decoration types</span></span>  
  
 <span data-ttu-id="7520a-108">Aby dodać dekoracji tekstu do tekstu, należy utworzyć <xref:System.Windows.TextDecoration> obiektów i modyfikowania jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="7520a-108">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="7520a-109">Użyj <xref:System.Windows.TextDecoration.Location%2A> właściwości w celu określenia, gdzie dekoracji tekstu pojawi się, takie jak podkreślenie.</span><span class="sxs-lookup"><span data-stu-id="7520a-109">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="7520a-110">Użyj <xref:System.Windows.TextDecoration.Pen%2A> właściwości w celu określenia wyglądu dekoracji tekstu, takiego jak wypełnienia kryjącego lub kolor gradientu.</span><span class="sxs-lookup"><span data-stu-id="7520a-110">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="7520a-111">Jeśli nie określisz wartości <xref:System.Windows.TextDecoration.Pen%2A> właściwości wartość domyślna dekoracje, to ten sam kolor jak tekst.</span><span class="sxs-lookup"><span data-stu-id="7520a-111">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="7520a-112">Po zdefiniowaniu <xref:System.Windows.TextDecoration> obiektu, dodaj ją do <xref:System.Windows.TextDecorations> kolekcji obiektu odpowiedni tekst.</span><span class="sxs-lookup"><span data-stu-id="7520a-112">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="7520a-113">Dekorację tekstu, który został wstawiony w pędzel gradientów liniowych i Pióro przerywaną, co można znaleźć w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7520a-113">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 <span data-ttu-id="7520a-114">![Dekoracja tekstu z podkreślenie gradientu liniowego](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span><span class="sxs-lookup"><span data-stu-id="7520a-114">![Text decoration with linear gradient underline](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span></span>  
<span data-ttu-id="7520a-115">Przykład podkreślenie styl gradientu liniowego pędzla i kreskowane pióra</span><span class="sxs-lookup"><span data-stu-id="7520a-115">Example of an underline styled with a linear gradient brush and dashed pen</span></span>  
  
 <span data-ttu-id="7520a-116"><xref:System.Windows.Documents.Hyperlink> Obiekt jest element zawartości śródwierszowy przepływ, który pozwala na hosta hiperlinki w dowolnej zawartości.</span><span class="sxs-lookup"><span data-stu-id="7520a-116">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="7520a-117">Domyślnie <xref:System.Windows.Documents.Hyperlink> używa <xref:System.Windows.TextDecoration> obiektu, aby wyświetlić podkreślenie.</span><span class="sxs-lookup"><span data-stu-id="7520a-117">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="7520a-118"><xref:System.Windows.TextDecoration> obiekty mogą być intensywnie do utworzenia wystąpienia, wydajność, zwłaszcza, jeśli dostępnych jest wiele <xref:System.Windows.Documents.Hyperlink> obiektów.</span><span class="sxs-lookup"><span data-stu-id="7520a-118"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="7520a-119">Jeśli wprowadzisz zwiększone użycie <xref:System.Windows.Documents.Hyperlink> elementów, warto wziąć pod uwagę przedstawiający podkreślenie, tylko wtedy, gdy wyzwalanie zdarzenia, takie jak <xref:System.Windows.ContentElement.MouseEnter> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7520a-119">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="7520a-120">W poniższym przykładzie jest dynamiczny podkreślenie dla linku "Mój MSN" — pojawia się tylko, gdy <xref:System.Windows.ContentElement.MouseEnter> zdarzenie jest wyzwalane.</span><span class="sxs-lookup"><span data-stu-id="7520a-120">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="7520a-121">![Wyświetlanie właściwości TextDecorations hiperłącza](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="7520a-121">![Hyperlinks displaying TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="7520a-122">Zdefiniowane za pomocą właściwości TextDecorations hiperłącza</span><span class="sxs-lookup"><span data-stu-id="7520a-122">Hyperlinks defined with TextDecorations</span></span>  
  
 <span data-ttu-id="7520a-123">Aby uzyskać więcej informacji, zobacz [określ czy hiperłącze jest podkreślone](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).</span><span class="sxs-lookup"><span data-stu-id="7520a-123">For more information, see [Specify Whether a Hyperlink is Underlined](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7520a-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="7520a-124">Example</span></span>  
 <span data-ttu-id="7520a-125">W poniższym przykładzie kodu podkreślenia dekoracji tekstu używa wartość domyślna czcionka.</span><span class="sxs-lookup"><span data-stu-id="7520a-125">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="7520a-126">W poniższym przykładzie kodu podkreślenia Dekoracja tekstu jest tworzony z pędzel pełnego koloru pióra.</span><span class="sxs-lookup"><span data-stu-id="7520a-126">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="7520a-127">W poniższym przykładzie kodu dekoracyjną podkreślenie jest tworzony z pędzel gradientów liniowych kreskowane pióra.</span><span class="sxs-lookup"><span data-stu-id="7520a-127">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="7520a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7520a-128">See also</span></span>
- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="7520a-129">Określanie, czy hiperlink jest podkreślony</span><span class="sxs-lookup"><span data-stu-id="7520a-129">Specify Whether a Hyperlink is Underlined</span></span>](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
