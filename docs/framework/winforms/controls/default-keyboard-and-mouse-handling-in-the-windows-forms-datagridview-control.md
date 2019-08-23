---
title: Domyślna obsługa myszy i klawiatury w kontrolce DataGridView Windows Forms
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
ms.openlocfilehash: 97b8c8c3e418586bbc0053c358a2924484115a26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969130"
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>Domyślna obsługa myszy i klawiatury w kontrolce DataGridView Windows Forms

W poniższych tabelach opisano sposób, w jaki użytkownicy mogą <xref:System.Windows.Forms.DataGridView> korzystać z kontrolki za pomocą klawiatury i myszy.  
  
> [!NOTE]
> Aby dostosować zachowanie klawiatury, można obsłużyć standardowe zdarzenia klawiatury, <xref:System.Windows.Forms.Control.KeyDown>takie jak. W trybie edycji jednak kontrolka hostowana Edycja otrzymuje dane wejściowe z klawiatury, a zdarzenia klawiatury nie są wykonywane dla <xref:System.Windows.Forms.DataGridView> kontrolki. Aby obsłużyć zdarzenia kontroli edycji, Dołącz do kontrolki edycji w programie <xref:System.Windows.Forms.DataGridView.EditingControlShowing> obsługi zdarzeń. Alternatywnie możesz dostosować zachowanie klawiatury w <xref:System.Windows.Forms.DataGridView> podklasie, <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> zastępując metody i <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A> .  
  
## <a name="default-keyboard-handling"></a>Domyślna obsługa klawiatury  
  
### <a name="basic-navigation-and-entry-keys"></a>Podstawowe klucze nawigacji i wejścia  
  
|Kombinacja klucza lub klucza|Opis|  
|----------------------------|-----------------|  
|STRZAŁKA W DÓŁ|Przenosi fokus do komórki bezpośrednio pod bieżącą komórką. Jeśli fokus znajduje się w ostatnim wierszu, nic nie robi.|  
|STRZAŁKA W LEWO|Przenosi fokus do poprzedniej komórki w wierszu. Jeśli fokus znajduje się w pierwszej komórce w wierszu, nic nie robi.|  
|STRZAŁKA W PRAWO|Przenosi fokus do następnej komórki w wierszu. Jeśli fokus znajduje się w ostatniej komórce w wierszu, nic nie robi.|  
|STRZAŁKA W GÓRĘ|Przenosi fokus do komórki bezpośrednio nad bieżącą komórką. Jeśli fokus znajduje się w pierwszym wierszu, nic nie robi.|  
|MOWA|Przenosi fokus do pierwszej komórki w bieżącym wierszu.|  
|END|Przenosi fokus do ostatniej komórki w bieżącym wierszu.|  
|STRONA W DÓŁ|Przewija formant w dół o liczbę wierszy, które są w pełni wyświetlane. Przenosi fokus do ostatniego w pełni wyświetlonego wiersza bez zmiany kolumn.|  
|STRONA W GÓRĘ|Przewija formant w górę o liczbę wierszy, które są w pełni wyświetlane. Przenosi fokus do pierwszego wyświetlanego wiersza bez zmiany kolumn.|  
|TAB|Jeśli wartość `false`właściwości jest, przenosi fokus do następnej komórki w bieżącym wierszu. <xref:System.Windows.Forms.DataGridView.StandardTab%2A> Jeśli fokus znajduje się już w ostatniej komórce wiersza, przenosi fokus do pierwszej komórki w następnym wierszu. Jeśli fokus znajduje się w ostatniej komórce kontrolki, przenosi fokus do następnego formantu w kolejności tabulacji kontenera nadrzędnego.<br /><br /> Jeśli wartość `true`właściwości jest, przenosi fokus do następnego formantu w kolejności tabulacji kontenera nadrzędnego. <xref:System.Windows.Forms.DataGridView.StandardTab%2A>|  
|SHIFT+TAB|Jeśli wartość `false`właściwości jest, przenosi fokus do poprzedniej komórki w bieżącym wierszu. <xref:System.Windows.Forms.DataGridView.StandardTab%2A> Jeśli fokus znajduje się już w pierwszej komórce wiersza, przenosi fokus do ostatniej komórki w poprzednim wierszu. Jeśli fokus znajduje się w pierwszej komórce w kontrolce, przenosi fokus do poprzedniego formantu w kolejności tabulacji kontenera nadrzędnego.<br /><br /> Jeśli wartość `true`właściwości jest, przenosi fokus do poprzedniego formantu w kolejności tabulacji kontenera nadrzędnego. <xref:System.Windows.Forms.DataGridView.StandardTab%2A>|  
|CTRL+TAB|Jeśli wartość `false`właściwości jest, przenosi fokus do następnego formantu w kolejności tabulacji kontenera nadrzędnego. <xref:System.Windows.Forms.DataGridView.StandardTab%2A><br /><br /> Jeśli wartość `true`właściwości jest, przenosi fokus do następnej komórki w bieżącym wierszu. <xref:System.Windows.Forms.DataGridView.StandardTab%2A> Jeśli fokus znajduje się już w ostatniej komórce wiersza, przenosi fokus do pierwszej komórki w następnym wierszu. Jeśli fokus znajduje się w ostatniej komórce kontrolki, przenosi fokus do następnego formantu w kolejności tabulacji kontenera nadrzędnego.|  
|CTRL+SHIFT+TAB|Jeśli wartość `false`właściwości jest, przenosi fokus do poprzedniego formantu w kolejności tabulacji kontenera nadrzędnego. <xref:System.Windows.Forms.DataGridView.StandardTab%2A><br /><br /> Jeśli wartość `true`właściwości jest, przenosi fokus do poprzedniej komórki w bieżącym wierszu. <xref:System.Windows.Forms.DataGridView.StandardTab%2A> Jeśli fokus znajduje się już w pierwszej komórce wiersza, przenosi fokus do ostatniej komórki w poprzednim wierszu. Jeśli fokus znajduje się w pierwszej komórce w kontrolce, przenosi fokus do poprzedniego formantu w kolejności tabulacji kontenera nadrzędnego.|  
|CTRL + STRZAŁKA|Przenosi fokus do najwcześniejszej komórki w kierunku strzałki.|  
|CTRL + HOME|Przenosi fokus do pierwszej komórki w kontrolce.|  
|CTRL+END|Przenosi fokus do ostatniej komórki w kontrolce.|  
|CTRL + PAGE DOWN/W DÓŁ|Analogicznie jak PAGE DOWN lub PAGE UP.|  
|F2|Umieszcza bieżącą komórkę w trybie edycji komórki, <xref:System.Windows.Forms.DataGridView.EditMode%2A> Jeśli właściwość ma <xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2> wartość lub <xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>.|
|F3|Sortuje bieżącą kolumnę, jeśli <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> wartość właściwości to. <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> Jest taka sama jak kliknięcie nagłówka bieżącej kolumny. Dostępne od .NET Framework 4.7.2. Aby włączyć tę funkcję, aplikacje muszą być ukierunkowane na .NET Framework 4.7.2 lub nowsze wersje albo jawnie dołączać się do ulepszeń ułatwień dostępu przy użyciu przełączników AppContext.|  
|F4|Jeśli bieżąca komórka to a <xref:System.Windows.Forms.DataGridViewComboBoxCell>, powoduje, że komórka jest w trybie edycji i wyświetla listę rozwijaną.|  
|ALT + STRZAŁKA W GÓRĘ/W DÓŁ|Jeśli bieżąca komórka to a <xref:System.Windows.Forms.DataGridViewComboBoxCell>, powoduje, że komórka jest w trybie edycji i wyświetla listę rozwijaną.|  
|ODSTĘP|<xref:System.Windows.Forms.DataGridViewButtonCell>Jeśli bieżąca komórka to, <xref:System.Windows.Forms.DataGridViewCheckBoxCell> <xref:System.Windows.Forms.DataGridViewLinkCell> ,lub<xref:System.Windows.Forms.DataGridView.CellContentClick> , wywołuje zdarzenia i.<xref:System.Windows.Forms.DataGridView.CellClick> Jeśli bieżąca komórka to a <xref:System.Windows.Forms.DataGridViewButtonCell>, naciśnij także przycisk. Jeśli bieżąca komórka to a <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, zmienia także stan zaznaczenia.|  
|ENTER|Zatwierdza wszelkie zmiany w bieżącej komórce i wierszu i przenosi fokus do komórki bezpośrednio pod bieżącą komórką. Jeśli fokus znajduje się w ostatnim wierszu, zatwierdza wszelkie zmiany bez przesuwania fokusu.|  
|ESC|Jeśli formant jest w trybie edycji, anuluje edycję. Jeśli formant nie jest w trybie edycji, program powraca wszelkie zmiany wprowadzone w bieżącym wierszu, jeśli formant jest powiązany ze źródłem danych, które obsługuje edytowanie lub tryb wirtualny, został zaimplementowany z zakresem zatwierdzania na poziomie wiersza.|  
|BACKSPACE|Usuwa znak przed punktem wstawiania podczas edytowania komórki.|  
|DELETE|Usuwa znak po punkcie wstawiania podczas edytowania komórki.|  
|CTRL+ENTER|Zatwierdza zmiany w bieżącej komórce bez przesuwania fokusu. Ponadto zatwierdza wszelkie zmiany w bieżącym wierszu, jeśli formant jest powiązany ze źródłem danych, które obsługuje edytowanie lub tryb wirtualny został zaimplementowany z zakresem zatwierdzania na poziomie wiersza.|  
|CTRL+0|Umożliwia wprowadzenie <xref:System.DBNull.Value?displayProperty=nameWithType> wartości w bieżącej komórce, jeśli komórka może być edytowana. Domyślnie wartość wyświetlana dla <xref:System.DBNull> wartości komórki jest wartością <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> obowiązujących dla bieżącej komórki.|  
  
### <a name="selection-keys"></a>Klucze wyboru

 Jeśli właściwość jest ustawiona na `false` , a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, zmiana bieżącej komórki za pomocą klawiszy nawigacyjnych spowoduje zmianę zaznaczenia do nowej komórki. <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> Klawisze SHIFT, CTRL i ALT nie wpływają na to zachowanie.  
  
 Jeśli jest ustawiona na <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, takie samo zachowanie występuje, ale z poniższymi dodatkami. <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
  
|Kombinacja klucza lub klucza|Opis|  
|----------------------------|-----------------|  
|SHIFT+SPACEBAR|Wybiera pełny wiersz lub kolumnę (tak samo jak kliknięcie nagłówka wiersza lub kolumny).|  
|klawisz nawigacyjny (klawisz Strzałka, Strona w górę/w dół, Strona główna, koniec)|Jeśli wybrano pełny wiersz lub kolumnę, zmiana bieżącej komórki na nowy wiersz lub kolumnę przenosi zaznaczenie do pełnego nowego wiersza lub kolumny (w zależności od trybu wyboru).|  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> jest ustawiona na `false` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> jest ustawiona <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> na lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, zmiana bieżącej komórki na nowy wiersz lub kolumnę przy użyciu klawiatury przenosi zaznaczenie do pełnego nowego wiersza lub kolumny. Klawisze SHIFT, CTRL i ALT nie wpływają na to zachowanie.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> jest ustawiona na `true`, zachowanie nawigowania nie zmienia się, ale Nawigowanie przy użyciu klawiatury podczas naciskania klawisza Shift (w tym Ctrl + Shift) spowoduje zmodyfikowanie zaznaczenia obejmującego wiele komórek. Przed rozpoczęciem nawigacji, formant oznacza bieżącą komórkę jako zakotwiczenie komórki. Podczas poruszania się po naciśnięciu klawisza SHIFT zaznaczenie obejmuje wszystkie komórki między komórką zakotwiczenie a bieżącą komórką. Inne komórki w kontrolce pozostaną zaznaczone, jeśli zostały już wybrane, ale mogą zostać usunięte, jeśli Nawigacja klawiatury tymczasowo umieści je między komórką zakotwiczoną i bieżącą komórką.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> jest ustawiona na `true` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> jest ustawiona <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> na lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, zachowanie komórki zakotwiczonej i bieżącej komórki jest takie samo, ale tylko pełne wiersze lub kolumny zostaną zaznaczone lub anulowane.  
  
## <a name="default-mouse-handling"></a>Domyślna obsługa myszy
  
### <a name="basic-mouse-handling"></a>Podstawowa obsługa myszy
  
> [!NOTE]
> Kliknięcie komórki z lewym przyciskiem myszy zawsze powoduje zmianę bieżącej komórki. Kliknięcie komórki z prawym przyciskiem myszy powoduje otwarcie menu skrótów, gdy jest ono dostępne.  
  
|Akcja myszy|Opis|  
|------------------|-----------------|  
|Lewy przycisk myszy w dół|Sprawia, że kliknięta komórka jest bieżącą komórką i <xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType> wywołuje zdarzenie.|  
|Lewy przycisk myszy w górę|<xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType> Podnosi zdarzenie|  
|Lewy przycisk myszy|<xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType> Podnosi zdarzenia <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> i|  
|Lewy przycisk myszy w dół i przeciągnij ją na komórkę nagłówka kolumny.|Jeśli właściwość jest `true`, przenosi kolumnę tak, aby mogła zostać porzucona do nowej pozycji. <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>|  
  
### <a name="mouse-selection"></a>Wybór myszy

 Żadne zachowanie wyboru nie jest skojarzone z środkowym przyciskiem myszy ani kółkiem myszy.  
  
 Jeśli właściwość jest ustawiona na `false` , a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, nastąpi następujące zachowanie. <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>  
  
|Akcja myszy|Opis|  
|------------------|-----------------|  
|Kliknij przycisk lewy przycisk myszy|Wybiera tylko bieżącą komórkę, jeśli użytkownik kliknie komórkę. Brak zachowania wyboru, jeśli użytkownik kliknie nagłówek wiersza lub kolumny.|  
|Kliknij prawy przycisk myszy|Wyświetla menu skrótów, jeśli jest dostępne.|  
  
 Takie samo zachowanie występuje, gdy <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> jest ustawiona na <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, z wyjątkiem tego, że w zależności od trybu zaznaczania kliknięcie nagłówka wiersza lub kolumny spowoduje wybranie pełnego wiersza lub kolumny i ustawienie bieżącej komórki na pierwszą komórkę w wierszu lub kolumnie.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> jest ustawiona na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, kliknięcie dowolnej komórki w wierszu lub kolumnie spowoduje wybranie pełnego wiersza lub kolumny.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> jest ustawiona na `true`, kliknięcie komórki podczas naciskania klawisza CTRL lub Shift spowoduje zmodyfikowanie zaznaczenia z obsługą kilku komórek.  
  
 Gdy klikniesz komórkę podczas naciskania klawisza CTRL, komórka zmieni swój stan zaznaczenia, a wszystkie pozostałe komórki zachowają bieżący stan zaznaczenia.  
  
 Gdy klikniesz komórkę lub serię komórek podczas naciskania klawisza SHIFT, zaznaczenie obejmuje wszystkie komórki między bieżącą komórką i komórką zakotwiczoną znajdującą się na pozycji bieżącej komórki przed pierwszym kliknięciem. Gdy klikniesz i przeciągniesz wskaźnik w wielu komórkach, komórka kotwicy jest komórką klikniętą na początku operacji przeciągania. Kolejne kliknięcia podczas naciskania klawisza SHIFT zmieniają bieżącą komórkę, ale nie do komórki zakotwiczonej. Inne komórki w kontrolce pozostaną zaznaczone, jeśli zostały już wybrane, ale mogą zostać usunięte, jeśli nawigacja myszy tymczasowo umieści je między komórką zakotwiczoną i bieżącą komórką.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> jest ustawiona na `true` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> jest ustawiona <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> na lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, kliknięcie nagłówka wiersza lub kolumny (w zależności od trybu wyboru) podczas naciskania klawisza Shift spowoduje zmodyfikowanie istniejącego zaznaczenia pełnych wierszy lub kolumn, jeśli takie zaznaczenie istnieje. W przeciwnym razie wyczyści zaznaczenie i rozpocznie nowy wybór pełnych wierszy lub kolumn. Kliknięcie nagłówka wiersza lub kolumny podczas naciskania klawisza CTRL spowoduje jednak dodanie lub usunięcie klikniętego wiersza lub kolumny z bieżącego zaznaczenia bez modyfikowania bieżącego zaznaczenia.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> jest ustawiona na `true` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> jest ustawiona na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, kliknięcie komórki podczas naciskania klawisza Shift lub CTRL zachowuje się tak samo, z tą różnicą, że dotyczy tylko pełnych wierszy i kolumn.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView, kontrolka](datagridview-control-windows-forms.md)
