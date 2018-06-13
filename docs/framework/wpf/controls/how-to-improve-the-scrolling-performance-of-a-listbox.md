---
title: Jak poprawić wydajność przesuwania ListBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
ms.openlocfilehash: 224b996ad97d9a71ce43023143b68c2ab5b8467b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552795"
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a>Jak poprawić wydajność przesuwania ListBox
Jeśli <xref:System.Windows.Controls.ListBox> zawiera wiele pozycji, mogą być powolne odpowiedzi interfejsu użytkownika, gdy użytkownik przewinie <xref:System.Windows.Controls.ListBox> za pomocą kółka myszy lub przeciąganie przycisku paska przewijania. Można zwiększyć wydajność <xref:System.Windows.Controls.ListBox> gdy użytkownik przewija widok przez ustawienie `VirtualizingStackPanel.VirtualizationMode` dołączona właściwość do <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.  
  
## <a name="example"></a>Przykład  
  
## <a name="description"></a>Opis  
Poniższy przykład tworzy <xref:System.Windows.Controls.ListBox> i ustawia `VirtualizingStackPanel.VirtualizationMode` dołączona właściwość do <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> aby poprawić wydajność podczas przewijania.  
  
## <a name="code"></a>Kod  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 W poniższym przykładzie przedstawiono dane w poprzednim przykładzie użyto.  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
