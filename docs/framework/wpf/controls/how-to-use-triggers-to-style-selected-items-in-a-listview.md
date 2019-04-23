---
title: 'Instrukcje: Używanie wyzwalaczy do nadawania stylu wybranym elementom w kontrolce ListView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
ms.openlocfilehash: ad64382b871bae9114a1e63257de3f8595376923
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145408"
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a>Instrukcje: Używanie wyzwalaczy do nadawania stylu wybranym elementom w kontrolce ListView
Ten przykład pokazuje jak zdefiniować <xref:System.Windows.Style.Triggers%2A> dla <xref:System.Windows.Controls.ListViewItem> kontroli, aby po wartości właściwości <xref:System.Windows.Controls.ListViewItem> zmian <xref:System.Windows.Style> z <xref:System.Windows.Controls.ListViewItem> zmianach w odpowiedzi.  
  
## <a name="example"></a>Przykład  
 Jeśli chcesz <xref:System.Windows.Style> z <xref:System.Windows.Controls.ListViewItem> zmiany w odpowiedzi na zmiany właściwości, zdefiniuj <xref:System.Windows.Style.Triggers%2A> dla <xref:System.Windows.Style> zmiany.  
  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.Trigger> określająca <xref:System.Windows.Controls.Control.Foreground%2A> właściwości <xref:System.Windows.Media.Brushes.Blue%2A> i zmienia <xref:System.Windows.FrameworkElement.Cursor%2A> do wyświetlenia <xref:System.Windows.Input.CursorType.Hand> podczas <xref:System.Windows.UIElement.IsMouseOver%2A> zmiany właściwości `true`.  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.MultiTrigger> określająca <xref:System.Windows.Controls.Control.Foreground%2A> właściwość <xref:System.Windows.Controls.ListViewItem> do <xref:System.Windows.Media.Brushes.Yellow%2A> podczas <xref:System.Windows.Controls.ListViewItem> wybranego elementu i ma fokus klawiatury.  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Tematy z instrukcjami](listview-how-to-topics.md)
- [ListView — omówienie](listview-overview.md)
- [GridView — omówienie](gridview-overview.md)
