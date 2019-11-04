---
title: Jak utworzyć efekt najazdu przy użyciu zdarzenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: ccdc8aeb26b538814b2f9020e1e3a5b311fa5a99
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460160"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="c8717-102">Jak utworzyć efekt najazdu przy użyciu zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c8717-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="c8717-103">Ten przykład pokazuje, jak zmienić kolor elementu, gdy wskaźnik myszy zostanie wprowadzony i opuszcza obszar zajęty przez element.</span><span class="sxs-lookup"><span data-stu-id="c8717-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="c8717-104">Ten przykład składa się z pliku [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i pliku związanego z kodem.</span><span class="sxs-lookup"><span data-stu-id="c8717-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8717-105">W tym przykładzie pokazano, jak używać zdarzeń, ale zalecanym sposobem osiągnięcia tego samego efektu jest użycie <xref:System.Windows.Trigger> w stylu.</span><span class="sxs-lookup"><span data-stu-id="c8717-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="c8717-106">Aby uzyskać więcej informacji, zobacz [Style i tworzenia szablonów](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c8717-106">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8717-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8717-107">Example</span></span>  
 <span data-ttu-id="c8717-108">Poniższy kod XAML tworzy interfejs użytkownika, który składa się z <xref:System.Windows.Controls.Border> wokół <xref:System.Windows.Controls.TextBlock> i dołącza obsługę zdarzeń <xref:System.Windows.Input.Mouse.MouseEnter> i <xref:System.Windows.UIElement.MouseLeave> do <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="c8717-108">The following XAML creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="c8717-109">Poniższy kod w tle tworzy procedury obsługi zdarzeń <xref:System.Windows.UIElement.MouseEnter> i <xref:System.Windows.UIElement.MouseLeave>.</span><span class="sxs-lookup"><span data-stu-id="c8717-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="c8717-110">Gdy wskaźnik myszy zostanie przesunięty do <xref:System.Windows.Controls.Border>, tło <xref:System.Windows.Controls.Border> zostanie zmienione na czerwony.</span><span class="sxs-lookup"><span data-stu-id="c8717-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="c8717-111">Gdy wskaźnik myszy opuszcza <xref:System.Windows.Controls.Border>, tło <xref:System.Windows.Controls.Border> zostanie zmienione z powrotem na biały.</span><span class="sxs-lookup"><span data-stu-id="c8717-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
