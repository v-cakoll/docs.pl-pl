---
title: "Jak utworzyć niestandardowy element panelu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eacc5435e259c20c25b64d6e82c33d07338602a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-panel-element"></a><span data-ttu-id="e2423-102">Jak utworzyć niestandardowy element panelu</span><span class="sxs-lookup"><span data-stu-id="e2423-102">How to: Create a Custom Panel Element</span></span>
## <a name="example"></a><span data-ttu-id="e2423-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2423-103">Example</span></span>  
 <span data-ttu-id="e2423-104">W tym przykładzie pokazano, jak zastąpić domyślne zachowanie układu <xref:System.Windows.Controls.Panel> element i utworzyć niestandardowy układ elementów, które są pochodnymi <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="e2423-104">This example shows how to override the default layout behavior of the <xref:System.Windows.Controls.Panel> element and create custom layout elements that are derived from <xref:System.Windows.Controls.Panel>.</span></span>  
  
 <span data-ttu-id="e2423-105">W przykładzie zdefiniowano niestandardowe proste <xref:System.Windows.Controls.Panel> element o nazwie `PlotPanel`, który określa położenie elementów podrzędnych zgodnie z dwóch ustalony współrzędne x i y-.</span><span class="sxs-lookup"><span data-stu-id="e2423-105">The example defines a simple custom <xref:System.Windows.Controls.Panel> element called `PlotPanel`, which positions child elements according to two hard-coded x- and y-coordinates.</span></span> <span data-ttu-id="e2423-106">W tym przykładzie `x` i `y` są ustawione na `50`; w związku z tym wszystkie elementy podrzędne znajdują się w tej lokalizacji na x i y osi.</span><span class="sxs-lookup"><span data-stu-id="e2423-106">In this example, `x` and `y` are both set to `50`; therefore, all child elements are positioned at that location on the x and y axes.</span></span>  
  
 <span data-ttu-id="e2423-107">Aby wdrożyć niestandardowy <xref:System.Windows.Controls.Panel> zachowania, w przykładzie użyto <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e2423-107">To implement custom <xref:System.Windows.Controls.Panel> behaviors, the example uses the <xref:System.Windows.FrameworkElement.MeasureOverride%2A> and <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> methods.</span></span> <span data-ttu-id="e2423-108">Każda metoda zwraca <xref:System.Windows.Size> danych, które są niezbędne do umieszczenia i renderowania elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="e2423-108">Each method returns the <xref:System.Windows.Size> data that is necessary to position and render child elements.</span></span>  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e2423-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2423-109">See Also</span></span>  
 <xref:System.Windows.Controls.Panel>  
 [<span data-ttu-id="e2423-110">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="e2423-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="e2423-111">Tworzenie niestandardowych przykładu panelu zawijania zawartości</span><span class="sxs-lookup"><span data-stu-id="e2423-111">Create a Custom Content-Wrapping Panel Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159979)
