---
title: "Jak malować obszar gradientem promieniowym"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55b707e4738a77a8fb093071ef6f5105b2200c16
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="e4762-102">Jak malować obszar gradientem promieniowym</span><span class="sxs-lookup"><span data-stu-id="e4762-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="e4762-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.RadialGradientBrush> klasy namalować obszar o gradientu promieniowego.</span><span class="sxs-lookup"><span data-stu-id="e4762-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4762-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4762-104">Example</span></span>  
 <span data-ttu-id="e4762-105">W poniższym przykładzie użyto <xref:System.Windows.Media.RadialGradientBrush> namalować prostokąt z gradientu promieniowego, który przejścia z żółtym na kolor czerwony, niebieski do Limonowy zielony.</span><span class="sxs-lookup"><span data-stu-id="e4762-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="e4762-106">Na poniższej ilustracji przedstawiono gradientu z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="e4762-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="e4762-107">Zatrzymuje gradientu ma zostały wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="e4762-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="e4762-108">![Gradientu promieniowego gradientu](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="e4762-108">![Gradient stops in a radial gradient](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4762-109">Przykłady w tym temacie Korzystanie z systemu współrzędnych domyślne ustawienie punkty kontrolne.</span><span class="sxs-lookup"><span data-stu-id="e4762-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="e4762-110">System współrzędnych domyślna jest określana względem obwiedni: 0 wskazuje 0 procent obwiedni, a wartość 1 oznacza 100 procent obwiedni.</span><span class="sxs-lookup"><span data-stu-id="e4762-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="e4762-111">Ten układ współrzędnych można zmienić, określając <xref:System.Windows.Media.GradientBrush.MappingMode%2A> na wartość <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="e4762-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="e4762-112">Bezwzględny układ współrzędnych nie jest określana względem obwiedni.</span><span class="sxs-lookup"><span data-stu-id="e4762-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="e4762-113">Wartości są interpretowane bezpośrednio w lokalnej przestrzeni.</span><span class="sxs-lookup"><span data-stu-id="e4762-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="e4762-114">Aby uzyskać dodatkowe <xref:System.Windows.Media.RadialGradientBrush> przykłady, zobacz [przykład pędzle](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="e4762-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="e4762-115">Aby uzyskać więcej informacji na temat gradientach i innych typów pędzle zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e4762-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>
