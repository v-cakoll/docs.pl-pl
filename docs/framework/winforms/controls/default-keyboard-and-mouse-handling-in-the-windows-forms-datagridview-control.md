---
title: Domyślna obsługa w formancie DataGridView formularzy Windows myszy i klawiatury
ms.date: 02/13/2018
helpviewer_keywords:
- data grids [Windows Forms], mouse handling
- DataGridView control [Windows Forms], navigation keys
- keyboards [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], keyboard handling
- mouse [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], mouse handling
- navigation keys [Windows Forms], DataGridView control
ms.assetid: 4519b928-bfc8-4e8b-bb9c-b1e76a0ca552
ms.openlocfilehash: 4d0a3cb7a56b388ee9bd3f932f9fec604b39fa62
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521767"
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>Domyślna obsługa w formancie DataGridView formularzy Windows myszy i klawiatury

W poniższych tabelach opisano, jak użytkownicy mogą korzystać z <xref:System.Windows.Forms.DataGridView> sterowanie za pośrednictwem klawiatury i myszy.  
  
> [!NOTE]
>  Aby dostosować zachowanie klawiatury, można obsługiwać zdarzenia standardowy interfejs użytkownika takich jak <xref:System.Windows.Forms.Control.KeyDown>. Jednak w trybie edycji hostowanej kontrolka edycji odbiera danych wprowadzonych z klawiatury i nie występują zdarzenia klawiatury dla <xref:System.Windows.Forms.DataGridView> kontroli. Obsługa zdarzeń formantów edycji, należy dołączyć do edycji kontrolek w inne programy obsługi <xref:System.Windows.Forms.DataGridView.EditingControlShowing> programu obsługi zdarzeń. Alternatywnie, można dostosować zachowanie klawiatury w <xref:System.Windows.Forms.DataGridView> podklasy przez zastąpienie <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> i <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A> metody.  
  
## <a name="default-keyboard-handling"></a>Domyślna obsługa klawiatury  
  
### <a name="basic-navigation-and-entry-keys"></a>Podstawowe klucze nawigacji i zapis  
  
|Klawisz lub kombinację klawiszy|Opis|  
|----------------------------|-----------------|  
|STRZAŁKA W DÓŁ|Przenosi fokus do komórki bezpośrednio poniżej bieżącej komórki. Jeśli fokus jest ustawiony w ostatnim wierszu, nic nie robi.|  
|STRZAŁKA W LEWO|Przenosi fokus do poprzedniej komórki w wierszu. Jeśli fokus znajduje się w pierwszej komórki w wierszu, nic nie robi.|  
|STRZAŁKA W PRAWO|Przenosi fokus do następnej komórki w wierszu. Jeśli fokus znajduje się w ostatniej komórki w wierszu, nic nie robi.|  
|STRZAŁKA W GÓRĘ|Przenosi fokus do komórki bezpośrednio powyżej bieżącej komórki. Jeśli fokus jest ustawiony w pierwszym wierszu, nic nie robi.|  
|STRONA GŁÓWNA|Przenosi fokus do pierwszej komórki w bieżącym wierszu.|  
|END|Przenosi fokus do ostatniej komórki w bieżącym wierszu.|  
|PAGE DOWN|Przewija formant w dół przez liczbę wierszy, które w pełni są wyświetlane. Przenosi fokus do ostatniego wiersza pełni wyświetlane bez zmieniania kolumn.|  
|PAGE UP|Przewija w górę kontrolki, przez liczbę wierszy, które w pełni są wyświetlane. Przenosi fokus do pierwszego wiersza wyświetlane bez zmieniania kolumn.|  
|TAB|Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `false`, przenosi fokus do następnej komórki w bieżącym wierszu. Jeśli fokus jest już w komórce ostatni wiersz, przenosi fokus do pierwszej komórki w kolejnym wierszu. Jeśli fokus znajduje się w ostatniej komórki w formancie, przenosi fokus do następnej kontrolki w kolejności tabulacji kontenera nadrzędnego.<br /><br /> Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `true`, przenosi fokus do następnej kontrolki w kolejności tabulacji kontenera nadrzędnego.|  
|SHIFT+TAB|Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `false`, przenosi fokus do poprzedniej komórki w bieżącym wierszu. Jeśli fokus jest już pierwszą komórkę w wierszu, przenosi fokus do ostatniej komórki w poprzednim wierszu. Jeśli fokus znajduje się w pierwszej komórki w formancie, przenosi fokus do poprzedniego formantu w kolejności tabulacji kontenera nadrzędnego.<br /><br /> Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `true`, przenosi fokus do poprzedniego formantu w kolejności tabulacji kontenera nadrzędnego.|  
|CTRL+TAB|Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `false`, przenosi fokus do następnej kontrolki w kolejności tabulacji kontenera nadrzędnego.<br /><br /> Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `true`, przenosi fokus do następnej komórki w bieżącym wierszu. Jeśli fokus jest już w komórce ostatni wiersz, przenosi fokus do pierwszej komórki w kolejnym wierszu. Jeśli fokus znajduje się w ostatniej komórki w formancie, przenosi fokus do następnej kontrolki w kolejności tabulacji kontenera nadrzędnego.|  
|CTRL+SHIFT+TAB|Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `false`, przenosi fokus do poprzedniego formantu w kolejności tabulacji kontenera nadrzędnego.<br /><br /> Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `true`, przenosi fokus do poprzedniej komórki w bieżącym wierszu. Jeśli fokus jest już pierwszą komórkę w wierszu, przenosi fokus do ostatniej komórki w poprzednim wierszu. Jeśli fokus znajduje się w pierwszej komórki w formancie, przenosi fokus do poprzedniego formantu w kolejności tabulacji kontenera nadrzędnego.|  
|CTRL + STRZAŁKA|Przenosi fokus do położony komórki w kierunku strzałki.|  
|CTRL+HOME|Przenosi fokus do pierwszej komórki w formancie.|  
|CTRL+END|Przenosi fokus do ostatniej komórki w formancie.|  
|CTRL + PAGE DOWN/UP|Taka sama jak PAGE DOWN lub PAGE UP.|  
|F2|Umieszcza bieżącej komórki w komórce trybu edycji, jeśli <xref:System.Windows.Forms.DataGridView.EditMode%2A> wartość właściwości jest <xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2> lub <xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>.|
|F3|Sortuje bieżącej kolumnie, jeśli <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> wartość właściwości jest <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>. Jest taka sama jak kliknięcie nagłówka kolumny w bieżącym. Available since .NET Framework 4.7.2. Aby włączyć tę funkcję, aplikacje muszą .NET Framework 4.7.2 lub nowsze wersje lub jawnie zoptymalizowany pod kątem do ulepszenia ułatwień dostępu za pomocą przełączników AppContext.|  
|F4|W przypadku bieżącej komórki <xref:System.Windows.Forms.DataGridViewComboBoxCell>, umieszcza komórkę w trybie edycji i umożliwia wyświetlenie listy rozwijanej.|  
|ALT + STRZAŁKA W GÓRĘ/STRZAŁKA|W przypadku bieżącej komórki <xref:System.Windows.Forms.DataGridViewComboBoxCell>, umieszcza komórkę w trybie edycji i umożliwia wyświetlenie listy rozwijanej.|  
|SPACE|W przypadku bieżącej komórki <xref:System.Windows.Forms.DataGridViewButtonCell>, <xref:System.Windows.Forms.DataGridViewLinkCell>, lub <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, zgłasza <xref:System.Windows.Forms.DataGridView.CellClick> i <xref:System.Windows.Forms.DataGridView.CellContentClick> zdarzenia. W przypadku bieżącej komórki <xref:System.Windows.Forms.DataGridViewButtonCell>, również naciśnie przycisk. W przypadku bieżącej komórki <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, zmienia także stan zaznaczenia.|  
|ENTER|Przekazuje zmiany na bieżącej komórki i wiersza i przenosi fokus do komórki bezpośrednio poniżej bieżącej komórki. Jeśli fokus jest ustawiony w ostatnim wierszu, przekazuje zmiany bez przenoszenia fokusu.|  
|ESC|Jeśli kontrolka jest w trybie edycji, anuluje edycji. Jeśli formant nie jest w trybie edycji, przywraca zmiany, które zostały wprowadzone do bieżącego wiersza, jeśli kontrolka jest powiązana ze źródłem danych, który obsługuje edycję lub trybu wirtualnego została zaimplementowana w zakresie zatwierdzenia na poziomie wiersza.|  
|BACKSPACE|Usuwa znak przed punkt wstawiania podczas edytowania komórki.|  
|DELETE|Usuwa znak od punktu wstawiania podczas edytowania komórki.|  
|CTRL+ENTER|Zatwierdza zmiany do bieżącej komórki bez przenoszenia fokusu. Również zatwierdzenia zmiany do bieżącego wiersza, jeśli kontrolka jest powiązana ze źródłem danych, który obsługuje tryb edycji lub wirtualnych została zaimplementowana za pomocą wiersza na poziomie zakresu zatwierdzania.|  
|CTRL+0|Wprowadza <xref:System.DBNull.Value?displayProperty=nameWithType> wartość do bieżącej komórki, gdy mogą być edytowane komórki. Domyślnie wartość wyświetlania <xref:System.DBNull> wartość komórki jest wartością <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle> dla bieżącej komórki.|  
  
### <a name="selection-keys"></a>Wybór kluczy

 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> właściwość jest ustawiona na `false` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, zmieniania bieżącej komórki za pomocą klawiszy nawigacyjnych zmienia zaznaczenie do nowej komórki. SHIFT, klawisz CTRL i ALT — klawisze nie wpływają na to zachowanie.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, wystąpi takie samo zachowanie, ale z następującymi dodatkami.  
  
|Klawisz lub kombinację klawiszy|Opis|  
|----------------------------|-----------------|  
|SHIFT+SPACEBAR|Wybiera pełny wiersz lub kolumnę, (taka sama jak kliknięcie nagłówka wiersza lub kolumny).|  
|klucz nawigacji (klawisz strzałki, strona wzrost-spadek, HOME, END)|Zaznaczenie pełnego wiersza lub kolumny zmiany bieżącej komórki do nowego wiersza lub kolumny przenosi zaznaczenie do pełnej nowego wiersza lub kolumny (w zależności od trybu zaznaczania).|  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ustawiono `false` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, zmieniania bieżącej komórki do nowego wiersza lub kolumny przy użyciu klawiatury przenosi zaznaczenie do pełnej nowego wiersza lub kolumny. SHIFT, klawisz CTRL i ALT — klawisze nie wpływają na to zachowanie.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ustawiono `true`, zachowanie nawigacji nie zmienia się, ale Nawigacja przy użyciu klawiatury, przytrzymaj klawisze SHIFT (w tym klawiszy CTRL + SHIFT) zmodyfikuje zaznaczenia wielu komórek. Przed rozpoczęciem nawigacji, formant oznacza bieżącej komórki jako komórka zakotwiczenia. Po przejściu przytrzymaj klawisze SHIFT zaznaczenie obejmuje wszystkie komórki między komórki zakotwiczenia i bieżącej komórki. Inne komórki w formancie pozostanie wybrane, jeśli zostały one jeszcze wybrana, ale może przestać niezaznaczone nawigacji klawiatury tymczasowo powodująca umieszczenie ich między komórki zakotwiczenia i bieżącej komórki.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ustawiono `true` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>zachowanie zakotwiczenia komórki i bieżącej komórki jest taka sama, ale tylko pełne wiersze lub kolumny stają się wybrane lub usunięto zaznaczenie.  
  
## <a name="default-mouse-handling"></a>Domyślna obsługa myszy
  
### <a name="basic-mouse-handling"></a>Obsługa myszy podstawowe
  
> [!NOTE]
>  Kliknij komórkę z lewego przycisku myszy zawsze zmiany bieżącej komórki. Jeśli klikniesz prawym przyciskiem myszy komórkę otwiera menu skrótów, gdy jest on dostępny.  
  
|Akcja myszy|Opis|  
|------------------|-----------------|  
|Lewy przycisk myszy wciśnięty|Sprawia, że kliknięto komórki bieżącej komórki, a następnie zgłasza <xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType> zdarzeń.|  
|Lewy przycisk myszy się|Wywołuje <xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType> zdarzeń|  
|Kliknij lewy przycisk myszy|Wywołuje <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> i <xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType> zdarzenia|  
|Lewego przycisku myszy w dół, a następnie przeciągnij na komórki nagłówka kolumny|Jeśli <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> właściwość `true`, przenosi kolumnę, tak aby można było porzucić do nowej pozycji.|  
  
### <a name="mouse-selection"></a>Wybór myszy

 Zachowanie dotyczące wyboru nie jest skojarzony z środkowego przycisku myszy lub kółka myszy.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> właściwość jest ustawiona na `false` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, spowoduje następujące zachowanie.  
  
|Akcja myszy|Opis|  
|------------------|-----------------|  
|Kliknij lewy przycisk myszy|Wybiera tylko bieżącej komórki, jeśli użytkownik kliknie komórki. Nie zachowanie podczas zaznaczania, jeśli użytkownik kliknie nagłówek wiersza lub kolumny.|  
|Kliknij prawym przyciskiem myszy|Wyświetla menu skrótów, jeśli jest dostępny.|  
  
 Takie samo zachowanie występuje, gdy <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, z tą różnicą, że w zależności od trybu zaznaczania, klikając nagłówek wiersza lub kolumny spowoduje zaznacz pełny wiersz lub kolumnę i ustawianie bieżącej komórki do pierwszej komórki w wierszu lub kolumnie.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, kliknięcie dowolną komórkę w wierszu lub kolumnie powoduje zaznaczenie pełnego wiersza lub kolumny.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ustawiono `true`, klikając komórką trakcie naciskania klawisza CTRL lub SHIFT zmodyfikuje zaznaczenia wielu komórek.  
  
 Po kliknięciu komórki podczas naciskania klawisza CTRL, komórki zmieni jego stan zaznaczenia, podczas gdy inne komórki zachować wraz z bieżącym stanem wyboru.  
  
 Po kliknięciu pozycji komórkę lub serii komórki przytrzymaj klawisze SHIFT zaznaczenie obejmuje wszystkie komórki między bieżącym zakotwiczenia komórkę i znajdujący się w pozycji bieżącej komórki przed pierwsze kliknięcie. Po kliknięciu i przeciągnij go na wiele komórek zakotwiczenia komórka jest kliknięty po rozpoczęciu operacji przeciągania. Kolejne kliknięć przytrzymaj klawisze SHIFT zmienić bieżącej komórki, ale nie komórki zakotwiczenia. Inne komórki w formancie pozostanie wybrane, jeśli zostały one jeszcze wybrana, ale może przestać niezaznaczone nawigacji myszy tymczasowo powodująca umieszczenie ich między komórki zakotwiczenia i bieżącej komórki.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ustawiono `true` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, klikając nagłówek wiersza lub kolumny (w zależności od trybu zaznaczania) podczas naciśnięcie klawisza SHIFT spowoduje zmianę istniejące zaznaczenie pełnego wierszy lub kolumn, jeżeli takie Wybór istnieje. W przeciwnym razie zostanie ona wyczyść zaznaczenie i Rozpocznij nowe Zaznaczanie pełną wierszy lub kolumn. Klikając nagłówek wiersza lub kolumny podczas naciskania klawisza CTRL, jednak spowoduje dodanie lub usunięcie kliknięto wiersz lub kolumnę z bieżącego zaznaczenia, bez konieczności wprowadzania zmian w przeciwnym razie bieżącego zaznaczenia.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ustawiono `true` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, kliknięcie komórki naciskaj klawisz SHIFT lub CTRL zachowuje się tak samo, z wyjątkiem że tylko pełną wiersze i kolumny ma wpływ.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView, kontrolka](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
