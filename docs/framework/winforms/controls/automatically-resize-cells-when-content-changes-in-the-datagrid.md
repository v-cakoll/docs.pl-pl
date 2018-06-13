---
title: 'Porady: automatyczne zmienianie rozmiaru komórek przy zmianie zawartości w formancie DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells automatically
- cells [Windows Forms], resizing automatically
- DataGridView control [Windows Forms], resizing cells
ms.assetid: 1d68934d-a04c-4b12-9e66-c856c6828131
ms.openlocfilehash: f93d2ddc0e60c6d66efb43fe672f4c3076af85f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525794"
---
# <a name="how-to-automatically-resize-cells-when-content-changes-in-the-windows-forms-datagridview-control"></a>Porady: automatyczne zmienianie rozmiaru komórek przy zmianie zawartości w formancie DataGridView formularzy systemu Windows
Można skonfigurować <xref:System.Windows.Forms.DataGridView> kontroli zmiany rozmiaru jego wiersze, kolumny i nagłówki automatycznie po każdej zmianie zmian zawartości, dzięki czemu komórek zawsze są wystarczająco duże, aby wyświetlić ich wartości bez przycinania.  
  
 Istnieje wiele opcji, aby ograniczyć komórek, które są używane do określania nowe rozmiary. Na przykład można skonfigurować formant automatycznie zmienia szerokość jego kolumn, tylko na podstawie wartości w wierszach, które są aktualnie wyświetlane. Dzięki temu można uniknąć nieefektywne podejście podczas pracy z dużą liczbę wierszy, mimo że w takim przypadku można używać metod zmiany rozmiaru, takich jak <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> dostosowanie rozmiaru w czasie wybrane.  
  
 Aby uzyskać więcej informacji na temat automatycznej zmiany rozmiaru, zobacz [opcje rozmiaru w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).  
  
 Poniższy przykład kodu pokazuje opcji dostępnych dla automatyczną zmianę rozmiaru.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Windows.Forms.DataGridView.AutoSizing#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CPP/autosizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.AutoSizing#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CS/autosizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.AutoSizing#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/VB/autosizing.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.  
  
-   Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>  
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>  
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>  
 [Zmiana rozmiaru wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 [Opcje ustalania rozmiaru w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 [Instrukcje: zmienianie w sposób programowy rozmiaru komórek w celu dopasowania do zawartości w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)
