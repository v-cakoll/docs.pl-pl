---
title: "Jak użyć kolorów systemowych w gradiencie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 105e22588f68d999811f5482342d53851a4d25eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-colors-in-a-gradient"></a><span data-ttu-id="6010c-102">Jak użyć kolorów systemowych w gradiencie</span><span class="sxs-lookup"><span data-stu-id="6010c-102">How to: Use System Colors in a Gradient</span></span>
<span data-ttu-id="6010c-103">Użyj kolorów systemu w gradiencie, należy użyć  *\<SystemColor >*kolorów i  *\<SystemColor >*ColorKey właściwości statycznej <xref:System.Windows.SystemColors> klasy w celu uzyskania Odwołanie do kolorów, gdzie  *\<SystemColor >* jest nazwą koloru żądany system.</span><span class="sxs-lookup"><span data-stu-id="6010c-103">To use a system color in a gradient, you use the *\<SystemColor>*Color and *\<SystemColor>*ColorKey static properties of the <xref:System.Windows.SystemColors> class to obtain a reference to the color, where *\<SystemColor>* is the name of the desired system color.</span></span> <span data-ttu-id="6010c-104">Użyj  *\<SystemColor >*ColorKey właściwości, gdy chcesz utworzyć odwołanie do dynamicznej aktualizacji automatycznie jako zmian kompozycji systemu.</span><span class="sxs-lookup"><span data-stu-id="6010c-104">Use the *\<SystemColor>*ColorKey properties when you want to create a dynamic reference that updates automatically as the system theme changes.</span></span> <span data-ttu-id="6010c-105">W przeciwnym razie użyj  *\<SystemColor >*kolor właściwości.</span><span class="sxs-lookup"><span data-stu-id="6010c-105">Otherwise, use the *\<SystemColor>*Color properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6010c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="6010c-106">Example</span></span>  
 <span data-ttu-id="6010c-107">W poniższym przykładzie użyto dynamicznego systemu kolor zasobów do Tworzenie gradientu.</span><span class="sxs-lookup"><span data-stu-id="6010c-107">The following example uses dynamic system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 <span data-ttu-id="6010c-108">W następnym przykładzie użyto zasobów kolorów systemu statycznego do Tworzenie gradientu.</span><span class="sxs-lookup"><span data-stu-id="6010c-108">The next example uses static system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="6010c-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6010c-109">See Also</span></span>  
 <xref:System.Windows.SystemColors>  
 [<span data-ttu-id="6010c-110">Malowanie obszar o pędzla systemu</span><span class="sxs-lookup"><span data-stu-id="6010c-110">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="6010c-111">Malowanie pełnych kolorów i gradientów — omówienie</span><span class="sxs-lookup"><span data-stu-id="6010c-111">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
