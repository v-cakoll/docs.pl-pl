---
title: "Jak wykazać zawartość rysowania Visual"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e498bc8e425198e479d7ce0b2328e0efa3ede70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="05f17-102">Jak wykazać zawartość rysowania Visual</span><span class="sxs-lookup"><span data-stu-id="05f17-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="05f17-103"><xref:System.Windows.Media.Drawing> Obiektu Podaj model obiektów dla wyliczania zawartość <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="05f17-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05f17-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="05f17-104">Example</span></span>  
 <span data-ttu-id="05f17-105">W poniższym przykładzie użyto <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metoda pobierania <xref:System.Windows.Media.DrawingGroup> wartość <xref:System.Windows.Media.Visual> i jej wyliczyć.</span><span class="sxs-lookup"><span data-stu-id="05f17-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05f17-106">Gdy są wyliczania zawartość elementu wizualnego, są pobierane <xref:System.Windows.Media.Drawing> obiektów, a nie podstawowy reprezentację danych renderowania jako listę instrukcji grafiki wektorowej.</span><span class="sxs-lookup"><span data-stu-id="05f17-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="05f17-107">Aby uzyskać więcej informacji, zobacz [Przegląd renderowania grafiki WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="05f17-107">For more information, see [WPF Graphics Rendering Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="05f17-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05f17-108">See Also</span></span>  
 <xref:System.Windows.Media.Drawing>  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 [<span data-ttu-id="05f17-109">Rysowanie obiekty — omówienie</span><span class="sxs-lookup"><span data-stu-id="05f17-109">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="05f17-110">Przegląd renderowania grafiki WPF</span><span class="sxs-lookup"><span data-stu-id="05f17-110">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
