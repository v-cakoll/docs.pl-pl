---
title: 'Instrukcje: Kodowanie i dekodowanie obrazu GIF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding GIF images [WPF]
- encoding image formats [WPF]
- decoding GIF images [WPF]
- decoding image formats [WPF]
- GIF decoding [WPF]
- GIF encoding [WPF]
ms.assetid: 9cdd9ec7-71eb-444b-b9e3-991958461163
ms.openlocfilehash: ec509a03d95e5f72af0b1f362e253799b07edc1f
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671691"
---
# <a name="how-to-encode-and-decode-a-gif-image"></a><span data-ttu-id="c9568-102">Instrukcje: Kodowanie i dekodowanie obrazu GIF</span><span class="sxs-lookup"><span data-stu-id="c9568-102">How to: Encode and Decode a GIF Image</span></span>
<span data-ttu-id="c9568-103">W poniższych przykładach pokazano, jak zdekodować i kodować obraz Graphics Interchange Format (GIF) przy użyciu <xref:System.Windows.Media.Imaging.GifBitmapDecoder> określonych <xref:System.Windows.Media.Imaging.GifBitmapEncoder> obiektów i.</span><span class="sxs-lookup"><span data-stu-id="c9568-103">The following examples show how to decode and encode a Graphics Interchange Format (GIF) image using the specific <xref:System.Windows.Media.Imaging.GifBitmapDecoder> and <xref:System.Windows.Media.Imaging.GifBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9568-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9568-104">Example</span></span>  
 <span data-ttu-id="c9568-105">W tym przykładzie pokazano, jak zdekodować obraz GIF przy <xref:System.Windows.Media.Imaging.GifBitmapDecoder> użyciu od <xref:System.IO.FileStream>a.</span><span class="sxs-lookup"><span data-stu-id="c9568-105">This example demonstrates how to decode a GIF image using a <xref:System.Windows.Media.Imaging.GifBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="c9568-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9568-106">Example</span></span>  
 <span data-ttu-id="c9568-107">Ten przykład ilustruje sposób kodowania <xref:System.Windows.Media.Imaging.BitmapSource> do obrazu GIF <xref:System.Windows.Media.Imaging.GifBitmapEncoder>przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="c9568-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a GIF image using a <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="c9568-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9568-108">See also</span></span>

- [<span data-ttu-id="c9568-109">Obrazowanie — przegląd</span><span class="sxs-lookup"><span data-stu-id="c9568-109">Imaging Overview</span></span>](imaging-overview.md)
