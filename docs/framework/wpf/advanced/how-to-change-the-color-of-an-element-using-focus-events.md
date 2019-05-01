---
title: 'Instrukcje: Zmienianie koloru elementu przy użyciu zdarzeń fokusu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
ms.openlocfilehash: 744963cc543110121a777e1d4c3cdcb3cec40d9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776899"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="d58b1-102">Instrukcje: Zmienianie koloru elementu przy użyciu zdarzeń fokusu</span><span class="sxs-lookup"><span data-stu-id="d58b1-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="d58b1-103">W tym przykładzie pokazano, jak zmienić kolor elementu uzyskuje i traci fokus przy użyciu <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d58b1-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="d58b1-104">W tym przykładzie składa się z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oraz plik CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="d58b1-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d58b1-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d58b1-105">Example</span></span>  
 <span data-ttu-id="d58b1-106">Następujące [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] tworzy interfejs użytkownika, który składa się z dwóch <xref:System.Windows.Controls.Button> obiektów i dołącza obsługę zdarzeń dla <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus> zdarzenia <xref:System.Windows.Controls.Button> obiektów.</span><span class="sxs-lookup"><span data-stu-id="d58b1-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="d58b1-107">Poniższy kod tworzy <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus> procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d58b1-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="d58b1-108">Gdy <xref:System.Windows.Controls.Button> za pomocą klawiatury uzyskuje fokus, <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> jest zmieniana na czerwono.</span><span class="sxs-lookup"><span data-stu-id="d58b1-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="d58b1-109">Gdy <xref:System.Windows.Controls.Button> straci fokus klawiatury <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> zmieniony na biały.</span><span class="sxs-lookup"><span data-stu-id="d58b1-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="d58b1-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d58b1-110">See also</span></span>

- [<span data-ttu-id="d58b1-111">Przegląd danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="d58b1-111">Input Overview</span></span>](input-overview.md)
