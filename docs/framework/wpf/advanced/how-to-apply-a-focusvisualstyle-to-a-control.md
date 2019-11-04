---
title: Jak zastosować FocusVisualStyle do formantu
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: b44330ee7554f953389556bd62ff49db120b5db9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459805"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a><span data-ttu-id="848f5-102">Jak zastosować FocusVisualStyle do formantu</span><span class="sxs-lookup"><span data-stu-id="848f5-102">How to: Apply a FocusVisualStyle to a Control</span></span>
<span data-ttu-id="848f5-103">Ten przykład pokazuje, jak utworzyć styl wizualizacji fokusu w zasobach i zastosować styl do kontrolki przy użyciu właściwości <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="848f5-103">This example shows you how to create a focus visual style in resources and apply the style to a control, using the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="848f5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="848f5-104">Example</span></span>  
 <span data-ttu-id="848f5-105">W poniższym przykładzie zdefiniowano styl, który tworzy dodatkowe elementy sterujące, które mają zastosowanie tylko wtedy, gdy ta kontrolka jest ukierunkowana na [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="848f5-105">The following example defines a style that creates additional control compositing that only applies when that control is keyboard focused in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="848f5-106">Jest to realizowane przez zdefiniowanie stylu z <xref:System.Windows.Controls.ControlTemplate>, a następnie odwołanie do tego stylu jako zasobu podczas ustawiania właściwości <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="848f5-106">This is accomplished by defining a style with a <xref:System.Windows.Controls.ControlTemplate>, then referencing that style as a resource when setting the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
 <span data-ttu-id="848f5-107">Zewnętrzny prostokąt przypominający obramowanie znajduje się poza prostokątnym obszarem.</span><span class="sxs-lookup"><span data-stu-id="848f5-107">An external rectangle resembling a border is placed outside of the rectangular area.</span></span> <span data-ttu-id="848f5-108">O ile nie zmodyfikowano inaczej, rozmiar stylu używa <xref:System.Windows.FrameworkElement.ActualHeight%2A> i <xref:System.Windows.FrameworkElement.ActualWidth%2A> prostokątnego formantu, w którym jest stosowany styl wizualizacji fokusu.</span><span class="sxs-lookup"><span data-stu-id="848f5-108">Unless otherwise modified, the sizing of the style uses the <xref:System.Windows.FrameworkElement.ActualHeight%2A> and <xref:System.Windows.FrameworkElement.ActualWidth%2A> of the rectangular control where the focus visual style is applied.</span></span> <span data-ttu-id="848f5-109">Ten przykład ustawia wartości ujemne dla <xref:System.Windows.FrameworkElement.Margin%2A>, aby obramowanie pojawiło się nieco poza kontrolką ukierunkowaną.</span><span class="sxs-lookup"><span data-stu-id="848f5-109">This example sets negative values for the <xref:System.Windows.FrameworkElement.Margin%2A> to make the border appear slightly outside the focused control.</span></span>  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <span data-ttu-id="848f5-110"><xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> jest dodatkiem do dowolnego stylu szablonu formantu, który pochodzi ze stylu jawnego lub stylu motywu; styl podstawowy formantu można nadal utworzyć przy użyciu <xref:System.Windows.Controls.ControlTemplate> i ustawić ten styl na Właściwość <xref:System.Windows.FrameworkElement.Style%2A>.</span><span class="sxs-lookup"><span data-stu-id="848f5-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> is additive to any control template style that comes either from an explicit style or a theme style; the primary style for a control can still be created by using a <xref:System.Windows.Controls.ControlTemplate> and setting that style to the <xref:System.Windows.FrameworkElement.Style%2A> property.</span></span>  
  
 <span data-ttu-id="848f5-111">Style wizualizacji fokusu powinny być stosowane spójnie między motywem lub interfejsem użytkownika, a nie przy użyciu różnych elementów dla każdego elementu możliwego do skoncentrowania.</span><span class="sxs-lookup"><span data-stu-id="848f5-111">Focus visual styles should be used consistently across a theme or a UI, rather than using a different one for each focusable element.</span></span> <span data-ttu-id="848f5-112">Aby uzyskać szczegółowe informacje, zobacz [Style do fokusu w kontrolkach i FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).</span><span class="sxs-lookup"><span data-stu-id="848f5-112">For details, see [Styling for Focus in Controls, and FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="848f5-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="848f5-113">See also</span></span>

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [<span data-ttu-id="848f5-114">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="848f5-114">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="848f5-115">Style dla fokusu w kontrolkach i styl FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="848f5-115">Styling for Focus in Controls, and FocusVisualStyle</span></span>](styling-for-focus-in-controls-and-focusvisualstyle.md)
