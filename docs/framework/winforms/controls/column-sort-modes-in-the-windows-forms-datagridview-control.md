---
title: Tryb sortowania kolumn w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: 9ebcfc435fcc7d2b0dfbfe3004d958c73dd1347c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Tryb sortowania kolumn w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> kolumny mają trzech trybów sortowania. Tryb sortowania dla każdej kolumny jest określany za pośrednictwem <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> właściwości kolumny, która może należeć do jednej z następujących <xref:System.Windows.Forms.DataGridViewColumnSortMode> wartości wyliczenia.  
  
|`DataGridViewColumnSortMode` Wartość|Opis|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Wartości domyślnej dla kolumny pola tekstowego. Chyba, że nagłówki kolumn są używane do wyboru, kliknięcie nagłówka kolumny automatycznie sortuje <xref:System.Windows.Forms.DataGridView> według tej kolumny i wyświetla symbolu wskazującą kolejność sortowania.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Domyślnie pole — kolumn. W tej kolumnie można sortować programowo; jednak nie ma ona do sortowania, więc miejsce nie jest zarezerwowana dla symbolu sortowania.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|W tej kolumnie można sortować programowo, a miejsca jest zarezerwowana dla symbolu sortowania.|  
  
 Możesz chcieć zmienić tryb sortowania kolumny, która domyślnie <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> zawiera wartości, które można uzyskać wiarygodny uporządkowane. Na przykład jeśli kolumna bazy danych zawierająca liczby, reprezentujące stanów elementu, można wyświetlić te liczby jako odpowiadające im ikony przez powiązanie kolumny obrazu do kolumny bazy danych. Można modyfikować wartości liczbowe komórki do wartości wyświetlania obrazu w procedurze obsługi dla <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> zdarzeń. W takim przypadku ustawienie <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> umożliwi użytkownikom posortować kolumnę. Automatyczne sortowanie umożliwi użytkownikom elementy grupy, które mają takim samym stanie, nawet jeśli stanów odpowiadający liczby ma fizycznych sekwencji. Pole wyboru kolumny są inny przykład, w którym automatyczne sortowanie jest przydatne w przypadku grupowanie elementów w tym samym stanie.  
  
 Można sortować <xref:System.Windows.Forms.DataGridView> programowo przez wartości w dowolnej kolumny lub wielu kolumn, niezależnie od tego, <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> ustawienia. Sortowanie programowe jest przydatne, gdy chcesz zapewnić z własnego interfejsu użytkownika (UI) do sortowania lub aby zaimplementować sortowanie niestandardowe. Warunkiem własne sortowania interfejsu użytkownika jest przydatne, na przykład po ustawieniu <xref:System.Windows.Forms.DataGridView> trybu wyboru, aby umożliwić wybór nagłówka kolumny. W takim przypadku chociaż nagłówki kolumn nie może służyć do sortowania, ma nadal nagłówków, aby wyświetlić odpowiednie symbolu sortowania, dlatego należy ustawić <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>.  
  
 Ustawiono tryb programowe sortowania kolumn nie są automatycznie sortowania symbolu. Dla tych kolumn, konieczne jest wyświetlenie symboli samodzielnie przez ustawienie <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> właściwości. Jest to konieczne, jeśli chcesz elastyczność w niestandardowych sortowania. Na przykład można posortować <xref:System.Windows.Forms.DataGridView> przez wiele kolumn, można wyświetlić wiele symboli sortowania lub nie sortowania symbolu.  
  
 Mimo że można sortować programowo <xref:System.Windows.Forms.DataGridView> według dowolnej kolumny, niektóre kolumny, takich jak przycisk kolumny, nie może zawierać wartości, które można uzyskać wiarygodny uporządkowane. Dla tych kolumn <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> ustawienie właściwości <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> wskazuje, że nigdy nie będzie on używane do sortowania, nie istnieje potrzeba aby zarezerwować miejsce w nagłówku sortowania symbolu.  
  
 Gdy <xref:System.Windows.Forms.DataGridView> jest sortowana, można określić zarówno Sortuj kolumny i kolejność sortowania sprawdzając wartości <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> i <xref:System.Windows.Forms.DataGridView.SortOrder%2A> właściwości. Wartości te nie są istotne po niestandardowych operacji sortowania. Aby uzyskać więcej informacji o niestandardowych sortowanie zobacz sekcję sortowanie niestandardowe w dalszej części tego tematu.  
  
 Gdy <xref:System.Windows.Forms.DataGridView> formant zawierający zarówno powiązane i niepowiązanych kolumn jest posortowana, wartości niepowiązanych kolumn nie może być obsługiwany automatycznie. Aby zachować te wartości, musi implementować trybie wirtualnym, ustawiając <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwości `true` i obsługi <xref:System.Windows.Forms.DataGridView.CellValueNeeded> i <xref:System.Windows.Forms.DataGridView.CellValuePushed> zdarzenia. Aby uzyskać więcej informacji, zobacz [porady: Implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md). Sortowanie według niepowiązanych kolumn w trybie powiązania nie jest obsługiwane.  
  
## <a name="programmatic-sorting"></a>Sortowanie programowe  
 Można sortować <xref:System.Windows.Forms.DataGridView> programowo przez wywołanie jego <xref:System.Windows.Forms.DataGridView.Sort%2A> metody.  
  
 `Sort(DataGridViewColumn,ListSortDirection)` Przeciążenia z <xref:System.Windows.Forms.DataGridView.Sort%2A> ma metodę <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.ComponentModel.ListSortDirection> wartość wyliczenia jako parametry. To przeciążenie jest przydatne podczas sortowania według kolumn z wartościami, które może zostać określona uzyskać wiarygodny, ale które nie chcesz skonfigurować do automatycznego sortowania. Kiedy wywołać tego przeciążenia i przekazać w kolumnie z <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> wartość właściwości <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> i <xref:System.Windows.Forms.DataGridView.SortOrder%2A> właściwości są ustawiane automatycznie i odpowiednie symbolu sortowania jest wyświetlany w nagłówku kolumny.  
  
> [!NOTE]
>  Gdy <xref:System.Windows.Forms.DataGridView> kontrolka jest powiązana z zewnętrznego źródła danych przez ustawienie <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwość `Sort(DataGridViewColumn,ListSortDirection)` przeciążenie metody nie działa w przypadku niepowiązanych kolumn. Ponadto, jeśli <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwość jest `true`, można wywołać tego przeciążenia tylko w przypadku powiązane kolumny. Aby określić, czy kolumna jest powiązany z danymi, należy sprawdzić <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A> wartości właściwości. Sortowanie niepowiązanych kolumn w trybie powiązania nie jest obsługiwane.  
  
## <a name="custom-sorting"></a>Sortowanie niestandardowe  
 Można dostosować <xref:System.Windows.Forms.DataGridView> za pomocą `Sort(IComparer)` przeciążenia z <xref:System.Windows.Forms.DataGridView.Sort%2A> metody lub obsługa <xref:System.Windows.Forms.DataGridView.SortCompare> zdarzeń.  
  
 `Sort(IComparer)` Przeciążenie metody przyjmuje wystąpienia klasy, która implementuje <xref:System.Collections.IComparer> interfejsu jako parametr. To przeciążenie jest przydatne, gdy chcesz zapewnić sortowania niestandardowych; na przykład, gdy wartości w kolumnie nie ma porządek sortowania fizyczne lub gdy porządek sortowania fizyczna jest nieodpowiedni. W takim przypadku nie można użyć automatyczne sortowanie, ale nadal ma użytkowników, aby sortować, klikając nagłówki kolumn. Można wywołać tego przeciążenia programu obsługi dla <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> zdarzeń, jeśli nie używasz nagłówki kolumn do wyboru.  
  
> [!NOTE]
>  `Sort(IComparer)` Przeciążenie metody działa tylko wtedy, gdy <xref:System.Windows.Forms.DataGridView> formant nie jest powiązany z zewnętrznego źródła danych i <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> wartość właściwości jest `false`. Aby dostosować sortowania dla kolumny powiązane z zewnętrznego źródła danych, należy użyć operacji sortowania podana przez źródło danych. W trybie wirtualnym należy podać operacji sortowania dla niepowiązanych kolumn.  
  
 Aby użyć `Sort(IComparer)` przeciążenie metody, należy utworzyć własne klasy, która implementuje <xref:System.Collections.IComparer> interfejsu. Ten interfejs wymaga klasy do zaimplementowania <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType> metody, do której <xref:System.Windows.Forms.DataGridView> przekazuje <xref:System.Windows.Forms.DataGridViewRow> obiekty jako danych wejściowych, gdy `Sort(IComparer)` jest wywoływana metoda przeciążenia. O tym można obliczyć kolejności poprawne wiersza na podstawie wartości w dowolnej kolumny.  
  
 `Sort(IComparer)` Przeciążenie metody nie ustawia <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> i <xref:System.Windows.Forms.DataGridView.SortOrder%2A> właściwości, więc należy zawsze ustawić <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> właściwość, aby wyświetlić sortowania symbolu.  
  
 Alternatywą wobec `Sort(IComparer)` przeciążenie metody można podać sortowanie niestandardowe zaimplementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.SortCompare> zdarzeń. To zdarzenie występuje, gdy użytkownik kliknie nagłówki kolumn skonfigurowane automatyczne sortowanie lub podczas wywoływania `Sort(DataGridViewColumn,ListSortDirection)` przeciążenia z <xref:System.Windows.Forms.DataGridView.Sort%2A> metody. Zdarzenie dla każdej pary wierszy w formancie, dzięki któremu można obliczyć ich kolejność.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.SortCompare> Zdarzenie nie występuje podczas <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwość jest ustawiona lub gdy <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> wartość właściwości jest `true`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>  
 [Sortowanie danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [Instrukcje: ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
 [Instrukcje: dostosowywanie sortowania w kontrolce DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
