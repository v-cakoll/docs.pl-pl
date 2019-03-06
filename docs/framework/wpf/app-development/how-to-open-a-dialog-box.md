---
title: 'Instrukcje: Otwórz okno dialogowe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
ms.openlocfilehash: 1182e22ad40b49ee13832c51986662373f36ee35
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351987"
---
# <a name="how-to-open-a-dialog-box"></a><span data-ttu-id="f47c8-102">Instrukcje: Otwórz okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="f47c8-102">How to: Open a Dialog Box</span></span>
<span data-ttu-id="f47c8-103">Ten przykład przedstawia sposób otworzyć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f47c8-103">This example shows how to open a dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f47c8-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f47c8-104">Example</span></span>  
 <span data-ttu-id="f47c8-105">Okno dialogowe jest oknem, która została otwarta przez utworzenie wystąpienia <xref:System.Windows.Window> i wywoływać metodę <xref:System.Windows.Window.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f47c8-105">A dialog box is a window that is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span> <span data-ttu-id="f47c8-106"><xref:System.Windows.Window.ShowDialog%2A> Otwiera okno i nie zwraca, aż nowe okno dialogowe zostało zamknięte.</span><span class="sxs-lookup"><span data-stu-id="f47c8-106"><xref:System.Windows.Window.ShowDialog%2A> opens a window and doesn't return until the new dialog box has been closed.</span></span> <span data-ttu-id="f47c8-107">Ten typ okna jest także znana jako *modalne* oknie oraz ogranicza dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f47c8-107">This type of window is also known as a *modal* window, and restricts user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="f47c8-108">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="f47c8-108">.NET Framework Security</span></span>  
 <span data-ttu-id="f47c8-109">Wywoływanie <xref:System.Windows.Window.ShowDialog%2A> wymaga uprawnień do używania wszystkich okien i zdarzenia wejściowe użytkownika bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="f47c8-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f47c8-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f47c8-110">See also</span></span>
- [<span data-ttu-id="f47c8-111">Zwracanie wyniku okna dialogowego</span><span class="sxs-lookup"><span data-stu-id="f47c8-111">Return a Dialog Box Result</span></span>](how-to-return-a-dialog-box-result.md)
