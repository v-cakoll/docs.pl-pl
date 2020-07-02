---
title: Pobieranie i Ustawianie bieżącej komórki w formancie DataGridView
description: Dowiedz się, jak programowo wykryć, która komórka jest aktualnie aktywna, pobierając i ustawiając bieżącą komórkę w kontrolce DataGridView Windows Forms.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 1651ca9c8fa0329f9435a70ce777bce68f15ff63
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622214"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Porady: pobieranie i ustawianie bieżącej komórki w formancie DataGridView formularzy systemu Windows
Interakcja z <xref:System.Windows.Forms.DataGridView> często wymaga, aby programowo wykryć, która komórka jest obecnie aktywna. Może być również konieczne Zmiana bieżącej komórki. Te zadania można wykonać przy użyciu <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> właściwości.  
  
> [!NOTE]
> Nie można ustawić bieżącej komórki w wierszu lub kolumnie, która ma <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> ustawioną właściwość `false` .  
  
 W zależności od <xref:System.Windows.Forms.DataGridView> trybu zaznaczania kontrolki Zmiana bieżącej komórki może zmienić zaznaczenie. Aby uzyskać więcej informacji, zobacz [Tryby wyboru w kontrolce DataGridView Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Aby programowo pobrać bieżącą komórkę  
  
- Użyj <xref:System.Windows.Forms.DataGridView> właściwości kontrolki <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Aby programowo ustawić bieżącą komórkę  
  
- Ustaw <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> Właściwość <xref:System.Windows.Forms.DataGridView> formantu. W poniższym przykładzie kodu bieżąca komórka jest ustawiona na wiersz 0, kolumna 1.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- <xref:System.Windows.Forms.Button>kontrolki nazwane `getCurrentCellButton` i `setCurrentCellButton` . W języku Visual C# należy dołączyć <xref:System.Windows.Forms.Control.Click> zdarzenia dla każdego przycisku do skojarzonego programu obsługi zdarzeń w przykładowym kodzie.  
  
- <xref:System.Windows.Forms.DataGridView>Kontrolka o nazwie `dataGridView1` .  
  
- Odwołania do <xref:System?displayProperty=nameWithType> zestawów i <xref:System.Windows.Forms?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Tryby wyboru w kontrolce DataGridView formularzy Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
