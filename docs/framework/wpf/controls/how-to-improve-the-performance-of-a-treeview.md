---
title: "Jak poprawić wydajność TreeView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 209f2c5645758aba4d1e10fc36fe773faa975e6b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a>Jak poprawić wydajność TreeView
Jeśli <xref:System.Windows.Controls.TreeView> zawiera wiele pozycji, czas potrzebny do załadowania może powodować znaczne opóźnienie w interfejsie użytkownika. Można zwiększyć czas ładowania, ustawiając `VirtualizingStackPanel.IsVirtualizing` dołączona właściwość do `true`.  Interfejs użytkownika może też być powolne reagować, gdy użytkownik przewinie <xref:System.Windows.Controls.TreeView> za pomocą kółka myszy lub przeciąganie przycisku paska przewijania. Można zwiększyć wydajność <xref:System.Windows.Controls.TreeView> gdy użytkownik przewija widok przez ustawienie `VirtualizingStackPanel.VirtualizationMode` dołączona właściwość do <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.  
  
## <a name="example"></a>Przykład  
  
## <a name="description"></a>Opis  
Poniższy przykład tworzy <xref:System.Windows.Controls.TreeView> stanowiąca `VirtualizingStackPanel.IsVirtualizing` dołączona właściwość na wartość true i `VirtualizingStackPanel.VirtualizationMode` dołączona właściwość do <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> zoptymalizować jego wydajność.  
  
## <a name="code"></a>Kod  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 W poniższym przykładzie przedstawiono dane w poprzednim przykładzie użyto.  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
