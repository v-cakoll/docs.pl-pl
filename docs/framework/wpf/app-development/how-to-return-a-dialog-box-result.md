---
title: "Porady: zwracanie wyniku — okno dialogowe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f8133ffa7be9cb4e0600fc2681402d5e0f7471c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-return-a-dialog-box-result"></a><span data-ttu-id="51cf9-102">Porady: zwracanie wyniku — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="51cf9-102">How to: Return a Dialog Box Result</span></span>
<span data-ttu-id="51cf9-103">W tym przykładzie pokazano, jak można pobrać wyniku okna dialogowego dla okna, która jest otwarta przez wywołanie metody <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="51cf9-103">This example shows how to retrieve the dialog result for a window that is opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51cf9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="51cf9-104">Example</span></span>  
 <span data-ttu-id="51cf9-105">Przed zamknięciem okno dialogowe, jego <xref:System.Windows.Window.DialogResult%2A> właściwości należy ustawić wartość z <xref:System.Nullable%601> <xref:System.Boolean> wskazujące, jak zostanie zamknięte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="51cf9-105">Before a dialog box closes, its <xref:System.Windows.Window.DialogResult%2A> property should be set with a <xref:System.Nullable%601><xref:System.Boolean> that indicates how the user closed the dialog box.</span></span> <span data-ttu-id="51cf9-106">Ta wartość jest zwracana przez <xref:System.Windows.Window.ShowDialog%2A> umożliwia kod klienta, aby określić sposób zamknięcia okna dialogowego i, w związku z tym, jak w celu przetworzenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="51cf9-106">This value is returned by <xref:System.Windows.Window.ShowDialog%2A> to allow client code to determine how the dialog box was closed and, consequently, how to process the result.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51cf9-107"><xref:System.Windows.Window.DialogResult%2A>może zostać ustawiona tylko, gdy okno zostało otwarte przez wywołanie metody <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="51cf9-107"><xref:System.Windows.Window.DialogResult%2A> can only be set if a window was opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="51cf9-108">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="51cf9-108">.NET Framework Security</span></span>  
 <span data-ttu-id="51cf9-109">Wywoływanie <xref:System.Windows.Window.ShowDialog%2A> wymaga uprawnienia do używania wszystkie okna i zdarzenia wejściowe użytkownika bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="51cf9-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>
