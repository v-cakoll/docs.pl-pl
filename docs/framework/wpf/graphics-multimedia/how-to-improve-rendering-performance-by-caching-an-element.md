---
title: 'Instrukcje: Poprawianie wydajności renderowania przez zapisanie elementu w pamięci podręcznej'
ms.date: 03/30/2017
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
ms.openlocfilehash: 118e8b0cca52c44788c9d5b291d710f765e7af2a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947280"
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a><span data-ttu-id="5359c-102">Instrukcje: Poprawianie wydajności renderowania przez zapisanie elementu w pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="5359c-102">How to: Improve Rendering Performance by Caching an Element</span></span>
<span data-ttu-id="5359c-103">Użyj <xref:System.Windows.Media.BitmapCache> klasy, aby zwiększyć wydajność renderowania złożony <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="5359c-103">Use the <xref:System.Windows.Media.BitmapCache> class to improve rendering performance of a complex <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="5359c-104">Aby element w pamięci podręcznej, należy utworzyć nowe wystąpienie klasy <xref:System.Windows.Media.BitmapCache> klasy i przypisz je do elementu <xref:System.Windows.UIElement.CacheMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5359c-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span> <span data-ttu-id="5359c-105">Można użyć ponownie <xref:System.Windows.Media.BitmapCache> wydajnie w <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="5359c-105">You can reuse a <xref:System.Windows.Media.BitmapCache> efficiently in a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5359c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5359c-106">Example</span></span>  
 <span data-ttu-id="5359c-107">Poniższy przykład kodu pokazuje, jak utworzyć element złożony i Buforuj go jako mapę bitową, co zwiększa wydajność, gdy element jest animowany.</span><span class="sxs-lookup"><span data-stu-id="5359c-107">The following code example shows how to create a complex element and cache it as a bitmap, which improves performance when the element is animated.</span></span> <span data-ttu-id="5359c-108">Element jest obszarem roboczym, który przechowuje kształt geometrii za pomocą wielu wierzchołków.</span><span class="sxs-lookup"><span data-stu-id="5359c-108">The element is a canvas that holds shape geometries with many vertices.</span></span> <span data-ttu-id="5359c-109">A <xref:System.Windows.Media.BitmapCache> z domyślnej wartości jest przypisane do <xref:System.Windows.UIElement.CacheMode%2A> obszaru roboczego i animacji pokazuje płynne Skalowanie pamięci podręcznej mapy bitowej.</span><span class="sxs-lookup"><span data-stu-id="5359c-109">A <xref:System.Windows.Media.BitmapCache> with default values is assigned to the <xref:System.Windows.UIElement.CacheMode%2A> of the canvas, and an animation shows the smooth scaling of the cached bitmap.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a><span data-ttu-id="5359c-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5359c-110">See also</span></span>

- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [<span data-ttu-id="5359c-111">Instrukcje: Użyj pamięci podręcznej elementu jako pędzla</span><span class="sxs-lookup"><span data-stu-id="5359c-111">How to: Use a Cached Element as a Brush</span></span>](how-to-use-a-cached-element-as-a-brush.md)
