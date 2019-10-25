---
title: Jak utworzyć niestandardowy element panelu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 31edc75114c5dad613e5b65e7d8b051e2c3713af
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799146"
---
# <a name="how-to-create-a-custom-panel-element"></a><span data-ttu-id="15f88-102">Jak utworzyć niestandardowy element panelu</span><span class="sxs-lookup"><span data-stu-id="15f88-102">How to: Create a Custom Panel Element</span></span>
## <a name="example"></a><span data-ttu-id="15f88-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="15f88-103">Example</span></span>  
 <span data-ttu-id="15f88-104">Ten przykład pokazuje, jak zastąpić domyślne zachowanie układu elementu <xref:System.Windows.Controls.Panel> i utworzyć niestandardowe elementy układu, które pochodzą z <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="15f88-104">This example shows how to override the default layout behavior of the <xref:System.Windows.Controls.Panel> element and create custom layout elements that are derived from <xref:System.Windows.Controls.Panel>.</span></span>  
  
 <span data-ttu-id="15f88-105">W przykładzie zdefiniowano prosty niestandardowy element <xref:System.Windows.Controls.Panel> o nazwie `PlotPanel`, który umieszcza elementy podrzędne w zależności od dwóch sztywnie zakodowanych współrzędnych x i y.</span><span class="sxs-lookup"><span data-stu-id="15f88-105">The example defines a simple custom <xref:System.Windows.Controls.Panel> element called `PlotPanel`, which positions child elements according to two hard-coded x- and y-coordinates.</span></span> <span data-ttu-id="15f88-106">W tym przykładzie `x` i `y` są ustawione na `50`; w związku z tym wszystkie elementy podrzędne są umieszczane w tej lokalizacji na osiach x i y.</span><span class="sxs-lookup"><span data-stu-id="15f88-106">In this example, `x` and `y` are both set to `50`; therefore, all child elements are positioned at that location on the x and y axes.</span></span>  
  
 <span data-ttu-id="15f88-107">W celu zaimplementowania niestandardowych zachowań <xref:System.Windows.Controls.Panel> w przykładzie stosowane są metody <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>.</span><span class="sxs-lookup"><span data-stu-id="15f88-107">To implement custom <xref:System.Windows.Controls.Panel> behaviors, the example uses the <xref:System.Windows.FrameworkElement.MeasureOverride%2A> and <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> methods.</span></span> <span data-ttu-id="15f88-108">Każda metoda zwraca <xref:System.Windows.Size> dane, które są niezbędne do pozycjonowania i renderowania elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="15f88-108">Each method returns the <xref:System.Windows.Size> data that is necessary to position and render child elements.</span></span>  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="15f88-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15f88-109">See also</span></span>

- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="15f88-110">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="15f88-110">Panels Overview</span></span>](panels-overview.md)
