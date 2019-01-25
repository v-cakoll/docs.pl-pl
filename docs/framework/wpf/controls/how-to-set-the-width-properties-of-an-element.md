---
title: 'Instrukcje: Ustaw właściwości szerokości elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: 739b041d8ca89abb9bd1934abb997d1154f08c95
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54673988"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a><span data-ttu-id="5d0f2-102">Instrukcje: Ustaw właściwości szerokości elementu</span><span class="sxs-lookup"><span data-stu-id="5d0f2-102">How to: Set the Width Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="5d0f2-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d0f2-103">Example</span></span>  
 <span data-ttu-id="5d0f2-104">W tym przykładzie przedstawiono wizualnie różnice między renderowania zachowanie między cztery właściwości związane z szerokość [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5d0f2-104">This example visually shows the differences in rendering behavior among the four width-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="5d0f2-105"><xref:System.Windows.FrameworkElement> Klasa udostępnia cztery właściwości, które opisują właściwości szerokości elementu.</span><span class="sxs-lookup"><span data-stu-id="5d0f2-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the width characteristics of an element.</span></span> <span data-ttu-id="5d0f2-106">Te cztery właściwości mogą powodować konflikt, a gdy tak robią, wartość, która ma pierwszeństwo przed jest określany w następujący sposób: <xref:System.Windows.FrameworkElement.MinWidth%2A> wartość ma pierwszeństwo przed <xref:System.Windows.FrameworkElement.MaxWidth%2A> wartość, która z kolei ma pierwszeństwo przed <xref:System.Windows.FrameworkElement.Width%2A> wartość.</span><span class="sxs-lookup"><span data-stu-id="5d0f2-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinWidth%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxWidth%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Width%2A> value.</span></span> <span data-ttu-id="5d0f2-107">Czwarty właściwość <xref:System.Windows.FrameworkElement.ActualWidth%2A>, jest tylko do odczytu i zgłasza rzeczywista szerokość zgodnie z ustaleniami interakcji z procesem układu.</span><span class="sxs-lookup"><span data-stu-id="5d0f2-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, is read-only, and reports the actual width as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="5d0f2-108">Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Rysowanie przykłady <xref:System.Windows.Shapes.Rectangle> — element (`rect1`) jako element podrzędny elementu <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="5d0f2-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="5d0f2-109">Można zmienić właściwości szerokości <xref:System.Windows.Shapes.Rectangle> przy użyciu szeregu <xref:System.Windows.Controls.ListBox> elementy, które reprezentują wartości właściwości <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, i <xref:System.Windows.FrameworkElement.Width%2A>.</span><span class="sxs-lookup"><span data-stu-id="5d0f2-109">You can change the width properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, and <xref:System.Windows.FrameworkElement.Width%2A>.</span></span> <span data-ttu-id="5d0f2-110">W ten sposób priorytet każdej właściwości jest wyświetlana wizualnie.</span><span class="sxs-lookup"><span data-stu-id="5d0f2-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="5d0f2-111">Poniższe przykłady związane z kodem obsługi zdarzeń, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> wywołuje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5d0f2-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="5d0f2-112">Każda metoda niestandardowego pobiera dane wejściowe z <xref:System.Windows.Controls.ListBox>, analizuje wartość jako <xref:System.Double>i dotyczy wartość określonej właściwości związane z szerokości.</span><span class="sxs-lookup"><span data-stu-id="5d0f2-112">Each custom method takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified width-related property.</span></span> <span data-ttu-id="5d0f2-113">Wartości szerokości również jest konwertowana na ciąg i zapisywane w różnych <xref:System.Windows.Controls.TextBlock> elementów (definicja tych elementów nie znajduje się w wybranej XAML).</span><span class="sxs-lookup"><span data-stu-id="5d0f2-113">The width values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="5d0f2-114">Aby uzyskać pełny przykład, zobacz [przykład porównania właściwości szerokości](https://go.microsoft.com/fwlink/?LinkID=160050).</span><span class="sxs-lookup"><span data-stu-id="5d0f2-114">For the complete sample, see [Width Properties Comparison Sample](https://go.microsoft.com/fwlink/?LinkID=160050).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d0f2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d0f2-115">See also</span></span>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [<span data-ttu-id="5d0f2-116">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="5d0f2-116">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
- [<span data-ttu-id="5d0f2-117">Ustawianie właściwości wysokości elementu</span><span class="sxs-lookup"><span data-stu-id="5d0f2-117">Set the Height Properties of an Element</span></span>](../../../../docs/framework/wpf/controls/how-to-set-the-height-properties-of-an-element.md)
- [<span data-ttu-id="5d0f2-118">Przykładowe porównanie właściwości szerokości</span><span class="sxs-lookup"><span data-stu-id="5d0f2-118">Width Properties Comparison Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160050)
