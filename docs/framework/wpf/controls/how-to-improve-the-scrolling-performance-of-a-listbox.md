---
title: 'Instrukcje: Poprawianie wydajności przesuwania w kontrolce ListBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
ms.openlocfilehash: a9d1ca1d8ac2ef830984408f3052eb0ed0987c5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770867"
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a><span data-ttu-id="8079e-102">Instrukcje: Poprawianie wydajności przesuwania w kontrolce ListBox</span><span class="sxs-lookup"><span data-stu-id="8079e-102">How to: Improve the Scrolling Performance of a ListBox</span></span>
<span data-ttu-id="8079e-103">Jeśli <xref:System.Windows.Controls.ListBox> zawiera wiele pozycji, odpowiedzi interfejsu użytkownika może działać powoli, gdy użytkownik przewinie <xref:System.Windows.Controls.ListBox> przy użyciu kółka myszy lub przeciąganie uchwytu pasek przewijania.</span><span class="sxs-lookup"><span data-stu-id="8079e-103">If a <xref:System.Windows.Controls.ListBox> contains many items, the user interface response can be slow when a user scrolls the <xref:System.Windows.Controls.ListBox> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="8079e-104">Można zwiększyć wydajność <xref:System.Windows.Controls.ListBox> po użytkownik przewija widok, ustawiając `VirtualizingStackPanel.VirtualizationMode` dołączonych właściwości <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8079e-104">You can improve the performance of the <xref:System.Windows.Controls.ListBox> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8079e-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="8079e-105">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="8079e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8079e-106">Description</span></span>  
<span data-ttu-id="8079e-107">Poniższy przykład tworzy <xref:System.Windows.Controls.ListBox> i ustawia `VirtualizingStackPanel.VirtualizationMode` dołączonych właściwości <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> aby poprawić wydajność podczas przewijania.</span><span class="sxs-lookup"><span data-stu-id="8079e-107">The following example creates a <xref:System.Windows.Controls.ListBox> and sets the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to improve performance during scrolling.</span></span>  
  
## <a name="code"></a><span data-ttu-id="8079e-108">Kod</span><span class="sxs-lookup"><span data-stu-id="8079e-108">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 <span data-ttu-id="8079e-109">Poniższy przykład pokazuje dane w poprzednim przykładzie użyto.</span><span class="sxs-lookup"><span data-stu-id="8079e-109">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
