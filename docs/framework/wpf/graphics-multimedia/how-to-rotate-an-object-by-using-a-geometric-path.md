---
title: "Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej"
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
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e4963d174f889ac51087356b042bc5b06990593
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej
W tym przykładzie pokazano, jak Obróć (Tabela przestawna) obiektu wzdłuż ścieżki geometryczne, która jest definiowana za pomocą <xref:System.Windows.Media.PathGeometry> obiektu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto trzy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> obiektów, które można przesuwać ścieżce geometrycznej.  
  
-   Pierwszy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.RotateTransform> do prostokąta zastosowano. Animacja generuje wartości kąta. Powoduje to dodanie prostokąta Obróć (Tabela przestawna) wzdłuż konturów ścieżki.  
  
-   Dwa obiekty animować <xref:System.Windows.Media.TranslateTransform.X%2A> i <xref:System.Windows.Media.TranslateTransform.Y%2A> wartości <xref:System.Windows.Media.TranslateTransform> do prostokąta zastosowano. Finalizowania prostokąt Przenieś poziomie i w pionie na ścieżce.  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 Obracanie obiektu przy użyciu ścieżki geometrycznych na innym sposobem jest użycie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu i ustawić jej <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwości `true`. Aby uzyskać więcej informacji i przykład zobacz [Obracanie obiektu przy użyciu ścieżki geometrycznych (macierzy Animacja)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).  
  
 Pełny przykład, zobacz [próbki animacji ścieżki](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
## <a name="see-also"></a>Zobacz też  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Ścieżka animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [Animacja ścieżki — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
