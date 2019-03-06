---
title: 'Instrukcje: Koduj i dekoduj obraz PNG'
ms.date: 03/30/2017
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
ms.openlocfilehash: 132ccc2fca4b1b3984c88f1e75d3fd1934d8bf24
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358096"
---
# <a name="how-to-encode-and-decode-a-png-image"></a><span data-ttu-id="8402d-102">Instrukcje: Koduj i dekoduj obraz PNG</span><span class="sxs-lookup"><span data-stu-id="8402d-102">How to: Encode and Decode a PNG Image</span></span>
<span data-ttu-id="8402d-103">W poniższych przykładach pokazano, jak dekodowanie i kodowanie [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] obrazów przy użyciu określonego <xref:System.Windows.Media.Imaging.PngBitmapDecoder> i <xref:System.Windows.Media.Imaging.PngBitmapEncoder> obiektów.</span><span class="sxs-lookup"><span data-stu-id="8402d-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] image using the specific <xref:System.Windows.Media.Imaging.PngBitmapDecoder> and <xref:System.Windows.Media.Imaging.PngBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8402d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8402d-104">Example</span></span>  
 <span data-ttu-id="8402d-105">W tym przykładzie pokazano, jak dekodowanie [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] obrazów przy użyciu <xref:System.Windows.Media.Imaging.PngBitmapDecoder> z <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="8402d-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image using a <xref:System.Windows.Media.Imaging.PngBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#1)]
 [!code-csharp[PngBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#1)]
 [!code-vb[PngBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="8402d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="8402d-106">Example</span></span>  
 <span data-ttu-id="8402d-107">W tym przykładzie pokazano, jak kodować <xref:System.Windows.Media.Imaging.BitmapSource> do [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] obrazów przy użyciu <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="8402d-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image using a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#4)]
 [!code-csharp[PngBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#4)]
 [!code-vb[PngBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="8402d-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8402d-108">See also</span></span>
- [<span data-ttu-id="8402d-109">Obrazowanie — przegląd</span><span class="sxs-lookup"><span data-stu-id="8402d-109">Imaging Overview</span></span>](imaging-overview.md)
