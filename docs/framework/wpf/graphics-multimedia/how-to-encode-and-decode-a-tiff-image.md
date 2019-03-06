---
title: 'Instrukcje: Koduj i dekoduj obraz TIFF'
ms.date: 03/30/2017
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
ms.openlocfilehash: e89f39dedcc210aaa6917b4b964d1944673047b5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356679"
---
# <a name="how-to-encode-and-decode-a-tiff-image"></a><span data-ttu-id="18a6b-102">Instrukcje: Koduj i dekoduj obraz TIFF</span><span class="sxs-lookup"><span data-stu-id="18a6b-102">How to: Encode and Decode a TIFF Image</span></span>
<span data-ttu-id="18a6b-103">W poniższych przykładach pokazano, jak dekodowanie i kodowanie [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)] obrazów przy użyciu określonego <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> i <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> obiektów.</span><span class="sxs-lookup"><span data-stu-id="18a6b-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)] image using the specific <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> and <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18a6b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="18a6b-104">Example</span></span>  
 <span data-ttu-id="18a6b-105">W tym przykładzie pokazano, jak dekodowanie [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] obrazów przy użyciu <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> z <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="18a6b-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] image using a <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#1)]
 [!code-csharp[TiffBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#1)]
 [!code-vb[TiffBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="18a6b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="18a6b-106">Example</span></span>  
 <span data-ttu-id="18a6b-107">W tym przykładzie pokazano, jak kodować <xref:System.Windows.Media.Imaging.BitmapSource> do [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] obrazów przy użyciu <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="18a6b-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] image using a <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#4)]
 [!code-csharp[TiffBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#4)]
 [!code-vb[TiffBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="18a6b-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18a6b-108">See also</span></span>
- [<span data-ttu-id="18a6b-109">Obrazowanie — przegląd</span><span class="sxs-lookup"><span data-stu-id="18a6b-109">Imaging Overview</span></span>](imaging-overview.md)
