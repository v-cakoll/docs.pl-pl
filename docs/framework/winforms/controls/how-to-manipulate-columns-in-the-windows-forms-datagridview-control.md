---
title: 'Instrukcje: Manipulowanie kolumnami w kontrolce DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGridView control [Windows Forms], manipulating columns
- columns [Windows Forms], manipulating
- data grids [Windows Forms], manipulating columns
ms.assetid: d8cfe6b3-bbab-4182-bec2-0517d9f1eaf6
ms.openlocfilehash: a2c2ae94fb769b6b2455d309db9dbc2231138ea0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496810"
---
# <a name="how-to-manipulate-columns-in-the-windows-forms-datagridview-control"></a>Instrukcje: Manipulowanie kolumnami w kontrolce DataGridView formularzy Windows Forms

Poniższy przykład kodu pokazuje różne sposoby manipulowania <xref:System.Windows.Forms.DataGridView> kolumn przy użyciu właściwości <xref:System.Windows.Forms.DataGridViewColumn> klasy.

## <a name="example"></a>Przykład

[!code-cpp[System.Windows.Forms.DataGridView.ButtonDemos#100](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CPP/DataGridViewColumnDemo.cpp#100)]
[!code-csharp[System.Windows.Forms.DataGridView.ButtonDemos#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CS/DataGridViewColumnDemo.cs#100)]
[!code-vb[System.Windows.Forms.DataGridView.ButtonDemos#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/VB/datagridviewcolumndemo.vb#100)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.

Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewBand>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Programowanie przy użyciu komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
