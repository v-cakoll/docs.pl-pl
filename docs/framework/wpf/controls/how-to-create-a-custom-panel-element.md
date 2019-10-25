---
title: Jak utworzyć niestandardowy element panelu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 31edc75114c5dad613e5b65e7d8b051e2c3713af
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799146"
---
# <a name="how-to-create-a-custom-panel-element"></a>Jak utworzyć niestandardowy element panelu
## <a name="example"></a>Przykład  
 Ten przykład pokazuje, jak zastąpić domyślne zachowanie układu elementu <xref:System.Windows.Controls.Panel> i utworzyć niestandardowe elementy układu, które pochodzą z <xref:System.Windows.Controls.Panel>.  
  
 W przykładzie zdefiniowano prosty niestandardowy element <xref:System.Windows.Controls.Panel> o nazwie `PlotPanel`, który umieszcza elementy podrzędne w zależności od dwóch sztywnie zakodowanych współrzędnych x i y. W tym przykładzie `x` i `y` są ustawione na `50`; w związku z tym wszystkie elementy podrzędne są umieszczane w tej lokalizacji na osiach x i y.  
  
 W celu zaimplementowania niestandardowych zachowań <xref:System.Windows.Controls.Panel> w przykładzie stosowane są metody <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>. Każda metoda zwraca <xref:System.Windows.Size> dane, które są niezbędne do pozycjonowania i renderowania elementów podrzędnych.  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Panel>
- [Panele — omówienie](panels-overview.md)
