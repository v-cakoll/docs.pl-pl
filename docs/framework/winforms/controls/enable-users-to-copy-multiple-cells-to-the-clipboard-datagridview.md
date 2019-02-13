---
title: 'Instrukcje: Umożliwianie użytkownikom kopiowania wielu komórek do Schowka z kontrolki DataGridView formularzy Windows Forms'
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
ms.openlocfilehash: b8b466aac35f928be66b46a2fe840945847f4bc6
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220260"
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a><span data-ttu-id="23e08-102">Instrukcje: Umożliwianie użytkownikom kopiowania wielu komórek do Schowka z kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="23e08-102">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="23e08-103">Po włączeniu kopiowanie komórki wprowadzić dane w Twojej <xref:System.Windows.Forms.DataGridView> łatwo dostępne dla innych aplikacji za pomocą kontrolki <xref:System.Windows.Forms.Clipboard>.</span><span class="sxs-lookup"><span data-stu-id="23e08-103">When you enable cell copying, you make the data in your <xref:System.Windows.Forms.DataGridView> control easily accessible to other applications through the <xref:System.Windows.Forms.Clipboard>.</span></span> <span data-ttu-id="23e08-104">Wartości zaznaczonych komórek są konwertowane na ciągi i dodane do Schowka jako tekst rozdzielany tabulatorami wartości wklejania w aplikacji, takich jak Notatnik, a program Excel, a w formacie HTML tabeli wklejania w aplikacji, takich jak Word.</span><span class="sxs-lookup"><span data-stu-id="23e08-104">The values of the selected cells are converted to strings and added to the Clipboard as tab-delimited text values for pasting into applications like Notepad and Excel, and as an HTML-formatted table for pasting into applications like Word.</span></span>  
  
 <span data-ttu-id="23e08-105">Można skonfigurować w komórce kopiowania do skopiowania tylko wartości komórek, zawierają tekst nagłówka wierszy i kolumn w danych ze Schowka lub zawierają tekst nagłówka, tylko wtedy, gdy użytkownicy wybierają całych wierszy lub kolumn.</span><span class="sxs-lookup"><span data-stu-id="23e08-105">You can configure cell copying to copy cell values only, to include row and column header text in the Clipboard data, or to include header text only when users select entire rows or columns.</span></span>  
  
 <span data-ttu-id="23e08-106">W zależności od trybu zaznaczania użytkownicy mogą wybrać wiele grup odłączonego komórek.</span><span class="sxs-lookup"><span data-stu-id="23e08-106">Depending on the selection mode, users can select multiple disconnected groups of cells.</span></span> <span data-ttu-id="23e08-107">Gdy użytkownik kopiuje komórek do Schowka, wierszy i kolumn z nie zaznaczone komórki nie są kopiowane.</span><span class="sxs-lookup"><span data-stu-id="23e08-107">When a user copies cells to the Clipboard, rows and columns with no selected cells are not copied.</span></span> <span data-ttu-id="23e08-108">Wszystkie pozostałe wiersze lub kolumny stają się wierszy i kolumn w tabeli dane skopiowane do Schowka.</span><span class="sxs-lookup"><span data-stu-id="23e08-108">All other rows or columns become rows and columns in the table of data copied to the Clipboard.</span></span> <span data-ttu-id="23e08-109">Niezaznaczone komórek w te wiersze lub kolumny są kopiowane jako elementy zastępcze pustego do Schowka.</span><span class="sxs-lookup"><span data-stu-id="23e08-109">Unselected cells in these rows or columns are copied as blank placeholders to the Clipboard.</span></span>  
  
### <a name="to-enable-cell-copying"></a><span data-ttu-id="23e08-110">Aby umożliwić kopiowanie komórki</span><span class="sxs-lookup"><span data-stu-id="23e08-110">To enable cell copying</span></span>  
  
-   <span data-ttu-id="23e08-111">Ustaw <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="23e08-111">Set the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a><span data-ttu-id="23e08-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="23e08-112">Example</span></span>  
 <span data-ttu-id="23e08-113">Poniższy przykład kompletny kod pokazuje, jak komórek są kopiowane do Schowka.</span><span class="sxs-lookup"><span data-stu-id="23e08-113">The following complete code example demonstrates how cells are copied to the Clipboard.</span></span> <span data-ttu-id="23e08-114">W tym przykładzie zawiera przycisk, który kopiuje zaznaczonych komórek do Schowka z użyciem <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> metody i wyświetla zawartość Schowka, w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="23e08-114">This example includes a button that copies the selected cells to the Clipboard using the <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> method and displays the Clipboard contents in a text box.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="23e08-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="23e08-115">Compiling the Code</span></span>  
 <span data-ttu-id="23e08-116">Ten kod wymaga:</span><span class="sxs-lookup"><span data-stu-id="23e08-116">This code requires:</span></span>  
  
-   <span data-ttu-id="23e08-117">Odwołania do zestawów N:System i N:System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="23e08-117">References to the N:System and N:System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="23e08-118">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="23e08-118">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="23e08-119">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="23e08-119">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23e08-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23e08-120">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>
- <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>
- [<span data-ttu-id="23e08-121">Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="23e08-121">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
