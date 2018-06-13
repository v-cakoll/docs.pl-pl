---
title: Jak użyć zachowanego w pamięci podręcznej elementu jako pędzla
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: c43c4ecbefe99d6e38766705378d85d92ecc5729
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561527"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="aa77c-102">Jak użyć zachowanego w pamięci podręcznej elementu jako pędzla</span><span class="sxs-lookup"><span data-stu-id="aa77c-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="aa77c-103">Użyj <xref:System.Windows.Media.BitmapCacheBrush> klasy do ponownego użycia pamięci podręcznej elementu wydajnie.</span><span class="sxs-lookup"><span data-stu-id="aa77c-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="aa77c-104">W pamięci podręcznej elementu, Utwórz nowe wystąpienie klasy <xref:System.Windows.Media.BitmapCache> klasy i przypisz je do elementu <xref:System.Windows.UIElement.CacheMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="aa77c-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa77c-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa77c-105">Example</span></span>  
 <span data-ttu-id="aa77c-106">Poniższy przykład kodu pokazuje, jak do ponownego użycia elementu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="aa77c-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="aa77c-107">Element pamięci podręcznej jest <xref:System.Windows.Controls.Image> kontrolkę wyświetlającą duży obraz.</span><span class="sxs-lookup"><span data-stu-id="aa77c-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="aa77c-108"><xref:System.Windows.Controls.Image> Kontroli pamięci podręcznej w postaci mapy bitowej przy użyciu <xref:System.Windows.Media.BitmapCache> klasy i pamięci podręcznej zostanie ponownie użyty przez przypisanie go do <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="aa77c-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="aa77c-109">Pędzel jest przypisany do tła przycisków dwadzieścia pięć pokazanie wydajne ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="aa77c-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="aa77c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa77c-110">See Also</span></span>  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [<span data-ttu-id="aa77c-111">Instrukcje: poprawianie wydajności renderowania przez zapisanie elementu w pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="aa77c-111">How to: Improve Rendering Performance by Caching an Element</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
