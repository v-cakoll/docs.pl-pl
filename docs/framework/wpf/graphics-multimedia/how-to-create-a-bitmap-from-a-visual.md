---
title: 'Instrukcje: Tworzenie mapy bitowej za pomocą wizualizacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: a622d99f7c477f8654526ed399f1eb37288682fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910263"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="b08d0-102">Instrukcje: Tworzenie mapy bitowej za pomocą wizualizacji</span><span class="sxs-lookup"><span data-stu-id="b08d0-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="b08d0-103">W tym przykładzie pokazano, jak utworzyć mapę bitową z <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="b08d0-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="b08d0-104">A <xref:System.Windows.Media.DrawingVisual> jest renderowany przy użyciu <xref:System.Windows.Media.FormattedText>.</span><span class="sxs-lookup"><span data-stu-id="b08d0-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="b08d0-105"><xref:System.Windows.Media.Visual> Jest następnie renderowany na <xref:System.Windows.Media.Imaging.RenderTargetBitmap> Tworzenie mapy bitowej danego tekstu.</span><span class="sxs-lookup"><span data-stu-id="b08d0-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b08d0-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b08d0-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="b08d0-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b08d0-107">See also</span></span>

- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="b08d0-108">Obrazowanie — przegląd</span><span class="sxs-lookup"><span data-stu-id="b08d0-108">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="b08d0-109">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="b08d0-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="b08d0-110">Użycie obiektów DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="b08d0-110">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
