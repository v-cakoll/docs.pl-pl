---
title: 'Instrukcje: Dostosuj znaczniki na suwaku'
ms.date: 03/30/2017
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
ms.openlocfilehash: b6ade07b0b4c04578d2523d6d8ba992b8b2d31f7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696675"
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a><span data-ttu-id="ad097-102">Instrukcje: Dostosuj znaczniki na suwaku</span><span class="sxs-lookup"><span data-stu-id="ad097-102">How to: Customize the Ticks on a Slider</span></span>
<span data-ttu-id="ad097-103">W tym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Controls.Slider> formant, który zawiera znaczniki.</span><span class="sxs-lookup"><span data-stu-id="ad097-103">This example shows how to create a <xref:System.Windows.Controls.Slider> control that has tick marks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad097-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad097-104">Example</span></span>  
 <span data-ttu-id="ad097-105"><xref:System.Windows.Controls.Primitives.TickBar> Wyświetlana po ustawieniu <xref:System.Windows.Controls.Slider.TickPlacement%2A> właściwości na wartość inną niż <xref:System.Windows.Controls.Primitives.TickPlacement.None>, która jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="ad097-105">The <xref:System.Windows.Controls.Primitives.TickBar> displays when you set the <xref:System.Windows.Controls.Slider.TickPlacement%2A> property to a value other than <xref:System.Windows.Controls.Primitives.TickPlacement.None>, which is the default value.</span></span>  
  
 <span data-ttu-id="ad097-106">Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Controls.Slider> z <xref:System.Windows.Controls.Primitives.TickBar> , wyświetla znaczniki.</span><span class="sxs-lookup"><span data-stu-id="ad097-106">The following example shows how to create a <xref:System.Windows.Controls.Slider> with a <xref:System.Windows.Controls.Primitives.TickBar> that displays tick marks.</span></span> <span data-ttu-id="ad097-107"><xref:System.Windows.Controls.Slider.TickPlacement%2A> i <xref:System.Windows.Controls.Slider.TickFrequency%2A> właściwości definiują lokalizację znaczników oraz interwału między nimi.</span><span class="sxs-lookup"><span data-stu-id="ad097-107">The <xref:System.Windows.Controls.Slider.TickPlacement%2A> and <xref:System.Windows.Controls.Slider.TickFrequency%2A> properties define the location of the tick marks and the interval between them.</span></span> <span data-ttu-id="ad097-108">Przy przenoszeniu <xref:System.Windows.Controls.Primitives.Thumb>, wyświetlania wartości w etykietkach ekranowych <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="ad097-108">When you move the <xref:System.Windows.Controls.Primitives.Thumb>, tooltips display the value of the <xref:System.Windows.Controls.Slider>.</span></span> <span data-ttu-id="ad097-109"><xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> Właściwość określa, gdzie występują etykietki narzędzi.</span><span class="sxs-lookup"><span data-stu-id="ad097-109">The <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> property defines where the tooltips occur.</span></span> <span data-ttu-id="ad097-110"><xref:System.Windows.Controls.Primitives.Thumb> Przeniesień odnoszą się do lokalizacji pliku znaczników ponieważ <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> ustawiono `true`.</span><span class="sxs-lookup"><span data-stu-id="ad097-110">The <xref:System.Windows.Controls.Primitives.Thumb> movements correspond to the location of the tick marks because <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> is set to `true`.</span></span>  
  
 <span data-ttu-id="ad097-111">Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.Slider.Ticks%2A> właściwości do utworzenia znaczniki wzdłuż osi <xref:System.Windows.Controls.Slider> w nieregularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="ad097-111">The following example shows how to use the <xref:System.Windows.Controls.Slider.Ticks%2A> property to create tick marks along the <xref:System.Windows.Controls.Slider> at irregular intervals.</span></span>  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ad097-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad097-112">See also</span></span>
- <xref:System.Windows.Controls.Slider>
- <xref:System.Windows.Controls.Primitives.TickBar>
- <xref:System.Windows.Controls.Slider.TickPlacement%2A>
- [<span data-ttu-id="ad097-113">Suwak tematy porad</span><span class="sxs-lookup"><span data-stu-id="ad097-113">Slider How-to Topics</span></span>](https://msdn.microsoft.com/library/534be86c-afb2-425d-8186-631278a9925e)
