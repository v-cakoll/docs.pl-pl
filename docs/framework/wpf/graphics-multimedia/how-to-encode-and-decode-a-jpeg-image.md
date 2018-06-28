---
title: 'Porady: kodowania i dekodowania obrazu JPEG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding image formats [WPF]
- decoding JPEG images [WPF]
- encoding JPEG images [WPF]
- decoding image formats [WPF]
- JPEG decoding [WPF]
- JPEG encoding [WPF]
ms.assetid: b8cfde37-9f68-4911-a05e-51d8d7bdec7b
ms.openlocfilehash: 916eab63938100daf91e6c1a5af31648a99108d0
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027970"
---
# <a name="how-to-encode-and-decode-a-jpeg-image"></a><span data-ttu-id="c6250-102">Porady: kodowania i dekodowania obrazu JPEG</span><span class="sxs-lookup"><span data-stu-id="c6250-102">How to: Encode and decode a JPEG image</span></span>

<span data-ttu-id="c6250-103">Poniższe przykłady przedstawiają sposób dekodowania i kodowanie obrazu JPEG, przy użyciu konkretnych <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> i <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> obiektów.</span><span class="sxs-lookup"><span data-stu-id="c6250-103">The following examples show how to decode and encode a JPEG image using the specific <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> and <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> objects.</span></span>  
  
## <a name="example---decode-a-jpeg-image"></a><span data-ttu-id="c6250-104">Przykład — dekodowanie obrazu JPEG</span><span class="sxs-lookup"><span data-stu-id="c6250-104">Example - Decode a JPEG image</span></span>

<span data-ttu-id="c6250-105">W tym przykładzie pokazano, jak dekodowanie obrazu JPEG przy użyciu <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> z <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="c6250-105">This example demonstrates how to decode a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
[!code-csharp[JpegBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
[!code-vb[JpegBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## <a name="example---encode-a-jpeg-image"></a><span data-ttu-id="c6250-106">Przykład — kodowanie obrazu JPEG</span><span class="sxs-lookup"><span data-stu-id="c6250-106">Example - Encode a JPEG image</span></span>

<span data-ttu-id="c6250-107">W tym przykładzie pokazano sposób kodowania <xref:System.Windows.Media.Imaging.BitmapSource> na format JPEG obrazu przy użyciu <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="c6250-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
[!code-csharp[JpegBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
[!code-vb[JpegBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="c6250-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6250-108">See also</span></span>

[<span data-ttu-id="c6250-109">Obrazowanie — przegląd</span><span class="sxs-lookup"><span data-stu-id="c6250-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)