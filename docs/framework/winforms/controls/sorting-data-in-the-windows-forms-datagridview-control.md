---
title: Sortowanie danych w formancie DataGridView formularzy Windows
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 606ffc7bd6136b775adaaaa79cf5042cf1e2dd70
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724924"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a>Sortowanie danych w formancie DataGridView formularzy Windows

Domyślnie użytkownicy mogą sortować dane w <xref:System.Windows.Forms.DataGridView> formantu przez kliknięcie nagłówka kolumny pola tekstowego (lub, naciskając klawisz F3, gdy komórka pole tekstowe koncentruje się na .NET Framework 4.7.2 i nowsze wersje). Możesz zmodyfikować <xref:System.Windows.Forms.DataGridViewColumn.SortMode> właściwości określone kolumny, aby zezwolić użytkownikom na sortowanie według innych typów kolumn, gdy warto to zrobić. Można również sortować dane programowo według dowolnej kolumny lub przez wiele kolumn.

## <a name="in-this-section"></a>W tej sekcji

[Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
W tym artykule opisano opcje sortowania danych w formancie.

[Instrukcje: Ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
W tym artykule opisano, jak umożliwić użytkownikom sortować według kolumn, które nie są sortowanie domyślne.

[Instrukcje: Dostosowywanie sortowania w kontrolce DataGridView formularzy Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
W tym artykule opisano sposób programowe sortowanie danych oraz dostosowywanie sortowania za pomocą <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> zdarzeń lub poprzez implementację <xref:System.Collections.IComparer> interfejsu.

## <a name="reference"></a>Tematy pomocy

<xref:System.Windows.Forms.DataGridView>  
Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView> kontroli.  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView.Sort%2A> metody.

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> właściwości.

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewColumnSortMode> wyliczenia.

## <a name="see-also"></a>Zobacz także

- [DataGridView, kontrolka](datagridview-control-windows-forms.md)
- [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
