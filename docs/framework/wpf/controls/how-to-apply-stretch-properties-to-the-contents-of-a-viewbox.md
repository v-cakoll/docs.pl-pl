---
title: 'Instrukcje: Stosowanie właściwości rozciągania do zawartości okna widoku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StretchDirection properties [WPF]
- Stretch properties [WPF]
- controls [WPF], Viewbox
- Viewbox control [WPF]
ms.assetid: b9c22ef4-bce4-4300-9e0c-8260b7db83cc
ms.openlocfilehash: 08358ea07e0c41e3b7cdf52251a3ed4296035e2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019038"
---
# <a name="how-to-apply-stretch-properties-to-the-contents-of-a-viewbox"></a><span data-ttu-id="0a683-102">Instrukcje: Stosowanie właściwości rozciągania do zawartości okna widoku</span><span class="sxs-lookup"><span data-stu-id="0a683-102">How to: Apply Stretch Properties to the Contents of a Viewbox</span></span>
## <a name="example"></a><span data-ttu-id="0a683-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a683-103">Example</span></span>  
 <span data-ttu-id="0a683-104">W tym przykładzie pokazano, jak zmienić wartość <xref:System.Windows.Controls.Viewbox.StretchDirection%2A> i <xref:System.Windows.Controls.Viewbox.Stretch%2A> właściwości <xref:System.Windows.Controls.Viewbox>.</span><span class="sxs-lookup"><span data-stu-id="0a683-104">This example shows how to change the value of the <xref:System.Windows.Controls.Viewbox.StretchDirection%2A> and <xref:System.Windows.Controls.Viewbox.Stretch%2A> properties of a <xref:System.Windows.Controls.Viewbox>.</span></span>  
  
 <span data-ttu-id="0a683-105">W pierwszym przykładzie użyto [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do definiowania <xref:System.Windows.Controls.Viewbox> elementu.</span><span class="sxs-lookup"><span data-stu-id="0a683-105">The first example uses [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.Viewbox> element.</span></span> <span data-ttu-id="0a683-106">Przypisuje <xref:System.Windows.FrameworkElement.MaxWidth%2A> i <xref:System.Windows.FrameworkElement.MaxHeight%2A> 400.</span><span class="sxs-lookup"><span data-stu-id="0a683-106">It assigns a <xref:System.Windows.FrameworkElement.MaxWidth%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> of 400.</span></span> <span data-ttu-id="0a683-107">Przykład zagnieżdża instrukcje <xref:System.Windows.Controls.Image> elemencie <xref:System.Windows.Controls.Viewbox>.</span><span class="sxs-lookup"><span data-stu-id="0a683-107">The example nests an <xref:System.Windows.Controls.Image> element within the <xref:System.Windows.Controls.Viewbox>.</span></span> <span data-ttu-id="0a683-108"><xref:System.Windows.Controls.Button> elementy, które odpowiadają wartości właściwości <xref:System.Windows.Controls.Viewbox.Stretch%2A> i <xref:System.Windows.Controls.StretchDirection> wyliczenia manipulowania rozciągania zachowanie zagnieżdżonego <xref:System.Windows.Controls.Image>.</span><span class="sxs-lookup"><span data-stu-id="0a683-108"><xref:System.Windows.Controls.Button> elements that correspond to the property values for the <xref:System.Windows.Controls.Viewbox.Stretch%2A> and <xref:System.Windows.Controls.StretchDirection> enumerations manipulate the stretching behavior of the nested <xref:System.Windows.Controls.Image>.</span></span>  
  
 [!code-xaml[viewboxStretchLayoutSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="0a683-109">Dojścia do plików poniższym kodem <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia, poprzedni [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykładzie zdefiniowano.</span><span class="sxs-lookup"><span data-stu-id="0a683-109">The following code-behind file handles the <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events that the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example defines.</span></span>  
  
 [!code-csharp[viewboxStretchLayoutSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[viewboxStretchLayoutSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/viewboxStretchLayoutSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0a683-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a683-110">See also</span></span>

- <xref:System.Windows.Controls.Viewbox>
- <xref:System.Windows.Media.Stretch>
- <xref:System.Windows.Controls.StretchDirection>
