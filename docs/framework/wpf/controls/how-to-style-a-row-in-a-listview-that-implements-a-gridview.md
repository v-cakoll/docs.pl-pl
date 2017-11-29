---
title: "Jak nadać styl wierszowi w ListView, który implementuje GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c51f6cc5c35200267aa84960655fd734a937a7c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Jak nadać styl wierszowi w ListView, który implementuje GridView
W tym przykładzie pokazano, jak do nadawania stylu wiersza w <xref:System.Windows.Controls.ListView> formant, który implementuje <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> tryb.  
  
## <a name="example"></a>Przykład  
 Styl możesz wiersza w <xref:System.Windows.Controls.ListView> kontroli przez ustawienie <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> na <xref:System.Windows.Controls.ListView> formantu. Ustawienie stylu dla jego elementów, które są reprezentowane jako <xref:System.Windows.Controls.ListViewItem> obiektów. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Odwołania <xref:System.Windows.Controls.ControlTemplate> obiektów, które są używane do wyświetlania zawartości wiersza.  
  
 Wyświetla całą próbkę następujące przykłady są wyodrębniane z, kolekcję utworu informacji przechowywanych w [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] bazy danych. Każdy utworu w bazie danych znajduje się pole klasyfikacji i wartość tego pola określa sposób wyświetlania wiersza utworu informacji.  
  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> dla <xref:System.Windows.Controls.ListViewItem> obiekty reprezentujące utworów muzycznych w kolekcji utworów. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Odwołania <xref:System.Windows.Controls.ControlTemplate> obiektów, które określają sposób wyświetlania wiersza utworu informacji.  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.ControlTemplate> dodaje ciąg tekstowy `"Strongly Recommended"` do wiersza. Ten szablon jest przywoływany w <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> i wyświetlany, gdy klasyfikacja utworu ma wartość 5 (pięć). <xref:System.Windows.Controls.ControlTemplate> Obejmuje <xref:System.Windows.Controls.GridViewRowPresenter> obiekt, który wychodzi poza zawartości wiersza w kolumnach, zgodnie z definicją <xref:System.Windows.Controls.GridView> trybu wyświetlania.  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.GridView>.  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Tematy porad](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView — omówienie](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Style i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
