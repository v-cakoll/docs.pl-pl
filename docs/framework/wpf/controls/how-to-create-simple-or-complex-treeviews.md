---
title: Jak utworzyć proste lub złożone TreeViews
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
ms.openlocfilehash: 54e9218ea1460a0c29d8b9d7b9c740c18ac7ab24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-simple-or-complex-treeviews"></a>Jak utworzyć proste lub złożone TreeViews
W tym przykładzie przedstawiono sposób tworzenia prostego lub złożonych <xref:System.Windows.Controls.TreeView> kontrolki.  
  
 A <xref:System.Windows.Controls.TreeView> składa się z hierarchii <xref:System.Windows.Controls.TreeViewItem> formanty, które może zawierać ciągów tekstowych proste i również w przypadku bardziej złożonych zawartości, takich jak <xref:System.Windows.Controls.Button> formanty lub <xref:System.Windows.Controls.StackPanel> z osadzoną zawartość. Można jawnie definiować <xref:System.Windows.Controls.TreeView> zawartości ani źródła danych można udostępnić zawartość. W tym temacie przedstawiono przykłady te pojęcia.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> Właściwość <xref:System.Windows.Controls.TreeViewItem> z zawartością który <xref:System.Windows.Controls.TreeView> wyświetla tego elementu. A <xref:System.Windows.Controls.TreeViewItem> ma także <xref:System.Windows.Controls.TreeViewItem> formanty jako jego elementy podrzędne, a można zdefiniować te elementy podrzędne za pomocą <xref:System.Windows.Controls.ItemsControl.Items%2A> właściwości.  
  
 Poniższy przykład przedstawia sposób jawnie definiować <xref:System.Windows.Controls.TreeViewItem> zawartości przez ustawienie <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> właściwości na ciąg tekstowy.  
  
 [!code-xaml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 Poniższym przykładzie pokazano, jak zdefiniować elementy podrzędne <xref:System.Windows.Controls.TreeViewItem> , definiując <xref:System.Windows.Controls.ItemsControl.Items%2A> , które są <xref:System.Windows.Controls.Button> kontrolki.  
  
 [!code-xaml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Controls.TreeView> gdzie <xref:System.Windows.Data.XmlDataProvider> zapewnia <xref:System.Windows.Controls.TreeViewItem> zawartości i <xref:System.Windows.HierarchicalDataTemplate> definiuje wygląd elementów zawartości.  
  
 [!code-xaml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Controls.TreeView> gdzie <xref:System.Windows.Controls.TreeViewItem> zawartość zawiera <xref:System.Windows.Controls.DockPanel> formantów, które zostały osadzone zawartości.  
  
 [!code-xaml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [TreeView — omówienie](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
