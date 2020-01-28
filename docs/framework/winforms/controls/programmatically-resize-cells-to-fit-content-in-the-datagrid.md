---
title: Programistyczne Zmienianie rozmiaru komórek w celu dopasowania do zawartości w formancie DataGridView
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
ms.openlocfilehash: df3b378a8ba358fa0bfe549a7901b3d59d53f556
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742448"
---
# <a name="how-to-programmatically-resize-cells-to-fit-content-in-the-windows-forms-datagridview-control"></a>Porady: zmienianie w sposób programowy rozmiaru komórek w celu dopasowania do zawartości w formancie DataGridView formularzy systemu Windows
Można użyć metod kontroli <xref:System.Windows.Forms.DataGridView>, aby zmienić rozmiar wierszy, kolumn i nagłówków, tak aby wyświetlały ich całe wartości bez obcinania. Za pomocą tych metod można zmieniać rozmiar <xref:System.Windows.Forms.DataGridView> elementów w miarę dokonania wyboru. Alternatywnie można skonfigurować kontrolkę do automatycznego zmieniania rozmiaru tych elementów przy każdej zmianie zawartości. Może to być niewydajne, jednak gdy pracujesz z dużymi zestawami danych lub często zmieniają się dane. Aby uzyskać więcej informacji, zobacz [Opcje ustalania rozmiarów w kontrolce DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).  
  
 Zwykle program programowo dostosowuje elementy <xref:System.Windows.Forms.DataGridView>, aby dopasować ich zawartość tylko podczas ładowania nowych danych ze źródła danych lub podczas edytowania wartości przez użytkownika. Jest to przydatne w celu optymalizacji wydajności, ale jest również przydatne, gdy chcesz umożliwić użytkownikom ręczne zmienianie rozmiaru wierszy i kolumn za pomocą myszy.  
  
 Poniższy przykład kodu demonstruje dostępne opcje umożliwiające programistyczne zmienianie rozmiarów.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CPP/programmaticsizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CS/programmaticsizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/VB/programmaticsizing.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Drawing i system. Windows. Forms.  
  
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
- [Instrukcje: automatyczne zmienianie rozmiaru komórek przy zmianie zawartości w kontrolce DataGridView formularzy Windows Forms](automatically-resize-cells-when-content-changes-in-the-datagrid.md)
