---
title: "Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej (animacja Matrix)"
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
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0c624b221c1e4c122728887a9d592a3275d8f8e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a>Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej (animacja Matrix)
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> i <xref:System.Windows.Media.MatrixTransform> obracania (Tabela przestawna) ścieżce geometryczne, zdefiniowane przez obiekt <xref:System.Windows.Media.PathGeometry> obiektu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu do animowania <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.MatrixTransform> Jest stosowana do przycisku i powoduje, że aby przesunąć wzdłuż ścieżki. Ponieważ <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwość jest ustawiona na `true`, prostokąt obraca wzdłuż tangens ścieżki.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Pełny przykład, zobacz [próbki animacji ścieżki](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Wersja kodu powyższego przykładu używane <xref:System.Windows.Media.Animation.Storyboard> do animowania <xref:System.Windows.Media.EllipseGeometry>, mimo że tylko jeden animacja została zastosowana. Prostsze dotyczą animacji jednej właściwości w kodzie jest użycie <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody. Na przykład zobacz [animowania właściwości bez Using scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Animacja — omówienie](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Ścieżka animacji — tematy porad](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [Ścieżka animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160028)
