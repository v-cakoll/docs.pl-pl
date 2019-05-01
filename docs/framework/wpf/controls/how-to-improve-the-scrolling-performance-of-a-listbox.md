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
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a>Instrukcje: Poprawianie wydajności przesuwania w kontrolce ListBox
Jeśli <xref:System.Windows.Controls.ListBox> zawiera wiele pozycji, odpowiedzi interfejsu użytkownika może działać powoli, gdy użytkownik przewinie <xref:System.Windows.Controls.ListBox> przy użyciu kółka myszy lub przeciąganie uchwytu pasek przewijania. Można zwiększyć wydajność <xref:System.Windows.Controls.ListBox> po użytkownik przewija widok, ustawiając `VirtualizingStackPanel.VirtualizationMode` dołączonych właściwości <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.  
  
## <a name="example"></a>Przykład  
  
## <a name="description"></a>Opis  
Poniższy przykład tworzy <xref:System.Windows.Controls.ListBox> i ustawia `VirtualizingStackPanel.VirtualizationMode` dołączonych właściwości <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> aby poprawić wydajność podczas przewijania.  
  
## <a name="code"></a>Kod  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 Poniższy przykład pokazuje dane w poprzednim przykładzie użyto.  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
