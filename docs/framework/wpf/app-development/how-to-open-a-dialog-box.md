---
title: 'Instrukcje: Otwieranie okna dialogowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
ms.openlocfilehash: 70ac31285dd22244b4bd6ad0d188d182eb6e6264
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084990"
---
# <a name="how-to-open-a-dialog-box"></a><span data-ttu-id="b1a21-102">Instrukcje: Otwieranie okna dialogowego</span><span class="sxs-lookup"><span data-stu-id="b1a21-102">How to: Open a Dialog Box</span></span>
<span data-ttu-id="b1a21-103">Ten przykład przedstawia sposób otworzyć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b1a21-103">This example shows how to open a dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1a21-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b1a21-104">Example</span></span>  
 <span data-ttu-id="b1a21-105">Okno dialogowe jest oknem, która została otwarta przez utworzenie wystąpienia <xref:System.Windows.Window> i wywoływać metodę <xref:System.Windows.Window.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b1a21-105">A dialog box is a window that is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span> <span data-ttu-id="b1a21-106"><xref:System.Windows.Window.ShowDialog%2A> Otwiera okno i nie zwraca, aż nowe okno dialogowe zostało zamknięte.</span><span class="sxs-lookup"><span data-stu-id="b1a21-106"><xref:System.Windows.Window.ShowDialog%2A> opens a window and doesn't return until the new dialog box has been closed.</span></span> <span data-ttu-id="b1a21-107">Ten typ okna jest także znana jako *modalne* oknie oraz ogranicza dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b1a21-107">This type of window is also known as a *modal* window, and restricts user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="b1a21-108">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="b1a21-108">.NET Framework Security</span></span>  
 <span data-ttu-id="b1a21-109">Wywoływanie <xref:System.Windows.Window.ShowDialog%2A> wymaga uprawnień do używania wszystkich okien i zdarzenia wejściowe użytkownika bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="b1a21-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a21-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1a21-110">See also</span></span>

- [<span data-ttu-id="b1a21-111">Zwracanie wyniku okna dialogowego</span><span class="sxs-lookup"><span data-stu-id="b1a21-111">Return a Dialog Box Result</span></span>](how-to-return-a-dialog-box-result.md)
