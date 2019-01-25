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
ms.openlocfilehash: db42411f71e2934f3e5f86a06f434da220f1882e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603511"
---
# <a name="how-to-encode-and-decode-a-jpeg-image"></a>Instrukcje: Koduj i dekoduj obraz JPEG

W poniższych przykładach pokazano, jak dekodowanie i kodowanie przy użyciu określonego obrazu JPEG <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> i <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> obiektów.  
  
## <a name="example---decode-a-jpeg-image"></a>Przykład — dekodowanie obrazu JPEG

W tym przykładzie pokazano, jak dekodowanie obrazu JPEG przy użyciu <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> z <xref:System.IO.FileStream>.  
  
[!code-cpp[JpegBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
[!code-csharp[JpegBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
[!code-vb[JpegBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## <a name="example---encode-a-jpeg-image"></a>Przykład — kodowanie obrazów JPEG

W tym przykładzie pokazano, jak kodować <xref:System.Windows.Media.Imaging.BitmapSource> na format JPEG, image, za pomocą <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.  
  
[!code-cpp[JpegBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
[!code-csharp[JpegBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
[!code-vb[JpegBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Obrazowanie — przegląd](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
