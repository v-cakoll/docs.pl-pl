---
title: 'Instrukcje: Używanie zachowanego w pamięci podręcznej elementu jako pędzla'
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: 78df242c7f00b69e36ea4ab6751f51509d9e2220
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229371"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="3a6b3-102">Instrukcje: Używanie zachowanego w pamięci podręcznej elementu jako pędzla</span><span class="sxs-lookup"><span data-stu-id="3a6b3-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="3a6b3-103">Użyj <xref:System.Windows.Media.BitmapCacheBrush> klasy do ponownego użycia pamięci podręcznej elementu wydajnie.</span><span class="sxs-lookup"><span data-stu-id="3a6b3-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="3a6b3-104">Aby element w pamięci podręcznej, należy utworzyć nowe wystąpienie klasy <xref:System.Windows.Media.BitmapCache> klasy i przypisz je do elementu <xref:System.Windows.UIElement.CacheMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3a6b3-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a6b3-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a6b3-105">Example</span></span>  
 <span data-ttu-id="3a6b3-106">W poniższym przykładzie kodu pokazano, jak to ponowne użycie pamięci podręcznej elementu.</span><span class="sxs-lookup"><span data-stu-id="3a6b3-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="3a6b3-107">Element pamięci podręcznej jest <xref:System.Windows.Controls.Image> kontrolkę wyświetlającą duży obraz.</span><span class="sxs-lookup"><span data-stu-id="3a6b3-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="3a6b3-108"><xref:System.Windows.Controls.Image> Kontroli pamięci podręcznej w postaci mapy bitowej przy użyciu <xref:System.Windows.Media.BitmapCache> klasy i pamięć podręczna jest ponownie, przypisując go do <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="3a6b3-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="3a6b3-109">Pędzel jest przypisany do tła przycisków dwadzieścia pięć pokazanie wydajne ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="3a6b3-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="3a6b3-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a6b3-110">See also</span></span>

- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [<span data-ttu-id="3a6b3-111">Instrukcje: Poprawianie wydajności renderowania przez zapisanie elementu w pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="3a6b3-111">How to: Improve Rendering Performance by Caching an Element</span></span>](how-to-improve-rendering-performance-by-caching-an-element.md)
