---
title: "Domyślna obsługa myszy i klawiatury w formancie DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], mouse handling
- DataGridView control [Windows Forms], navigation keys
- keyboards [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], keyboard handling
- mouse [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], mouse handling
- navigation keys [Windows Forms], DataGridView control
ms.assetid: 4519b928-bfc8-4e8b-bb9c-b1e76a0ca552
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 627784f3d68ddf03f1f6c94975405dded3163c06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>Domyślna obsługa myszy i klawiatury w formancie DataGridView formularzy systemu Windows
W poniższych tabelach opisano sposób interakcji użytkowników z <xref:System.Windows.Forms.DataGridView> sterowanie za pośrednictwem klawiatury i myszy.  
  
> [!NOTE]
>  Aby dostosować zachowanie klawiatury, może obsłużyć zdarzenia klawiatury standardowe takich jak <xref:System.Windows.Forms.Control.KeyDown>. Jednak w trybie edycji obsługiwanego formantu edycji odbiera wejście klawiatury i nie występują zdarzenia klawiatury dla <xref:System.Windows.Forms.DataGridView> formantu. Do obsługi zdarzenia formantów edycji, Dołącz programu obsługi do edycji kontrolek w <xref:System.Windows.Forms.DataGridView.EditingControlShowing> obsługi zdarzeń. Alternatywnie można dostosować zachowanie klawiatury w <xref:System.Windows.Forms.DataGridView> podklasy przez zastąpienie <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> i <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A> metody.  
  
## <a name="default-keyboard-handling"></a>Domyślna obsługa klawiatury  
  
### <a name="basic-navigation-and-entry-keys"></a>Podstawowe klucze nawigacji i wpis  
  
|Klucz lub kombinacji klawiszy|Opis|  
|----------------------------|-----------------|  
|STRZAŁKA W DÓŁ|Przenosi fokus do komórki bezpośrednio pod bieżącą komórką. Jeśli fokus jest ustawiony w ostatnim wierszu, nie działają.|  
|STRZAŁKA W LEWO|Przenosi fokus do poprzedniej komórki w wierszu. Jeśli fokus znajduje się w pierwszej komórki w wierszu, nie działają.|  
|STRZAŁKA W PRAWO|Przenosi fokus do następnej komórki w wierszu. Jeśli fokus znajduje się w ostatniej komórki w wierszu, nie działają.|  
|STRZAŁKA W GÓRĘ|Przenosi fokus do komórki bezpośrednio powyżej bieżącej komórki. Jeśli skupiono się w pierwszym wierszu, nie działają.|  
|STRONA GŁÓWNA|Przenosi fokus do pierwszej komórki w bieżącym wierszu.|  
|END|Przenosi fokus do ostatniej komórki w bieżącym wierszu.|  
|PAGE DOWN|Przewija dół formantu przez liczbę wierszy, jaką pełni są wyświetlane. Przenosi fokus do ostatniego wiersza pełni wyświetlanych bez zmieniania kolumn.|  
|STRONA W GÓRĘ|Przewija formantu w górę przez liczbę wierszy, jaką pełni są wyświetlane. Przenosi fokus do pierwszego wiersza wyświetlany bez zmieniania kolumn.|  
|TAB|Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `false`, przenosi fokus do następnej komórki w bieżącym wierszu. Jeśli fokus jest już w komórce ostatniego wiersza, przenosi fokus do pierwszej komórki w następnym wierszu. Jeśli fokus znajduje się w ostatniej komórki w formancie, przenosi fokus do następnego formantu w kolejności tabulacji kontenera nadrzędnego.<br /><br /> Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `true`, przenosi fokus do następnego formantu w kolejności tabulacji kontenera nadrzędnego.|  
|SHIFT+TAB|Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `false`, przenosi fokus do poprzedniej komórki w bieżącym wierszu. Jeśli fokus jest już pierwszej komórki wiersza, przenosi fokus do ostatniej komórki w poprzednim wierszu. Jeśli fokus znajduje się w pierwszej komórki w formancie, przenosi fokus do poprzedniego formantu w kolejności tabulacji kontenera nadrzędnego.<br /><br /> Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `true`, przenosi fokus do poprzedniego formantu w kolejności tabulacji kontenera nadrzędnego.|  
|CTRL + TAB|Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `false`, przenosi fokus do następnego formantu w kolejności tabulacji kontenera nadrzędnego.<br /><br /> Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `true`, przenosi fokus do następnej komórki w bieżącym wierszu. Jeśli fokus jest już w komórce ostatniego wiersza, przenosi fokus do pierwszej komórki w następnym wierszu. Jeśli fokus znajduje się w ostatniej komórki w formancie, przenosi fokus do następnego formantu w kolejności tabulacji kontenera nadrzędnego.|  
|CTRL + SHIFT + TAB|Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `false`, przenosi fokus do poprzedniego formantu w kolejności tabulacji kontenera nadrzędnego.<br /><br /> Jeśli <xref:System.Windows.Forms.DataGridView.StandardTab%2A> wartość właściwości jest `true`, przenosi fokus do poprzedniej komórki w bieżącym wierszu. Jeśli fokus jest już pierwszej komórki wiersza, przenosi fokus do ostatniej komórki w poprzednim wierszu. Jeśli fokus znajduje się w pierwszej komórki w formancie, przenosi fokus do poprzedniego formantu w kolejności tabulacji kontenera nadrzędnego.|  
|CTRL + STRZAŁKA|Przenosi fokus do najbardziej komórki w kierunku strzałki.|  
|CTRL + HOME|Przenosi fokus do pierwszej komórki w formancie.|  
|CTRL + END|Przenosi fokus do ostatniej komórki w formancie.|  
|CTRL + STRONĘ W GÓRĘ/DÓŁ|Taka sama jak PAGE DOWN lub PAGE UP.|  
|F2|Umieszcza bieżącej komórki w trybie edycji komórki Jeśli <xref:System.Windows.Forms.DataGridView.EditMode%2A> wartość właściwości jest <xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2> lub <xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>.|  
|F4|W przypadku bieżącej komórki <xref:System.Windows.Forms.DataGridViewComboBoxCell>, umieszcza komórki w trybie edycji i umożliwia wyświetlenie listy rozwijanej.|  
|ALT + STRZAŁKA W GÓRĘ LUB W DÓŁ, STRZAŁKI|W przypadku bieżącej komórki <xref:System.Windows.Forms.DataGridViewComboBoxCell>, umieszcza komórki w trybie edycji i umożliwia wyświetlenie listy rozwijanej.|  
|MIEJSCA|W przypadku bieżącej komórki <xref:System.Windows.Forms.DataGridViewButtonCell>, <xref:System.Windows.Forms.DataGridViewLinkCell>, lub <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, zgłasza <xref:System.Windows.Forms.DataGridView.CellClick> i <xref:System.Windows.Forms.DataGridView.CellContentClick> zdarzenia. W przypadku bieżącej komórki <xref:System.Windows.Forms.DataGridViewButtonCell>, również naciśnie przycisk. W przypadku bieżącej komórki <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, również zmianę stanu zaznaczenia.|  
|ENTER|Przekazuje zmiany na bieżącej komórki i wiersza i przenosi fokus do komórki bezpośrednio pod bieżącą komórką. Jeśli fokus jest ustawiony w ostatnim wierszu, przekazuje zmiany bez przenoszenia fokusu.|  
|ESC|Jeśli formant jest w trybie edycji, anulowanie edycji. Jeśli formant nie jest w trybie edycji, przywraca wszystkie zmiany, które zostały wprowadzone do bieżącego wiersza, jeśli formant jest powiązany ze źródłem danych, który obsługuje edycję lub tryb wirtualny zostało zaimplementowane w zakresie zatwierdzania na poziomie wiersza.|  
|BACKSPACE|Usuwa znak przed punkt wstawiania podczas edytowania komórki.|  
|DELETE|Usuwa znak od punktu wstawiania podczas edytowania komórki.|  
|CTRL + ENTER|Zatwierdza wszystkie zmiany do bieżącej komórki bez przenoszenia fokusu. Również zatwierdzeń została zaimplementowana wszystkie zmiany do bieżącego wiersza, jeśli formant jest powiązany ze źródłem danych, który obsługuje tryb edycji lub wirtualne z poziomu wiersza zakresu zatwierdzania.|  
|CTRL + 0|Wprowadza <xref:System.DBNull.Value?displayProperty=nameWithType> wartość do bieżącej komórki, gdy mogą być edytowane komórki. Domyślnie wartość wyświetlania <xref:System.DBNull> wartość komórki jest wartością <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle> dla bieżącej komórki.|  
  
### <a name="selection-keys"></a>Wybór kluczy  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> właściwość jest ustawiona na `false` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, bieżącej komórki za pomocą klawiszy nawigacyjnych zmiana zaznaczenie do nowej komórki. SHIFT, CTRL i ALT — klawisze nie wpływają na to zachowanie.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, występuje takie samo zachowanie, ale z następującymi dodatkami.  
  
|Klucz lub kombinacji klawiszy|Opis|  
|----------------------------|-----------------|  
|SHIFT + SPACJA|Wybiera pełny wiersz lub kolumnę (taką jak kliknięcie nagłówka wierszy lub kolumn).|  
|klucz nawigacji (strzałka, wzrost-spadek strony, HOME, END)|Jeśli wybrano pełny wiersz lub kolumnę, zmiana bieżącej komórki na nowy wiersz lub kolumnę przenosi zaznaczenie do pełnej nowy wiersz lub kolumnę (w zależności od trybu wyboru).|  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ustawiono `false` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, zmiana bieżącej komórki do nowego wiersza lub komórki za pomocą klawiatury przenosi zaznaczenie do pełnej nowy wiersz lub kolumnę. SHIFT, CTRL i ALT — klawisze nie wpływają na to zachowanie.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ma ustawioną wartość `true`, zachowanie nawigacji nie ulega zmianie, ale Nawigacja przy użyciu klawiatury, przytrzymaj klawisze SHIFT (w tym klawiszy CTRL + SHIFT) zmodyfikuje zaznaczenia wielu komórek. Przed rozpoczęciem nawigacji formantu oznacza bieżącej komórki jako komórki zakotwiczenia. Po przejściu naciskaj klawisz SHIFT, zaznaczenie obejmuje wszystkie komórki między komórki zakotwiczenia i bieżącej komórki. Jeśli zostały one już wybrane, ale ich może stać się niezaznaczone nawigacji klawiatury tymczasowo umieszczane między komórki zakotwiczenia i bieżącej komórki pozostanie wybranego innych komórek w formancie.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ustawiono `true` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>zachowanie komórki zakotwiczenia i bieżącej komórki jest taki sam, ale tylko pełna wierszy lub kolumn stają się zaznaczone lub niezaznaczone.  
  
## <a name="default-mouse-handling"></a>Domyślna obsługa myszy  
  
### <a name="basic-mouse-handling"></a>Obsługa myszy podstawowe  
  
> [!NOTE]
>  Kliknij komórkę z lewego przycisku myszy zawsze zmiany bieżącej komórki. Jeśli klikniesz komórkę prawym przyciskiem myszy otwiera menu skrótów, gdy jest on dostępny.  
  
|Akcja myszy|Opis|  
|------------------|-----------------|  
|Lewy przycisk myszy w dół|Sprawia, że klikniętej komórki bieżącej komórki i zgłasza <xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType> zdarzeń.|  
|Lewy przycisk myszy górę|Zgłasza <xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType> zdarzeń|  
|Kliknij lewy przycisk myszy|Zgłasza <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> i <xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType> zdarzeń|  
|Lewy przycisk myszy w dół, a następnie przeciągnij w komórce nagłówka kolumny|Jeśli <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> właściwość jest `true`, przenosi kolumnę, tak aby można było porzucić do nowej pozycji.|  
  
### <a name="mouse-selection"></a>Wybór myszy  
 Zachowanie dotyczące wyboru nie jest skojarzony z środkowego przycisku myszy i kółka myszy.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> właściwość jest ustawiona na `false` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, spowoduje następujące zachowanie.  
  
|Akcja myszy|Opis|  
|------------------|-----------------|  
|Kliknij lewy przycisk myszy|Wybiera tylko bieżącej komórki, gdy użytkownik kliknie komórki. Nie zachowanie dotyczące wyboru gdy użytkownik kliknie wiersz lub nagłówek kolumny.|  
|Kliknij prawym przyciskiem myszy|Wyświetla menu skrótów, jeśli jest dostępny.|  
  
 Takie samo zachowanie występuje podczas <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, ale w zależności od trybu wyboru, klikając wiersz lub nagłówek kolumny zostanie zaznacz pełny wiersz lub kolumnę i ustawianie bieżącej komórki do pierwszej komórki w wierszu lub kolumnie.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, kliknij dowolną komórkę w wiersz lub kolumnę wybierze pełny wiersz lub kolumnę.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ma ustawioną wartość `true`, klikając komórkę naciskaj klawisz CTRL lub SHIFT zmodyfikuje zaznaczenia wielu komórek.  
  
 Po kliknięciu komórki trzymając wciśnięty klawisz CTRL podczas wszystkich komórkach zachować ich bieżący stan zaznaczenia komórki zmieni jego stan zaznaczenia.  
  
 Po kliknięciu komórki lub serii komórki naciskaj klawisz SHIFT zaznaczenie obejmuje wszystkie komórki między bieżącą komórką i komórki zakotwiczenia znajdujący się w pozycji przed pierwszym kliknięciem bieżącej komórki. Kliknij i przeciągnij go na wiele komórek, komórki zakotwiczenia po komórki kliknięty na początku operacji przeciągania. Kolejne kliknięć naciskaj klawisz SHIFT zmienić bieżącej komórki, ale nie komórki zakotwiczenia. Jeśli zostały one już wybrane, ale ich może stać się niezaznaczone nawigacji myszy tymczasowo umieszczane między komórki zakotwiczenia i bieżącej komórki pozostanie wybranego innych komórek w formancie.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ustawiono `true` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, klikając wiersz lub nagłówek kolumny (w zależności od trybu wyboru) podczas naciśnięcie klawisza SHIFT spowoduje zmianę istniejącego zaznaczenia pełne wierszy lub kolumn, jeżeli takie wybrany element znajduje się. W przeciwnym razie utworzy wyczyść zaznaczenie i Rozpocznij nowe zaznaczenie pełnego wierszy lub kolumn. Klikając wiersz lub nagłówek kolumny, trzymając wciśnięty klawisz CTRL, jednak spowoduje dodanie lub usunięcie klikniętej wiersz lub kolumnę z bieżącego zaznaczenia bez modyfikowanie bieżącego zaznaczenia.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> ustawiono `true` i <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, klikając komórkę naciskaj klawisz SHIFT lub CTRL zachowuje się tak samo, z wyjątkiem tego tylko całe wiersze i kolumny dotyczy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 [DataGridView, kontrolka](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
