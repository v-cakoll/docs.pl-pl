---
title: "Jak użyć szablonów do stylu ListView która korzysta z GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 246c144a18d7c1014096a6e37ad09b6eec5ad932
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a>Jak użyć szablonów do stylu ListView która korzysta z GridView
Ten przykład przedstawia sposób użycia <xref:System.Windows.DataTemplate> i <xref:System.Windows.Style> obiektów, aby określić wygląd <xref:System.Windows.Controls.ListView> formant, który używa <xref:System.Windows.Controls.GridView> trybu wyświetlania.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano <xref:System.Windows.Style> i <xref:System.Windows.DataTemplate> obiektów, które dostosowanie wyglądu nagłówek kolumny dla <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 Poniższy przykład przedstawia użycie tych <xref:System.Windows.Style> i <xref:System.Windows.DataTemplate> obiektów, aby ustawić <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> i <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> właściwości <xref:System.Windows.Controls.GridViewColumn>. <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Właściwość definiuje zawartość komórki kolumny.  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> i <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> są tylko dwóch kilka właściwości, które można dostosować wygląd nagłówka kolumny <xref:System.Windows.Controls.GridView> formantu. Aby uzyskać więcej informacji, zobacz [Omówienie szablonów i style nagłówka kolumny w widoku GridView](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).  
  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.DataTemplate> który dostosowuje wygląd komórek w <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 Poniższy przykład przedstawia sposób użycia to <xref:System.Windows.DataTemplate> do definiowania zawartość <xref:System.Windows.Controls.GridViewColumn> komórki. Ten szablon jest używany zamiast <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> właściwość, która jest wyświetlana w poprzedniej <xref:System.Windows.Controls.GridViewColumn> przykład.  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Omówienie widoku GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView — omówienie](../../../../docs/framework/wpf/controls/listview-overview.md)
