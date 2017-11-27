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
# <a name="how-to-improve-the-performance-of-a-treeview"></a><span data-ttu-id="29af0-102">Jak poprawić wydajność TreeView</span><span class="sxs-lookup"><span data-stu-id="29af0-102">How to: Improve the Performance of a TreeView</span></span>
<span data-ttu-id="29af0-103">Jeśli <xref:System.Windows.Controls.TreeView> zawiera wiele pozycji, czas potrzebny do załadowania może powodować znaczne opóźnienie w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="29af0-103">If a <xref:System.Windows.Controls.TreeView> contains many items, the amount of time it takes to load may cause a significant delay in the user interface.</span></span> <span data-ttu-id="29af0-104">Można zwiększyć czas ładowania, ustawiając `VirtualizingStackPanel.IsVirtualizing` dołączona właściwość do `true`.</span><span class="sxs-lookup"><span data-stu-id="29af0-104">You can improve the load time by setting the `VirtualizingStackPanel.IsVirtualizing` attached property to `true`.</span></span>  <span data-ttu-id="29af0-105">Interfejs użytkownika może też być powolne reagować, gdy użytkownik przewinie <xref:System.Windows.Controls.TreeView> za pomocą kółka myszy lub przeciąganie przycisku paska przewijania.</span><span class="sxs-lookup"><span data-stu-id="29af0-105">The UI might also be slow to react when a user scrolls the <xref:System.Windows.Controls.TreeView> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="29af0-106">Można zwiększyć wydajność <xref:System.Windows.Controls.TreeView> gdy użytkownik przewija widok przez ustawienie `VirtualizingStackPanel.VirtualizationMode` dołączona właściwość do <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="29af0-106">You can improve the performance of the <xref:System.Windows.Controls.TreeView> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29af0-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="29af0-107">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="29af0-108">Opis</span><span class="sxs-lookup"><span data-stu-id="29af0-108">Description</span></span>  
<span data-ttu-id="29af0-109">Poniższy przykład tworzy <xref:System.Windows.Controls.TreeView> stanowiąca `VirtualizingStackPanel.IsVirtualizing` dołączona właściwość na wartość true i `VirtualizingStackPanel.VirtualizationMode` dołączona właściwość do <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> zoptymalizować jego wydajność.</span><span class="sxs-lookup"><span data-stu-id="29af0-109">The following example creates a <xref:System.Windows.Controls.TreeView> that sets the `VirtualizingStackPanel.IsVirtualizing` attached property to true and the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to optimize its performance.</span></span>  
  
## <a name="code"></a><span data-ttu-id="29af0-110">Kod</span><span class="sxs-lookup"><span data-stu-id="29af0-110">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 <span data-ttu-id="29af0-111">W poniższym przykładzie przedstawiono dane w poprzednim przykładzie użyto.</span><span class="sxs-lookup"><span data-stu-id="29af0-111">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a><span data-ttu-id="29af0-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29af0-112">See Also</span></span>  
 [<span data-ttu-id="29af0-113">Formanty</span><span class="sxs-lookup"><span data-stu-id="29af0-113">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
