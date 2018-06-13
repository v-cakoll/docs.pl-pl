---
title: Jak przyciąć obraz
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], cropping
- cropping images [WPF]
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
ms.openlocfilehash: 46c559356447688e52508b823cc260c13128208f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553809"
---
# <a name="how-to-crop-an-image"></a>Jak przyciąć obraz
W tym przykładzie pokazano, jak Przytnij obraz przy użyciu <xref:System.Windows.Media.Imaging.CroppedBitmap>.  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap> jest używany głównie podczas kodowania przyciętą wersję obrazu do zapisywane w pliku. Aby przyciąć obraz do wyświetlania celów zobacz [utworzyć obszar przycinania](http://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376) tematu.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] definiuje zasoby używane w ramach przykłady poniżej.  
  
 [!code-xaml[imageelementexample#CroppedXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 Poniższy przykład tworzy obraz przy użyciu <xref:System.Windows.Media.Imaging.CroppedBitmap> jako źródło.  
  
 [!code-xaml[imageelementexample#CroppedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap> Może również służyć jako źródła innego <xref:System.Windows.Media.Imaging.CroppedBitmap>, łańcucha przycinania. Należy pamiętać, że <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> używa wartości, które są względem źródła przycięte mapy bitowej i obraz początkowy.  
  
 [!code-xaml[imageelementexample#CroppedXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Utwórz obszar przycinania](http://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376)
