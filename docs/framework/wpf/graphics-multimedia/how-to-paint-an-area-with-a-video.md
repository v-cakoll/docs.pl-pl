---
title: 'Instrukcje: Maluj obszar za pomocą wideo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
ms.openlocfilehash: 0756a9e87840648b55ecad4b3f1ce6e0e5452eb7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363296"
---
# <a name="how-to-paint-an-area-with-a-video"></a><span data-ttu-id="22ca1-102">Instrukcje: Maluj obszar za pomocą wideo</span><span class="sxs-lookup"><span data-stu-id="22ca1-102">How to: Paint an Area with a Video</span></span>
<span data-ttu-id="22ca1-103">Ten przykład pokazuje, jak malować obszar za pomocą nośnika.</span><span class="sxs-lookup"><span data-stu-id="22ca1-103">This example shows how to paint an area with media.</span></span> <span data-ttu-id="22ca1-104">Jednym ze sposobów Maluj obszar za pomocą nośnika jest użycie <xref:System.Windows.Controls.MediaElement> wraz z <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="22ca1-104">One way to paint an area with media is to use a <xref:System.Windows.Controls.MediaElement> together with a <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="22ca1-105">Użyj <xref:System.Windows.Controls.MediaElement> do ładowania i odtwarzania nośnika i użyj go, aby ustawić <xref:System.Windows.Media.VisualBrush.Visual%2A> właściwość <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="22ca1-105">Use the <xref:System.Windows.Controls.MediaElement> to load and play the media, and then use it to set the <xref:System.Windows.Media.VisualBrush.Visual%2A> property of the <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="22ca1-106">Następnie można użyć <xref:System.Windows.Media.VisualBrush> można malować obszar za pomocą załadowane nośniki.</span><span class="sxs-lookup"><span data-stu-id="22ca1-106">You can then use the <xref:System.Windows.Media.VisualBrush> to paint an area with the loaded media.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22ca1-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="22ca1-107">Example</span></span>  
 <span data-ttu-id="22ca1-108">W poniższym przykładzie użyto <xref:System.Windows.Controls.MediaElement> i <xref:System.Windows.Media.VisualBrush> namalować <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> kontrolki wideo.</span><span class="sxs-lookup"><span data-stu-id="22ca1-108">The following example uses a <xref:System.Windows.Controls.MediaElement> and a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Controls.TextBlock.Foreground%2A> of a <xref:System.Windows.Controls.TextBlock> control with video.</span></span> <span data-ttu-id="22ca1-109">W tym przykładzie <xref:System.Windows.Controls.MediaElement.IsMuted%2A> właściwość <xref:System.Windows.Controls.MediaElement> do `true` tak, aby generuje Brak dźwięku.</span><span class="sxs-lookup"><span data-stu-id="22ca1-109">This example sets the <xref:System.Windows.Controls.MediaElement.IsMuted%2A> property of the <xref:System.Windows.Controls.MediaElement> to `true` so that it produces no sound.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a><span data-ttu-id="22ca1-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="22ca1-110">Example</span></span>  
 <span data-ttu-id="22ca1-111">Ponieważ <xref:System.Windows.Media.VisualBrush> dziedziczy <xref:System.Windows.Media.TileBrush> klasy, udostępnia kilka metod fragmentacji.</span><span class="sxs-lookup"><span data-stu-id="22ca1-111">Because <xref:System.Windows.Media.VisualBrush> inherits from the <xref:System.Windows.Media.TileBrush> class, it provides several tiling modes.</span></span> <span data-ttu-id="22ca1-112">Ustawiając <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwość <xref:System.Windows.Media.VisualBrush> do <xref:System.Windows.Media.TileMode.Tile> i ustawiając jego <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwości na wartość mniejszą niż malowanego obszaru, możesz utworzyć fragmentacji wzorca.</span><span class="sxs-lookup"><span data-stu-id="22ca1-112">By setting the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.VisualBrush> to <xref:System.Windows.Media.TileMode.Tile> and by setting its <xref:System.Windows.Media.TileBrush.Viewport%2A> property to a value smaller than the area that you are painting, you can create a tiled pattern.</span></span>  
  
 <span data-ttu-id="22ca1-113">Poniższy przykład jest identyczny z poprzednim przykładem, chyba że <xref:System.Windows.Media.VisualBrush> generuje wzorca z filmu wideo.</span><span class="sxs-lookup"><span data-stu-id="22ca1-113">The following example is identical to the previous example, except that the <xref:System.Windows.Media.VisualBrush> generates a pattern from the video.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 <span data-ttu-id="22ca1-114">Aby uzyskać informacje dotyczące dodawania pliku zawartości, takich jak plik multimedialny do aplikacji, zobacz [zasoby aplikacji WPF, zawartość i pliki danych](../app-development/wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="22ca1-114">For information about how to add a content file, such as a media file, to your application, see [WPF Application Resource, Content, and Data Files](../app-development/wpf-application-resource-content-and-data-files.md).</span></span> <span data-ttu-id="22ca1-115">Po dodaniu pliku nośnika, należy dodać jako pliku zawartości, a nie jako plik zasobów.</span><span class="sxs-lookup"><span data-stu-id="22ca1-115">When you add a media file, you must add it as a content file, not as a resource file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22ca1-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22ca1-116">See also</span></span>
- <xref:System.Windows.Media.VisualBrush>
- [<span data-ttu-id="22ca1-117">Malowanie przy użyciu obrazów, rysowania i wizualizacji</span><span class="sxs-lookup"><span data-stu-id="22ca1-117">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="22ca1-118">TileBrush — przegląd</span><span class="sxs-lookup"><span data-stu-id="22ca1-118">TileBrush Overview</span></span>](tilebrush-overview.md)
- [<span data-ttu-id="22ca1-119">Multimedia — przegląd</span><span class="sxs-lookup"><span data-stu-id="22ca1-119">Multimedia Overview</span></span>](multimedia-overview.md)
