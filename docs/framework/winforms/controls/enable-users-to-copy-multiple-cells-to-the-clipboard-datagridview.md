---
title: Umożliwienie użytkownikom kopiowania wielu komórek do schowka z formantu DataGridView
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
ms.openlocfilehash: 2bb74a1f0c59b28ab496ce9c89c1c1b5f9d8147b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745783"
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a><span data-ttu-id="f541f-102">Porady: umożliwianie użytkownikom kopiowania wielu komórek do schowka z formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f541f-102">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f541f-103">Po włączeniu kopiowania komórek dane w <xref:System.Windows.Forms.DataGridView> formantu są łatwo dostępne dla innych aplikacji za pomocą <xref:System.Windows.Forms.Clipboard>.</span><span class="sxs-lookup"><span data-stu-id="f541f-103">When you enable cell copying, you make the data in your <xref:System.Windows.Forms.DataGridView> control easily accessible to other applications through the <xref:System.Windows.Forms.Clipboard>.</span></span> <span data-ttu-id="f541f-104">Wartości zaznaczonych komórek są konwertowane na ciągi i dodawane do Schowka jako wartości tekstowe rozdzielane znakami tabulacji w celu wklejenia do aplikacji, takich jak Notepad i Excel, oraz jako tabelę sformatowaną w formacie HTML do wklejania do aplikacji, takich jak Word.</span><span class="sxs-lookup"><span data-stu-id="f541f-104">The values of the selected cells are converted to strings and added to the Clipboard as tab-delimited text values for pasting into applications like Notepad and Excel, and as an HTML-formatted table for pasting into applications like Word.</span></span>  
  
 <span data-ttu-id="f541f-105">Kopiowanie komórek można skonfigurować tak, aby kopiować tylko wartości komórek, w celu dołączania tekstu nagłówka wiersza i kolumny w danych Schowka lub do dołączania tekstu nagłówka tylko wtedy, gdy użytkownicy wybierają całe wiersze lub kolumny.</span><span class="sxs-lookup"><span data-stu-id="f541f-105">You can configure cell copying to copy cell values only, to include row and column header text in the Clipboard data, or to include header text only when users select entire rows or columns.</span></span>  
  
 <span data-ttu-id="f541f-106">W zależności od trybu zaznaczania użytkownicy mogą wybrać wiele odłączonych grup komórek.</span><span class="sxs-lookup"><span data-stu-id="f541f-106">Depending on the selection mode, users can select multiple disconnected groups of cells.</span></span> <span data-ttu-id="f541f-107">Gdy użytkownik kopiuje komórki do schowka, wiersze i kolumny bez zaznaczonych komórek nie są kopiowane.</span><span class="sxs-lookup"><span data-stu-id="f541f-107">When a user copies cells to the Clipboard, rows and columns with no selected cells are not copied.</span></span> <span data-ttu-id="f541f-108">Wszystkie inne wiersze lub kolumny stają się wierszami i kolumnami w tabeli danych skopiowanymi do Schowka.</span><span class="sxs-lookup"><span data-stu-id="f541f-108">All other rows or columns become rows and columns in the table of data copied to the Clipboard.</span></span> <span data-ttu-id="f541f-109">Niezaznaczone komórki w tych wierszach lub kolumnach są kopiowane jako puste symbole zastępcze do Schowka.</span><span class="sxs-lookup"><span data-stu-id="f541f-109">Unselected cells in these rows or columns are copied as blank placeholders to the Clipboard.</span></span>  
  
### <a name="to-enable-cell-copying"></a><span data-ttu-id="f541f-110">Aby włączyć kopiowanie komórek</span><span class="sxs-lookup"><span data-stu-id="f541f-110">To enable cell copying</span></span>  
  
- <span data-ttu-id="f541f-111">Ustaw właściwość <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f541f-111">Set the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a><span data-ttu-id="f541f-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f541f-112">Example</span></span>  
 <span data-ttu-id="f541f-113">Poniższy pełny kod ilustruje sposób kopiowania komórek do Schowka.</span><span class="sxs-lookup"><span data-stu-id="f541f-113">The following complete code example demonstrates how cells are copied to the Clipboard.</span></span> <span data-ttu-id="f541f-114">Ten przykład zawiera przycisk, który kopiuje zaznaczone komórki do schowka przy użyciu metody <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> i wyświetla zawartość schowka w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="f541f-114">This example includes a button that copies the selected cells to the Clipboard using the <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> method and displays the Clipboard contents in a text box.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f541f-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f541f-115">Compiling the Code</span></span>  
 <span data-ttu-id="f541f-116">Ten kod wymaga:</span><span class="sxs-lookup"><span data-stu-id="f541f-116">This code requires:</span></span>  
  
- <span data-ttu-id="f541f-117">Odwołania do zestawów N:System i N:System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="f541f-117">References to the N:System and N:System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f541f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f541f-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>
- <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>
- [<span data-ttu-id="f541f-119">Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f541f-119">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
