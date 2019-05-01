---
title: 'Instrukcje: Poprawianie wydajności kontrolki TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
ms.openlocfilehash: de1b46da2a7c6c3db0c0c19cdbb654fcf2fbbd6c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771010"
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a>Instrukcje: Poprawianie wydajności kontrolki TreeView
Jeśli <xref:System.Windows.Controls.TreeView> zawiera wiele pozycji, czas potrzebny do załadowania może spowodować znaczne opóźnienie w interfejsie użytkownika. Możesz poprawić czas ładowania, ustawiając `VirtualizingStackPanel.IsVirtualizing` dołączonych właściwości `true`.  Interfejs użytkownika może być również wolno reagować, gdy użytkownik przewinie <xref:System.Windows.Controls.TreeView> przy użyciu kółka myszy lub przeciąganie uchwytu pasek przewijania. Można zwiększyć wydajność <xref:System.Windows.Controls.TreeView> po użytkownik przewija widok, ustawiając `VirtualizingStackPanel.VirtualizationMode` dołączonych właściwości <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.  
  
## <a name="example"></a>Przykład  
  
## <a name="description"></a>Opis  
Poniższy przykład tworzy <xref:System.Windows.Controls.TreeView> określająca `VirtualizingStackPanel.IsVirtualizing` dołączona właściwość na wartość true i `VirtualizingStackPanel.VirtualizationMode` dołączonych właściwości <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> zoptymalizowania wydajności.  
  
## <a name="code"></a>Kod  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 Poniższy przykład pokazuje dane w poprzednim przykładzie użyto.  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a>Zobacz także

- [Kontrolki](../advanced/optimizing-performance-controls.md)
