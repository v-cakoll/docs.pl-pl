---
title: 'Instrukcje: pobieranie i ustawianie bieżącej komórki w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: fb71a6e3259d3007e11f528377c95a9c4cbeb023
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971330"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Instrukcje: pobieranie i ustawianie bieżącej komórki w kontrolce DataGridView formularzy systemu Windows
Interakcja z <xref:System.Windows.Forms.DataGridView> często wymaga się, że programowo odkryjesz komórki, która jest obecnie aktywna. Również może być konieczna zmiana bieżącej komórki. Możesz wykonywać te zadania za pomocą <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> właściwości.  
  
> [!NOTE]
>  Nie można ustawić bieżącej komórki w wierszu lub kolumnie, który ma jej <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> właściwością `false`.  
  
 W zależności od <xref:System.Windows.Forms.DataGridView> trybu zaznaczania kontrolki, zmieniania bieżącej komórki dokonać zmian. Aby uzyskać więcej informacji, zobacz [tryby wyboru w kontrolce DataGridView formularzy Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Aby programowo uzyskać bieżącej komórki  
  
- Użyj <xref:System.Windows.Forms.DataGridView> kontrolki <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> właściwości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Aby programowo ustawić bieżącej komórki  
  
- Ustaw <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> właściwość <xref:System.Windows.Forms.DataGridView> kontroli. W poniższym przykładzie kodu bieżącej komórki jest równa 0, kolumna 1 wiersz.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- <xref:System.Windows.Forms.Button> kontrolki o nazwie `getCurrentCellButton` i `setCurrentCellButton`. W elemencie wizualnym C#, należy dołączyć <xref:System.Windows.Forms.Control.Click> zdarzenia dla każdego przycisku do obsługi skojarzone ze zdarzeniem w przykładowym kodzie.  
  
- A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
- Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Tryby wyboru w kontrolce DataGridView formularzy Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
