---
title: "Jak kodować i dekodować obraz PNG"
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
- cpp
helpviewer_keywords:
- PNG encoding [WPF]
- decoding PNG images [WPF]
- PNG decoding [WPF]
- encoding image formats [WPF]
- decoding image formats [WPF]
- encoding PNG images [WPF]
ms.assetid: 3d31d186-af73-47f0-b5a7-c26ae46409a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3687beb2f661b04c79d382bb7bbff6e0f7999924
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-encode-and-decode-a-png-image"></a><span data-ttu-id="c1fa4-102">Jak kodować i dekodować obraz PNG</span><span class="sxs-lookup"><span data-stu-id="c1fa4-102">How to: Encode and Decode a PNG Image</span></span>
<span data-ttu-id="c1fa4-103">Poniższe przykłady przedstawiają sposób dekodowania i kodowanie [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] obrazu przy użyciu konkretnych <xref:System.Windows.Media.Imaging.PngBitmapDecoder> i <xref:System.Windows.Media.Imaging.PngBitmapEncoder> obiektów.</span><span class="sxs-lookup"><span data-stu-id="c1fa4-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] image using the specific <xref:System.Windows.Media.Imaging.PngBitmapDecoder> and <xref:System.Windows.Media.Imaging.PngBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1fa4-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1fa4-104">Example</span></span>  
 <span data-ttu-id="c1fa4-105">W tym przykładzie pokazano sposób dekodowania [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] obrazu przy użyciu <xref:System.Windows.Media.Imaging.PngBitmapDecoder> z <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="c1fa4-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image using a <xref:System.Windows.Media.Imaging.PngBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#1)]
 [!code-csharp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#1)]
 [!code-vb[PngBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="c1fa4-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1fa4-106">Example</span></span>  
 <span data-ttu-id="c1fa4-107">W tym przykładzie pokazano sposób kodowania <xref:System.Windows.Media.Imaging.BitmapSource> do [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] obrazu przy użyciu <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="c1fa4-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image using a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#4)]
 [!code-csharp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#4)]
 [!code-vb[PngBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="c1fa4-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1fa4-108">See Also</span></span>  
 [<span data-ttu-id="c1fa4-109">Omówienie tworzenia obrazu</span><span class="sxs-lookup"><span data-stu-id="c1fa4-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
