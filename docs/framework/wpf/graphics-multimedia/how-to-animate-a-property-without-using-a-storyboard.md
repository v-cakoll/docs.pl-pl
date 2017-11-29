---
title: "Jak animować właściwości bez użycia scenorysu"
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
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cfc1de83c6c91e7a42c09b080b647aaf440e5a61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>Jak animować właściwości bez użycia scenorysu
W tym przykładzie przedstawiono jeden sposób zastosowania animacji do właściwości bez użycia <xref:System.Windows.Media.Animation.Storyboard>.  
  
> [!NOTE]
>  Ta funkcja nie jest dostępna w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Informacje o animowania właściwości w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zobacz [animować właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Aby zastosować animacji lokalnego do właściwości, należy użyć <xref:System.Windows.UIElement.BeginAnimation%2A> metody. Ta metoda przyjmuje dwa parametry: <xref:System.Windows.DependencyProperty> , który określa właściwość animacji i animacji do zastosowania do tej właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób animować kolor tła i szerokość <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 Różne klasy animacji w <xref:System.Windows.Media.Animation> przestrzeni nazw istnieją różne typy właściwości animacji. Aby uzyskać więcej informacji na temat właściwości animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Aby uzyskać więcej informacji na temat właściwości zależności (typ właściwości, które są wyświetlane w tym przykładzie) i ich funkcje, zobacz [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 Istnieją inne sposoby animować bez użycia <xref:System.Windows.Media.Animation.Storyboard> obiektów; Aby uzyskać więcej informacji, zobacz [— Przegląd właściwości animacji techniki](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.AnimationTimeline>  
 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [Omówienie techniki animacji właściwość](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Animacja — omówienie](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
