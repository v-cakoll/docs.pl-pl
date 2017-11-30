---
title: "Jak utworzyć niestandardowy element panelu"
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
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7e7cca5b6f7a0d5085e70c4ab6ac33ff83b75217
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-panel-element"></a>Jak utworzyć niestandardowy element panelu
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak zastąpić domyślne zachowanie układu <xref:System.Windows.Controls.Panel> element i utworzyć niestandardowy układ elementów, które są pochodnymi <xref:System.Windows.Controls.Panel>.  
  
 W przykładzie zdefiniowano niestandardowe proste <xref:System.Windows.Controls.Panel> element o nazwie `PlotPanel`, który określa położenie elementów podrzędnych zgodnie z dwóch ustalony współrzędne x i y-. W tym przykładzie `x` i `y` są ustawione na `50`; w związku z tym wszystkie elementy podrzędne znajdują się w tej lokalizacji na x i y osi.  
  
 Aby wdrożyć niestandardowy <xref:System.Windows.Controls.Panel> zachowania, w przykładzie użyto <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody. Każda metoda zwraca <xref:System.Windows.Size> danych, które są niezbędne do umieszczenia i renderowania elementów podrzędnych.  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Panel>  
 [Omówienie paneli](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Tworzenie niestandardowych przykładu panelu zawijania zawartości](http://go.microsoft.com/fwlink/?LinkID=159979)
