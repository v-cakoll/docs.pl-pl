---
title: Jak malować obszar jednolitym kolorem
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: 7e8e3fa5a379f02c3bb126c17bbe37fc0f3d57cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a><span data-ttu-id="63c53-102">Jak malować obszar jednolitym kolorem</span><span class="sxs-lookup"><span data-stu-id="63c53-102">How to: Paint an Area with a Solid Color</span></span>
<span data-ttu-id="63c53-103">Namalować obszar jednolitym kolorem służy pędzel wstępnie zdefiniowanych systemu, takich jak <xref:System.Windows.Media.Brushes.Red%2A> lub <xref:System.Windows.Media.Brushes.Blue%2A>, lub można utworzyć nowy <xref:System.Windows.Media.SolidColorBrush> i opisz jego <xref:System.Windows.Media.SolidColorBrush.Color%2A> przy użyciu wartości alfa, czerwony, zielony i niebieski.</span><span class="sxs-lookup"><span data-stu-id="63c53-103">To paint an area with a solid color, you can use a predefined system brush, such as <xref:System.Windows.Media.Brushes.Red%2A> or <xref:System.Windows.Media.Brushes.Blue%2A>, or you can create a new <xref:System.Windows.Media.SolidColorBrush> and describe its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using alpha, red, green, and blue values.</span></span> <span data-ttu-id="63c53-104">W języku XAML może również malowanie obszar jednolitym kolorem przy użyciu notacji szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="63c53-104">In XAML, you may also paint an area with a solid color by using hexidecimal notation.</span></span>  
  
 <span data-ttu-id="63c53-105">W poniższym przykładzie użyto każdego z tych metod do malowania <xref:System.Windows.Shapes.Rectangle> niebieski.</span><span class="sxs-lookup"><span data-stu-id="63c53-105">The following examples uses each of these techniques to paint a <xref:System.Windows.Shapes.Rectangle> blue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63c53-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="63c53-106">Example</span></span>  
 <span data-ttu-id="63c53-107">**Używanie pędzla wstępnie zdefiniowane**</span><span class="sxs-lookup"><span data-stu-id="63c53-107">**Using a Predefined Brush**</span></span>  
  
 <span data-ttu-id="63c53-108">W poniższym przykładzie używa wstępnie zdefiniowanych pędzla <xref:System.Windows.Media.Brushes.Blue%2A> namalować niebieski prostokąta.</span><span class="sxs-lookup"><span data-stu-id="63c53-108">In the following example uses the predefined brush <xref:System.Windows.Media.Brushes.Blue%2A> to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 <span data-ttu-id="63c53-109">**Przy użyciu notacji szesnastkowej**</span><span class="sxs-lookup"><span data-stu-id="63c53-109">**Using Hexadecimal Notation**</span></span>  
  
 <span data-ttu-id="63c53-110">W następnym przykładzie użyto szesnastkowym 8-cyfrowy namalować niebieski prostokąta.</span><span class="sxs-lookup"><span data-stu-id="63c53-110">The next example uses 8-digit hexadecimal notation to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 <span data-ttu-id="63c53-111">**Przy użyciu wartości ARGB**</span><span class="sxs-lookup"><span data-stu-id="63c53-111">**Using ARGB Values**</span></span>  
  
 <span data-ttu-id="63c53-112">W następnym przykładzie jest tworzony <xref:System.Windows.Media.SolidColorBrush> oraz opis jego <xref:System.Windows.Media.SolidColorBrush.Color%2A> przy użyciu ARGB wartości kolor niebieski.</span><span class="sxs-lookup"><span data-stu-id="63c53-112">The next example creates a <xref:System.Windows.Media.SolidColorBrush> and describes its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using the ARGB values for the color blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 <span data-ttu-id="63c53-113">Dla innych sposobów opisujący kolor <xref:System.Windows.Media.Color> struktury.</span><span class="sxs-lookup"><span data-stu-id="63c53-113">For other ways of describing color, see the <xref:System.Windows.Media.Color> structure.</span></span>  
  
 <span data-ttu-id="63c53-114">**Tematy pokrewne**</span><span class="sxs-lookup"><span data-stu-id="63c53-114">**Related Topics**</span></span>  
  
 <span data-ttu-id="63c53-115">Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.SolidColorBrush> i dodatkowe przykłady, zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) omówienie.</span><span class="sxs-lookup"><span data-stu-id="63c53-115">For more information about <xref:System.Windows.Media.SolidColorBrush> and additional examples, see the [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) overview.</span></span>  
  
 <span data-ttu-id="63c53-116">Ten przykładowy kod jest częścią większego przykładu udostępnionego dla <xref:System.Windows.Media.SolidColorBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="63c53-116">This code example is part of a larger example provided for the <xref:System.Windows.Media.SolidColorBrush> class.</span></span> <span data-ttu-id="63c53-117">Pełny przykład, zobacz [przykład pędzle](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="63c53-117">For the complete sample, see the [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c53-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63c53-118">See Also</span></span>  
 <xref:System.Windows.Media.Brushes>
