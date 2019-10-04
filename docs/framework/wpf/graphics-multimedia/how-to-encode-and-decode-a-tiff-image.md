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
# <a name="how-to-encode-and-decode-a-tiff-image"></a>Instrukcje: kodowanie i dekodowanie obrazu TIFF
W poniższych przykładach pokazano, jak zdekodować i kodować obraz Tagged Image File Format (TIFF) przy użyciu określonych <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> i <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> obiektów.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak zdekodować obraz TIFF przy użyciu <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> z <xref:System.Uri>.  
  
 [!code-cpp[TiffBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#1)]
 [!code-csharp[TiffBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#1)]
 [!code-vb[TiffBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#1)]  
  
## <a name="example"></a>Przykład  
 Ten przykład ilustruje sposób kodowania <xref:System.Windows.Media.Imaging.BitmapSource> do obrazu TIFF przy użyciu <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.  
  
 [!code-cpp[TiffBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#4)]
 [!code-csharp[TiffBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#4)]
 [!code-vb[TiffBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd obrazu](imaging-overview.md)
