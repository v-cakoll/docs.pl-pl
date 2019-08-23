---
title: 'Instrukcje: Zwracanie wyniku okna dialogowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: 5e3670006762bcd09634b29314ecf2d05b1a44da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968231"
---
# <a name="how-to-return-a-dialog-box-result"></a><span data-ttu-id="aa1af-102">Instrukcje: Zwracanie wyniku okna dialogowego</span><span class="sxs-lookup"><span data-stu-id="aa1af-102">How to: Return a Dialog Box Result</span></span>
<span data-ttu-id="aa1af-103">Ten przykład pokazuje, jak pobrać wynik okna dialogowego dla okna, które jest otwierane przez <xref:System.Windows.Window.ShowDialog%2A>wywołanie.</span><span class="sxs-lookup"><span data-stu-id="aa1af-103">This example shows how to retrieve the dialog result for a window that is opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa1af-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa1af-104">Example</span></span>  
 <span data-ttu-id="aa1af-105">Przed zamknięciem okna dialogowego, jego <xref:System.Windows.Window.DialogResult%2A> właściwość powinna być ustawiona <xref:System.Nullable%601> <xref:System.Boolean> z, która wskazuje, jak użytkownik zamknął okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="aa1af-105">Before a dialog box closes, its <xref:System.Windows.Window.DialogResult%2A> property should be set with a <xref:System.Nullable%601><xref:System.Boolean> that indicates how the user closed the dialog box.</span></span> <span data-ttu-id="aa1af-106">Ta wartość jest zwracana przez <xref:System.Windows.Window.ShowDialog%2A> program, aby umożliwić kodowi klienta ustalenie, jak okno dialogowe zostało zamknięte, i w związku z tym, jak przetworzyć wynik.</span><span class="sxs-lookup"><span data-stu-id="aa1af-106">This value is returned by <xref:System.Windows.Window.ShowDialog%2A> to allow client code to determine how the dialog box was closed and, consequently, how to process the result.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa1af-107"><xref:System.Windows.Window.DialogResult%2A>można ustawić tylko wtedy, gdy okno zostało otwarte przez wywołanie <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="aa1af-107"><xref:System.Windows.Window.DialogResult%2A> can only be set if a window was opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="aa1af-108">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="aa1af-108">.NET Framework Security</span></span>  
 <span data-ttu-id="aa1af-109">Wywołanie <xref:System.Windows.Window.ShowDialog%2A> wymaga uprawnień do używania wszystkich zdarzeń systemu Windows i danych wejściowych użytkownika bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="aa1af-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>
