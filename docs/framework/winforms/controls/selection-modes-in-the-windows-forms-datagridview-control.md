---
title: Tryby wyboru w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: c512a296f618ab32781dd8718a47c4b20fd7f54a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745912"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Tryby wyboru w formancie DataGridView formularzy systemu Windows
Czasami aplikacja do wykonania akcji, w zależności od wyborów użytkownika w ramach <xref:System.Windows.Forms.DataGridView> kontroli. W zależności od akcji można ograniczyć rodzajów wyboru, które są możliwe. Na przykład załóżmy, że aplikację można wydrukować raport dla obecnie wybranego rekordu. W takich przypadkach możesz chcieć skonfigurować <xref:System.Windows.Forms.DataGridView> kontrolki tak, aby klikanie wiersz zawsze wybiera cały wiersz, i tak aby tylko jeden wiersz jednocześnie można wybrać.  
  
 Można określić opcji dozwolone przez ustawienie <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> jedną z następujących właściwości <xref:System.Windows.Forms.DataGridViewSelectionMode> wartości wyliczenia.  
  
|Wartość DataGridViewSelectionMode|Opis|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Kliknij komórkę, aby zaznaczyć go. Nagłówki wierszy i kolumn nie można używać do wyboru.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Kliknij komórkę, aby zaznaczyć go. Kliknij nagłówek kolumny, aby zaznaczyć całą kolumnę. Nagłówki kolumn nie można użyć do sortowania.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Kliknij komórkę lub nagłówek kolumny, aby zaznaczyć całą kolumnę. Nagłówki kolumn nie można użyć do sortowania.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Kliknij komórkę lub nagłówek wiersza, aby zaznaczyć cały wiersz.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Domyślny tryb wyboru. Kliknij komórkę, aby zaznaczyć go. Kliknij nagłówek wiersza, aby zaznaczyć cały wiersz.|  
  
> [!NOTE]
>  Zmiana trybu zaznaczania w czasie wykonywania, automatycznie wyczyści bieżące zaznaczenie.  
  
 Domyślnie użytkownicy mogą wybrać wiele wierszy, kolumny lub komórki, przeciągając myszą, naciskając klawisz CTRL lub SHIFT podczas zaznaczania, aby rozszerzyć lub zmodyfikować zaznaczenie lub klikając komórkę nagłówka w lewym górnym rogu, aby zaznaczyć wszystkie komórki w formancie. Aby temu zapobiec, należy ustawić <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> właściwość `false`.  
  
 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> i <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> tryby Zezwalaj użytkownikom na usuwanie wierszy, zaznaczając je i naciskając klawisz DELETE. Użytkownicy mogą usuwać wiersze, tylko wtedy, gdy bieżącej komórki nie jest w trybie edycji <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> właściwość jest ustawiona na `true`, i źródła danych obsługuje usuwania wiersza oparte na użytkownika. Należy pamiętać, te ustawienia nie uniemożliwiają usunięcie programowe wiersza.  
  
## <a name="programmatic-selection"></a>Wybór programowy  
 Bieżący tryb wyboru ogranicza zachowanie programowy wybór, a także wybór użytkownika. Bieżące zaznaczenie można zmienić programowo przez ustawienie `Selected` właściwość żadnych komórek, wierszy lub kolumn w <xref:System.Windows.Forms.DataGridView> kontroli. Możesz również wybrać wszystkie komórki w formancie za pośrednictwem <xref:System.Windows.Forms.DataGridView.SelectAll%2A> metody, w zależności od trybu wyboru. Aby wyczyścić zaznaczenie, należy użyć <xref:System.Windows.Forms.DataGridView.ClearSelection%2A> metody.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> właściwość jest ustawiona na `true`, możesz dodać <xref:System.Windows.Forms.DataGridView> elementy, aby je lub usuń zaznaczenie, zmieniając `Selected` właściwości elementu. W przeciwnym razie ustawienie `Selected` właściwość `true` dla jednego elementu automatycznie usuwa innych elementów z zaznaczenia.  
  
 Należy pamiętać, że zmiana wartości <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> właściwość nie ma wpływu na bieżące zaznaczenie.  
  
 Możesz pobrać zbiór aktualnie zaznaczonych komórek, wierszy lub kolumn za pomocą <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> właściwości <xref:System.Windows.Forms.DataGridView> kontroli. Uzyskiwanie dostępu do tych właściwości jest nieefektywne, w przypadku wybrania każdej komórki w formancie. Aby uniknąć w tym przypadku spadek wydajności, należy użyć <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metoda pierwszy. Ponadto dostęp do tych kolekcji, aby określić liczbę wybranych komórek, wierszy lub kolumn może być mało wydajne. Zamiast tego należy używać <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>, lub <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A> metody, przekazując <xref:System.Windows.Forms.DataGridViewElementStates.Selected> wartość.  
  
> [!TIP]
>  Przykładowy kod, który demonstruje użycie programowe zaznaczonych komórek można znaleźć w <xref:System.Windows.Forms.DataGridView> klasa — Przegląd.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Instrukcje: Ustawianie trybu zaznaczania kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
