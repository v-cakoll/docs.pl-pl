---
title: Jak zmienić kolor elementu przy użyciu elementów Fokus
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
ms.openlocfilehash: 5c59dc5f2f8f26fac69933f9ef641a3a51306619
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004836"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="90bad-102">Jak zmienić kolor elementu przy użyciu elementów Fokus</span><span class="sxs-lookup"><span data-stu-id="90bad-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="90bad-103">Ten przykład pokazuje, jak zmienić kolor elementu, gdy zyskuje i traci fokus przy użyciu zdarzeń <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="90bad-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="90bad-104">Ten przykład składa się z pliku [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i pliku związanego z kodem.</span><span class="sxs-lookup"><span data-stu-id="90bad-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90bad-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="90bad-105">Example</span></span>  
 <span data-ttu-id="90bad-106">Poniższy kod XAML tworzy interfejs użytkownika, który składa się z dwóch <xref:System.Windows.Controls.Button> obiektów i dołącza obsługę zdarzeń dla zdarzeń <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus> do obiektów <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="90bad-106">The following XAML creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="90bad-107">Poniższy kod w tle tworzy procedury obsługi zdarzeń <xref:System.Windows.UIElement.GotFocus> i <xref:System.Windows.UIElement.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="90bad-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="90bad-108">Gdy <xref:System.Windows.Controls.Button> ma fokus klawiatury, <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> zostanie zmieniony na czerwony.</span><span class="sxs-lookup"><span data-stu-id="90bad-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="90bad-109">Gdy <xref:System.Windows.Controls.Button> utraci fokus klawiatury, <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> zostanie zmieniony z powrotem na biały.</span><span class="sxs-lookup"><span data-stu-id="90bad-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="90bad-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90bad-110">See also</span></span>

- [<span data-ttu-id="90bad-111">Przegląd danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="90bad-111">Input Overview</span></span>](input-overview.md)
