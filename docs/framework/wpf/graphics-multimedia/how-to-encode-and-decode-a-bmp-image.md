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
ms.openlocfilehash: 7d3520a1b1913fe68fedb0ea9d76cc138ed661c4
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331732"
---
# <a name="how-to-encode-and-decode-a-bmp-image"></a>Instrukcje: Kodowanie i dekodowanie obrazu BMP
W poniższych przykładach pokazano, jak zdekodować i kodować mapę bitową (BMP) przy <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> użyciu <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> określonych obiektów i.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak zdekodować obraz BMP przy <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> użyciu od <xref:System.Uri>a.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
## <a name="example"></a>Przykład  
 Ten przykład ilustruje sposób kodowania <xref:System.Windows.Media.Imaging.BitmapSource> do obrazu BMP <xref:System.Windows.Media.Imaging.BmpBitmapEncoder>przy użyciu.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#4)]
 [!code-csharp[BmpBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#4)]
 [!code-vb[BmpBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Obrazowanie — przegląd](imaging-overview.md)
