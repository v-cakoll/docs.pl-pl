---
title: 'Porady: zwracanie wyniku — okno dialogowe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: 8f754577a355a58060238bbbb487c36aea14658c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-return-a-dialog-box-result"></a><span data-ttu-id="76e96-102">Porady: zwracanie wyniku — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="76e96-102">How to: Return a Dialog Box Result</span></span>
<span data-ttu-id="76e96-103">W tym przykładzie pokazano, jak można pobrać wyniku okna dialogowego dla okna, która jest otwarta przez wywołanie metody <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="76e96-103">This example shows how to retrieve the dialog result for a window that is opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76e96-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="76e96-104">Example</span></span>  
 <span data-ttu-id="76e96-105">Przed zamknięciem okno dialogowe, jego <xref:System.Windows.Window.DialogResult%2A> właściwości należy ustawić wartość z <xref:System.Nullable%601> <xref:System.Boolean> wskazujące, jak zostanie zamknięte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="76e96-105">Before a dialog box closes, its <xref:System.Windows.Window.DialogResult%2A> property should be set with a <xref:System.Nullable%601><xref:System.Boolean> that indicates how the user closed the dialog box.</span></span> <span data-ttu-id="76e96-106">Ta wartość jest zwracana przez <xref:System.Windows.Window.ShowDialog%2A> umożliwia kod klienta, aby określić sposób zamknięcia okna dialogowego i, w związku z tym, jak w celu przetworzenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="76e96-106">This value is returned by <xref:System.Windows.Window.ShowDialog%2A> to allow client code to determine how the dialog box was closed and, consequently, how to process the result.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76e96-107"><xref:System.Windows.Window.DialogResult%2A> może zostać ustawiona tylko, gdy okno zostało otwarte przez wywołanie metody <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="76e96-107"><xref:System.Windows.Window.DialogResult%2A> can only be set if a window was opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="76e96-108">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="76e96-108">.NET Framework Security</span></span>  
 <span data-ttu-id="76e96-109">Wywoływanie <xref:System.Windows.Window.ShowDialog%2A> wymaga uprawnienia do używania wszystkie okna i zdarzenia wejściowe użytkownika bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="76e96-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>
