---
title: 'Instrukcje: Koduj i dekoduj obraz JPEG'
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
ms.openlocfilehash: 0f64ef8537f22ea996cbcf274885de1f3968267a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373793"
---
# <a name="how-to-encode-and-decode-a-jpeg-image"></a><span data-ttu-id="29840-102">Instrukcje: Koduj i dekoduj obraz JPEG</span><span class="sxs-lookup"><span data-stu-id="29840-102">How to: Encode and decode a JPEG image</span></span>

<span data-ttu-id="29840-103">W poniższych przykładach pokazano, jak dekodowanie i kodowanie przy użyciu określonego obrazu JPEG <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> i <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> obiektów.</span><span class="sxs-lookup"><span data-stu-id="29840-103">The following examples show how to decode and encode a JPEG image using the specific <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> and <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> objects.</span></span>  
  
## <a name="example---decode-a-jpeg-image"></a><span data-ttu-id="29840-104">Przykład — dekodowanie obrazu JPEG</span><span class="sxs-lookup"><span data-stu-id="29840-104">Example - Decode a JPEG image</span></span>

<span data-ttu-id="29840-105">W tym przykładzie pokazano, jak dekodowanie obrazu JPEG przy użyciu <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> z <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="29840-105">This example demonstrates how to decode a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
[!code-csharp[JpegBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
[!code-vb[JpegBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## <a name="example---encode-a-jpeg-image"></a><span data-ttu-id="29840-106">Przykład — kodowanie obrazów JPEG</span><span class="sxs-lookup"><span data-stu-id="29840-106">Example - Encode a JPEG image</span></span>

<span data-ttu-id="29840-107">W tym przykładzie pokazano, jak kodować <xref:System.Windows.Media.Imaging.BitmapSource> na format JPEG, image, za pomocą <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="29840-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
[!code-csharp[JpegBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
[!code-vb[JpegBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="29840-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29840-108">See also</span></span>

- [<span data-ttu-id="29840-109">Obrazowanie — przegląd</span><span class="sxs-lookup"><span data-stu-id="29840-109">Imaging Overview</span></span>](imaging-overview.md)
