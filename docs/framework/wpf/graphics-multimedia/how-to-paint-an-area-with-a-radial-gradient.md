---
title: 'Instrukcje: Malowanie obszaru gradientem promieniowym'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: c3bcc11dea4b1f223f629415591ab03588881dde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921836"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="00b55-102">Instrukcje: Malowanie obszaru gradientem promieniowym</span><span class="sxs-lookup"><span data-stu-id="00b55-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="00b55-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.RadialGradientBrush> klasy Maluj obszar gradientem promieniowym.</span><span class="sxs-lookup"><span data-stu-id="00b55-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00b55-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="00b55-104">Example</span></span>  
 <span data-ttu-id="00b55-105">W poniższym przykładzie użyto <xref:System.Windows.Media.RadialGradientBrush> prostokąt gradientem promieniowym, które przechodzi z żółty czerwony na niebieski do Limonowozielony malowania.</span><span class="sxs-lookup"><span data-stu-id="00b55-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="00b55-106">Poniższa ilustracja przedstawia gradientu z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="00b55-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="00b55-107">Podkreślono zatrzymuje gradientu.</span><span class="sxs-lookup"><span data-stu-id="00b55-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="00b55-108">![Ograniczniki gradientu w gradient promieniowy](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="00b55-108">![Gradient stops in a radial gradient](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00b55-109">Przykłady w tym temacie na użytek w układzie współrzędnych domyślne ustawienie punktów kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="00b55-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="00b55-110">System współrzędnych domyślne są określane względem obwiedni: 0 oznacza wartość 0 procent obwiedni, a wartość 1 oznacza 100 procent obwiedni.</span><span class="sxs-lookup"><span data-stu-id="00b55-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="00b55-111">Ten układ współrzędnych można zmienić, określając <xref:System.Windows.Media.GradientBrush.MappingMode%2A> właściwości na wartość <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="00b55-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="00b55-112">Bezwzględnych współrzędnych jest względem obwiedni.</span><span class="sxs-lookup"><span data-stu-id="00b55-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="00b55-113">Wartości są interpretowane bezpośrednio w przestrzeni lokalnej.</span><span class="sxs-lookup"><span data-stu-id="00b55-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="00b55-114">Dla dodatkowych <xref:System.Windows.Media.RadialGradientBrush> przykłady, zobacz [przykład pędzle](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="00b55-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="00b55-115">Aby uzyskać więcej informacji na temat gradientów oraz inne rodzaje pędzle, zobacz [malowanie jednolitymi kolorami i gradientami — Przegląd](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="00b55-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
