---
title: Pobieranie i Ustawianie bieżącej komórki w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 0fb01d5392e02b53e0e5bf905c872dbeeb22fad9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745664"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Porady: pobieranie i ustawianie bieżącej komórki w formancie DataGridView formularzy systemu Windows
Interakcja z <xref:System.Windows.Forms.DataGridView> często wymaga, aby można było programowo wykryć, która komórka jest obecnie aktywna. Może być również konieczne Zmiana bieżącej komórki. Te zadania można wykonać za pomocą właściwości <xref:System.Windows.Forms.DataGridView.CurrentCell%2A>.  
  
> [!NOTE]
> Nie można ustawić bieżącej komórki w wierszu lub kolumnie, która ma właściwość <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> ustawioną na `false`.  
  
 W zależności od trybu zaznaczania kontrolki <xref:System.Windows.Forms.DataGridView>, zmiana bieżącej komórki może zmienić zaznaczenie. Aby uzyskać więcej informacji, zobacz [Tryby wyboru w kontrolce DataGridView Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Aby programowo pobrać bieżącą komórkę  
  
- Użyj właściwości <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> kontrolki <xref:System.Windows.Forms.DataGridView>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Aby programowo ustawić bieżącą komórkę  
  
- Ustaw właściwość <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> kontrolki <xref:System.Windows.Forms.DataGridView>. W poniższym przykładzie kodu bieżąca komórka jest ustawiona na wiersz 0, kolumna 1.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- <xref:System.Windows.Forms.Button> kontrolki o nazwach `getCurrentCellButton` i `setCurrentCellButton`. W wizualizacji C#należy dołączyć zdarzenia <xref:System.Windows.Forms.Control.Click> dla każdego przycisku do skojarzonego programu obsługi zdarzeń w przykładowym kodzie.  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Tryby wyboru w kontrolce DataGridView formularzy Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
