---
title: 'Instrukcje: Programowe zmienianie rozmiaru komórek w celu dopasowania do zawartości w kontrolce DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells to fit content
- cells [Windows Forms], resizing to fit contents
- DataGridView control [Windows Forms], resizing cells
- grids [Windows Forms], resizing cells to fit content
ms.assetid: 63d770dc-b3f5-462b-901a-3125b2753792
ms.openlocfilehash: 09ac5e43653a3389737777258db3bb5e0ed4c0a1
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722922"
---
# <a name="how-to-programmatically-resize-cells-to-fit-content-in-the-windows-forms-datagridview-control"></a>Instrukcje: Programowe zmienianie rozmiaru komórek w celu dopasowania do zawartości w kontrolce DataGridView formularzy Windows Forms
Możesz użyć <xref:System.Windows.Forms.DataGridView> kontrolować metody, aby zmienić rozmiar wiersze, kolumny i nagłówków, tak że wyświetlają one całej wartości bez obcinania. Można użyć tych metod, aby zmienić rozmiar <xref:System.Windows.Forms.DataGridView> elementy w czasie wybrane. Alternatywnie można skonfigurować formant Aby automatycznie zmienić rozmiar tych elementów, zawsze wtedy, gdy zmiany zawartości. Może to być mało wydajne, jednak podczas pracy z dużymi zestawami danych lub jeśli dane zmieniają się często. Aby uzyskać więcej informacji, zobacz [opcje ustalania rozmiaru w formancie DataGridView formularzy Windows](sizing-options-in-the-windows-forms-datagridview-control.md).  
  
 Zazwyczaj można programowo skoryguje <xref:System.Windows.Forms.DataGridView> elementy, aby zmieścić ich zawartość tylko wtedy, gdy ładowanie nowych danych ze źródła danych lub wartość ma edytować użytkownika. Dzięki takiemu grupowaniu można zoptymalizować wydajność, ale jest to również przydatne, jeśli chcesz umożliwić użytkownikom w taki sposób ręcznie zmienić rozmiar wierszy i kolumn za pomocą myszy.  
  
 Poniższy przykład kodu demonstruje opcje dostępne i umożliwiają programowe Zmienianie rozmiaru.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CPP/programmaticsizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CS/programmaticsizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/VB/programmaticsizing.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [Zmiana rozmiaru wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Opcje ustalania rozmiaru w kontrolce DataGridView formularzy Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Automatycznie zmienia rozmiar komórek, gdy zmienia się zawartość w kontrolce DataGridView formularzy Windows Forms](automatically-resize-cells-when-content-changes-in-the-datagrid.md)
