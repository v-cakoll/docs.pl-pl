---
title: Jak utworzyć niestandardowy tryb widoku dla ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: b8600a2e201fdbcb566e6a322e3ecdabbe1641ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>Jak utworzyć niestandardowy tryb widoku dla ListView
W tym przykładzie przedstawiono sposób tworzenia niestandardowego <xref:System.Windows.Controls.ListView.View%2A> tryb <xref:System.Windows.Controls.ListView> formantu.  
  
## <a name="example"></a>Przykład  
 Należy użyć <xref:System.Windows.Controls.ViewBase> klasy utworzenie widoku niestandardowego służącego do <xref:System.Windows.Controls.ListView> formantu. W poniższym przykładzie przedstawiono sposób wyświetlania, które jest wywoływane w `PlainView`, która jest pochodną <xref:System.Windows.Controls.ViewBase> klasy.  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 Aby zastosować styl widok niestandardowy, należy użyć <xref:System.Windows.Style> klasy. W poniższym przykładzie zdefiniowano <xref:System.Windows.Style> dla `PlainView` trybu wyświetlania. W poprzednim przykładzie ten styl jest ustawiony jako wartość <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> właściwość, która jest zdefiniowana dla `PlainView`.  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 Aby zdefiniować układ danych w trybie Widok niestandardowy, należy zdefiniować <xref:System.Windows.DataTemplate> obiektu. W poniższym przykładzie zdefiniowano <xref:System.Windows.DataTemplate> można wyświetlić dane w `PlainView` trybu wyświetlania.  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.ResourceKey> dla `PlainView` trybu wyświetlania, która używa <xref:System.Windows.DataTemplate> zdefiniowanego w poprzednim przykładzie.  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 A <xref:System.Windows.Controls.ListView> kontroli służy widok niestandardowy, jeśli ustawisz <xref:System.Windows.Controls.ListView.View%2A> klucz zasobu dla właściwości. Poniższy przykład przedstawia sposób określić `PlainView` jako tryb widoku <xref:System.Windows.Controls.ListView>.  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 Pełny przykład, zobacz [element ListView z wielu widoków próbki](http://go.microsoft.com/fwlink/?LinkID=160013).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView — omówienie](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView — omówienie](../../../../docs/framework/wpf/controls/gridview-overview.md)
