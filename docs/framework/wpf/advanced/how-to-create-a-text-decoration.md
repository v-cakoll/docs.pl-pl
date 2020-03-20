---
title: Jak utworzyć dekorację tekstu
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
ms.openlocfilehash: cf3b3c3bcb75153a0be4f7ced03b38134b79a930
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185920"
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="93e6c-102">Jak utworzyć dekorację tekstu</span><span class="sxs-lookup"><span data-stu-id="93e6c-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="93e6c-103">Obiekt <xref:System.Windows.TextDecoration> jest ozdobą wizualną, którą można dodać do tekstu.</span><span class="sxs-lookup"><span data-stu-id="93e6c-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="93e6c-104">Istnieją cztery typy dekoracji tekstu: podkreślenie, linia bazowa, przekreślenie i linia zbyta.</span><span class="sxs-lookup"><span data-stu-id="93e6c-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="93e6c-105">W poniższym przykładzie przedstawiono lokalizacje dekoracji tekstu względem tekstu.</span><span class="sxs-lookup"><span data-stu-id="93e6c-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 ![Diagram typów dekoracji tekstu](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 <span data-ttu-id="93e6c-107">Aby dodać dekorację tekstu do <xref:System.Windows.TextDecoration> tekstu, utwórz obiekt i zmodyfikuj jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="93e6c-107">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="93e6c-108">Użyj <xref:System.Windows.TextDecoration.Location%2A> właściwości, aby określić, gdzie pojawia się dekoracja tekstu, takich jak podkreślenie.</span><span class="sxs-lookup"><span data-stu-id="93e6c-108">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="93e6c-109">Użyj <xref:System.Windows.TextDecoration.Pen%2A> właściwości, aby określić wygląd dekoracji tekstu, na przykład pełny kolor wypełnienia lub gradientu.</span><span class="sxs-lookup"><span data-stu-id="93e6c-109">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="93e6c-110">Jeśli nie określisz wartości <xref:System.Windows.TextDecoration.Pen%2A> właściwości, dekoracje domyślnie mają ten sam kolor co tekst.</span><span class="sxs-lookup"><span data-stu-id="93e6c-110">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="93e6c-111">Po zdefiniowaniu <xref:System.Windows.TextDecoration> obiektu dodaj go <xref:System.Windows.TextDecorations> do kolekcji żądanego obiektu tekstowego.</span><span class="sxs-lookup"><span data-stu-id="93e6c-111">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="93e6c-112">W poniższym przykładzie przedstawiono dekorację tekstu stylizowaną za pomocą pędzla gradientu liniowego i pióra przerywanego.</span><span class="sxs-lookup"><span data-stu-id="93e6c-112">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 ![Dekoracja tekstu z podkreśleniem gradientu liniowego](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 <span data-ttu-id="93e6c-114">Obiekt <xref:System.Windows.Documents.Hyperlink> jest elementem zawartości przepływu na poziomie wbudowanym, który umożliwia hostować hiperłącza w zawartości przepływu.</span><span class="sxs-lookup"><span data-stu-id="93e6c-114">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="93e6c-115">Domyślnie <xref:System.Windows.Documents.Hyperlink> obiekt jest <xref:System.Windows.TextDecoration> używany do wyświetlania podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="93e6c-115">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="93e6c-116"><xref:System.Windows.TextDecoration>obiekty mogą być intensywnie wydajne do wystąpienia, <xref:System.Windows.Documents.Hyperlink> szczególnie jeśli masz wiele obiektów.</span><span class="sxs-lookup"><span data-stu-id="93e6c-116"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="93e6c-117">Jeśli szeroko korzystać <xref:System.Windows.Documents.Hyperlink> z elementów, można rozważyć pokazano podkreślenie tylko podczas <xref:System.Windows.ContentElement.MouseEnter> wyzwalania zdarzenia, takich jak zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="93e6c-117">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="93e6c-118">W poniższym przykładzie podkreślenie łącza "Moje MSN" jest <xref:System.Windows.ContentElement.MouseEnter> dynamiczne — pojawia się tylko wtedy, gdy zdarzenie jest wyzwalane.</span><span class="sxs-lookup"><span data-stu-id="93e6c-118">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 ![Hiperłącza wyświetlające dekoracje tekstowe](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  

 <span data-ttu-id="93e6c-120">Aby uzyskać więcej informacji, zobacz [Określanie, czy hiperłącze jest podkreślone](how-to-specify-whether-a-hyperlink-is-underlined.md).</span><span class="sxs-lookup"><span data-stu-id="93e6c-120">For more information, see [Specify Whether a Hyperlink is Underlined](how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="93e6c-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="93e6c-121">Example</span></span>  
 <span data-ttu-id="93e6c-122">W poniższym przykładzie kodu dekoracja tekstu podkreślenia używa domyślnej wartości czcionki.</span><span class="sxs-lookup"><span data-stu-id="93e6c-122">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="93e6c-123">W poniższym przykładzie kodu zostanie utworzona dekoracja tekstu podkreślenia za pomocą pędzla z jednolitym kolorem pióra.</span><span class="sxs-lookup"><span data-stu-id="93e6c-123">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="93e6c-124">W poniższym przykładzie kodu zostanie utworzona dekoracja tekstu podkreślenia za pomocą pędzla gradientu liniowego dla pióra przerywanego.</span><span class="sxs-lookup"><span data-stu-id="93e6c-124">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="93e6c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93e6c-125">See also</span></span>

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="93e6c-126">Określanie, czy hiperlink jest podkreślony</span><span class="sxs-lookup"><span data-stu-id="93e6c-126">Specify Whether a Hyperlink is Underlined</span></span>](how-to-specify-whether-a-hyperlink-is-underlined.md)
