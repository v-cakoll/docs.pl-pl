---
title: Jak ustawić właściwości szerokości elementu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: 682929625612114d042e4619d8388617988b3c48
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124276"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a><span data-ttu-id="9285f-102">Jak ustawić właściwości szerokości elementu</span><span class="sxs-lookup"><span data-stu-id="9285f-102">How to: Set the Width Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="9285f-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="9285f-103">Example</span></span>  
 <span data-ttu-id="9285f-104">Ten przykład wizualnie pokazuje różnice w zachowaniu renderowania między właściwościami powiązanymi z szerokością w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9285f-104">This example visually shows the differences in rendering behavior among the four width-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="9285f-105">Klasa <xref:System.Windows.FrameworkElement> uwidacznia cztery właściwości, które opisują charakterystykę szerokości elementu.</span><span class="sxs-lookup"><span data-stu-id="9285f-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the width characteristics of an element.</span></span> <span data-ttu-id="9285f-106">Te cztery właściwości mogą powodować konflikt i gdy tak się stanie, wartość, która ma pierwszeństwo, jest określana w następujący sposób: wartość <xref:System.Windows.FrameworkElement.MinWidth%2A> ma pierwszeństwo przed wartością <xref:System.Windows.FrameworkElement.MaxWidth%2A>, która z kolei ma pierwszeństwo przed wartością <xref:System.Windows.FrameworkElement.Width%2A>.</span><span class="sxs-lookup"><span data-stu-id="9285f-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinWidth%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxWidth%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Width%2A> value.</span></span> <span data-ttu-id="9285f-107">Czwarta właściwość, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, jest tylko do odczytu i raportuje rzeczywistą szerokość określoną przez interakcje z procesem układu.</span><span class="sxs-lookup"><span data-stu-id="9285f-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, is read-only, and reports the actual width as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="9285f-108">Poniższe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykłady rysują element <xref:System.Windows.Shapes.Rectangle> (`rect1`) jako element podrzędny <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="9285f-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="9285f-109">Właściwości szerokości <xref:System.Windows.Shapes.Rectangle> można zmienić przy użyciu serii <xref:System.Windows.Controls.ListBox> elementów, które reprezentują wartości właściwości <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>i <xref:System.Windows.FrameworkElement.Width%2A>.</span><span class="sxs-lookup"><span data-stu-id="9285f-109">You can change the width properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, and <xref:System.Windows.FrameworkElement.Width%2A>.</span></span> <span data-ttu-id="9285f-110">Dzięki temu pierwszeństwo każdej właściwości jest wyświetlane wizualnie.</span><span class="sxs-lookup"><span data-stu-id="9285f-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="9285f-111">Poniższe przykłady kodu obsługują zdarzenia zgłoszone przez zdarzenie <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>.</span><span class="sxs-lookup"><span data-stu-id="9285f-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="9285f-112">Każda metoda niestandardowa pobiera dane wejściowe z <xref:System.Windows.Controls.ListBox>, analizuje wartość jako <xref:System.Double>i stosuje wartość do określonej właściwości powiązanej z szerokością.</span><span class="sxs-lookup"><span data-stu-id="9285f-112">Each custom method takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified width-related property.</span></span> <span data-ttu-id="9285f-113">Wartości szerokości są również konwertowane na ciąg i zapisywane na różne elementy <xref:System.Windows.Controls.TextBlock> (definicja tych elementów nie jest pokazana w wybranym kodzie XAML).</span><span class="sxs-lookup"><span data-stu-id="9285f-113">The width values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="9285f-114">Aby zapoznać się z kompletnym przykładem, zobacz [przykłady porównania właściwości Width](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties).</span><span class="sxs-lookup"><span data-stu-id="9285f-114">For the complete sample, see [Width Properties Comparison Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9285f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9285f-115">See also</span></span>

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [<span data-ttu-id="9285f-116">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="9285f-116">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="9285f-117">Ustawianie właściwości wysokości elementu</span><span class="sxs-lookup"><span data-stu-id="9285f-117">Set the Height Properties of an Element</span></span>](how-to-set-the-height-properties-of-an-element.md)
- [<span data-ttu-id="9285f-118">Przykład porównania właściwości Width</span><span class="sxs-lookup"><span data-stu-id="9285f-118">Width Properties Comparison Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties)
