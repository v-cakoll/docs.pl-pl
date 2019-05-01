---
title: Tryb sortowania kolumn w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: b8f6048946d367dd79b1ce0d23d84446ffdb1115
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956224"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Tryb sortowania kolumn w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> kolumny mają trzy tryby sortowania. Tryb sortowania dla każdej kolumny jest określony za pomocą <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> właściwości kolumny, które można ustawić na jeden z następujących <xref:System.Windows.Forms.DataGridViewColumnSortMode> wartości wyliczenia.  
  
|`DataGridViewColumnSortMode` Wartość|Opis|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Domyślny tekst pola kolumn. Chyba, że nagłówki kolumn są używane do wyboru, kliknięcie nagłówka kolumny automatycznie sortuje <xref:System.Windows.Forms.DataGridView> według tej kolumny i wyświetla glif określającą kolejność sortowania.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Domyślnie w polu — kolumnach. W tej kolumnie można sortować programowo; jednak go nie ma do sortowania, aby miejsce nie jest zarezerwowana dla symbol sortowania.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|W tej kolumnie można sortować programowo, a miejsce jest zarezerwowane dla symbol sortowania.|  
  
 Możesz chcieć zmienić tryb sortowania kolumn, które domyślnie <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> zawiera wartości, które mogą znacząco uporządkowane. Na przykład jeśli kolumna bazy danych zawierająca numery, które reprezentują stany elementów, możesz wyświetlić te liczby jako odpowiadające im ikony przez powiązanie kolumny obrazu kolumny bazy danych. Można modyfikować wartości liczbowe komórki do wartości wyświetlania obrazu w obsłudze dla <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> zdarzeń. W takim przypadku ustawienie <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> właściwość <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> umożliwi użytkownikom posortować kolumnę. Automatyczne sortowanie umożliwi użytkownikom grupowanie elementów, które mają ten sam stan, nawet jeśli stany odpowiadający liczby nie mają naturalnego sekwencji. Pole wyboru kolumny są inny przykład, w którym automatyczne sortowanie jest przydatne w przypadku grupowanie elementów w tym samym stanie.  
  
 Można sortować <xref:System.Windows.Forms.DataGridView> programowo według wartości w dowolnej kolumnie lub w wielu kolumnach, niezależnie od tego, <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> ustawienia. Programowe sortowanie jest przydatne, gdy chcesz udostępnić własnego interfejsu użytkownika (UI) na potrzeby sortowania lub gdy chcesz zaimplementować niestandardowy sortowania. Udostępniając własne sortowania interfejsu użytkownika jest przydatne, na przykład po ustawieniu <xref:System.Windows.Forms.DataGridView> tryb wyboru, aby umożliwić wybór nagłówka kolumny. W tym przypadku mimo, że nagłówki kolumn nie można użyć do sortowania i nadal ma nagłówki, aby wyświetlić odpowiedni symbol sortowania, więc należy ustawić <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> właściwość <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>.  
  
 Ustawiony tryb programowe sortowanie kolumn nie są automatycznie wyświetlane symbol sortowania. W tych kolumnach, należy wyświetlić glif samodzielnie, ustawiając <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> właściwości. Jest to konieczne, jeśli potrzebna jest elastyczność w niestandardowym sortowaniem. Na przykład jeśli sortujesz <xref:System.Windows.Forms.DataGridView> przez wiele kolumn, możesz chcieć wyświetlić wiele symbole sortowania lub nie symbol sortowania.  
  
 Mimo że można programowo sortować <xref:System.Windows.Forms.DataGridView> według dowolnej kolumny, niektóre kolumny, takie jak kolumnach przycisków, nie będzie zawierać wartości, które mogą znacząco uporządkowane. W tych kolumnach <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> ustawienie właściwości <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> wskazuje, że nigdy nie będzie on używane do sortowania, więc nie ma potrzeby aby zarezerwować miejsce w nagłówku symbol sortowania.  
  
 Gdy <xref:System.Windows.Forms.DataGridView> jest sortowana, można określić kolumnę sortowania i porządek sortowania, sprawdzając wartości <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> i <xref:System.Windows.Forms.DataGridView.SortOrder%2A> właściwości. Te wartości nie są istotne po niestandardowych operacji sortowania. Aby uzyskać więcej informacji na temat niestandardowych sortowanie sekcja sortowania niestandardowych w dalszej części tego tematu.  
  
 Gdy <xref:System.Windows.Forms.DataGridView> kontrolka zawiera zarówno powiązane i niepowiązanych kolumn jest sortowana, wartości w niepowiązanych kolumn nie może być obsługiwany automatycznie. Aby zachować te wartości, należy zaimplementować trybu wirtualnego przez ustawienie <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwości `true` i obsługa <xref:System.Windows.Forms.DataGridView.CellValueNeeded> i <xref:System.Windows.Forms.DataGridView.CellValuePushed> zdarzenia. Aby uzyskać więcej informacji, zobacz [jak: Implementowanie trybu wirtualnego w Windows formantu DataGridView formularzy](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md). Sortowanie według niepowiązanych kolumn w powiązanej tryb nie jest obsługiwane.  
  
## <a name="programmatic-sorting"></a>Programowe sortowanie  
 Można sortować <xref:System.Windows.Forms.DataGridView> programowo przez wywołanie jego <xref:System.Windows.Forms.DataGridView.Sort%2A> metody.  
  
 `Sort(DataGridViewColumn,ListSortDirection)` Przeciążenia <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda przyjmuje <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.ComponentModel.ListSortDirection> wartość wyliczenia jako parametry. To przeciążenie jest przydatne, gdy sortowanie według kolumny z wartościami, które może zostać określona znacząco, ale które nie chcesz skonfigurować do automatycznego sortowania. Kiedy wywołać tego przeciążenia i przekazywać w kolumnie z <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> wartość właściwości <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> i <xref:System.Windows.Forms.DataGridView.SortOrder%2A> właściwości są ustawiane automatycznie i odpowiedni symbol sortowania pojawia się w nagłówku kolumny.  
  
> [!NOTE]
>  Gdy <xref:System.Windows.Forms.DataGridView> kontrolka jest powiązana z zewnętrznego źródła danych, ustawiając <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości `Sort(DataGridViewColumn,ListSortDirection)` przeciążenie metody nie działa w przypadku niepowiązanych kolumn. Ponadto, jeśli <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwość `true`, można wywołać tego przeciążenia tylko do powiązanych kolumn. Aby określić, czy kolumna jest powiązany z danymi, sprawdzić <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A> wartości właściwości. Sortowanie niepowiązanych kolumn w powiązanej tryb nie jest obsługiwane.  
  
## <a name="custom-sorting"></a>Sortowanie niestandardowe  
 Można dostosować <xref:System.Windows.Forms.DataGridView> przy użyciu `Sort(IComparer)` przeciążenia <xref:System.Windows.Forms.DataGridView.Sort%2A> metody lub obsługując <xref:System.Windows.Forms.DataGridView.SortCompare> zdarzeń.  
  
 `Sort(IComparer)` Przeciążenie metody pobierające wystąpienie klasy, która implementuje <xref:System.Collections.IComparer> interfejsu jako parametr. To przeciążenie jest przydatne w przypadku, gdy chcesz zapewnić sortowania niestandardowych; na przykład, gdy wartości w kolumnie ma naturalny porządek lub gdy naturalny porządek sortowania jest nieodpowiedni. W tym przypadku nie można użyć automatycznego sortowania, ale nadal ma użytkowników, aby sortować, klikając nagłówki kolumn. Można wywołać tego przeciążenia w obsłudze dla <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> zdarzeń, jeśli nie używasz nagłówki kolumn do wyboru.  
  
> [!NOTE]
>  `Sort(IComparer)` Przeciążenie metody działa tylko wtedy, gdy <xref:System.Windows.Forms.DataGridView> kontrolka nie jest powiązana z zewnętrznego źródła danych i <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> wartość właściwości jest `false`. Aby dostosować sortowanie dla kolumny powiązane z zewnętrznego źródła danych, należy użyć operacji sortowania, dostarczone przez źródło danych. W trybie wirtualnym należy podać operacji sortowania dla kolumn niepowiązanej.  
  
 Aby użyć `Sort(IComparer)` przeciążenia metody, należy utworzyć własne klasy, która implementuje <xref:System.Collections.IComparer> interfejsu. Ten interfejs wymaga klasy do zaimplementowania <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType> metody, do którego <xref:System.Windows.Forms.DataGridView> przekazuje <xref:System.Windows.Forms.DataGridViewRow> obiektów jako danych wejściowych, gdy `Sort(IComparer)` przeciążenie metody jest wywoływana. Dzięki temu można obliczyć, porządkowanie odpowiedni wiersz na podstawie wartości w dowolnej kolumnie.  
  
 `Sort(IComparer)` Przeciążenie metody nie ustawia <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> i <xref:System.Windows.Forms.DataGridView.SortOrder%2A> właściwości, dzięki czemu zawsze należy ustawić <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> właściwość, aby wyświetlić symbol sortowania.  
  
 Jako alternatywę dla `Sort(IComparer)` przeciążenia metody, można podać niestandardowy sortowanie poprzez implementację obsługi dla <xref:System.Windows.Forms.DataGridView.SortCompare> zdarzeń. To zdarzenie występuje, gdy użytkownik kliknie nagłówki kolumn skonfigurowane do automatycznego sortowania lub gdy wywołujesz `Sort(DataGridViewColumn,ListSortDirection)` przeciążenia <xref:System.Windows.Forms.DataGridView.Sort%2A> metody. Dla każdej pary wierszy w formancie, dzięki któremu można obliczyć kolejności wystąpieniu zdarzenia.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.SortCompare> Zdarzenie nie występuje podczas <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwość jest ustawiona lub jeśli <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> wartość właściwości jest `true`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Sortowanie danych w kontrolce DataGridView formularzy Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [Instrukcje: Dostosowywanie sortowania w kontrolce DataGridView formularzy Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
