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
ms.openlocfilehash: 71711c0392576930e97986078ec5926ff6ca9813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963014"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>Instrukcje: Animowanie właściwości bez użycia scenorysu
Ten przykład pokazuje jeden ze sposobów zastosowania animacji do właściwości bez użycia <xref:System.Windows.Media.Animation.Storyboard>.  
  
> [!NOTE]
> Ta funkcja nie jest dostępna w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]programie. Aby uzyskać informacje na temat animowania właściwości [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]w programie, zobacz [Animuj a Property przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Aby zastosować animację lokalną do właściwości, użyj <xref:System.Windows.UIElement.BeginAnimation%2A> metody. Ta metoda przyjmuje dwa parametry: a <xref:System.Windows.DependencyProperty> określa właściwość do animowania oraz animację, która ma zostać zastosowana do tej właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak animować szerokość i kolor <xref:System.Windows.Controls.Button>tła.  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 Istnieje wiele klas animacji w <xref:System.Windows.Media.Animation> przestrzeni nazw dla animowania różnych typów właściwości. Aby uzyskać więcej informacji na temat animowania właściwości, zobacz [Omówienie animacji](animation-overview.md). Aby uzyskać więcej informacji na temat właściwości zależności (typ właściwości, które są wyświetlane w tych przykładach) i ich funkcji, zobacz [Omówienie właściwości zależności](../advanced/dependency-properties-overview.md).  
  
 Istnieją inne sposoby animacji bez używania <xref:System.Windows.Media.Animation.Storyboard> obiektów; Aby uzyskać więcej informacji, zobacz [Omówienie technik animacji właściwości](property-animation-techniques-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Techniki animacji właściwości — przegląd](property-animation-techniques-overview.md)
- [Animacja — przegląd](animation-overview.md)
