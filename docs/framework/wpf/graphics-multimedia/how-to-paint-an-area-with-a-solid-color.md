---
title: Jak malować obszar jednolitym kolorem
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: be28a0af04c4e43cdf745a5429468aee99e34c40
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849525"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a><span data-ttu-id="97913-102">Jak malować obszar jednolitym kolorem</span><span class="sxs-lookup"><span data-stu-id="97913-102">How to: Paint an Area with a Solid Color</span></span>
<span data-ttu-id="97913-103">Aby pomalować obszar jednolitym kolorem, można użyć wstępnie zdefiniowanego <xref:System.Windows.Media.Brushes.Blue%2A>pędzla systemowego, <xref:System.Windows.Media.SolidColorBrush> takiego <xref:System.Windows.Media.SolidColorBrush.Color%2A> jak <xref:System.Windows.Media.Brushes.Red%2A> lub , lub utworzyć nowy i opisać jego użycie przy użyciu wartości alfa, czerwonej, zielonej i niebieskiej.</span><span class="sxs-lookup"><span data-stu-id="97913-103">To paint an area with a solid color, you can use a predefined system brush, such as <xref:System.Windows.Media.Brushes.Red%2A> or <xref:System.Windows.Media.Brushes.Blue%2A>, or you can create a new <xref:System.Windows.Media.SolidColorBrush> and describe its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using alpha, red, green, and blue values.</span></span> <span data-ttu-id="97913-104">W języku XAML można również malować obszar o jednolitym kolorze za pomocą notacji szesnastkowej.</span><span class="sxs-lookup"><span data-stu-id="97913-104">In XAML, you may also paint an area with a solid color by using hexidecimal notation.</span></span>  
  
 <span data-ttu-id="97913-105">Poniższe przykłady używa każdej z tych <xref:System.Windows.Shapes.Rectangle> technik do malowania niebieski.</span><span class="sxs-lookup"><span data-stu-id="97913-105">The following examples uses each of these techniques to paint a <xref:System.Windows.Shapes.Rectangle> blue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97913-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="97913-106">Example</span></span>  
 <span data-ttu-id="97913-107">**Korzystanie ze wstępnie zdefiniowanego pędzla**</span><span class="sxs-lookup"><span data-stu-id="97913-107">**Using a Predefined Brush**</span></span>  
  
 <span data-ttu-id="97913-108">W poniższym przykładzie użyto wstępnie <xref:System.Windows.Media.Brushes.Blue%2A> zdefiniowanego pędzla do malowania prostokąta na niebiesko.</span><span class="sxs-lookup"><span data-stu-id="97913-108">In the following example uses the predefined brush <xref:System.Windows.Media.Brushes.Blue%2A> to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 <span data-ttu-id="97913-109">**Korzystanie z notacji szesnastkowej**</span><span class="sxs-lookup"><span data-stu-id="97913-109">**Using Hexadecimal Notation**</span></span>  
  
 <span data-ttu-id="97913-110">W następnym przykładzie użyto 8-cyfrowego notacji szesnastkowe do malowania prostokąta na niebiesko.</span><span class="sxs-lookup"><span data-stu-id="97913-110">The next example uses 8-digit hexadecimal notation to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 <span data-ttu-id="97913-111">**Korzystanie z wartości ARGB**</span><span class="sxs-lookup"><span data-stu-id="97913-111">**Using ARGB Values**</span></span>  
  
 <span data-ttu-id="97913-112">Następny przykład tworzy <xref:System.Windows.Media.SolidColorBrush> i <xref:System.Windows.Media.SolidColorBrush.Color%2A> opisuje jego przy użyciu argb wartości dla koloru niebieskiego.</span><span class="sxs-lookup"><span data-stu-id="97913-112">The next example creates a <xref:System.Windows.Media.SolidColorBrush> and describes its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using the ARGB values for the color blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 <span data-ttu-id="97913-113">Aby uzyskać inne sposoby opisywania koloru, zobacz strukturę. <xref:System.Windows.Media.Color></span><span class="sxs-lookup"><span data-stu-id="97913-113">For other ways of describing color, see the <xref:System.Windows.Media.Color> structure.</span></span>  
  
 <span data-ttu-id="97913-114">**Tematy pokrewne**</span><span class="sxs-lookup"><span data-stu-id="97913-114">**Related Topics**</span></span>  
  
 <span data-ttu-id="97913-115">Aby uzyskać <xref:System.Windows.Media.SolidColorBrush> więcej informacji na temat i dodatkowych przykładów, zobacz [Omówienie malowania z jednolitymi kolorami i gradientami.](painting-with-solid-colors-and-gradients-overview.md)</span><span class="sxs-lookup"><span data-stu-id="97913-115">For more information about <xref:System.Windows.Media.SolidColorBrush> and additional examples, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md) overview.</span></span>  
  
 <span data-ttu-id="97913-116">W tym przykładzie kodu jest częścią <xref:System.Windows.Media.SolidColorBrush> większego przykładu przewidzianego dla klasy.</span><span class="sxs-lookup"><span data-stu-id="97913-116">This code example is part of a larger example provided for the <xref:System.Windows.Media.SolidColorBrush> class.</span></span> <span data-ttu-id="97913-117">Aby uzyskać pełną próbkę, zobacz [Próbka pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="97913-117">For the complete sample, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97913-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97913-118">See also</span></span>

- <xref:System.Windows.Media.Brushes>
