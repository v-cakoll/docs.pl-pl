---
title: 'Instrukcje: Użyj kolorów systemowych w gradiencie'
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 44dfd30dc8d21e638855a383f1c9360a61ce81f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726419"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a><span data-ttu-id="15cee-102">Instrukcje: Użyj kolorów systemowych w gradiencie</span><span class="sxs-lookup"><span data-stu-id="15cee-102">How to: Use System Colors in a Gradient</span></span>
<span data-ttu-id="15cee-103">Aby użyć kolorów systemowych w gradiencie, należy użyć  *\<SystemColor >* kolorów i  *\<SystemColor >* właściwości statycznej ColorKey <xref:System.Windows.SystemColors> klasy w celu uzyskania Odwołanie do koloru, gdzie  *\<SystemColor >* jest nazwą koloru żądany system.</span><span class="sxs-lookup"><span data-stu-id="15cee-103">To use a system color in a gradient, you use the *\<SystemColor>* Color and *\<SystemColor>* ColorKey static properties of the <xref:System.Windows.SystemColors> class to obtain a reference to the color, where *\<SystemColor>* is the name of the desired system color.</span></span> <span data-ttu-id="15cee-104">Użyj  *\<SystemColor >* ColorKey właściwości, gdy użytkownik chce utworzyć dynamiczne odwołania, który jest aktualizowany automatycznie, zgodnie ze zmianami motywu systemu.</span><span class="sxs-lookup"><span data-stu-id="15cee-104">Use the *\<SystemColor>* ColorKey properties when you want to create a dynamic reference that updates automatically as the system theme changes.</span></span> <span data-ttu-id="15cee-105">W przeciwnym razie użyj  *\<SystemColor >* koloru właściwości.</span><span class="sxs-lookup"><span data-stu-id="15cee-105">Otherwise, use the *\<SystemColor>* Color properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15cee-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="15cee-106">Example</span></span>  
 <span data-ttu-id="15cee-107">W poniższym przykładzie użyto dynamicznego systemu zasoby koloru do Tworzenie gradientu.</span><span class="sxs-lookup"><span data-stu-id="15cee-107">The following example uses dynamic system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 <span data-ttu-id="15cee-108">W następnym przykładzie użyto statycznego zasoby koloru do Tworzenie gradientu.</span><span class="sxs-lookup"><span data-stu-id="15cee-108">The next example uses static system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="15cee-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15cee-109">See also</span></span>
- <xref:System.Windows.SystemColors>
- [<span data-ttu-id="15cee-110">Malowanie obszaru pędzlem systemowym</span><span class="sxs-lookup"><span data-stu-id="15cee-110">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="15cee-111">Malowanie jednolitymi kolorami i gradientami — przegląd</span><span class="sxs-lookup"><span data-stu-id="15cee-111">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
