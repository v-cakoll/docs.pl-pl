---
title: Tryby wyboru w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: e20bf6307d77bf189b698e847c6b855c249dc3c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743040"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Tryby wyboru w formancie DataGridView formularzy systemu Windows

Czasami chcesz, aby aplikacja wykonywała akcje na podstawie opcji wybranych przez użytkownika w ramach kontrolki <xref:System.Windows.Forms.DataGridView>. W zależności od akcji można ograniczyć wybór możliwy do wyboru. Załóżmy na przykład, że aplikacja może wydrukować raport dla aktualnie wybranego rekordu. W takim przypadku można skonfigurować kontrolkę <xref:System.Windows.Forms.DataGridView> tak, aby kliknięcia w dowolnym miejscu w wierszu zawsze zaznaczają cały wiersz i aby można było wybrać tylko jeden wiersz naraz.

Można określić opcje dozwolone przez ustawienie właściwości <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> na jedną z następujących <xref:System.Windows.Forms.DataGridViewSelectionMode> wartości wyliczenia.

|DataGridViewSelectionMode wartość|Opis|
|-------------------------------------|-----------------|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Kliknięcie komórki spowoduje jej wybranie. Nagłówki wierszy i kolumn nie mogą być używane do zaznaczania.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Kliknięcie komórki spowoduje jej wybranie. Kliknięcie nagłówka kolumny powoduje wybranie całej kolumny. Nagłówki kolumn nie mogą być używane do sortowania.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Kliknięcie komórki lub nagłówka kolumny powoduje zaznaczenie całej kolumny. Nagłówki kolumn nie mogą być używane do sortowania.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Kliknięcie komórki lub nagłówka wiersza powoduje zaznaczenie całego wiersza.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Domyślny tryb zaznaczania. Kliknięcie komórki spowoduje jej wybranie. Kliknięcie nagłówka wiersza powoduje zaznaczenie całego wiersza.|

> [!NOTE]
> Zmiana trybu wyboru w czasie wykonywania automatycznie czyści bieżące zaznaczenie.

Domyślnie użytkownicy mogą zaznaczyć wiele wierszy, kolumn lub komórek przeciągając myszą, naciskając klawisz CTRL lub SHIFT podczas zaznaczania lub modyfikowania zaznaczenia lub klikając komórkę nagłówka w lewym górnym rogu, aby zaznaczyć wszystkie komórki w formancie. Aby uniknąć tego zachowania, ustaw właściwość <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> na `false`.

Tryby <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> i <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> umożliwiają użytkownikom usuwanie wierszy, zaznaczając je i naciskając klawisz DELETE. Użytkownicy mogą usuwać wiersze tylko wtedy, gdy bieżąca komórka nie jest w trybie edycji, właściwość <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> jest ustawiona na `true`, a bazowe źródło danych obsługuje usuwanie wierszy sterowane przez użytkownika. Należy zauważyć, że te ustawienia nie uniemożliwiają programowego usuwania wierszy.

## <a name="programmatic-selection"></a>Wybór programistyczny

Tryb bieżącego wyboru ogranicza zachowanie wyboru programistycznego, a także wybór użytkownika. Bieżące zaznaczenie można zmienić programowo przez ustawienie właściwości `Selected` dowolnych komórek, wierszy lub kolumn znajdujących się w kontrolce <xref:System.Windows.Forms.DataGridView>. Możesz również zaznaczyć wszystkie komórki w kontrolce za pomocą metody <xref:System.Windows.Forms.DataGridView.SelectAll%2A>, w zależności od trybu zaznaczania. Aby wyczyścić zaznaczenie, użyj metody <xref:System.Windows.Forms.DataGridView.ClearSelection%2A>.

Jeśli właściwość <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> jest ustawiona na `true`, można dodać elementy <xref:System.Windows.Forms.DataGridView> lub usunąć je z zaznaczenia, zmieniając właściwość `Selected` elementu. W przeciwnym razie ustawienie właściwości `Selected` na `true` dla jednego elementu automatycznie usunie inne elementy z zaznaczenia.

Należy zauważyć, że zmiana wartości właściwości <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> nie powoduje zmiany bieżącego zaznaczenia.

Możesz pobrać kolekcję obecnie zaznaczonych komórek, wierszy lub kolumn za pomocą właściwości <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> formantu <xref:System.Windows.Forms.DataGridView>. Dostęp do tych właściwości jest nieefektywny, gdy jest zaznaczona każda komórka w kontrolce. Aby uniknąć spadek wydajności w tym przypadku, najpierw Użyj metody <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>. Ponadto uzyskanie dostępu do tych kolekcji pozwala określić liczbę wybranych komórek, wierszy lub kolumn, które mogą być niewydajne. Zamiast tego należy użyć metody <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>lub <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A>, przekazując wartość <xref:System.Windows.Forms.DataGridViewElementStates.Selected>.

> [!TIP]
> Przykładowy kod, który demonstruje użycie programistyczne wybranych komórek, można znaleźć w temacie <xref:System.Windows.Forms.DataGridView> klasy Przegląd.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Instrukcje: ustawianie trybu zaznaczania kontrolki DataGridView formularzy Windows Forms](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
