---
title: 'Instrukcje: Tworzenie prostej lub złożonej kontrolki TreeView'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
ms.openlocfilehash: 7edb4933ebcc0f0d2cb02754238c2342ee9dd4a2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205150"
---
# <a name="how-to-create-simple-or-complex-treeviews"></a>Instrukcje: Tworzenie prostej lub złożonej kontrolki TreeView
W tym przykładzie pokazano, jak utworzyć proste lub złożone <xref:System.Windows.Controls.TreeView> kontrolki.  
  
 A <xref:System.Windows.Controls.TreeView> składa się z hierarchią <xref:System.Windows.Controls.TreeViewItem> formanty, które mogą zawierać ciągi zwykły tekst i również bardziej złożonych zawartości, takie jak <xref:System.Windows.Controls.Button> kontrolki lub <xref:System.Windows.Controls.StackPanel> przy użyciu osadzonej zawartości. Można jawnie określić <xref:System.Windows.Controls.TreeView> zawartości lub źródło danych może zapewnić zawartości. Ten temat zawiera przykłady tych koncepcji.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> Właściwość <xref:System.Windows.Controls.TreeViewItem> z zawartością, <xref:System.Windows.Controls.TreeView> wyświetla dla tego elementu. A <xref:System.Windows.Controls.TreeViewItem> może także zawierać <xref:System.Windows.Controls.TreeViewItem> służy jako jego elementy podrzędne i można zdefiniować te elementy podrzędne przy użyciu <xref:System.Windows.Controls.ItemsControl.Items%2A> właściwości.  
  
 Poniższy przykład pokazuje, jak jawne zdefiniowanie <xref:System.Windows.Controls.TreeViewItem> zawartości, ustawiając <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> właściwość ciągu tekstowego.  
  
 [!code-xaml[TreeViewSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 Poniższy przykład pokazują, jak zdefiniować elementy podrzędne <xref:System.Windows.Controls.TreeViewItem> , definiując <xref:System.Windows.Controls.ItemsControl.Items%2A> , które są <xref:System.Windows.Controls.Button> kontrolki.  
  
 [!code-xaml[TreeViewSimple#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Controls.TreeView> gdzie <xref:System.Windows.Data.XmlDataProvider> zapewnia <xref:System.Windows.Controls.TreeViewItem> zawartości i <xref:System.Windows.HierarchicalDataTemplate> definiuje wygląd elementów zawartości.  
  
 [!code-xaml[TreeViewSimple#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Controls.TreeView> gdzie <xref:System.Windows.Controls.TreeViewItem> zawartość zawiera <xref:System.Windows.Controls.DockPanel> formantów, które zostały osadzone zawartości.  
  
 [!code-xaml[TreeViewSimple#9](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [TreeView — Przegląd](treeview-overview.md)
- [— Tematy porad](treeview-how-to-topics.md)
