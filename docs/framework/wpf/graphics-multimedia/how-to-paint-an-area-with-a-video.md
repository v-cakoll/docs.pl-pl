---
title: "Jak malować obszar za pomocą wideo"
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
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 362231bbd1f4e95c260370a99233b7e8c2617ca1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-paint-an-area-with-a-video"></a><span data-ttu-id="900c8-102">Jak malować obszar za pomocą wideo</span><span class="sxs-lookup"><span data-stu-id="900c8-102">How to: Paint an Area with a Video</span></span>
<span data-ttu-id="900c8-103">W tym przykładzie pokazano, jak namalować obszar z nośnika.</span><span class="sxs-lookup"><span data-stu-id="900c8-103">This example shows how to paint an area with media.</span></span> <span data-ttu-id="900c8-104">Jednym ze sposobów Malowanie obszaru z nośnika jest użycie <xref:System.Windows.Controls.MediaElement> razem z <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="900c8-104">One way to paint an area with media is to use a <xref:System.Windows.Controls.MediaElement> together with a <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="900c8-105">Użyj <xref:System.Windows.Controls.MediaElement> do ładowania i odtwarzanie multimediów i użyj jej do ustawienia <xref:System.Windows.Media.VisualBrush.Visual%2A> właściwość <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="900c8-105">Use the <xref:System.Windows.Controls.MediaElement> to load and play the media, and then use it to set the <xref:System.Windows.Media.VisualBrush.Visual%2A> property of the <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="900c8-106">Następnie można użyć <xref:System.Windows.Media.VisualBrush> namalować obszar o załadowane nośniki.</span><span class="sxs-lookup"><span data-stu-id="900c8-106">You can then use the <xref:System.Windows.Media.VisualBrush> to paint an area with the loaded media.</span></span>  
  
## <a name="example"></a><span data-ttu-id="900c8-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="900c8-107">Example</span></span>  
 <span data-ttu-id="900c8-108">W poniższym przykładzie użyto <xref:System.Windows.Controls.MediaElement> i <xref:System.Windows.Media.VisualBrush> namalować <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> formantu o wideo.</span><span class="sxs-lookup"><span data-stu-id="900c8-108">The following example uses a <xref:System.Windows.Controls.MediaElement> and a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Controls.TextBlock.Foreground%2A> of a <xref:System.Windows.Controls.TextBlock> control with video.</span></span> <span data-ttu-id="900c8-109">W tym przykładzie <xref:System.Windows.Controls.MediaElement.IsMuted%2A> właściwość <xref:System.Windows.Controls.MediaElement> do `true` tak, aby generuje Brak dźwięku.</span><span class="sxs-lookup"><span data-stu-id="900c8-109">This example sets the <xref:System.Windows.Controls.MediaElement.IsMuted%2A> property of the <xref:System.Windows.Controls.MediaElement> to `true` so that it produces no sound.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a><span data-ttu-id="900c8-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="900c8-110">Example</span></span>  
 <span data-ttu-id="900c8-111">Ponieważ <xref:System.Windows.Media.VisualBrush> dziedziczy <xref:System.Windows.Media.TileBrush> klasy, udostępnia kilka metod kafelków.</span><span class="sxs-lookup"><span data-stu-id="900c8-111">Because <xref:System.Windows.Media.VisualBrush> inherits from the <xref:System.Windows.Media.TileBrush> class, it provides several tiling modes.</span></span> <span data-ttu-id="900c8-112">Przez ustawienie <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwość <xref:System.Windows.Media.VisualBrush> do <xref:System.Windows.Media.TileMode.Tile> i ustawiając jego <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwości na wartość mniejszą niż malowanego obszaru, możesz utworzyć wzorzec sąsiadującym.</span><span class="sxs-lookup"><span data-stu-id="900c8-112">By setting the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.VisualBrush> to <xref:System.Windows.Media.TileMode.Tile> and by setting its <xref:System.Windows.Media.TileBrush.Viewport%2A> property to a value smaller than the area that you are painting, you can create a tiled pattern.</span></span>  
  
 <span data-ttu-id="900c8-113">Poniższy przykład jest taki sam jak poprzedni przykład, z wyjątkiem <xref:System.Windows.Media.VisualBrush> generuje wzorca z wideo.</span><span class="sxs-lookup"><span data-stu-id="900c8-113">The following example is identical to the previous example, except that the <xref:System.Windows.Media.VisualBrush> generates a pattern from the video.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 <span data-ttu-id="900c8-114">Aby uzyskać informacje o sposobie dodawania pliku zawartości, takich jak plik multimedialny do aplikacji, zobacz [zasób w aplikacji WPF, zawartość i pliki danych](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="900c8-114">For information about how to add a content file, such as a media file, to your application, see [WPF Application Resource, Content, and Data Files](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).</span></span> <span data-ttu-id="900c8-115">Podczas dodawania pliku nośnika, należy dodać jako plik zawartości, a nie jako plik zasobów.</span><span class="sxs-lookup"><span data-stu-id="900c8-115">When you add a media file, you must add it as a content file, not as a resource file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="900c8-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="900c8-116">See Also</span></span>  
 <xref:System.Windows.Media.VisualBrush>  
 [<span data-ttu-id="900c8-117">Malowanie obrazów, rysunki i elementy wizualne</span><span class="sxs-lookup"><span data-stu-id="900c8-117">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="900c8-118">Omówienie TileBrush</span><span class="sxs-lookup"><span data-stu-id="900c8-118">TileBrush Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [<span data-ttu-id="900c8-119">Omówienie multimediów</span><span class="sxs-lookup"><span data-stu-id="900c8-119">Multimedia Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)
