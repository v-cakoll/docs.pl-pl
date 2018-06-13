---
title: Jak dostosować znaczniki na suwaku
ms.date: 03/30/2017
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
ms.openlocfilehash: 667ec5d5504e18449800598f0b14548b7463bdf3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550881"
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a><span data-ttu-id="1ca2e-102">Jak dostosować znaczniki na suwaku</span><span class="sxs-lookup"><span data-stu-id="1ca2e-102">How to: Customize the Ticks on a Slider</span></span>
<span data-ttu-id="1ca2e-103">W tym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Controls.Slider> formantu, który ma znaczniki osi.</span><span class="sxs-lookup"><span data-stu-id="1ca2e-103">This example shows how to create a <xref:System.Windows.Controls.Slider> control that has tick marks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ca2e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ca2e-104">Example</span></span>  
 <span data-ttu-id="1ca2e-105"><xref:System.Windows.Controls.Primitives.TickBar> Wyświetla po ustawieniu <xref:System.Windows.Controls.Slider.TickPlacement%2A> właściwości na wartość inną niż <xref:System.Windows.Controls.Primitives.TickPlacement.None>, która jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="1ca2e-105">The <xref:System.Windows.Controls.Primitives.TickBar> displays when you set the <xref:System.Windows.Controls.Slider.TickPlacement%2A> property to a value other than <xref:System.Windows.Controls.Primitives.TickPlacement.None>, which is the default value.</span></span>  
  
 <span data-ttu-id="1ca2e-106">Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Controls.Slider> z <xref:System.Windows.Controls.Primitives.TickBar> czy wyświetla znaczniki.</span><span class="sxs-lookup"><span data-stu-id="1ca2e-106">The following example shows how to create a <xref:System.Windows.Controls.Slider> with a <xref:System.Windows.Controls.Primitives.TickBar> that displays tick marks.</span></span> <span data-ttu-id="1ca2e-107"><xref:System.Windows.Controls.Slider.TickPlacement%2A> i <xref:System.Windows.Controls.Slider.TickFrequency%2A> właściwości definiowanie lokalizacji znaczników oraz interwału między nimi.</span><span class="sxs-lookup"><span data-stu-id="1ca2e-107">The <xref:System.Windows.Controls.Slider.TickPlacement%2A> and <xref:System.Windows.Controls.Slider.TickFrequency%2A> properties define the location of the tick marks and the interval between them.</span></span> <span data-ttu-id="1ca2e-108">Po przeniesieniu <xref:System.Windows.Controls.Primitives.Thumb>, etykietki narzędzi zawierają wartość <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="1ca2e-108">When you move the <xref:System.Windows.Controls.Primitives.Thumb>, tooltips display the value of the <xref:System.Windows.Controls.Slider>.</span></span> <span data-ttu-id="1ca2e-109"><xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> Właściwość określa, gdzie występuje etykietki narzędzi.</span><span class="sxs-lookup"><span data-stu-id="1ca2e-109">The <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> property defines where the tooltips occur.</span></span> <span data-ttu-id="1ca2e-110"><xref:System.Windows.Controls.Primitives.Thumb> Przeniesień odpowiadają lokalizacji znaczników, ponieważ <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> ma ustawioną wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="1ca2e-110">The <xref:System.Windows.Controls.Primitives.Thumb> movements correspond to the location of the tick marks because <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> is set to `true`.</span></span>  
  
 <span data-ttu-id="1ca2e-111">Poniższy przykład przedstawia użycie <xref:System.Windows.Controls.Slider.Ticks%2A> właściwość, aby utworzyć znaczniki wzdłuż osi <xref:System.Windows.Controls.Slider> w nieregularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="1ca2e-111">The following example shows how to use the <xref:System.Windows.Controls.Slider.Ticks%2A> property to create tick marks along the <xref:System.Windows.Controls.Slider> at irregular intervals.</span></span>  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="1ca2e-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ca2e-112">See Also</span></span>  
 <xref:System.Windows.Controls.Slider>  
 <xref:System.Windows.Controls.Primitives.TickBar>  
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>  
 [<span data-ttu-id="1ca2e-113">Suwak — tematy porad</span><span class="sxs-lookup"><span data-stu-id="1ca2e-113">Slider How-to Topics</span></span>](http://msdn.microsoft.com/library/534be86c-afb2-425d-8186-631278a9925e)
