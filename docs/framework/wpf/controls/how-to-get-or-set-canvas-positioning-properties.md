---
title: 'Instrukcje: Pobieranie lub ustawianie właściwości ustawienia kanwy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
ms.openlocfilehash: 06508e1198736ccb1cbda41641dff4bc634ef82b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910484"
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a><span data-ttu-id="e2d4d-102">Instrukcje: Pobieranie lub ustawianie właściwości ustawienia kanwy</span><span class="sxs-lookup"><span data-stu-id="e2d4d-102">How to: Get or Set Canvas Positioning Properties</span></span>
<span data-ttu-id="e2d4d-103">W tym przykładzie pokazano, jak używać metody pozycjonowania <xref:System.Windows.Controls.Canvas> element, aby umieścić zawartość elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="e2d4d-103">This example shows how to use the positioning methods of the <xref:System.Windows.Controls.Canvas> element to position child content.</span></span> <span data-ttu-id="e2d4d-104">W tym przykładzie użyto zawartość <xref:System.Windows.Controls.ListBoxItem> do reprezentowania pozycjonowanie wartości i konwertuje wartości wystąpienia elementu <xref:System.Double>, którego argument jest wymagany do pozycjonowania.</span><span class="sxs-lookup"><span data-stu-id="e2d4d-104">This example uses content in a <xref:System.Windows.Controls.ListBoxItem> to represent positioning values and converts the values into instances of <xref:System.Double>, which is a required argument for positioning.</span></span> <span data-ttu-id="e2d4d-105">Wartości są konwertowane do ciągów i wyświetlane jako tekst w <xref:System.Windows.Controls.TextBlock> elementu za pomocą <xref:System.Windows.Controls.Canvas.GetLeft%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e2d4d-105">The values are then converted back into strings and displayed as text in a <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.Canvas.GetLeft%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2d4d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2d4d-106">Example</span></span>  
 <span data-ttu-id="e2d4d-107">Poniższy przykład tworzy <xref:System.Windows.Controls.ListBox> element, który ma jedenaście wybieralna <xref:System.Windows.Controls.ListBoxItem> elementów.</span><span class="sxs-lookup"><span data-stu-id="e2d4d-107">The following example creates a <xref:System.Windows.Controls.ListBox> element that has eleven selectable <xref:System.Windows.Controls.ListBoxItem> elements.</span></span> <span data-ttu-id="e2d4d-108"><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> Wyzwalaczy zdarzeń `ChangeLeft` niestandardowe metody, która definiuje blok kolejnych kodu.</span><span class="sxs-lookup"><span data-stu-id="e2d4d-108">The <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event triggers the `ChangeLeft` custom method, which the subsequent code block defines.</span></span>  
  
 <span data-ttu-id="e2d4d-109">Każdy <xref:System.Windows.Controls.ListBoxItem> reprezentuje <xref:System.Double> wartość, która jest jeden z argumentów, <xref:System.Windows.Controls.Canvas.SetLeft%2A> metody <xref:System.Windows.Controls.Canvas> akceptuje.</span><span class="sxs-lookup"><span data-stu-id="e2d4d-109">Each <xref:System.Windows.Controls.ListBoxItem> represents a <xref:System.Double> value, which is one of the arguments that the <xref:System.Windows.Controls.Canvas.SetLeft%2A> method of <xref:System.Windows.Controls.Canvas> accepts.</span></span> <span data-ttu-id="e2d4d-110">Aby można było używać <xref:System.Windows.Controls.ListBoxItem> do reprezentowania instancji <xref:System.Double>, należy najpierw przekonwertować <xref:System.Windows.Controls.ListBoxItem> poprawny typ danych.</span><span class="sxs-lookup"><span data-stu-id="e2d4d-110">In order to use a <xref:System.Windows.Controls.ListBoxItem> to represent an instance of <xref:System.Double>, you must first convert the <xref:System.Windows.Controls.ListBoxItem> to the correct data type.</span></span>  
  
 [!code-xaml[CanvasPositioningProperties#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="e2d4d-111">Gdy użytkownik zmienia <xref:System.Windows.Controls.ListBox> zaznaczenia, wywołuje ono `ChangeLeft` niestandardową metodę.</span><span class="sxs-lookup"><span data-stu-id="e2d4d-111">When a user changes the <xref:System.Windows.Controls.ListBox> selection, it invokes the `ChangeLeft` custom method.</span></span> <span data-ttu-id="e2d4d-112">Ta metoda przekazuje <xref:System.Windows.Controls.ListBoxItem> do <xref:System.Windows.LengthConverter> obiektu, który konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do wystąpienia <xref:System.Double> (należy zauważyć, że ta wartość została przekonwertowana na <xref:System.String> przy użyciu <xref:System.Windows.Controls.Control.ToString%2A> Metoda).</span><span class="sxs-lookup"><span data-stu-id="e2d4d-112">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.LengthConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double> (notice that this value has already been converted to a <xref:System.String> by using the <xref:System.Windows.Controls.Control.ToString%2A> method).</span></span> <span data-ttu-id="e2d4d-113">Ta wartość jest następnie przekazywany do <xref:System.Windows.Controls.Canvas.SetLeft%2A> i <xref:System.Windows.Controls.Canvas.GetLeft%2A> metody <xref:System.Windows.Controls.Canvas> Aby zmienić położenie `text1` obiektu.</span><span class="sxs-lookup"><span data-stu-id="e2d4d-113">This value is then passed back to the <xref:System.Windows.Controls.Canvas.SetLeft%2A> and <xref:System.Windows.Controls.Canvas.GetLeft%2A> methods of <xref:System.Windows.Controls.Canvas> in order to change the position of the `text1` object.</span></span>  
  
 [!code-csharp[CanvasPositioningProperties#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e2d4d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2d4d-114">See also</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.ListBoxItem>
- <xref:System.Windows.LengthConverter>
- [<span data-ttu-id="e2d4d-115">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="e2d4d-115">Panels Overview</span></span>](panels-overview.md)
