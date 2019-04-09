---
title: 'Instrukcje: Kodowanie i dekodowanie obrazu BMP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding BMP images [WPF]
- BMP encoding [WPF]
- decoding BMP images [WPF]
- encoding image formats [WPF]
- BMP decoding [WPF]
- decoding image formats [WPF]
ms.assetid: feb5ef27-28ac-40ab-bfc2-e0456990d32c
ms.openlocfilehash: b7d5ace8aead864cb69a9e696a3f1f925e232600
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121904"
---
# <a name="how-to-encode-and-decode-a-bmp-image"></a><span data-ttu-id="b2866-102">Instrukcje: Kodowanie i dekodowanie obrazu BMP</span><span class="sxs-lookup"><span data-stu-id="b2866-102">How to: Encode and Decode a BMP Image</span></span>
<span data-ttu-id="b2866-103">W poniższych przykładach pokazano, jak dekodowanie i kodowanie [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)] obrazów przy użyciu określonego <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> i <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> obiektów.</span><span class="sxs-lookup"><span data-stu-id="b2866-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)] image using the specific <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> and <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2866-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2866-104">Example</span></span>  
 <span data-ttu-id="b2866-105">W tym przykładzie pokazano, jak dekodowanie [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] obrazów przy użyciu <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> z <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="b2866-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] image using a <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="b2866-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2866-106">Example</span></span>  
 <span data-ttu-id="b2866-107">W tym przykładzie pokazano, jak kodować <xref:System.Windows.Media.Imaging.BitmapSource> do [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] obrazów przy użyciu <xref:System.Windows.Media.Imaging.BmpBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="b2866-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] image using a <xref:System.Windows.Media.Imaging.BmpBitmapEncoder>.</span></span>  
  
 [!code-cpp[BmpBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#4)]
 [!code-csharp[BmpBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#4)]
 [!code-vb[BmpBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b2866-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2866-108">See also</span></span>

- [<span data-ttu-id="b2866-109">Przegląd Obrazowanie</span><span class="sxs-lookup"><span data-stu-id="b2866-109">Imaging Overview</span></span>](imaging-overview.md)
