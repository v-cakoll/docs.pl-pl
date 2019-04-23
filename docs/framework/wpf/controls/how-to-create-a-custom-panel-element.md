---
title: 'Instrukcje: Tworzenie niestandardowego elementu panelu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: d4fc9d76ada9f27bd52619280b323691af9382c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139571"
---
# <a name="how-to-create-a-custom-panel-element"></a>Instrukcje: Tworzenie niestandardowego elementu panelu
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak zastąpić domyślne zachowanie układu <xref:System.Windows.Controls.Panel> elementu i tworzenie elementów układu niestandardowego, które są uzyskiwane z <xref:System.Windows.Controls.Panel>.  
  
 W przykładzie zdefiniowano niestandardowe proste <xref:System.Windows.Controls.Panel> element o nazwie `PlotPanel`, który określa położenie elementów podrzędnych zgodnie z dwóch ustaloną współrzędnych x i y. W tym przykładzie `x` i `y` są ustawione na `50`; w związku z tym, wszystkie elementy podrzędne są umieszczane w tej lokalizacji na x i y osi.  
  
 Aby zaimplementować niestandardowy <xref:System.Windows.Controls.Panel> zachowań, w przykładzie użyto <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody. Każda metoda zwraca <xref:System.Windows.Size> danych, które są niezbędne do umieszczenia i renderowanie elementów podrzędnych.  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Panel>
- [Panele — omówienie](panels-overview.md)
- [Tworzenie niestandardowych przykładowej panelu zawijania zawartości](https://go.microsoft.com/fwlink/?LinkID=159979)
