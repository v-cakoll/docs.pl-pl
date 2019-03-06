---
title: 'Instrukcje: Popraw wydajność TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
ms.openlocfilehash: d04d5997e6f02a4227704b668fdf19324ea20f26
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364739"
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a><span data-ttu-id="57d4a-102">Instrukcje: Popraw wydajność TreeView</span><span class="sxs-lookup"><span data-stu-id="57d4a-102">How to: Improve the Performance of a TreeView</span></span>
<span data-ttu-id="57d4a-103">Jeśli <xref:System.Windows.Controls.TreeView> zawiera wiele pozycji, czas potrzebny do załadowania może spowodować znaczne opóźnienie w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="57d4a-103">If a <xref:System.Windows.Controls.TreeView> contains many items, the amount of time it takes to load may cause a significant delay in the user interface.</span></span> <span data-ttu-id="57d4a-104">Możesz poprawić czas ładowania, ustawiając `VirtualizingStackPanel.IsVirtualizing` dołączonych właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="57d4a-104">You can improve the load time by setting the `VirtualizingStackPanel.IsVirtualizing` attached property to `true`.</span></span>  <span data-ttu-id="57d4a-105">Interfejs użytkownika może być również wolno reagować, gdy użytkownik przewinie <xref:System.Windows.Controls.TreeView> przy użyciu kółka myszy lub przeciąganie uchwytu pasek przewijania.</span><span class="sxs-lookup"><span data-stu-id="57d4a-105">The UI might also be slow to react when a user scrolls the <xref:System.Windows.Controls.TreeView> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="57d4a-106">Można zwiększyć wydajność <xref:System.Windows.Controls.TreeView> po użytkownik przewija widok, ustawiając `VirtualizingStackPanel.VirtualizationMode` dołączonych właściwości <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="57d4a-106">You can improve the performance of the <xref:System.Windows.Controls.TreeView> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57d4a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="57d4a-107">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="57d4a-108">Opis</span><span class="sxs-lookup"><span data-stu-id="57d4a-108">Description</span></span>  
<span data-ttu-id="57d4a-109">Poniższy przykład tworzy <xref:System.Windows.Controls.TreeView> określająca `VirtualizingStackPanel.IsVirtualizing` dołączona właściwość na wartość true i `VirtualizingStackPanel.VirtualizationMode` dołączonych właściwości <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> zoptymalizowania wydajności.</span><span class="sxs-lookup"><span data-stu-id="57d4a-109">The following example creates a <xref:System.Windows.Controls.TreeView> that sets the `VirtualizingStackPanel.IsVirtualizing` attached property to true and the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to optimize its performance.</span></span>  
  
## <a name="code"></a><span data-ttu-id="57d4a-110">Kod</span><span class="sxs-lookup"><span data-stu-id="57d4a-110">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 <span data-ttu-id="57d4a-111">Poniższy przykład pokazuje dane w poprzednim przykładzie użyto.</span><span class="sxs-lookup"><span data-stu-id="57d4a-111">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a><span data-ttu-id="57d4a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57d4a-112">See also</span></span>
- [<span data-ttu-id="57d4a-113">Kontrolki</span><span class="sxs-lookup"><span data-stu-id="57d4a-113">Controls</span></span>](../advanced/optimizing-performance-controls.md)
