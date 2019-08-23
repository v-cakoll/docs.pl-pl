---
title: 'Instrukcje: Znajdowanie elementu TreeViewItem w kontrolce TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
ms.openlocfilehash: ad72c7a7fb11dfe605db4119dde831b47dd7c5a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962094"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>Instrukcje: Znajdowanie elementu TreeViewItem w kontrolce TreeView
<xref:System.Windows.Controls.TreeView> Formant zapewnia wygodny sposób wyświetlania danych hierarchicznych. Jeśli jest powiązany ze źródłem danych <xref:System.Windows.Controls.TreeView.SelectedItem%2A> , właściwość zapewnia wygodny sposób na szybkie pobranie wybranego obiektu danych. <xref:System.Windows.Controls.TreeView> Zazwyczaj najlepszym rozwiązaniem jest współdziałanie z obiektem danych bazowych, ale czasami może zajść konieczność programistycznego manipulowania <xref:System.Windows.Controls.TreeViewItem>zawierającymi go danymi. Na przykład może być konieczne programistyczne rozwinięcie <xref:System.Windows.Controls.TreeViewItem>lub wybranie innego elementu <xref:System.Windows.Controls.TreeView>w.  
  
 Aby znaleźć <xref:System.Windows.Controls.TreeViewItem> , który zawiera określony obiekt danych, należy przejść na każdy poziom <xref:System.Windows.Controls.TreeView>. Elementy w a <xref:System.Windows.Controls.TreeView> mogą być również zwirtualizowane w celu zwiększenia wydajności. W przypadku, gdy elementy mogą być zwirtualizowane, należy również pamiętać <xref:System.Windows.Controls.TreeViewItem> , aby sprawdzić, czy zawiera on obiekt danych.  
  
## <a name="example"></a>Przykład  
  
## <a name="description"></a>Opis  
 Poniższy przykład wyszukuje <xref:System.Windows.Controls.TreeView> określony obiekt i zwraca obiekt zawierający <xref:System.Windows.Controls.TreeViewItem>. W przykładzie zagwarantujemy <xref:System.Windows.Controls.TreeViewItem> , że poszczególne wystąpienia są tworzone, aby można było przeszukiwać elementy podrzędne. Ten przykład działa również wtedy, <xref:System.Windows.Controls.TreeView> gdy nie używa zwirtualizowanych elementów.  
  
> [!NOTE]
> Poniższy przykład działa dla dowolnego <xref:System.Windows.Controls.TreeView>, niezależnie od modelu danych, i wyszukuje co <xref:System.Windows.Controls.TreeViewItem> do momentu znalezienia obiektu. Inną techniką mającą lepszą wydajność jest przeszukanie modelu danych dla określonego obiektu, śledzenie jego lokalizacji w hierarchii danych, a następnie znalezienie odpowiedniego <xref:System.Windows.Controls.TreeViewItem> elementu <xref:System.Windows.Controls.TreeView>w. Jednak technika, która ma lepszą wydajność, wymaga znajomości modelu danych i nie może być uogólniona dla każdego z nich <xref:System.Windows.Controls.TreeView>.  
  
## <a name="code"></a>Kod  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 Poprzedni kod opiera się na niestandardowym <xref:System.Windows.Controls.VirtualizingStackPanel> , który uwidacznia metodę o `BringIntoView`nazwie. Poniższy kod definiuje niestandardowy <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 Poniższy kod XAML pokazuje, jak utworzyć obiekt <xref:System.Windows.Controls.TreeView> , który używa niestandardowych <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Poprawianie wydajności kontrolki TreeView](how-to-improve-the-performance-of-a-treeview.md)
