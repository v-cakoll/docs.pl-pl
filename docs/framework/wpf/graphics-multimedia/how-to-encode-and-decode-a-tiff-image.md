---
title: "Jak kodować i dekodować obraz TIFF"
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
- TIFF encoding [WPF]
- encoding TIFF images [WPF]
- encoding image formats [WPF]
- decoding TIFF images [WPF]
- decoding image formats [WPF]
- TIFF decoding [WPF]
ms.assetid: 1dfe3209-fc73-40e6-ad1c-71c1c58b3364
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c839f449a0b19f2aa3bbe26a393bdfd2226fa9f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-encode-and-decode-a-tiff-image"></a><span data-ttu-id="4f5ba-102">Jak kodować i dekodować obraz TIFF</span><span class="sxs-lookup"><span data-stu-id="4f5ba-102">How to: Encode and Decode a TIFF Image</span></span>
<span data-ttu-id="4f5ba-103">Poniższe przykłady przedstawiają sposób dekodowania i kodowanie [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)] obrazu przy użyciu konkretnych <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> i <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> obiektów.</span><span class="sxs-lookup"><span data-stu-id="4f5ba-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)] image using the specific <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> and <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f5ba-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f5ba-104">Example</span></span>  
 <span data-ttu-id="4f5ba-105">W tym przykładzie pokazano sposób dekodowania [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] obrazu przy użyciu <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> z <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="4f5ba-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] image using a <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#1)]
 [!code-csharp[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#1)]
 [!code-vb[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="4f5ba-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f5ba-106">Example</span></span>  
 <span data-ttu-id="4f5ba-107">W tym przykładzie pokazano sposób kodowania <xref:System.Windows.Media.Imaging.BitmapSource> do [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] obrazu przy użyciu <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="4f5ba-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] image using a <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#4)]
 [!code-csharp[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#4)]
 [!code-vb[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4f5ba-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f5ba-108">See Also</span></span>  
 [<span data-ttu-id="4f5ba-109">Omówienie tworzenia obrazu</span><span class="sxs-lookup"><span data-stu-id="4f5ba-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
