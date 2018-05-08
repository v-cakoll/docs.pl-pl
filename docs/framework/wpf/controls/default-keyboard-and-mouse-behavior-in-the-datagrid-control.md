---
title: Domyślne zachowanie myszy i klawiatury w formancie DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid [WPF], keyboard behavior
- DataGrid [WPF], mouse behavior
- keyboard behavior [WPF], DataGrid
- mouse behavior [WPF], DataGrid
ms.assetid: 563b8854-ca39-4d97-8235-17eaa0f93c8d
ms.openlocfilehash: 559b84d3e6b5ece6c71f17e6766cac4ec14824cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="default-keyboard-and-mouse-behavior-in-the-datagrid-control"></a>Domyślne zachowanie myszy i klawiatury w formancie DataGrid
W tym temacie opisano sposób interakcji użytkowników z <xref:System.Windows.Controls.DataGrid> formantu przy użyciu klawiatury i myszy.  
  
 Typowy interakcji z <xref:System.Windows.Controls.DataGrid> obejmują nawigację, zaznaczenia i edycji. Wpływ na zachowanie dotyczące wyboru <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> i <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> właściwości. Wartości domyślne, które powodują zachowanie opisane w tym temacie są <xref:System.Windows.Controls.DataGridSelectionMode.Extended?displayProperty=nameWithType> i <xref:System.Windows.Controls.DataGridSelectionUnit.FullRow?displayProperty=nameWithType>. Zmiana tych wartości może spowodować zachowanie różni się od opisanych. Gdy komórka jest w trybie edycji, edycji kontrolek mogą zastąpić zachowanie klawiatury standardowej <xref:System.Windows.Controls.DataGrid>.  
  
## <a name="default-keyboard-behavior"></a>Domyślne zachowanie klawiatury  
 W poniższej tabeli przedstawiono domyślne zachowanie klawiatury dla <xref:System.Windows.Controls.DataGrid>.  
  
|Klucz lub kombinacji klawiszy|Opis|  
|----------------------------|-----------------|  
|STRZAŁKA W DÓŁ|Przenosi fokus do komórki bezpośrednio pod bieżącą komórką. Jeśli fokus jest ustawiony w ostatnim wierszu, naciskając klawisz Strzałka w dół nie działa.|  
|STRZAŁKA W GÓRĘ|Przenosi fokus do komórki bezpośrednio powyżej bieżącej komórki. Jeśli skupiono się w pierwszym wierszu, naciskając klawisz strzałki w górę nie działa.|  
|STRZAŁKA W LEWO|Przenosi fokus do poprzedniej komórki w wierszu. Jeśli fokus znajduje się w pierwszej komórki w wierszu, naciskając klawisz Strzałka w lewo nie działa.|  
|STRZAŁKA W PRAWO|Przenosi fokus do następnej komórki w wierszu. Jeśli fokus znajduje się w ostatniej komórki w wierszu, naciskając klawisz strzałki w prawo nie działa.|  
|STRONA GŁÓWNA|Przenosi fokus do pierwszej komórki w bieżącym wierszu.|  
|END|Przenosi fokus do ostatniej komórki w bieżącym wierszu.|  
|PAGE DOWN|Jeśli nie są zgrupowane wiersze, Przewija dół formantu przez liczbę wierszy, jaką pełni są wyświetlane. Przenosi fokus do ostatniego wiersza pełni wyświetlanych bez zmieniania kolumn.<br /><br /> Jeśli wiersze są grupowane, przenosi fokus do ostatniego wiersza w <xref:System.Windows.Controls.DataGrid> bez zmieniania kolumn.|  
|STRONA W GÓRĘ|Jeśli nie są zgrupowane wiersze, należy w górę Przewija formantu przez liczbę wierszy, jaką pełni są wyświetlane. Przenosi fokus do pierwszego wiersza wyświetlany bez zmieniania kolumn.<br /><br /> Jeśli wiersze są grupowane, przenosi fokus do pierwszego wiersza w <xref:System.Windows.Controls.DataGrid> bez zmieniania kolumn.|  
|TAB|Przenosi fokus do następnej komórki w bieżącym wierszu. Jeśli skupiono się w komórce ostatniego wiersza, przenosi fokus do pierwszej komórki w następnym wierszu. Jeśli fokus znajduje się w ostatniej komórki w formancie, przenosi fokus do następnego formantu w kolejności tabulacji kontenera nadrzędnego.<br /><br /> W przypadku bieżącej komórki w trybu edycji, a następnie naciskając klawisz kartę przyczyny fokus Przenieś poza bieżący wiersz, wszystkie zmiany dokonane w tym wierszu są zatwierdzone przed fokus zostanie zmieniona.|  
|SHIFT+TAB|Przenosi fokus do poprzedniej komórki w bieżącym wierszu. Jeśli fokus jest już pierwszej komórki wiersza, przenosi fokus do ostatniej komórki w poprzednim wierszu. Jeśli fokus znajduje się w pierwszej komórki w formancie, przenosi fokus do poprzedniego formantu w kolejności tabulacji kontenera nadrzędnego.<br /><br /> W przypadku bieżącej komórki w trybu edycji, a następnie naciskając klawisz kartę przyczyny fokus Przenieś poza bieżący wiersz, wszystkie zmiany dokonane w tym wierszu są zatwierdzone przed fokus zostanie zmieniona.|  
|CTRL + STRZAŁKA W DÓŁ|Przenosi fokus do ostatniej komórki w bieżącej kolumny.|  
|CTRL + STRZAŁKA W GÓRĘ|Przenosi fokus do pierwszej komórki w bieżącej kolumny.|  
|CTRL + STRZAŁKA W PRAWO|Przenosi fokus do ostatniej komórki w bieżącym wierszu.|  
|CTRL + STRZAŁKA W LEWO|Przenosi fokus do pierwszej komórki w bieżącym wierszu.|  
|CTRL + HOME|Przenosi fokus do pierwszej komórki w formancie.|  
|CTRL+END|Przenosi fokus do ostatniej komórki w formancie.|  
|CTRL + PAGE DOWN|Taka sama jak PAGE DOWN.|  
|CTRL + PAGE UP|Taka sama jak PAGE UP.|  
|F2|Jeśli <xref:System.Windows.Controls.DataGrid.IsReadOnly%2A?displayProperty=nameWithType> właściwość jest `false` i <xref:System.Windows.Controls.DataGridColumn.IsReadOnly%2A?displayProperty=nameWithType> jest właściwość `false` dla bieżącej kolumny umieszcza bieżącej komórki w trybie edycji komórki.|  
|ENTER|Przekazuje zmiany na bieżącej komórki i wiersza i przenosi fokus do komórki bezpośrednio pod bieżącą komórką. Jeśli fokus jest ustawiony w ostatnim wierszu, przekazuje zmiany bez przenoszenia fokusu.|  
|ESC|Jeśli formant jest w trybie edycji, anuluje edycji i przywraca wszystkie zmiany wprowadzone w formancie. Jeśli implementuje źródło danych <xref:System.ComponentModel.IEditableObject>, naciskając klawisz ESC po raz drugi anuluje trybu edycji dla całego wiersza.|  
|BACKSPACE|Usuwa znak przed kursorem podczas edytowania komórki.|  
|DELETE|Usuwa znak po kursora podczas edytowania komórki.|  
|CTRL+ENTER|Zatwierdza wszystkie zmiany do bieżącej komórki bez przenoszenia fokusu.|  
|CTRL+A|Jeśli <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ustawiono <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, wybiera wszystkie wiersze w <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="selection-keys"></a>Wybór kluczy  
 Jeśli <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, zachowanie nawigacji nie ulega zmianie, ale Nawigacja przy użyciu klawiatury, przytrzymaj klawisze SHIFT (w tym klawiszy CTRL + SHIFT) zmodyfikuje zaznaczenia wielu wierszy. Przed rozpoczęciem nawigacji formantu oznacza bieżącego wiersza jako zakotwiczenia wiersza. Po przejściu naciskaj klawisz SHIFT, zaznaczenie obejmuje wszystkie wiersze między zakotwiczenia wiersza i bieżącego wiersza.  
  
 Następujące klucze wybór zmodyfikować zaznaczenie wielu wiersza.  
  
-   SHIFT + STRZAŁKA W DÓŁ  
  
-   SHIFT + STRZAŁKA W GÓRĘ  
  
-   SHIFT + PAGE DOWN  
  
-   SHIFT + STRONĘ W GÓRĘ  
  
-   CTRL + SHIFT + STRZAŁKA W DÓŁ, STRZAŁKI  
  
-   CTRL + SHIFT + STRZAŁKA W GÓRĘ, STRZAŁKI  
  
-   CTRL + SHIFT + HOME  
  
-   CTRL + SHIFT + END  
  
## <a name="default-mouse-behavior"></a>Domyślne zachowanie myszy  
 W poniższej tabeli przedstawiono domyślne zachowanie myszy dla <xref:System.Windows.Controls.DataGrid>.  
  
|Akcja myszy|Opis|  
|------------------|-----------------|  
|Kliknij wiersz niezaznaczone|Sprawia, że wiersz klikniętej bieżącego wiersza i klikniętej komórki bieżącej komórki.|  
|Kliknij przycisk bieżącej komórki|Umieszcza bieżącej komórki w trybie edycji.|  
|Przeciągnij komórki nagłówka kolumny|Jeśli <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A?displayProperty=nameWithType> właściwość jest `true` i <xref:System.Windows.Controls.DataGridColumn.CanUserReorder%2A?displayProperty=nameWithType> jest właściwość `true` dla bieżącej kolumny przenosi kolumnę, tak, aby można było porzucić do nowej pozycji.|  
|Przeciągnij separator nagłówek kolumny|Jeśli <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> właściwość jest `true` i <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> jest właściwość `true` dla bieżącej kolumny zmienia rozmiar kolumny.|  
|Kliknij dwukrotnie separator nagłówek kolumny|Jeśli <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> właściwość jest `true` i <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> właściwość jest `true` dla bieżącej kolumny rozmiary automatycznie przy użyciu kolumny <xref:System.Windows.Controls.DataGridLength.Auto%2A> tryb zmiany rozmiaru.|  
|Kliknij komórkę nagłówka kolumny|Jeśli <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A?displayProperty=nameWithType> właściwość jest `true` i <xref:System.Windows.Controls.DataGridColumn.CanUserSort%2A?displayProperty=nameWithType> jest właściwość `true` dla bieżącej kolumny sortowania kolumny.<br /><br /> Kliknięcie nagłówka kolumny, która jest już posortowane będzie odwrócić kierunek sortowania tej kolumny.<br /><br /> Naciśnięcie klawisza SHIFT podczas kliknięcie wielu nagłówków kolumn sortowania według wielu kolumn w kolejności kliknięty.|  
|CTRL + kliknij wiersz|Jeśli <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ma ustawioną wartość <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, modyfikuje nieciągłych zaznaczenia wielu wierszy.<br /><br /> Jeśli wiersz jest zaznaczona, powoduje usunięcie zaznaczenia wiersza.|  
|SHIFT + kliknij wiersz|Jeśli <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ma ustawioną wartość <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, zmienia ciągłych zaznaczenia wielu wierszy.|  
|Kliknij nagłówek grupy|Rozwija lub zwija grupy.|  
|Kliknij przycisk Wybierz wszystko w lewym górnym rogu aplikacji <xref:System.Windows.Controls.DataGrid>|Jeśli <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ustawiono <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, wybiera wszystkie wiersze w <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="mouse-selection"></a>Wybór myszy  
 Jeśli <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, klikając wiersz naciskaj klawisz CTRL lub SHIFT zmodyfikuje zaznaczenia wielu wierszy.  
  
 Po kliknięciu wiersza trzymając wciśnięty klawisz CTRL podczas wszystkich innych wierszy zachować ich bieżący stan zaznaczenia wiersza zmieni jego stan zaznaczenia. W tym do wybrania wierszy z systemem innym niż sąsiadujących ze sobą.  
  
 Po kliknięciu wiersza naciskaj klawisz SHIFT zaznaczenie zawiera wszystkie wiersze między bieżący wiersz i wiersz zakotwiczenia znajdujący się w pozycji przed kliknięcie bieżącego wiersza. Kolejne kliknięć przytrzymaj klawisze SHIFT zmienić bieżącego wiersza, ale nie zakotwiczenia wiersza. To zrobić, aby wybrać zakres sąsiadujących wierszy.  
  
 CTRL + SHIFT można łączyć, aby wybrać-sąsiadujące zakresy sąsiadujące. Aby to zrobić, wybierz pierwszy zakres przy użyciu SHIFT + kliknij zgodnie z wcześniejszym opisem. Po wybraniu pierwszej zakres wierszy, użyj kombinacji klawisza CTRL + kliknij, aby zaznaczyć pierwszy wiersz w zakresie dalej, a następnie kliknij ostatni wiersz w zakresie dalej przytrzymaj klawisze CTRL + SHIFT.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.DataGrid>  
 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A>
