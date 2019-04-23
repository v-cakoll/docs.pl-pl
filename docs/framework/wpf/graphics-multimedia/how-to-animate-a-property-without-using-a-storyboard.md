---
title: 'Instrukcje: Animowanie właściwości bez użycia scenorysu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
ms.openlocfilehash: 93609cdeb4d879cbec0f90096e4fa2c131a2ec5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091710"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>Instrukcje: Animowanie właściwości bez użycia scenorysu
Ten przykład przedstawia sposób zastosowania animacji właściwości bez użycia <xref:System.Windows.Media.Animation.Storyboard>.  
  
> [!NOTE]
>  Ta funkcja nie jest dostępna w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Aby uzyskać informacje na temat Animowanie właściwości w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zobacz [animować właściwość przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Aby zastosować lokalna Animacja na właściwość, należy użyć <xref:System.Windows.UIElement.BeginAnimation%2A> metody. Ta metoda przyjmuje dwa parametry: <xref:System.Windows.DependencyProperty> , który określa właściwość, animować i animacji, aby zastosować do tej właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak animować kolor tła i szerokość <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 Różne klasy animacji w <xref:System.Windows.Media.Animation> przestrzeń nazw istnieje animowania różnego rodzaju właściwości. Aby uzyskać więcej informacji na temat Animowanie właściwości, zobacz [Przegląd animacja](animation-overview.md). Aby uzyskać więcej informacji na temat właściwości zależności (typ właściwości, które są wyświetlane w tych przykładach) i ich funkcji, zobacz [Przegląd właściwości zależności](../advanced/dependency-properties-overview.md).  
  
 Istnieją inne sposoby, aby animować bez użycia <xref:System.Windows.Media.Animation.Storyboard> obiektów; Aby uzyskać więcej informacji, zobacz [Przegląd techniki animacji właściwości](property-animation-techniques-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Techniki animacji właściwości — przegląd](property-animation-techniques-overview.md)
- [Animacja — przegląd](animation-overview.md)
