---
title: 'Instrukcje: Zastosuj FocusVisualStyle do formantu'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: ae7820dac011425251d087dd4109c3f40bdd308c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493251"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a><span data-ttu-id="2267f-102">Instrukcje: Zastosuj FocusVisualStyle do formantu</span><span class="sxs-lookup"><span data-stu-id="2267f-102">How to: Apply a FocusVisualStyle to a Control</span></span>
<span data-ttu-id="2267f-103">W tym przykładzie pokazano, jak utworzyć styl wizualny fokusu w zasobach i zastosować styl do kontrolki, za pomocą <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2267f-103">This example shows you how to create a focus visual style in resources and apply the style to a control, using the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2267f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2267f-104">Example</span></span>  
 <span data-ttu-id="2267f-105">W poniższym przykładzie zdefiniowano styl, który tworzy dodatkową kontrolę składania, które tylko wtedy, gdy kontrola jest klawiatury w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2267f-105">The following example defines a style that creates additional control compositing that only applies when that control is keyboard focused in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="2267f-106">Jest to realizowane przez zdefiniowanie styl z <xref:System.Windows.Controls.ControlTemplate>, a następnie odwołuje się do tego stylu jako zasób podczas ustawiania <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2267f-106">This is accomplished by defining a style with a <xref:System.Windows.Controls.ControlTemplate>, then referencing that style as a resource when setting the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
 <span data-ttu-id="2267f-107">Prostokąt zewnętrznych przypominającą obramowanie jest umieszczany poza prostokątny obszar.</span><span class="sxs-lookup"><span data-stu-id="2267f-107">An external rectangle resembling a border is placed outside of the rectangular area.</span></span> <span data-ttu-id="2267f-108">O ile nie zmodyfikowano inaczej, korzysta z rozmiaru stylu <xref:System.Windows.FrameworkElement.ActualHeight%2A> i <xref:System.Windows.FrameworkElement.ActualWidth%2A> prostokątny kontrolki, w której stosowana jest styl wizualny fokusu.</span><span class="sxs-lookup"><span data-stu-id="2267f-108">Unless otherwise modified, the sizing of the style uses the <xref:System.Windows.FrameworkElement.ActualHeight%2A> and <xref:System.Windows.FrameworkElement.ActualWidth%2A> of the rectangular control where the focus visual style is applied.</span></span> <span data-ttu-id="2267f-109">W tym przykładzie wartości ujemnych dla <xref:System.Windows.FrameworkElement.Margin%2A> Aby obramowanie pojawiają się nieco poza kontrolą wąsko zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="2267f-109">This example sets negative values for the <xref:System.Windows.FrameworkElement.Margin%2A> to make the border appear slightly outside the focused control.</span></span>  
  
 [!code-xaml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <span data-ttu-id="2267f-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> jest dodatku na dowolny styl szablonu kontrolki, dostarczanego z style jawne lub style motyw; podstawowy styl kontrolki nadal można utworzyć za pomocą <xref:System.Windows.Controls.ControlTemplate> i ustawienie stylu <xref:System.Windows.FrameworkElement.Style%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2267f-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> is additive to any control template style that comes either from an explicit style or a theme style; the primary style for a control can still be created by using a <xref:System.Windows.Controls.ControlTemplate> and setting that style to the <xref:System.Windows.FrameworkElement.Style%2A> property.</span></span>  
  
 <span data-ttu-id="2267f-111">Fokus stylów wizualnych powinien stosowane konsekwentnie w motywu lub interfejsu użytkownika, a nie przy użyciu innej dla każdego elementu focusable.</span><span class="sxs-lookup"><span data-stu-id="2267f-111">Focus visual styles should be used consistently across a theme or a UI, rather than using a different one for each focusable element.</span></span> <span data-ttu-id="2267f-112">Aby uzyskać więcej informacji, zobacz [style dla fokusu w formantach i FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).</span><span class="sxs-lookup"><span data-stu-id="2267f-112">For details, see [Styling for Focus in Controls, and FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2267f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2267f-113">See also</span></span>
- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [<span data-ttu-id="2267f-114">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="2267f-114">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="2267f-115">Style dla fokusu w kontrolkach i styl FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="2267f-115">Styling for Focus in Controls, and FocusVisualStyle</span></span>](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)
