---
title: 'Instrukcje: Utwórz niestandardowy element panelu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 93d9ebacda8c753ab5a4446999e1aa86828a2b9e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621935"
---
# <a name="how-to-create-a-custom-panel-element"></a>Instrukcje: Utwórz niestandardowy element panelu
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak zastąpić domyślne zachowanie układu <xref:System.Windows.Controls.Panel> elementu i tworzenie elementów układu niestandardowego, które są uzyskiwane z <xref:System.Windows.Controls.Panel>.  
  
 W przykładzie zdefiniowano niestandardowe proste <xref:System.Windows.Controls.Panel> element o nazwie `PlotPanel`, który określa położenie elementów podrzędnych zgodnie z dwóch ustaloną współrzędnych x i y. W tym przykładzie `x` i `y` są ustawione na `50`; w związku z tym, wszystkie elementy podrzędne są umieszczane w tej lokalizacji na x i y osi.  
  
 Aby zaimplementować niestandardowy <xref:System.Windows.Controls.Panel> zachowań, w przykładzie użyto <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody. Każda metoda zwraca <xref:System.Windows.Size> danych, które są niezbędne do umieszczenia i renderowanie elementów podrzędnych.  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.Panel>
- [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Tworzenie niestandardowych przykładowej panelu zawijania zawartości](https://go.microsoft.com/fwlink/?LinkID=159979)
