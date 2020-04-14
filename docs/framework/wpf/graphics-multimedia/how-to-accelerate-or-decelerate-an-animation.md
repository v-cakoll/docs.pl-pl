---
title: Jak przyspieszyć lub zwolnić animację
ms.date: 03/30/2017
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
ms.openlocfilehash: 7ab55ba44b866a992b9021284f170858f0108d15
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243014"
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a>Jak: Przyspieszenie lub spowolnienie animacji

W tym przykładzie pokazano, jak sprawić, by animacja przyspieszyła i spowolniła wraz z czasem. W poniższym przykładzie kilka prostokątów są animowane <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> przez animacje z różnych i ustawień.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[timingbehaviors_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 Kod został pominięty w tym przykładzie. Aby uzyskać pełny kod, zobacz [zachowanie chronometrażu animacji (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp) lub [Zachowanie chronometrażu animacji (Visual Basic).](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic)
