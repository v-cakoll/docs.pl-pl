---
title: "Jak upewnić się, że GridSplitter jest widoczny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8692d356b1b20c7405b4478cef1d16c173389ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a>Jak upewnić się, że GridSplitter jest widoczny
W tym przykładzie pokazano, jak upewnij się, że <xref:System.Windows.Controls.GridSplitter> formantu nie jest ukryty przez inne formanty w <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.Panel.Children%2A> z <xref:System.Windows.Controls.Grid> formantu są renderowane w kolejności, że są one zdefiniowane w znaczników lub kodu. <xref:System.Windows.Controls.GridSplitter>Formanty można ukryć przez inne formanty, jeśli nie definiują jako ostatni elementów w <xref:System.Windows.Controls.Panel.Children%2A> kolekcji lub jeśli musisz podać inne formanty wyższej <xref:System.Windows.Controls.Panel.ZIndexProperty>.  
  
 Aby zapobiec ukryte <xref:System.Windows.Controls.GridSplitter> formantów, wykonaj jedną z następujących czynności.  
  
-   Upewnij się, że <xref:System.Windows.Controls.GridSplitter> kontrolki są ostatniego <xref:System.Windows.Controls.Panel.Children%2A> dodane do <xref:System.Windows.Controls.Grid>. W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.GridSplitter> jako ostatni element <xref:System.Windows.Controls.Panel.Children%2A> kolekcji <xref:System.Windows.Controls.Grid>.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   Ustaw <xref:System.Windows.Controls.Panel.ZIndexProperty> na <xref:System.Windows.Controls.GridSplitter> wyższe niż kontroli, które w przeciwnym razie spowoduje ukrycie. Poniższy przykład zawiera <xref:System.Windows.Controls.GridSplitter> kontrolować wyższej <xref:System.Windows.Controls.Panel.ZIndexProperty> niż <xref:System.Windows.Controls.Button> formantu.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   Ustaw marginesy w formancie, które w przeciwnym razie spowoduje ukrycie <xref:System.Windows.Controls.GridSplitter> , aby <xref:System.Windows.Controls.GridSplitter> jest widoczna. Poniższy przykład przedstawia marginesy na formant, który będzie w przeciwnym razie nakładki i Ukryj <xref:System.Windows.Controls.GridSplitter>.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.GridSplitter>  
 [Tematy porad](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
