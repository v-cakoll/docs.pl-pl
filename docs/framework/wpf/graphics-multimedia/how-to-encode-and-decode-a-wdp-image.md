---
title: Jak kodować i dekodować obraz WDP
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WDP encoding [WPF]
- WDP decoding [WPF]
- encoding image formats [WPF]
- decoding WDP images [WPF]
- decoding image formats [WPF]
- encoding WDP images [WPF]
ms.assetid: 911777d1-516b-49db-a87b-b54e31b18532
ms.openlocfilehash: 8c5c312c7e58d48a865e493c38c3defd3f5f3d1d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040776"
---
# <a name="how-to-encode-and-decode-a-wdp-image"></a>Jak kodować i dekodować obraz WDP
W poniższych przykładach pokazano, jak zdekodować i kodować obraz Microsoft Windows Media Photo przy użyciu określonych <xref:System.Windows.Media.Imaging.WmpBitmapDecoder> i <xref:System.Windows.Media.Imaging.WmpBitmapEncoder> obiektów.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak zdekodować obraz zdjęć Windows Media przy użyciu <xref:System.Windows.Media.Imaging.WmpBitmapDecoder> z <xref:System.Uri>.  
  
 [!code-cpp[WdpBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CPP/WDPEncoderDecoder.cpp#1)]
 [!code-csharp[WdpBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CSharp/WDPEncoderDecoder.cs#1)]
 [!code-vb[WdpBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/VB/WDPEncoderDecoder.vb#1)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak kodować <xref:System.Windows.Media.Imaging.BitmapSource> w obrazie zdjęć systemu Windows Media przy użyciu <xref:System.Windows.Media.Imaging.WmpBitmapEncoder>.  
  
 [!code-cpp[WdpBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CPP/WDPEncoderDecoder.cpp#4)]
 [!code-csharp[WdpBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CSharp/WDPEncoderDecoder.cs#4)]
 [!code-vb[WdpBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/VB/WDPEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Obrazowanie — przegląd](imaging-overview.md)
