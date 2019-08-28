---
title: Tryby wyboru w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: cfe80d5ccb73208f1c61a2ac6c9963343d398bcb
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046420"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Tryby wyboru w formancie DataGridView formularzy systemu Windows

Czasami aplikacja ma wykonywać działania w oparciu o wybory użytkownika w <xref:System.Windows.Forms.DataGridView> kontrolce. W zależności od akcji można ograniczyć wybór możliwy do wyboru. Załóżmy na przykład, że aplikacja może wydrukować raport dla aktualnie wybranego rekordu. W takim przypadku można skonfigurować <xref:System.Windows.Forms.DataGridView> kontrolkę tak, aby kliknięcia w dowolnym miejscu w wierszu zawsze zaznaczają cały wiersz i tak, aby można było wybrać tylko jeden wiersz naraz.

Można określić opcje dozwolone przez ustawienie <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> właściwości na jedną z następujących <xref:System.Windows.Forms.DataGridViewSelectionMode> wartości wyliczenia.

|DataGridViewSelectionMode wartość|Opis|
|-------------------------------------|-----------------|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Kliknięcie komórki spowoduje jej wybranie. Nagłówki wierszy i kolumn nie mogą być używane do zaznaczania.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Kliknięcie komórki spowoduje jej wybranie. Kliknięcie nagłówka kolumny powoduje wybranie całej kolumny. Nagłówki kolumn nie mogą być używane do sortowania.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Kliknięcie komórki lub nagłówka kolumny powoduje zaznaczenie całej kolumny. Nagłówki kolumn nie mogą być używane do sortowania.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Kliknięcie komórki lub nagłówka wiersza powoduje zaznaczenie całego wiersza.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Domyślny tryb zaznaczania. Kliknięcie komórki spowoduje jej wybranie. Kliknięcie nagłówka wiersza powoduje zaznaczenie całego wiersza.|

> [!NOTE]
> Zmiana trybu wyboru w czasie wykonywania automatycznie czyści bieżące zaznaczenie.

Domyślnie użytkownicy mogą zaznaczyć wiele wierszy, kolumn lub komórek przeciągając myszą, naciskając klawisz CTRL lub SHIFT podczas zaznaczania lub modyfikowania zaznaczenia lub klikając komórkę nagłówka w lewym górnym rogu, aby zaznaczyć wszystkie komórki w formancie. Aby uniknąć tego zachowania, należy ustawić <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> właściwość na `false`.

Tryby <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> i<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> umożliwiają użytkownikom usuwanie wierszy, zaznaczając je i naciskając klawisz Delete. Użytkownicy mogą usuwać wiersze tylko wtedy, gdy bieżąca komórka nie jest w trybie edycji, <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> właściwość jest ustawiona na `true`, a bazowe źródło danych obsługuje usuwanie wierszy sterowane przez użytkownika. Należy zauważyć, że te ustawienia nie uniemożliwiają programowego usuwania wierszy.

## <a name="programmatic-selection"></a>Wybór programistyczny

Tryb bieżącego wyboru ogranicza zachowanie wyboru programistycznego, a także wybór użytkownika. Bieżące zaznaczenie można zmienić programowo przez ustawienie `Selected` właściwości dowolnych komórek, wierszy lub kolumn znajdujących <xref:System.Windows.Forms.DataGridView> się w kontrolce. Możesz również zaznaczyć wszystkie komórki w kontrolce za pomocą <xref:System.Windows.Forms.DataGridView.SelectAll%2A> metody, w zależności od trybu zaznaczania. Aby wyczyścić zaznaczenie, użyj <xref:System.Windows.Forms.DataGridView.ClearSelection%2A> metody.

Jeśli właściwość jest ustawiona na `true`, można dodawać <xref:System.Windows.Forms.DataGridView> elementy do zaznaczenia lub z nich `Selected` usuwać, zmieniając właściwość elementu. <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> W przeciwnym razie ustawienie `Selected` `true` właściwości dla jednego elementu automatycznie usunie inne elementy z zaznaczenia.

Należy zauważyć, że zmiana wartości <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> właściwości nie powoduje zmiany bieżącego zaznaczenia.

Można pobrać kolekcję obecnie zaznaczonych komórek, wierszy <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>lub kolumn za pomocą właściwości <xref:System.Windows.Forms.DataGridView> , <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> kontrolki. Dostęp do tych właściwości jest nieefektywny, gdy jest zaznaczona każda komórka w kontrolce. Aby uniknąć spadek wydajności w tym przypadku, należy najpierw użyć <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metody. Ponadto uzyskanie dostępu do tych kolekcji pozwala określić liczbę wybranych komórek, wierszy lub kolumn, które mogą być niewydajne. Zamiast <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>tego należy użyć metody, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>, lub <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A> , przekazując <xref:System.Windows.Forms.DataGridViewElementStates.Selected> wartość.

> [!TIP]
> Przykładowy kod, który demonstruje użycie programistyczne wybranych komórek, można znaleźć w <xref:System.Windows.Forms.DataGridView> temacie Omówienie klasy.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Instrukcje: Ustawianie trybu zaznaczania Windows Forms formancie DataGridView](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
