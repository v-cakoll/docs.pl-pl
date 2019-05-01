---
title: 'Instrukcje: Pobieranie elementu ListBoxItem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox controls [WPF], getting a ListBoxItem
- ListBoxItem [WPF]
ms.assetid: da877c6f-5fd8-40cb-8909-225cbfd99aa5
ms.openlocfilehash: 27a435feb4a941c77af221ab25bd63ea98b16e92
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910328"
---
# <a name="how-to-get-a-listboxitem"></a>Instrukcje: Pobieranie elementu ListBoxItem
Jeśli zajdzie potrzeba przywrócenia określonej <xref:System.Windows.Controls.ListBoxItem> pod określonym indeksem <xref:System.Windows.Controls.ListBox>, możesz użyć <xref:System.Windows.Controls.ItemContainerGenerator>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.ListBox> i jego elementów.  
  
 [!code-xaml[ListBoxItems#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml#1)]  
  
 Poniższy przykład pokazuje, jak pobrać elementu, określając indeks elementu w <xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromIndex%2A> właściwość <xref:System.Windows.Controls.ItemContainerGenerator>.  
  
 [!code-csharp[ListBoxItems#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ListBoxItems#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#2)]  
  
 Po pobraniu elementu pola listy, możesz wyświetlić zawartość elementu, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[ListBoxItems#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#3)]
 [!code-vb[ListBoxItems#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#3)]
