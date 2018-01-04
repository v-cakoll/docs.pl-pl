---
title: "Jak animować Matrix z wykorzystaniem klatek kluczowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 862e1afdcd823181dff0948fab43b1656b85f721
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Jak animować Matrix z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość <xref:System.Windows.Media.MatrixTransform> przy użyciu klucza ramki.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> klasy do animowania <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość <xref:System.Windows.Media.MatrixTransform>. W przykładzie użyto <xref:System.Windows.Media.MatrixTransform> obiekt, aby przekształcić wyglądu i położenia <xref:System.Windows.Controls.Button>.  
  
 Używa tego animacji <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> klas do utworzenia dwóch ramek kluczowych i wykonuje następujące z nich:  
  
1.  Animuje pierwszy <xref:System.Windows.Media.Matrix> podczas pierwszego 0,2 sekundy. Przykład zmiany <xref:System.Windows.Media.Matrix.M11%2A> i <xref:System.Windows.Media.Matrix.M12%2A> właściwości <xref:System.Windows.Media.Matrix>. Ta zmiana powoduje, że przycisk, aby rozciągać i stać się niesymetryczna. W przykładzie również zmieniono <xref:System.Windows.Media.Matrix.OffsetX%2A> i <xref:System.Windows.Media.Matrix.OffsetY%2A> właściwości tak, aby przycisk zmienia pozycję.  
  
2.  Animuje drugi <xref:System.Windows.Media.Matrix> w sekundach 1.0. Przycisk przemieszczeniu na inne stanowisko, gdy przycisk jest już niesymetryczna lub rozciągnięty.  
  
3.  Powtarza animacji w nieskończoność.  
  
> [!NOTE]
>  Klucz ramek, które pochodzą z <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> obiekt tworzenie nagłym przechodzi między wartościami, przenoszenie animacji jest jerky.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>  
 <xref:System.Windows.Media.MatrixTransform>  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Klatki kluczowe — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
