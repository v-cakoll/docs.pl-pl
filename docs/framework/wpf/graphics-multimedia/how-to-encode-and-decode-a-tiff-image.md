---
title: 'Instrukcje: kodowanie i dekodowanie obrazu TIFF'
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
ms.openlocfilehash: 173a30e785b16a3617b82b771c463083356d6e6e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835293"
---
# <a name="how-to-encode-and-decode-a-tiff-image"></a><span data-ttu-id="3a3a7-102">Instrukcje: kodowanie i dekodowanie obrazu TIFF</span><span class="sxs-lookup"><span data-stu-id="3a3a7-102">How to: Encode and Decode a TIFF Image</span></span>
<span data-ttu-id="3a3a7-103">W poniższych przykładach pokazano, jak zdekodować i kodować obraz Tagged Image File Format (TIFF) przy użyciu określonych <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> i <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> obiektów.</span><span class="sxs-lookup"><span data-stu-id="3a3a7-103">The following examples show how to decode and encode a Tagged Image File Format (TIFF) image using the specific <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> and <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a3a7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a3a7-104">Example</span></span>  
 <span data-ttu-id="3a3a7-105">W tym przykładzie pokazano, jak zdekodować obraz TIFF przy użyciu <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> z <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="3a3a7-105">This example demonstrates how to decode a TIFF image using a <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#1)]
 [!code-csharp[TiffBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#1)]
 [!code-vb[TiffBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="3a3a7-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a3a7-106">Example</span></span>  
 <span data-ttu-id="3a3a7-107">Ten przykład ilustruje sposób kodowania <xref:System.Windows.Media.Imaging.BitmapSource> do obrazu TIFF przy użyciu <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="3a3a7-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a TIFF image using a <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#4)]
 [!code-csharp[TiffBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#4)]
 [!code-vb[TiffBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="3a3a7-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a3a7-108">See also</span></span>

- [<span data-ttu-id="3a3a7-109">Przegląd obrazu</span><span class="sxs-lookup"><span data-stu-id="3a3a7-109">Imaging Overview</span></span>](imaging-overview.md)
