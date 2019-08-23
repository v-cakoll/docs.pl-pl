---
title: 'Instrukcje: Tworzenie efektu najazdu przy użyciu zdarzeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 3996a3b9bb976dd5f2e5b675de3894bbaba7d9d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960388"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="9eaa5-102">Instrukcje: Tworzenie efektu najazdu przy użyciu zdarzeń</span><span class="sxs-lookup"><span data-stu-id="9eaa5-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="9eaa5-103">Ten przykład pokazuje, jak zmienić kolor elementu, gdy wskaźnik myszy zostanie wprowadzony i opuszcza obszar zajęty przez element.</span><span class="sxs-lookup"><span data-stu-id="9eaa5-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="9eaa5-104">Ten przykład zawiera [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plik i plik związany z kodem.</span><span class="sxs-lookup"><span data-stu-id="9eaa5-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9eaa5-105"><xref:System.Windows.Trigger> W tym przykładzie pokazano, jak używać zdarzeń, ale zalecanym sposobem osiągnięcia tego samego efektu jest użycie w stylu.</span><span class="sxs-lookup"><span data-stu-id="9eaa5-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="9eaa5-106">Aby uzyskać więcej informacji, zobacz [Style i tworzenia szablonów](../controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="9eaa5-106">For more information, see [Styling and Templating](../controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eaa5-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9eaa5-107">Example</span></span>  
 <span data-ttu-id="9eaa5-108">Poniżej [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] można utworzyć interfejs użytkownika, który składa się <xref:System.Windows.Controls.Border> z około <xref:System.Windows.Controls.TextBlock>a i dołącza <xref:System.Windows.Input.Mouse.MouseEnter> obsługę zdarzeń i <xref:System.Windows.UIElement.MouseLeave> do <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="9eaa5-108">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="9eaa5-109">Poniższy kod w tle tworzy <xref:System.Windows.UIElement.MouseEnter> programy i <xref:System.Windows.UIElement.MouseLeave> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9eaa5-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="9eaa5-110">Gdy wskaźnik myszy <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Border> zostanie wprowadzony, tło zostanie zmienione na czerwony.</span><span class="sxs-lookup"><span data-stu-id="9eaa5-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="9eaa5-111">Gdy wskaźnik myszy <xref:System.Windows.Controls.Border> zostanie pozostawiony <xref:System.Windows.Controls.Border>, tło zostanie zmienione z powrotem na biały.</span><span class="sxs-lookup"><span data-stu-id="9eaa5-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
