---
title: 'Instrukcje: Utwórz mapę bitową z Visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: dbbf7691508e5e5ddf3ed3af768f757ee0c3f20c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705460"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="c9ec9-102">Instrukcje: Utwórz mapę bitową z Visual</span><span class="sxs-lookup"><span data-stu-id="c9ec9-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="c9ec9-103">W tym przykładzie pokazano, jak utworzyć mapę bitową z <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="c9ec9-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="c9ec9-104">A <xref:System.Windows.Media.DrawingVisual> jest renderowany przy użyciu <xref:System.Windows.Media.FormattedText>.</span><span class="sxs-lookup"><span data-stu-id="c9ec9-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="c9ec9-105"><xref:System.Windows.Media.Visual> Jest następnie renderowany na <xref:System.Windows.Media.Imaging.RenderTargetBitmap> Tworzenie mapy bitowej danego tekstu.</span><span class="sxs-lookup"><span data-stu-id="c9ec9-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9ec9-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9ec9-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="c9ec9-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9ec9-107">See also</span></span>
- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="c9ec9-108">Obrazowanie — przegląd</span><span class="sxs-lookup"><span data-stu-id="c9ec9-108">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
- [<span data-ttu-id="c9ec9-109">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="c9ec9-109">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="c9ec9-110">Użycie obiektów DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="c9ec9-110">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
