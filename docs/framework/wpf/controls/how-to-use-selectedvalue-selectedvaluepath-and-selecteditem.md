---
title: Jak użyć SelectedValue, SelectedValuePath i SelectedItem
description: Dowiedz się, jak użyć właściwości SelectedValue i SelectedValuePath, aby określić wartość dla SelectedItem Windows Presentation Foundation TreeView.
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
ms.openlocfilehash: ddac2455dee0bf69d25307340eddd5364e43e823
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166279"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>Jak użyć SelectedValue, SelectedValuePath i SelectedItem
Ten przykład pokazuje, jak użyć <xref:System.Windows.Controls.TreeView.SelectedValue%2A> właściwości i, <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Aby określić wartość dla <xref:System.Windows.Controls.TreeView.SelectedItem%2A> a <xref:System.Windows.Controls.TreeView> .  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>Właściwość umożliwia określenie <xref:System.Windows.Controls.TreeView.SelectedValue%2A> dla elementu <xref:System.Windows.Controls.TreeView.SelectedItem%2A> w <xref:System.Windows.Controls.TreeView> . <xref:System.Windows.Controls.TreeView.SelectedItem%2A>Reprezentuje obiekt w <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekcji i <xref:System.Windows.Controls.TreeView> wyświetla wartość pojedynczej właściwości wybranego elementu. <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>Właściwość określa ścieżkę do właściwości, która jest używana do określenia wartości <xref:System.Windows.Controls.TreeView.SelectedValue%2A> właściwości. Przykłady w tym temacie ilustrują tę koncepcję.  
  
 Poniższy przykład pokazuje <xref:System.Windows.Data.XmlDataProvider> , który zawiera informacje o pracowniku.  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.HierarchicalDataTemplate> , który wyświetla `EmployeeName` i `EmployeeWorkDay` `Employee` . Należy zauważyć, że program nie <xref:System.Windows.HierarchicalDataTemplate> określa `EmployeeNumber` jako części szablonu.  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 Poniższy przykład pokazuje <xref:System.Windows.Controls.TreeView> , że używa poprzednio zdefiniowanego <xref:System.Windows.HierarchicalDataTemplate> i ustawia <xref:System.Windows.Controls.TreeView.SelectedValue%2A> Właściwość na `EmployeeNumber` . Po wybraniu `EmployeeName` w <xref:System.Windows.Controls.TreeView> , <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Właściwość zwraca `EmployeeInfo` element danych, który odpowiada wybranemu `EmployeeName` . Jednak ponieważ dla <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> tego ustawienia ustawiono wartość <xref:System.Windows.Controls.TreeView> `EmployeeNumber` , <xref:System.Windows.Controls.TreeView.SelectedValue%2A> jest ustawiona na `EmployeeNumber` .  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [TreeView — Przegląd](treeview-overview.md)
- [— Tematy porad](treeview-how-to-topics.md)
