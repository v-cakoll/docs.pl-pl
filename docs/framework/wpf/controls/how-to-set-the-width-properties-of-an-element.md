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
ms.openlocfilehash: 72617744a8b2565857d19a1c6ef41bf4211c89ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-width-properties-of-an-element"></a><span data-ttu-id="0b186-102">Jak ustawić właściwości szerokości elementu</span><span class="sxs-lookup"><span data-stu-id="0b186-102">How to: Set the Width Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="0b186-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b186-103">Example</span></span>  
 <span data-ttu-id="0b186-104">W tym przykładzie przedstawiono wizualnie różnice między renderowania zachowanie spośród czterech właściwości związanych z szerokość [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b186-104">This example visually shows the differences in rendering behavior among the four width-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="0b186-105"><xref:System.Windows.FrameworkElement> Klasa udostępnia cztery właściwości, które opisują cechy szerokość elementu.</span><span class="sxs-lookup"><span data-stu-id="0b186-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the width characteristics of an element.</span></span> <span data-ttu-id="0b186-106">Te właściwości cztery mogą powodować konflikt, a gdy tak robią, wartość, która ma pierwszeństwo przed jest określane w następujący sposób: <xref:System.Windows.FrameworkElement.MinWidth%2A> wartość ma pierwszeństwo przed <xref:System.Windows.FrameworkElement.MaxWidth%2A> wartość, która z kolei ma pierwszeństwo przed <xref:System.Windows.FrameworkElement.Width%2A> wartość.</span><span class="sxs-lookup"><span data-stu-id="0b186-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinWidth%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxWidth%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Width%2A> value.</span></span> <span data-ttu-id="0b186-107">Właściwość czwarty <xref:System.Windows.FrameworkElement.ActualWidth%2A>, jest tylko do odczytu i raporty rzeczywista szerokość ustalany na podstawie interakcji z procesem układu.</span><span class="sxs-lookup"><span data-stu-id="0b186-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, is read-only, and reports the actual width as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="0b186-108">Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykłady rysowania <xref:System.Windows.Shapes.Rectangle> elementu (`rect1`) jako element podrzędny <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="0b186-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="0b186-109">Można zmienić właściwości szerokość <xref:System.Windows.Shapes.Rectangle> przy użyciu serii <xref:System.Windows.Controls.ListBox> elementy, które reprezentują wartości właściwości <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, i <xref:System.Windows.FrameworkElement.Width%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b186-109">You can change the width properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, and <xref:System.Windows.FrameworkElement.Width%2A>.</span></span> <span data-ttu-id="0b186-110">W ten sposób pierwszeństwo każdej właściwości wizualnie jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="0b186-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="0b186-111">W poniższych przykładach kodu powiązanego obsługiwać zdarzenia który <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> zgłasza zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0b186-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="0b186-112">Każda metoda niestandardowych pobiera dane wejściowe z <xref:System.Windows.Controls.ListBox>, analizuje wartość jako <xref:System.Double>i dotyczy wartość określonej właściwości związanych z szerokości.</span><span class="sxs-lookup"><span data-stu-id="0b186-112">Each custom method takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified width-related property.</span></span> <span data-ttu-id="0b186-113">Wartości szerokości są również konwertowana na ciąg i zapisywane w różnych <xref:System.Windows.Controls.TextBlock> elementów (definicja tych elementów nie znajduje się w wybranej XAML).</span><span class="sxs-lookup"><span data-stu-id="0b186-113">The width values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="0b186-114">Pełny przykład, zobacz [przykład porównania właściwości szerokość](http://go.microsoft.com/fwlink/?LinkID=160050).</span><span class="sxs-lookup"><span data-stu-id="0b186-114">For the complete sample, see [Width Properties Comparison Sample](http://go.microsoft.com/fwlink/?LinkID=160050).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b186-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b186-115">See Also</span></span>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.FrameworkElement.ActualWidth%2A>  
 <xref:System.Windows.FrameworkElement.MaxWidth%2A>  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 [<span data-ttu-id="0b186-116">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="0b186-116">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="0b186-117">Ustawianie właściwości wysokości elementu</span><span class="sxs-lookup"><span data-stu-id="0b186-117">Set the Height Properties of an Element</span></span>](../../../../docs/framework/wpf/controls/how-to-set-the-height-properties-of-an-element.md)  
 [<span data-ttu-id="0b186-118">Przykład porównania właściwości szerokości</span><span class="sxs-lookup"><span data-stu-id="0b186-118">Width Properties Comparison Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160050)
