---
title: 'Porady: umożliwianie użytkownikom kopiowania wielu komórek do schowka z formantu DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], copying to Clipboard
- DataGridView control [Windows Forms], copying multiple cells
- data grids [Windows Forms], copying multiple cells
- Clipboard [Windows Forms], copying multiple cells
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
ms.openlocfilehash: db70c919aa13cfc679b33285b38e7a0a27868c00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a><span data-ttu-id="fbfbf-102">Porady: umożliwianie użytkownikom kopiowania wielu komórek do schowka z formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fbfbf-102">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fbfbf-103">Po włączeniu kopiowanie komórki wprowadzeniu danych w sieci <xref:System.Windows.Forms.DataGridView> łatwo dostępne dla innych aplikacji za pomocą formantu <xref:System.Windows.Forms.Clipboard>.</span><span class="sxs-lookup"><span data-stu-id="fbfbf-103">When you enable cell copying, you make the data in your <xref:System.Windows.Forms.DataGridView> control easily accessible to other applications through the <xref:System.Windows.Forms.Clipboard>.</span></span> <span data-ttu-id="fbfbf-104">Wartości zaznaczonych komórek są konwertowane na ciągi i dodane do Schowka jako wartości tekstowe tabulacji wklejania w aplikacjach, takich jak Notatnik, a program Excel, a w formacie HTML tabeli wklejania w aplikacjach, takich jak Word.</span><span class="sxs-lookup"><span data-stu-id="fbfbf-104">The values of the selected cells are converted to strings and added to the Clipboard as tab-delimited text values for pasting into applications like Notepad and Excel, and as an HTML-formatted table for pasting into applications like Word.</span></span>  
  
 <span data-ttu-id="fbfbf-105">Można skonfigurować komórki kopiowanie skopiować tylko wartości komórek, zawierają tekst nagłówka wiersza i kolumny w danych ze Schowka lub zawierają tekst nagłówka, tylko wtedy, gdy użytkownicy wybierają całego wierszy lub kolumn.</span><span class="sxs-lookup"><span data-stu-id="fbfbf-105">You can configure cell copying to copy cell values only, to include row and column header text in the Clipboard data, or to include header text only when users select entire rows or columns.</span></span>  
  
 <span data-ttu-id="fbfbf-106">W zależności od trybu wyboru użytkownicy mogą wybierać wielu grup odłączonego komórek.</span><span class="sxs-lookup"><span data-stu-id="fbfbf-106">Depending on the selection mode, users can select multiple disconnected groups of cells.</span></span> <span data-ttu-id="fbfbf-107">Gdy użytkownik kopiuje komórek do Schowka, wierszy i kolumn z nie zaznaczone komórki nie są kopiowane.</span><span class="sxs-lookup"><span data-stu-id="fbfbf-107">When a user copies cells to the Clipboard, rows and columns with no selected cells are not copied.</span></span> <span data-ttu-id="fbfbf-108">Wszystkie inne wierszy lub kolumn stają się wierszy i kolumn w tabeli danych skopiowany do Schowka.</span><span class="sxs-lookup"><span data-stu-id="fbfbf-108">All other rows or columns become rows and columns in the table of data copied to the Clipboard.</span></span> <span data-ttu-id="fbfbf-109">Niezaznaczone komórek w tych wierszy lub kolumn są kopiowane jako puste elementy zastępcze do Schowka.</span><span class="sxs-lookup"><span data-stu-id="fbfbf-109">Unselected cells in these rows or columns are copied as blank placeholders to the Clipboard.</span></span>  
  
### <a name="to-enable-cell-copying"></a><span data-ttu-id="fbfbf-110">Aby umożliwić kopiowanie komórki</span><span class="sxs-lookup"><span data-stu-id="fbfbf-110">To enable cell copying</span></span>  
  
-   <span data-ttu-id="fbfbf-111">Ustaw <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fbfbf-111">Set the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a><span data-ttu-id="fbfbf-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="fbfbf-112">Example</span></span>  
 <span data-ttu-id="fbfbf-113">W poniższym przykładzie kompletny kod pokazano, jak komórki są kopiowane do Schowka.</span><span class="sxs-lookup"><span data-stu-id="fbfbf-113">The following complete code example demonstrates how cells are copied to the Clipboard.</span></span> <span data-ttu-id="fbfbf-114">Ten przykład zawiera przycisk, który kopiuje zaznaczonych komórek do Schowka przy użyciu <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> — metoda i wyświetla zawartość Schowka w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="fbfbf-114">This example includes a button that copies the selected cells to the Clipboard using the <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> method and displays the Clipboard contents in a text box.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fbfbf-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="fbfbf-115">Compiling the Code</span></span>  
 <span data-ttu-id="fbfbf-116">Ten kod wymaga:</span><span class="sxs-lookup"><span data-stu-id="fbfbf-116">This code requires:</span></span>  
  
-   <span data-ttu-id="fbfbf-117">Odwołania do zestawów N:System i N:System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="fbfbf-117">References to the N:System and N:System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="fbfbf-118">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="fbfbf-118">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="fbfbf-119">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="fbfbf-119">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="fbfbf-120">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="fbfbf-120">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbfbf-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbfbf-121">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>  
 [<span data-ttu-id="fbfbf-122">Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fbfbf-122">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
