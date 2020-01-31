---
title: Sortowanie danych w formancie DataGridView
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 1fcd5a5f5c6d690c573c4c2c5fa7c32aa0292441
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742945"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a>Sortowanie danych w kontrolce DataGridView Windows Forms

Domyślnie użytkownicy mogą sortować dane w kontrolce <xref:System.Windows.Forms.DataGridView>, klikając nagłówek kolumny pola tekstowego (lub naciskając klawisz F3, gdy komórka pola tekstowego koncentruje się na .NET Framework 4.7.2 i nowszych wersjach). Możesz zmodyfikować właściwość <xref:System.Windows.Forms.DataGridViewColumn.SortMode> określonych kolumn, aby umożliwić użytkownikom sortowanie według innych typów kolumn, gdy ma to sens. Możesz również sortować dane programowo według dowolnej kolumny lub według wielu kolumn.

## <a name="in-this-section"></a>W tej sekcji

[Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
Opisuje opcje sortowania danych w formancie.

[Instrukcje: ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
Opisuje, jak umożliwić użytkownikom sortowanie według kolumn, które nie są domyślnie sortowane.

[Instrukcje: dostosowywanie sortowania w kontrolce DataGridView Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
Opisuje sposób programistycznego sortowania danych i dostosowywania sortowania przy użyciu zdarzenia <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> lub przez implementację interfejsu <xref:System.Collections.IComparer>.

## <a name="reference"></a>Tematy pomocy

<xref:System.Windows.Forms.DataGridView>  
Zawiera dokumentację referencyjną dla kontrolki <xref:System.Windows.Forms.DataGridView>.  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
Zawiera dokumentację referencyjną dla metody <xref:System.Windows.Forms.DataGridView.Sort%2A>.

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
Zawiera dokumentację referencyjną dla właściwości <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>.

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
Zawiera dokumentację referencyjną dla wyliczenia <xref:System.Windows.Forms.DataGridViewColumnSortMode>.

## <a name="see-also"></a>Zobacz także

- [DataGridView, kontrolka](datagridview-control-windows-forms.md)
- [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
