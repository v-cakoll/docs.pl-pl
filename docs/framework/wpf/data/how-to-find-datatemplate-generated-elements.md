---
title: "Porady: znajdowanie elementów generowanych przez DataTemplate"
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
helpviewer_keywords:
- finding DataTemplate elements [WPF]
- DataTemplate [WPF]
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 22d5f393d376935f04459e2713e9658c80af6efa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-datatemplate-generated-elements"></a>Porady: znajdowanie elementów generowanych przez DataTemplate
W tym przykładzie pokazano, jak znaleźć elementy, które są generowane przez <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest <xref:System.Windows.Controls.ListBox> który jest powiązany z niektórymi [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych:  
  
 [!code-xaml[FindGeneratedItems#LB](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 <xref:System.Windows.Controls.ListBox> Są używane następujące <xref:System.Windows.DataTemplate>:  
  
 [!code-xaml[FindGeneratedItems#DT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Jeśli chcesz pobrać <xref:System.Windows.Controls.TextBlock> wygenerowanych przez element <xref:System.Windows.DataTemplate> pewnego <xref:System.Windows.Controls.ListBoxItem>, należy uzyskać <xref:System.Windows.Controls.ListBoxItem>, Znajdź <xref:System.Windows.Controls.ContentPresenter> w tym <xref:System.Windows.Controls.ListBoxItem>, a następnie wywołać <xref:System.Windows.FrameworkTemplate.FindName%2A> na <xref:System.Windows.DataTemplate> na które ustawiono <xref:System.Windows.Controls.ContentPresenter>. Poniższy przykład przedstawia sposób wykonywania tych kroków. Dla celów demonstracyjnych, w tym przykładzie tworzy komunikat, który zawiera tekst zawartości <xref:System.Windows.DataTemplate>-generowane bloku tekstu.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 Poniżej przedstawiono wykonania `FindVisualChild`, który korzysta z <xref:System.Windows.Media.VisualTreeHelper> metod:  
  
 [!code-csharp[FindGeneratedItems#FVC](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: znajdowanie elementy wygenerowane ControlTemplate](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)  
 [Omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Style i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Namescopes WPF XAML](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)  
 [Drzewa na platformie WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
