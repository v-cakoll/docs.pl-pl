---
title: 'Porady: Utwórz dekorację tekstu'
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
ms.openlocfilehash: 22ff91770786e39e019de307167007548396ab33
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411333"
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="9659d-102">Instrukcje: Utwórz dekorację tekstu</span><span class="sxs-lookup"><span data-stu-id="9659d-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="9659d-103">A <xref:System.Windows.TextDecoration> obiekt jest ornamentacji visual, można dodać do tekstu.</span><span class="sxs-lookup"><span data-stu-id="9659d-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="9659d-104">Istnieją cztery typy dekoracje tekstu: podkreślenie, linii bazowej, przekreślenia i nadkreślenia.</span><span class="sxs-lookup"><span data-stu-id="9659d-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="9659d-105">Poniższy przykład przedstawia lokalizacje dekoracje tekstu względem tekstu.</span><span class="sxs-lookup"><span data-stu-id="9659d-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 ![Diagram przedstawiający typów dekoracji tekstu](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 <span data-ttu-id="9659d-107">Aby dodać dekoracji tekstu do tekstu, należy utworzyć <xref:System.Windows.TextDecoration> obiektów i modyfikowania jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="9659d-107">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="9659d-108">Użyj <xref:System.Windows.TextDecoration.Location%2A> właściwości w celu określenia, gdzie dekoracji tekstu pojawi się, takie jak podkreślenie.</span><span class="sxs-lookup"><span data-stu-id="9659d-108">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="9659d-109">Użyj <xref:System.Windows.TextDecoration.Pen%2A> właściwości w celu określenia wyglądu dekoracji tekstu, takiego jak wypełnienia kryjącego lub kolor gradientu.</span><span class="sxs-lookup"><span data-stu-id="9659d-109">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="9659d-110">Jeśli nie określisz wartości <xref:System.Windows.TextDecoration.Pen%2A> właściwości wartość domyślna dekoracje, to ten sam kolor jak tekst.</span><span class="sxs-lookup"><span data-stu-id="9659d-110">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="9659d-111">Po zdefiniowaniu <xref:System.Windows.TextDecoration> obiektu, dodaj ją do <xref:System.Windows.TextDecorations> kolekcji obiektu odpowiedni tekst.</span><span class="sxs-lookup"><span data-stu-id="9659d-111">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="9659d-112">Dekorację tekstu, który został wstawiony w pędzel gradientów liniowych i Pióro przerywaną, co można znaleźć w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9659d-112">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 ![Dekoracja tekstu z podkreślenie gradientu liniowego](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 <span data-ttu-id="9659d-114"><xref:System.Windows.Documents.Hyperlink> Obiekt jest element zawartości śródwierszowy przepływ, który pozwala na hosta hiperlinki w dowolnej zawartości.</span><span class="sxs-lookup"><span data-stu-id="9659d-114">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="9659d-115">Domyślnie <xref:System.Windows.Documents.Hyperlink> używa <xref:System.Windows.TextDecoration> obiektu, aby wyświetlić podkreślenie.</span><span class="sxs-lookup"><span data-stu-id="9659d-115">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="9659d-116"><xref:System.Windows.TextDecoration> obiekty mogą być intensywnie do utworzenia wystąpienia, wydajność, zwłaszcza, jeśli dostępnych jest wiele <xref:System.Windows.Documents.Hyperlink> obiektów.</span><span class="sxs-lookup"><span data-stu-id="9659d-116"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="9659d-117">Jeśli wprowadzisz zwiększone użycie <xref:System.Windows.Documents.Hyperlink> elementów, warto wziąć pod uwagę przedstawiający podkreślenie, tylko wtedy, gdy wyzwalanie zdarzenia, takie jak <xref:System.Windows.ContentElement.MouseEnter> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9659d-117">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="9659d-118">W poniższym przykładzie jest dynamiczny podkreślenie dla linku "Mój MSN" — pojawia się tylko, gdy <xref:System.Windows.ContentElement.MouseEnter> zdarzenie jest wyzwalane.</span><span class="sxs-lookup"><span data-stu-id="9659d-118">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 ![Wyświetlanie właściwości TextDecorations hiperłącza](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  
   
 <span data-ttu-id="9659d-120">Aby uzyskać więcej informacji, zobacz [określ czy hiperłącze jest podkreślone](how-to-specify-whether-a-hyperlink-is-underlined.md).</span><span class="sxs-lookup"><span data-stu-id="9659d-120">For more information, see [Specify Whether a Hyperlink is Underlined](how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9659d-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="9659d-121">Example</span></span>  
 <span data-ttu-id="9659d-122">W poniższym przykładzie kodu podkreślenia dekoracji tekstu używa wartość domyślna czcionka.</span><span class="sxs-lookup"><span data-stu-id="9659d-122">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="9659d-123">W poniższym przykładzie kodu podkreślenia Dekoracja tekstu jest tworzony z pędzel pełnego koloru pióra.</span><span class="sxs-lookup"><span data-stu-id="9659d-123">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="9659d-124">W poniższym przykładzie kodu dekoracyjną podkreślenie jest tworzony z pędzel gradientów liniowych kreskowane pióra.</span><span class="sxs-lookup"><span data-stu-id="9659d-124">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="9659d-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9659d-125">See also</span></span>
- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="9659d-126">Określanie, czy hiperlink jest podkreślony</span><span class="sxs-lookup"><span data-stu-id="9659d-126">Specify Whether a Hyperlink is Underlined</span></span>](how-to-specify-whether-a-hyperlink-is-underlined.md)
