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
ms.openlocfilehash: 670708f342e1cd1ac495c215b7508093349ac2e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933700"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Instrukcje: pobieranie i ustawianie bieżącej komórki w kontrolce DataGridView formularzy systemu Windows
Interakcja z <xref:System.Windows.Forms.DataGridView> często wymaga, aby programowo wykryć, która komórka jest obecnie aktywna. Może być również konieczne Zmiana bieżącej komórki. Te zadania można wykonać przy użyciu <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> właściwości.  
  
> [!NOTE]
> Nie można ustawić bieżącej komórki w wierszu lub kolumnie, która ma <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> `false`ustawioną właściwość.  
  
 W zależności <xref:System.Windows.Forms.DataGridView> od trybu zaznaczania kontrolki Zmiana bieżącej komórki może zmienić zaznaczenie. Aby uzyskać więcej informacji, zobacz [Tryby wyboru w kontrolce DataGridView Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Aby programowo pobrać bieżącą komórkę  
  
- <xref:System.Windows.Forms.DataGridView> Użyj właściwości<xref:System.Windows.Forms.DataGridView.CurrentCell%2A> kontrolki.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Aby programowo ustawić bieżącą komórkę  
  
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> Ustaw Właściwość<xref:System.Windows.Forms.DataGridView> formantu. W poniższym przykładzie kodu bieżąca komórka jest ustawiona na wiersz 0, kolumna 1.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- <xref:System.Windows.Forms.Button>kontrolki `getCurrentCellButton` nazwane `setCurrentCellButton`i. W wizualizacji C#, należy dołączyć <xref:System.Windows.Forms.Control.Click> zdarzenia dla każdego przycisku do skojarzonego programu obsługi zdarzeń w przykładowym kodzie.  
  
- Kontrolka o `dataGridView1`nazwie. <xref:System.Windows.Forms.DataGridView>  
  
- Odwołania do <xref:System?displayProperty=nameWithType> zestawów i <xref:System.Windows.Forms?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Tryby wyboru w kontrolce DataGridView formularzy Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
