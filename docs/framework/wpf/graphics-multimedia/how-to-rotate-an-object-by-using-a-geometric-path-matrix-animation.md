---
title: Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej (animacja Matrix)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 63dc873a2b840ea3f870a8c60c5691ab271c1c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187412"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a>Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej (animacja Matrix)
W tym przykładzie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> pokazano, <xref:System.Windows.Media.MatrixTransform> jak za pomocą a i a obracać <xref:System.Windows.Media.PathGeometry> (przestawiać) obiekt wzdłuż ścieżki geometrycznej zdefiniowanej przez obiekt.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> użyto <xref:System.Windows.Media.MatrixTransform.Matrix%2A> obiektu do <xref:System.Windows.Media.MatrixTransform>animowania właściwości programu . Jest <xref:System.Windows.Media.MatrixTransform> stosowany do przycisku i powoduje, że porusza się po zakrzywionej ścieżce. Ponieważ <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwość jest `true`ustawiona na , prostokąt obraca się wzdłuż stycznej ścieżki.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład animacji ścieżki](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 Wersja kodu poprzedniego przykładu używane <xref:System.Windows.Media.Animation.Storyboard> do animowania <xref:System.Windows.Media.EllipseGeometry>, mimo że zastosowano tylko jedną animację. Łatwiejszym sposobem zastosowania pojedynczej animacji do właściwości w <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> kodzie jest użycie metody. Na przykład zobacz [Animowanie właściwości bez użycia scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd Animacja](animation-overview.md)
- [Animacja ścieżki — tematy z instrukcjami](path-animation-how-to-topics.md)
- [Przykład animacji ścieżki](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
