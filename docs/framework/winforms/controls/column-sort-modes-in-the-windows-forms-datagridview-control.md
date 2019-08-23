---
title: Tryb sortowania kolumn w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: d0d743ccae38d101eda5bb9780b33ae18dfb608a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918446"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Tryb sortowania kolumn w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView>kolumny mają trzy tryby sortowania. Tryb sortowania dla każdej kolumny jest określany za pomocą <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> właściwości kolumny, która może być ustawiona na jedną z następujących <xref:System.Windows.Forms.DataGridViewColumnSortMode> wartości wyliczenia.  
  
|`DataGridViewColumnSortMode`wartościami|Opis|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Wartość domyślna kolumn pól tekstowych. Jeśli nagłówki kolumn nie są używane do zaznaczania, kliknięcie nagłówka kolumny automatycznie sortuje <xref:System.Windows.Forms.DataGridView> według tej kolumny i wyświetla glif wskazujący kolejność sortowania.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Wartość domyślna dla kolumn innych niż pola tekstowe. Tę kolumnę można programowo sortować. nie jest to jednak przeznaczone do sortowania, więc żadne miejsce nie jest zarezerwowane dla glifu sortowania.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|Można sortować tę kolumnę programowo, a miejsce jest zarezerwowane dla glifu sortowania.|  
  
 Można zmienić tryb sortowania dla kolumny, która domyślnie jest wartością domyślną <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> , jeśli zawiera ona wartości, które mogą być zrozumiałe. Na przykład, jeśli istnieje kolumna bazy danych zawierająca liczby, które reprezentują Stany elementów, można wyświetlić te liczby jako odpowiednie ikony przez powiązanie kolumny obrazu z kolumną bazy danych. Następnie można zmienić wartości komórki liczbowej na wartości wyświetlane w obrazie w programie obsługi <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> zdarzenia. W takim przypadku ustawienie <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> właściwości na <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> spowoduje umożliwienie użytkownikom sortowania kolumny. Automatyczne sortowanie umożliwi użytkownikom grupowanie elementów, które mają ten sam stan nawet wtedy, gdy Stany odpowiadające liczbom nie mają naturalnej sekwencji. Kolumny pól wyboru to kolejny przykład, w którym sortowanie automatyczne jest przydatne w przypadku grupowania elementów w tym samym stanie.  
  
 Można sortować <xref:System.Windows.Forms.DataGridView> programowo przez wartości w dowolnej kolumnie lub w wielu kolumnach, niezależnie <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> od ustawień. Sortowanie programistyczne jest przydatne, gdy chcesz zapewnić własny interfejs użytkownika do sortowania lub Kiedy chcesz zaimplementować sortowanie niestandardowe. Udostępnianie własnego interfejsu użytkownika sortowania jest przydatne, na przykład podczas ustawiania <xref:System.Windows.Forms.DataGridView> trybu zaznaczania, aby włączyć wybieranie nagłówka kolumny. W tym przypadku, chociaż nagłówki kolumn nie mogą być używane do sortowania, nadal chcesz, aby nagłówki wyświetlały odpowiedni symbol sortowania, więc ustaw <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> właściwość na. <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>  
  
 Kolumny ustawione na tryb sortowania programistycznego nie wyświetlają automatycznie symbolu sortowania. Dla tych kolumn należy samodzielnie wyświetlić symbol, ustawiając <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> właściwość. Jest to konieczne, jeśli chcesz mieć elastyczność w sortowaniu niestandardowym. Na przykład, jeśli sortujesz <xref:System.Windows.Forms.DataGridView> według wielu kolumn, możesz chcieć wyświetlić wiele glifów sortowania lub bez glifów sortowania.  
  
 Mimo że można programowo sortować <xref:System.Windows.Forms.DataGridView> według dowolnej kolumny, niektóre kolumny, takie jak kolumny przycisków, mogą nie zawierać wartości, które mogą być zrozumiałe. Dla tych kolumn <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> ustawienie właściwości wskazuje, że nigdy nie będzie używane do sortowania, więc nie ma potrzeby rezerwowania miejsca w nagłówku dla symbolu sortowania.  
  
 Gdy jest sortowany, można określić zarówno kolumnę sortowania, jak i porządek sortowania, sprawdzając wartości <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> właściwości i <xref:System.Windows.Forms.DataGridView.SortOrder%2A>. <xref:System.Windows.Forms.DataGridView> Te wartości nie mają znaczenia po niestandardowej operacji sortowania. Aby uzyskać więcej informacji na temat sortowania niestandardowego, zobacz sekcję niestandardowe sortowanie w dalszej części tego tematu.  
  
 Po posortowaniu <xref:System.Windows.Forms.DataGridView> kontrolki zawierającej kolumny powiązane i niepowiązane nie można automatycznie utrzymywać wartości w kolumnach niepowiązanych. Aby zachować te wartości, należy zaimplementować tryb <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> wirtualny przez ustawienie właściwości na `true` i obsługę <xref:System.Windows.Forms.DataGridView.CellValueNeeded> zdarzeń i <xref:System.Windows.Forms.DataGridView.CellValuePushed> . Aby uzyskać więcej informacji, zobacz [jak: Zaimplementuj tryb wirtualny w kontrolce](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms. Sortowanie według niepowiązanych kolumn w trybie związanym nie jest obsługiwane.  
  
## <a name="programmatic-sorting"></a>Sortowanie programistyczne  
 Można sortować <xref:System.Windows.Forms.DataGridView> programowo, <xref:System.Windows.Forms.DataGridView.Sort%2A> wywołując metodę.  
  
 `Sort(DataGridViewColumn,ListSortDirection)` Przeciążenie <xref:System.Windows.Forms.DataGridView.Sort%2A> metodyprzyjmuje<xref:System.Windows.Forms.DataGridViewColumn> jako parametry i wartość wyliczenia.<xref:System.ComponentModel.ListSortDirection> To przeciążenie jest przydatne podczas sortowania według kolumn z wartościami, które mogą być uporządkowane w sposób znaczący, ale których nie chcesz konfigurować do automatycznego sortowania. Po wywołaniu tego przeciążenia i <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> przejściu do kolumny z <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>wartością właściwości, <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> właściwości i <xref:System.Windows.Forms.DataGridView.SortOrder%2A> są ustawiane automatycznie, a odpowiedni symbol sortowania pojawia się w nagłówku kolumny.  
  
> [!NOTE]
> Gdy formant jest powiązany z zewnętrznym źródłem danych przez <xref:System.Windows.Forms.DataGridView.DataSource%2A> ustawienie właściwości, `Sort(DataGridViewColumn,ListSortDirection)` Przeciążenie metody nie działa w przypadku kolumn niepowiązanych. <xref:System.Windows.Forms.DataGridView> Ponadto, gdy <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwość jest `true`, można wywołać to Przeciążenie tylko dla kolumn powiązanych. Aby określić, czy kolumna jest powiązana z danymi, sprawdź <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A> wartość właściwości. Sortowanie kolumn niepowiązanych w trybie związanym nie jest obsługiwane.  
  
## <a name="custom-sorting"></a>Sortowanie niestandardowe  
 Można dostosować <xref:System.Windows.Forms.DataGridView> przy `Sort(IComparer)` użyciu przeciążenia <xref:System.Windows.Forms.DataGridView.Sort%2A> metody lub przez obsługę <xref:System.Windows.Forms.DataGridView.SortCompare> zdarzenia.  
  
 Przeciążenie metody przyjmuje wystąpienie klasy <xref:System.Collections.IComparer> implementującej interfejs jako parametr. `Sort(IComparer)` To przeciążenie jest przydatne, gdy chcesz zapewnić niestandardowe sortowanie; na przykład, gdy wartości w kolumnie nie mają naturalnej kolejności sortowania lub gdy porządek sortowania naturalny jest nieodpowiedni. W takim przypadku nie można użyć automatycznego sortowania, ale możesz nadal sortować użytkowników, klikając nagłówki kolumn. Można wywołać to Przeciążenie w procedurze obsługi dla zdarzenia, <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> Jeśli nie używasz nagłówków kolumn do wyboru.  
  
> [!NOTE]
> Przeciążenie metody działa tylko wtedy, <xref:System.Windows.Forms.DataGridView> gdy formant nie jest powiązany z <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> zewnętrznym źródłem danych, a wartość właściwości to `false`. `Sort(IComparer)` Aby dostosować sortowanie dla kolumn powiązanych z zewnętrznym źródłem danych, należy użyć operacji sortowania dostarczonych przez źródło danych. W trybie wirtualnym należy zapewnić własne operacje sortowania dla kolumn niepowiązanych.  
  
 Aby użyć `Sort(IComparer)` przeciążenia metody, należy utworzyć własną klasę, która <xref:System.Collections.IComparer> implementuje interfejs. Ten interfejs wymaga, <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType> aby Klasa zaimplementował metodę, do <xref:System.Windows.Forms.DataGridView> której obiekty <xref:System.Windows.Forms.DataGridViewRow> są przekazywane jako dane wejściowe `Sort(IComparer)` , gdy wywoływana jest metoda przeciążenia. Dzięki temu można obliczyć prawidłowe porządkowanie wierszy na podstawie wartości w dowolnej kolumnie.  
  
 Przeciążenie metody nie <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> ustawia <xref:System.Windows.Forms.DataGridView.SortOrder%2A> właściwościi,dlategonależyzawszeustawićwłaściwość,abywyświetlićSymbolsortowania.<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> `Sort(IComparer)`  
  
 Alternatywą dla `Sort(IComparer)` przeciążenia metody jest możliwość zapewnienia niestandardowego sortowania przez implementację procedury obsługi <xref:System.Windows.Forms.DataGridView.SortCompare> dla zdarzenia. To zdarzenie występuje, gdy użytkownicy klikają nagłówki kolumn skonfigurowane do automatycznego sortowania lub podczas wywoływania `Sort(DataGridViewColumn,ListSortDirection)` przeciążenia <xref:System.Windows.Forms.DataGridView.Sort%2A> metody. Zdarzenie występuje dla każdej pary wierszy w kontrolce, co umożliwia obliczenie prawidłowej kolejności.  
  
> [!NOTE]
> Zdarzenie nie występuje, <xref:System.Windows.Forms.DataGridView.DataSource%2A> gdy właściwość <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> jest ustawiona lub gdy wartość właściwości jest `true`. <xref:System.Windows.Forms.DataGridView.SortCompare>  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Sortowanie danych w kontrolce DataGridView formularzy Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Ustawianie trybów sortowania kolumn w kontrolce DataGridView Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [Instrukcje: Dostosuj sortowanie w kontrolce DataGridView Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
