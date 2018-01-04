---
title: "Porady: zwracanie wyniku — okno dialogowe"
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
helpviewer_keywords: dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f8133ffa7be9cb4e0600fc2681402d5e0f7471c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-return-a-dialog-box-result"></a>Porady: zwracanie wyniku — okno dialogowe
W tym przykładzie pokazano, jak można pobrać wyniku okna dialogowego dla okna, która jest otwarta przez wywołanie metody <xref:System.Windows.Window.ShowDialog%2A>.  
  
## <a name="example"></a>Przykład  
 Przed zamknięciem okno dialogowe, jego <xref:System.Windows.Window.DialogResult%2A> właściwości należy ustawić wartość z <xref:System.Nullable%601> <xref:System.Boolean> wskazujące, jak zostanie zamknięte okno dialogowe. Ta wartość jest zwracana przez <xref:System.Windows.Window.ShowDialog%2A> umożliwia kod klienta, aby określić sposób zamknięcia okna dialogowego i, w związku z tym, jak w celu przetworzenia wyniku.  
  
> [!NOTE]
>  <xref:System.Windows.Window.DialogResult%2A>może zostać ustawiona tylko, gdy okno zostało otwarte przez wywołanie metody <xref:System.Windows.Window.ShowDialog%2A>.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Wywoływanie <xref:System.Windows.Window.ShowDialog%2A> wymaga uprawnienia do używania wszystkie okna i zdarzenia wejściowe użytkownika bez ograniczeń.
