---
title: 'Instrukcje: dostosowywanie sortowania w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 0e7dffa45dc8d3ac467129d44a7c73a8c4b4bfa2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59192917"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a>Instrukcje: dostosowywanie sortowania w kontrolce DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Control oferuje automatyczne sortowanie, ale w zależności od potrzeb, może być konieczne dostosowanie operacjach sortowania. Na przykład umożliwia sortowanie programowe tworzenie alternatywny interfejs użytkownika (UI). Alternatywnie, można obsługiwać <xref:System.Windows.Forms.DataGridView.SortCompare> zdarzenia lub wywołanie `Sort(IComparer)` przeciążenia <xref:System.Windows.Forms.DataGridView.Sort%2A> metody sortowania funkcje i elastyczność, takich jak sortowanie wielu kolumn.  
  
 Poniższe przykłady kodu ilustrują te trzy sposoby sortowania niestandardowych. Aby uzyskać więcej informacji, zobacz [Tryb sortowania kolumn w formancie DataGridView formularzy Windows](column-sort-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="programmatic-sorting"></a>Programowe sortowanie  
 Poniższy przykład kodu demonstruje programowe sortowanie, za pomocą <xref:System.Windows.Forms.DataGridView.SortOrder%2A> i <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> właściwości, aby określić kierunek sortowania, a <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> właściwości, aby ręcznie ustawić symbol sortowania. `Sort(DataGridViewColumn,ListSortDirection)` Przeciążenia <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda jest używana do sortowania danych tylko w przypadku zaznaczenia jednej kolumny.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a>Niestandardowe sortowanie, za pomocą zdarzenia SortCompare  
 Poniższy przykład kodu demonstruje, niestandardowe sortowanie, za pomocą <xref:System.Windows.Forms.DataGridView.SortCompare> programu obsługi zdarzeń. Wybrane <xref:System.Windows.Forms.DataGridViewColumn> jest sortowana i, jeśli istnieją zduplikowane wartości w kolumnie, kolumna Identyfikatora służy do określenia końcowego zamówienia.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a>Sortowanie niestandardowe przy użyciu interfejsu IComparer  
 Poniższy przykład kodu demonstruje, niestandardowe sortowanie, za pomocą `Sort(IComparer)` przeciążenia <xref:System.Windows.Forms.DataGridView.Sort%2A> metody, która przyjmuje implementację <xref:System.Collections.IComparer> interfejsu, aby wykonać sortowanie wielu kolumn.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wymagaj tych przykładach:  
  
-   Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
 Aby uzyskać informacje o tworzeniu tych przykładów z poziomu wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Sortowanie danych w kontrolce DataGridView formularzy Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)
