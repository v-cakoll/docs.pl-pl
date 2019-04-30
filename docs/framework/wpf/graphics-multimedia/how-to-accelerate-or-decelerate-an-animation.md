---
title: 'Instrukcje: Przyspieszanie lub zwalnianie animacji'
ms.date: 03/30/2017
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
ms.openlocfilehash: d4fcaf4a684c37590f27d603ef5cb2c86a6fb854
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762166"
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a>Instrukcje: Przyspieszanie lub zwalnianie animacji
W tym przykładzie pokazano, jak utworzyć animację, Przyspiesz i zwalnianie wraz z upływem czasu. W poniższym przykładzie animowanych przez animacje przy użyciu różnych prostokątów kilka <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> i <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> ustawienia.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[timingbehaviors_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 W tym przykładzie została pominięta kodu. Aby uzyskać kompletny kod, zobacz [zachowania chronometrażu animacji (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp) lub [zachowania chronometrażu animacji (Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic).
