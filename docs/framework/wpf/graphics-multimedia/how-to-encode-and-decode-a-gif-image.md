---
title: 'Instrukcje: Koduj i dekoduj obraz GIF'
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
ms.openlocfilehash: 9b13ac8021b6f2d25209a89ff2ff9b4bb7531ad3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562469"
---
# <a name="how-to-encode-and-decode-a-gif-image"></a><span data-ttu-id="d2f03-102">Instrukcje: Koduj i dekoduj obraz GIF</span><span class="sxs-lookup"><span data-stu-id="d2f03-102">How to: Encode and Decode a GIF Image</span></span>
<span data-ttu-id="d2f03-103">W poniższych przykładach pokazano, jak dekodowanie i kodowanie [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] obrazów przy użyciu określonego <xref:System.Windows.Media.Imaging.GifBitmapDecoder> i <xref:System.Windows.Media.Imaging.GifBitmapEncoder> obiektów.</span><span class="sxs-lookup"><span data-stu-id="d2f03-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] image using the specific <xref:System.Windows.Media.Imaging.GifBitmapDecoder> and <xref:System.Windows.Media.Imaging.GifBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2f03-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2f03-104">Example</span></span>  
 <span data-ttu-id="d2f03-105">W tym przykładzie pokazano, jak dekodowanie [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] obrazów przy użyciu <xref:System.Windows.Media.Imaging.GifBitmapDecoder> z <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="d2f03-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] image using a <xref:System.Windows.Media.Imaging.GifBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="d2f03-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2f03-106">Example</span></span>  
 <span data-ttu-id="d2f03-107">W tym przykładzie pokazano, jak kodować <xref:System.Windows.Media.Imaging.BitmapSource> do [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] obrazów przy użyciu <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="d2f03-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] image using a <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="d2f03-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2f03-108">See also</span></span>
- [<span data-ttu-id="d2f03-109">Obrazowanie — przegląd</span><span class="sxs-lookup"><span data-stu-id="d2f03-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
