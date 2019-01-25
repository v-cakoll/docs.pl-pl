---
title: Domyślne zachowanie myszy i klawiatury w formancie DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid [WPF], keyboard behavior
- DataGrid [WPF], mouse behavior
- keyboard behavior [WPF], DataGrid
- mouse behavior [WPF], DataGrid
ms.assetid: 563b8854-ca39-4d97-8235-17eaa0f93c8d
ms.openlocfilehash: f122eb97719182b4cad5fb0e757cd3647e575094
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741616"
---
# <a name="default-keyboard-and-mouse-behavior-in-the-datagrid-control"></a>Domyślne zachowanie myszy i klawiatury w formancie DataGrid
W tym temacie opisano, jak użytkownicy mogą korzystać z <xref:System.Windows.Controls.DataGrid> kontroli przy użyciu klawiatury i myszy.  
  
 Typowe interakcji z <xref:System.Windows.Controls.DataGrid> obejmują nawigacji, wybór i edycji. Zachowanie podczas zaznaczania jest zależna od <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> i <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> właściwości. Wartości domyślne, które powodują zachowanie opisane w tym temacie są <xref:System.Windows.Controls.DataGridSelectionMode.Extended?displayProperty=nameWithType> i <xref:System.Windows.Controls.DataGridSelectionUnit.FullRow?displayProperty=nameWithType>. Zmiana tych wartości może spowodować zachowanie, które różni się od opisujące. Gdy komórka jest w trybie edycji, kontrolka edycji mogą zastąpić zachowanie standardowy interfejs użytkownika <xref:System.Windows.Controls.DataGrid>.  
  
## <a name="default-keyboard-behavior"></a>Domyślne zachowanie klawiatury  
 W poniższej tabeli wymieniono domyślne zachowanie klawiatury dla <xref:System.Windows.Controls.DataGrid>.  
  
|Klawisz lub kombinację klawiszy|Opis|  
|----------------------------|-----------------|  
|STRZAŁKA W DÓŁ|Przenosi fokus do komórki bezpośrednio poniżej bieżącej komórki. Jeśli fokus jest ustawiony w ostatnim wierszu, naciskając klawisz Strzałka w dół nic nie robi.|  
|STRZAŁKA W GÓRĘ|Przenosi fokus do komórki bezpośrednio powyżej bieżącej komórki. Jeśli fokus jest ustawiony w pierwszym wierszu, naciskając klawisz Strzałka w górę nic nie robi.|  
|STRZAŁKA W LEWO|Przenosi fokus do poprzedniej komórki w wierszu. Jeśli fokus znajduje się w pierwszej komórki w wierszu, naciskając klawisz Strzałka w lewo nic nie robi.|  
|STRZAŁKA W PRAWO|Przenosi fokus do następnej komórki w wierszu. Jeśli fokus znajduje się w ostatniej komórki w wierszu, naciskając klawisz Strzałka w prawo nic nie robi.|  
|STRONA GŁÓWNA|Przenosi fokus do pierwszej komórki w bieżącym wierszu.|  
|END|Przenosi fokus do ostatniej komórki w bieżącym wierszu.|  
|PAGE DOWN|Jeśli nie są zgrupowane wiersze, Przewija formant w dół przez liczbę wierszy, które w pełni są wyświetlane. Przenosi fokus do ostatniego wiersza pełni wyświetlane bez zmieniania kolumn.<br /><br /> Jeśli wiersze są grupowane, przenosi fokus do ostatniego wiersza w <xref:System.Windows.Controls.DataGrid> bez zmieniania kolumn.|  
|PAGE UP|Jeśli nie są zgrupowane wiersze, przewija się, formant w górę przez liczbę wierszy, które w pełni są wyświetlane. Przenosi fokus do pierwszego wiersza wyświetlane bez zmieniania kolumn.<br /><br /> Jeśli wiersze są grupowane, przenosi fokus do pierwszego wiersza w <xref:System.Windows.Controls.DataGrid> bez zmieniania kolumn.|  
|TAB|Przenosi fokus do następnej komórki w bieżącym wierszu. Jeśli fokus jest ustawiony w komórce ostatni wiersz, przenosi fokus do pierwszej komórki w kolejnym wierszu. Jeśli fokus znajduje się w ostatniej komórki w formancie, przenosi fokus do następnej kontrolki w kolejności tabulacji kontenera nadrzędnego.<br /><br /> Jeśli bieżącej komórki jest w trybie edycji i naciśnięcie powoduje, że fokus na klawiszu TAB do przesuwania kursora od bieżącego wiersza, wszelkie zmiany, które zostały wprowadzone do wiersza są stosowane przed zmianą fokus.|  
|SHIFT+TAB|Przenosi fokus do poprzedniej komórki w bieżącym wierszu. Jeśli fokus jest już pierwszą komórkę w wierszu, przenosi fokus do ostatniej komórki w poprzednim wierszu. Jeśli fokus znajduje się w pierwszej komórki w formancie, przenosi fokus do poprzedniego formantu w kolejności tabulacji kontenera nadrzędnego.<br /><br /> Jeśli bieżącej komórki jest w trybie edycji i naciśnięcie powoduje, że fokus na klawiszu TAB do przesuwania kursora od bieżącego wiersza, wszelkie zmiany, które zostały wprowadzone do wiersza są stosowane przed zmianą fokus.|  
|CTRL+DOWN ARROW|Przenosi fokus do ostatniej komórki w bieżącej kolumnie.|  
|CTRL + STRZAŁKA W GÓRĘ|Przenosi fokus do pierwszej komórki w bieżącej kolumnie.|  
|CTRL + STRZAŁKA W PRAWO|Przenosi fokus do ostatniej komórki w bieżącym wierszu.|  
|CTRL + STRZAŁKA W LEWO|Przenosi fokus do pierwszej komórki w bieżącym wierszu.|  
|CTRL+HOME|Przenosi fokus do pierwszej komórki w formancie.|  
|CTRL+END|Przenosi fokus do ostatniej komórki w formancie.|  
|CTRL + PAGE DOWN|Taka sama jak PAGE DOWN.|  
|CTRL + PAGE UP|Taka sama jak PAGE UP.|  
|F2|Jeśli <xref:System.Windows.Controls.DataGrid.IsReadOnly%2A?displayProperty=nameWithType> właściwość `false` i <xref:System.Windows.Controls.DataGridColumn.IsReadOnly%2A?displayProperty=nameWithType> właściwość `false` bieżącej kolumny umieszcza bieżącej komórki w komórce trybu edycji.|  
|ENTER|Przekazuje zmiany na bieżącej komórki i wiersza i przenosi fokus do komórki bezpośrednio poniżej bieżącej komórki. Jeśli fokus jest ustawiony w ostatnim wierszu, przekazuje zmiany bez przenoszenia fokusu.|  
|ESC|Jeśli kontrolka jest w trybie edycji, anuluje edycji i przywraca zmiany wprowadzone w kontrolce. Jeśli dane bazowe źródło implementuje <xref:System.ComponentModel.IEditableObject>, naciskając klawisz ESC po raz drugi anuluje trybu edycji dla całego wiersza.|  
|BACKSPACE|Usuwa znak przed kursora, edycji komórki.|  
|DELETE|Usuwa znak po kursora, edycji komórki.|  
|CTRL+ENTER|Zatwierdza zmiany do bieżącej komórki bez przenoszenia fokusu.|  
|CTRL+A|Jeśli <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ustawiono <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, wybiera wszystkie wiersze w <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="selection-keys"></a>Wybór kluczy  
 Jeśli <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, zachowanie nawigacji nie zmienia się, ale Nawigacja przy użyciu klawiatury, przytrzymaj klawisze SHIFT (w tym klawiszy CTRL + SHIFT) zmodyfikuje Zaznaczanie wielu wierszy. Przed rozpoczęciem nawigacji, formant oznacza bieżący wiersz jako zakotwiczenia wiersza. Po przejściu przytrzymaj klawisze SHIFT zaznaczenie obejmuje wszystkie wiersze między zakotwiczenia wiersza i bieżącego wiersza.  
  
 Następujące klucze wybór zmodyfikować wielowierszowych wybór.  
  
-   SHIFT + STRZAŁKA W DÓŁ  
  
-   SHIFT + STRZAŁKA W GÓRĘ  
  
-   SHIFT + PAGE DOWN  
  
-   SHIFT + PAGE UP  
  
-   STRZAŁKA CTRL + SHIFT + STRZAŁKA W DÓŁ  
  
-   STRZAŁKA CTRL + SHIFT + STRZAŁKA W GÓRĘ  
  
-   CTRL+SHIFT+HOME  
  
-   CTRL+SHIFT+END  
  
## <a name="default-mouse-behavior"></a>Domyślne zachowanie myszy  
 W poniższej tabeli wymieniono domyślne zachowanie myszy dla <xref:System.Windows.Controls.DataGrid>.  
  
|Akcja myszy|Opis|  
|------------------|-----------------|  
|Kliknij wybrany wiersz|Sprawia, że wiersz kliknięto bieżący wiersz i kliknięto komórki bieżącej komórki.|  
|Kliknij przycisk bieżącej komórki|Umieszcza bieżącej komórki w trybie edycji.|  
|Przeciągnij komórki nagłówka kolumny|Jeśli <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A?displayProperty=nameWithType> właściwość `true` i <xref:System.Windows.Controls.DataGridColumn.CanUserReorder%2A?displayProperty=nameWithType> właściwość `true` bieżącej kolumny przenosi kolumnę tak, aby można było porzucić do nowej pozycji.|  
|Przeciągnij separator nagłówek kolumny|Jeśli <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> właściwość `true` i <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> właściwość `true` bieżącej kolumny zmienia rozmiar kolumny.|  
|Kliknij dwukrotnie separator nagłówek kolumny|Jeśli <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> właściwość `true` i <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> właściwość `true` dla bieżącej kolumny całościowy przy użyciu kolumny <xref:System.Windows.Controls.DataGridLength.Auto%2A> tryb zmiany rozmiaru.|  
|Kliknij komórkę nagłówka kolumny|Jeśli <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A?displayProperty=nameWithType> właściwość `true` i <xref:System.Windows.Controls.DataGridColumn.CanUserSort%2A?displayProperty=nameWithType> właściwość `true` bieżącej kolumny sortowania kolumny.<br /><br /> Kliknięcie nagłówka kolumny, która jest już sortowana będzie odwrócić kierunek sortowania tej kolumny.<br /><br /> Naciśnięcie klawisza SHIFT, a kliknięcie wielu nagłówków kolumn sortowania według wielu kolumn w kolejności kliknięto.|  
|CTRL + kliknięcie wiersza|Jeśli <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ustawiono <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, modyfikuje nieciągłe zaznaczenie wielu wierszy.<br /><br /> Jeśli wiersz jest już zaznaczone, powoduje usunięcie zaznaczenia wiersza.|  
|SHIFT + kliknięcie wiersza|Jeśli <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ustawiono <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, modyfikuje wyboru wielowierszowych ciągłego.|  
|Kliknij nagłówek grupy wierszy|Rozwija lub zwija grupy.|  
|Kliknij przycisk Zaznacz wszystko w lewym górnym rogu aplikacji <xref:System.Windows.Controls.DataGrid>|Jeśli <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ustawiono <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, wybiera wszystkie wiersze w <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="mouse-selection"></a>Wybór myszy  
 Jeśli <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, klikając wiersz w trakcie naciskania klawisza CTRL lub SHIFT zmodyfikuje Zaznaczanie wielu wierszy.  
  
 Po kliknięciu wiersz podczas naciskania klawisza CTRL, wiersz zmieni jego stan zaznaczenia, a wszystkie pozostałe wiersze zachować wraz z bieżącym stanem wyboru. W tym celu wybrania wierszy sąsiadują.  
  
 Po kliknięciu wiersz przytrzymaj klawisze SHIFT zaznaczenie obejmuje wszystkie wiersze między bieżący wiersz i wiersz zakotwiczenia znajdujący się w pozycji bieżącego wiersza przed kliknięcie. Kolejne kliknięć przytrzymaj klawisze SHIFT zmienić bieżący wiersz, ale nie zakotwiczenia wiersza. To zrobić, aby wybrać zakres sąsiadujących wierszy.  
  
 Aby wybrać niesąsiadujące zakresy sąsiadujące można łączyć CTRL + SHIFT. Aby to zrobić, wybierz pierwszy zakres, korzystając z klawisza SHIFT + kliknij zgodnie z wcześniejszym opisem. Po wybraniu pierwszego zakres wierszy należy użyj kombinacji klawisza CTRL i kliknij, aby zaznaczyć pierwszy wiersz w zakresie dalej, a następnie kliknij ostatni wiersz w zakresie dalej przytrzymaj klawisze CTRL + SHIFT.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGrid.SelectionMode%2A>
