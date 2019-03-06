---
title: 'Instrukcje: Zwracanie wyniku okno dialogowe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: b574a5bbc08d947371837116915c2fc8c13ec81d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357771"
---
# <a name="how-to-return-a-dialog-box-result"></a><span data-ttu-id="d1bd3-102">Instrukcje: Zwracanie wyniku okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="d1bd3-102">How to: Return a Dialog Box Result</span></span>
<span data-ttu-id="d1bd3-103">Ten przykład pokazuje, jak można pobrać wyniku okna dialogowego okna, który jest otwierany, wywołując <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-103">This example shows how to retrieve the dialog result for a window that is opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1bd3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1bd3-104">Example</span></span>  
 <span data-ttu-id="d1bd3-105">Przed zamknięciem okna dialogowego, jego <xref:System.Windows.Window.DialogResult%2A> właściwość powinna być ustawiona za pomocą <xref:System.Nullable%601> <xref:System.Boolean> oznacza to, jak użytkownik zamknięte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-105">Before a dialog box closes, its <xref:System.Windows.Window.DialogResult%2A> property should be set with a <xref:System.Nullable%601><xref:System.Boolean> that indicates how the user closed the dialog box.</span></span> <span data-ttu-id="d1bd3-106">Ta wartość jest zwracana przez <xref:System.Windows.Window.ShowDialog%2A> umożliwia kod klienta określić, jak zostało zamknięte okno dialogowe i, w związku z tym, jak Przetwórz wynik.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-106">This value is returned by <xref:System.Windows.Window.ShowDialog%2A> to allow client code to determine how the dialog box was closed and, consequently, how to process the result.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1bd3-107"><xref:System.Windows.Window.DialogResult%2A> można ustawić tylko jeśli okno zostało otwarte przez wywołanie metody <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-107"><xref:System.Windows.Window.DialogResult%2A> can only be set if a window was opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="d1bd3-108">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d1bd3-108">.NET Framework Security</span></span>  
 <span data-ttu-id="d1bd3-109">Wywoływanie <xref:System.Windows.Window.ShowDialog%2A> wymaga uprawnień do używania wszystkich okien i zdarzenia wejściowe użytkownika bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="d1bd3-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>
