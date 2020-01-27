---
title: Automatycznie zmieniaj rozmiar komórek, gdy zmienia się zawartość w formancie DataGridView
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
ms.openlocfilehash: 86e3bce993aa06546e301c6d7a7e03a31013c337
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732065"
---
# <a name="how-to-automatically-resize-cells-when-content-changes-in-the-windows-forms-datagridview-control"></a>Porady: automatyczne zmienianie rozmiaru komórek przy zmianie zawartości w formancie DataGridView formularzy systemu Windows
Można skonfigurować kontrolkę <xref:System.Windows.Forms.DataGridView>, aby zmienić rozmiar swoich wierszy, kolumn i nagłówków automatycznie przy każdej zmianie zawartości, dzięki czemu komórki są zawsze wystarczająco duże, aby wyświetlić ich wartości bez obcinania.  
  
 Istnieje wiele opcji ograniczających, które komórki są używane do określania nowych rozmiarów. Na przykład można skonfigurować kontrolkę tak, aby automatycznie zmieniała szerokość kolumn na podstawie wartości w wierszach, które są aktualnie wyświetlane. Dzięki temu można uniknąć nieefektywności podczas pracy z dużymi liczbami wierszy, chociaż w tym przypadku można użyć metod ustalania rozmiaru, takich jak <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>, aby dostosować rozmiary w miarę dokonania wyboru.  
  
 Aby uzyskać więcej informacji na temat automatycznej zmiany rozmiarów, zobacz [Opcje ustalania rozmiarów w kontrolce DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).  
  
 Poniższy przykład kodu demonstruje opcje dostępne dla automatycznej zmiany rozmiarów.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CPP/autosizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CS/autosizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/VB/autosizing.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [Zmiana rozmiaru wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Opcje ustalania rozmiaru w kontrolce DataGridView formularzy Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: zmienianie w sposób programowy rozmiaru komórek w celu dopasowania do zawartości w kontrolce DataGridView formularzy Windows Forms](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)
