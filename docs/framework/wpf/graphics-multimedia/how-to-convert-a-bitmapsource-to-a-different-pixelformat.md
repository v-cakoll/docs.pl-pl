---
title: "Jak konwertować BitmapSource na inny PixelFormat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BitmapSource objects [WPF], converting to indexed pixel format
- converting images [WPF]
- converting [WPF], BitmapSource objects to indexed pixel formats
- converting [WPF], BitmapSource objects to palettized pixel format
- BitmapSource objects [WPF], converting to palettized pixel format
ms.assetid: cd9df1e4-d5dc-4f57-b67b-4ec67e086b33
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 00c6b05adf92800b2f2c7119bb44cec109765727
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-convert-a-bitmapsource-to-a-different-pixelformat"></a>Jak konwertować BitmapSource na inny PixelFormat
W tym przykładzie pokazano, jak przekonwertować <xref:System.Windows.Media.Imaging.BitmapSource> obiektu (<xref:System.Windows.Media.Imaging.BitmapImage>) z innym <xref:System.Windows.Media.PixelFormat> przy użyciu <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#PixelFormatConversion](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/PixelFormatsExample.cs#pixelformatconversion)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#PixelFormatConversion](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/PixelFormatsExample.vb#pixelformatconversion)]  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie tworzenia obrazu](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
