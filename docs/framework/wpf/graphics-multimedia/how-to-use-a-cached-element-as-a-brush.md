---
title: 'Instrukcje: Użyj pamięci podręcznej elementu jako pędzla'
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: 008bec87390a807ae2b4797af8b86aaf59c92ef5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372493"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="3149d-102">Instrukcje: Użyj pamięci podręcznej elementu jako pędzla</span><span class="sxs-lookup"><span data-stu-id="3149d-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="3149d-103">Użyj <xref:System.Windows.Media.BitmapCacheBrush> klasy do ponownego użycia pamięci podręcznej elementu wydajnie.</span><span class="sxs-lookup"><span data-stu-id="3149d-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="3149d-104">Aby element w pamięci podręcznej, należy utworzyć nowe wystąpienie klasy <xref:System.Windows.Media.BitmapCache> klasy i przypisz je do elementu <xref:System.Windows.UIElement.CacheMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3149d-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3149d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3149d-105">Example</span></span>  
 <span data-ttu-id="3149d-106">W poniższym przykładzie kodu pokazano, jak to ponowne użycie pamięci podręcznej elementu.</span><span class="sxs-lookup"><span data-stu-id="3149d-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="3149d-107">Element pamięci podręcznej jest <xref:System.Windows.Controls.Image> kontrolkę wyświetlającą duży obraz.</span><span class="sxs-lookup"><span data-stu-id="3149d-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="3149d-108"><xref:System.Windows.Controls.Image> Kontroli pamięci podręcznej w postaci mapy bitowej przy użyciu <xref:System.Windows.Media.BitmapCache> klasy i pamięć podręczna jest ponownie, przypisując go do <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="3149d-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="3149d-109">Pędzel jest przypisany do tła przycisków dwadzieścia pięć pokazanie wydajne ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="3149d-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="3149d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3149d-110">See also</span></span>
- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [<span data-ttu-id="3149d-111">Instrukcje: Poprawianie wydajności renderowania przez zapisanie elementu w pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="3149d-111">How to: Improve Rendering Performance by Caching an Element</span></span>](how-to-improve-rendering-performance-by-caching-an-element.md)
