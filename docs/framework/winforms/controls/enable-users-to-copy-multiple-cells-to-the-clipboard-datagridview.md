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
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a>Porady: umożliwianie użytkownikom kopiowania wielu komórek do schowka z formantu DataGridView formularzy systemu Windows
Po włączeniu kopiowania komórek dane w <xref:System.Windows.Forms.DataGridView> formantu są łatwo dostępne dla innych aplikacji za pomocą <xref:System.Windows.Forms.Clipboard>. Wartości zaznaczonych komórek są konwertowane na ciągi i dodawane do Schowka jako wartości tekstowe rozdzielane znakami tabulacji w celu wklejenia do aplikacji, takich jak Notepad i Excel, oraz jako tabelę sformatowaną w formacie HTML do wklejania do aplikacji, takich jak Word.  
  
 Kopiowanie komórek można skonfigurować tak, aby kopiować tylko wartości komórek, w celu dołączania tekstu nagłówka wiersza i kolumny w danych Schowka lub do dołączania tekstu nagłówka tylko wtedy, gdy użytkownicy wybierają całe wiersze lub kolumny.  
  
 W zależności od trybu zaznaczania użytkownicy mogą wybrać wiele odłączonych grup komórek. Gdy użytkownik kopiuje komórki do schowka, wiersze i kolumny bez zaznaczonych komórek nie są kopiowane. Wszystkie inne wiersze lub kolumny stają się wierszami i kolumnami w tabeli danych skopiowanymi do Schowka. Niezaznaczone komórki w tych wierszach lub kolumnach są kopiowane jako puste symbole zastępcze do Schowka.  
  
### <a name="to-enable-cell-copying"></a>Aby włączyć kopiowanie komórek  
  
- Ustaw właściwość <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a>Przykład  
 Poniższy pełny kod ilustruje sposób kopiowania komórek do Schowka. Ten przykład zawiera przycisk, który kopiuje zaznaczone komórki do schowka przy użyciu metody <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> i wyświetla zawartość schowka w polu tekstowym.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten kod wymaga:  
  
- Odwołania do zestawów N:System i N:System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>
- <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>
- [Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
