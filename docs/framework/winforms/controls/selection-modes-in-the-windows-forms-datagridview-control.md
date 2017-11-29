---
title: Tryby wyboru w formancie DataGridView formularzy systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f6b603382382971249b08cddd482566ec6e5fa5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Tryby wyboru w formancie DataGridView formularzy systemu Windows
Czasami ma aplikacji do wykonywania akcji na podstawie wybranych użytkowników w ramach <xref:System.Windows.Forms.DataGridView> formantu. W zależności od akcji których chcesz ograniczyć rodzaje wybór, które są możliwe. Na przykład załóżmy, że aplikację można wydrukować raportu dla aktualnie wybranego rekordu. W takim przypadku można skonfigurować <xref:System.Windows.Forms.DataGridView> sterowania, aby klikanie wiersza zawsze wybiera cały wiersz i tak aby tylko jeden wiersz jednocześnie można wybrać.  
  
 Możesz określić wartość dozwolona przez ustawienie <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> jedną z następujących właściwości <xref:System.Windows.Forms.DataGridViewSelectionMode> wartości wyliczenia.  
  
|Wartość DataGridViewSelectionMode|Opis|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Kliknięcie komórki zaznacza go. Nagłówki wierszy i kolumn nie może służyć do wyboru.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Kliknięcie komórki zaznacza go. Kliknięcie nagłówka kolumny zaznacza cały kolumny. Nagłówki kolumn nie można użyć do sortowania.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Kliknięcie nagłówka kolumny lub komórki zaznacza cały kolumny. Nagłówki kolumn nie można użyć do sortowania.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Kliknij komórkę lub nagłówka wiersza, aby zaznaczyć cały wiersz.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Domyślny tryb wyboru. Kliknięcie komórki zaznacza go. Kliknięcie nagłówka wiersza zaznacza cały wiersz.|  
  
> [!NOTE]
>  Zmiana trybu wyboru w czasie wykonywania automatycznie usuwa bieżące zaznaczenie.  
  
 Domyślnie użytkownicy mogą wybrać wiele wierszy, kolumny lub komórki przeciągając myszą, naciskając klawisz CTRL lub SHIFT podczas wybierania, aby rozszerzyć lub zmodyfikować zaznaczenie lub klikając komórkę nagłówka w lewym górnym, aby zaznaczyć wszystkie komórki w formancie. Aby temu zapobiec, należy ustawić <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> właściwości `false`.  
  
 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> i <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> tryby Zezwalaj użytkownikom na usuwanie wierszy, zaznaczając je i naciskając klawisz DELETE. Użytkownicy mogą usuwać wiersze tylko w przypadku bieżącej komórki nie jest w trybie edycji <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> właściwość jest ustawiona na `true`, i źródła danych obsługuje usunięcia wierszy zmiennych użytkownika. Należy pamiętać, te ustawienia nie uniemożliwiają usunięcie programowe wiersza.  
  
## <a name="programmatic-selection"></a>Programowy wybór  
 Bieżący tryb zaznaczania ogranicza zachowanie programowy wybór, a także wybór użytkownika. Bieżące zaznaczenie można zmienić programowo, ustawiając `Selected` właściwości żadnych komórek, wierszy lub kolumn w <xref:System.Windows.Forms.DataGridView> formantu. Można również zaznaczyć wszystkie komórki w formancie za pośrednictwem <xref:System.Windows.Forms.DataGridView.SelectAll%2A> metody, w zależności od trybu wyboru. Aby wyczyścić zaznaczenie, należy użyć <xref:System.Windows.Forms.DataGridView.ClearSelection%2A> metody.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> właściwość jest ustawiona na `true`, możesz dodać <xref:System.Windows.Forms.DataGridView> elementy lub usuń je z zaznaczenia, zmieniając `Selected` właściwości elementu. W przeciwnym razie ustawienie `Selected` właściwości `true` dla jednego elementu automatycznie usuwa inne elementy z zaznaczenia.  
  
 Należy pamiętać, że zmiana wartości <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> właściwość nie ma wpływu na bieżące zaznaczenie.  
  
 Kolekcja aktualnie zaznaczonych komórek, wierszy lub kolumn za pomocą można pobrać <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> właściwości <xref:System.Windows.Forms.DataGridView> formantu. Uzyskiwanie dostępu do tych właściwości jest nieefektywne w przypadku wybrania każdej komórki w formancie. Aby uniknąć w takim przypadku spadek wydajności, należy użyć <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metody pierwszy. Ponadto dostęp do tych kolekcji w celu ustalenia liczby zaznaczonych komórek, wierszy i kolumn może być mało wydajne. Zamiast tego należy używać <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>, lub <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A> metody, przekazując <xref:System.Windows.Forms.DataGridViewElementStates.Selected> wartość.  
  
> [!TIP]
>  Przykładowy kod, który demonstruje programowy użycia zaznaczonych komórek można znaleźć w <xref:System.Windows.Forms.DataGridView> Przegląd klasy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
 <xref:System.Windows.Forms.DataGridViewSelectionMode>  
 [Wybór i używanie Schowka z formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 [Porady: Ustawianie trybu zaznaczania formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
