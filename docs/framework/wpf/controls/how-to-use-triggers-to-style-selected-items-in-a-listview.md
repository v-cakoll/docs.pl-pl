---
title: 'Instrukcje: Użyj wyzwalaczy, aby nadać styl zaznaczonym elementom w ListView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
ms.openlocfilehash: 5229c8db70d7d1200c75c7cbefd497e62cf72bdd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682066"
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a>Instrukcje: Użyj wyzwalaczy, aby nadać styl zaznaczonym elementom w ListView
Ten przykład pokazuje jak zdefiniować <xref:System.Windows.Style.Triggers%2A> dla <xref:System.Windows.Controls.ListViewItem> kontroli, aby po wartości właściwości <xref:System.Windows.Controls.ListViewItem> zmian <xref:System.Windows.Style> z <xref:System.Windows.Controls.ListViewItem> zmianach w odpowiedzi.  
  
## <a name="example"></a>Przykład  
 Jeśli chcesz <xref:System.Windows.Style> z <xref:System.Windows.Controls.ListViewItem> zmiany w odpowiedzi na zmiany właściwości, zdefiniuj <xref:System.Windows.Style.Triggers%2A> dla <xref:System.Windows.Style> zmiany.  
  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.Trigger> określająca <xref:System.Windows.Controls.Control.Foreground%2A> właściwości <xref:System.Windows.Media.Brushes.Blue%2A> i zmienia <xref:System.Windows.FrameworkElement.Cursor%2A> do wyświetlenia <xref:System.Windows.Input.CursorType.Hand> podczas <xref:System.Windows.UIElement.IsMouseOver%2A> zmiany właściwości `true`.  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.MultiTrigger> określająca <xref:System.Windows.Controls.Control.Foreground%2A> właściwość <xref:System.Windows.Controls.ListViewItem> do <xref:System.Windows.Media.Brushes.Yellow%2A> podczas <xref:System.Windows.Controls.ListViewItem> wybranego elementu i ma fokus klawiatury.  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
- [ListView — omówienie](../../../../docs/framework/wpf/controls/listview-overview.md)
- [GridView — omówienie](../../../../docs/framework/wpf/controls/gridview-overview.md)
