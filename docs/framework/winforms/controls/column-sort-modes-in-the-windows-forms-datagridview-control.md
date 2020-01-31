---
title: Tryby sortowania kolumn w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: d1e2f582c9759332e0ed963cb7f88ee052616c45
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744197"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Tryb sortowania kolumn w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> kolumny mają trzy tryby sortowania. Tryb sortowania dla każdej kolumny jest określany za pomocą właściwości <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> kolumny, która może być ustawiona na jedną z następujących <xref:System.Windows.Forms.DataGridViewColumnSortMode> wartości wyliczenia.  
  
|wartość `DataGridViewColumnSortMode`|Opis|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Wartość domyślna kolumn pól tekstowych. Jeśli nagłówki kolumn nie są używane do zaznaczania, kliknięcie nagłówka kolumny automatycznie sortuje <xref:System.Windows.Forms.DataGridView> według tej kolumny i wyświetla glif wskazujący kolejność sortowania.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Wartość domyślna dla kolumn innych niż pola tekstowe. Tę kolumnę można programowo sortować. nie jest to jednak przeznaczone do sortowania, więc żadne miejsce nie jest zarezerwowane dla glifu sortowania.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|Można sortować tę kolumnę programowo, a miejsce jest zarezerwowane dla glifu sortowania.|  
  
 Może zajść potrzeba zmiany trybu sortowania dla kolumny, która domyślnie <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>, jeśli zawiera ona wartości, które mogą być zrozumiałe. Na przykład, jeśli istnieje kolumna bazy danych zawierająca liczby, które reprezentują Stany elementów, można wyświetlić te liczby jako odpowiednie ikony przez powiązanie kolumny obrazu z kolumną bazy danych. Następnie można zmienić wartości komórki liczbowej na wartości wyświetlane w obrazie w programie obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>. W takim przypadku ustawienie właściwości <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> na <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> umożliwi użytkownikom sortowanie kolumn. Automatyczne sortowanie umożliwi użytkownikom grupowanie elementów, które mają ten sam stan nawet wtedy, gdy Stany odpowiadające liczbom nie mają naturalnej sekwencji. Kolumny pól wyboru to kolejny przykład, w którym sortowanie automatyczne jest przydatne w przypadku grupowania elementów w tym samym stanie.  
  
 Można sortować <xref:System.Windows.Forms.DataGridView> programowo przez wartości w dowolnej kolumnie lub w wielu kolumnach, niezależnie od ustawień <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>. Sortowanie programistyczne jest przydatne, gdy chcesz zapewnić własny interfejs użytkownika do sortowania lub Kiedy chcesz zaimplementować sortowanie niestandardowe. Udostępnianie własnego interfejsu użytkownika sortowania jest przydatne na przykład podczas ustawiania trybu wyboru <xref:System.Windows.Forms.DataGridView>, aby włączyć wybieranie nagłówka kolumny. W tym przypadku, chociaż nagłówki kolumn nie mogą być używane do sortowania, nadal chcesz, aby nagłówki wyświetlały odpowiedni symbol sortowania, więc ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> na <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>.  
  
 Kolumny ustawione na tryb sortowania programistycznego nie wyświetlają automatycznie symbolu sortowania. Dla tych kolumn należy samodzielnie wyświetlić symbol, ustawiając właściwość <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>. Jest to konieczne, jeśli chcesz mieć elastyczność w sortowaniu niestandardowym. Na przykład, jeśli sortujesz <xref:System.Windows.Forms.DataGridView> według wielu kolumn, możesz chcieć wyświetlić wiele glifów sortowania lub bez glifów sortowania.  
  
 Mimo że można programowo sortować <xref:System.Windows.Forms.DataGridView> według dowolnej kolumny, niektóre kolumny, takie jak kolumny przycisków, mogą nie zawierać wartości, które mogą być zrozumiałe. Dla tych kolumn ustawienie właściwości <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> wskazuje, że nigdy nie będzie używane do sortowania, więc nie ma potrzeby rezerwowania miejsca w nagłówku dla symbolu sortowania.  
  
 Gdy <xref:System.Windows.Forms.DataGridView> jest sortowana, można określić zarówno kolumnę sortowania, jak i kolejność sortowania, sprawdzając wartości właściwości <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> i <xref:System.Windows.Forms.DataGridView.SortOrder%2A>. Te wartości nie mają znaczenia po niestandardowej operacji sortowania. Aby uzyskać więcej informacji na temat sortowania niestandardowego, zobacz sekcję niestandardowe sortowanie w dalszej części tego tematu.  
  
 Gdy sortowany jest formant <xref:System.Windows.Forms.DataGridView> zawierający kolumny powiązane i niepowiązane, wartości z kolumn niepowiązanych nie mogą być obsługiwane automatycznie. Aby zachować te wartości, należy zaimplementować tryb wirtualny, ustawiając właściwość <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>, aby `true` i obsługiwały zdarzenia <xref:System.Windows.Forms.DataGridView.CellValueNeeded> i <xref:System.Windows.Forms.DataGridView.CellValuePushed>. Aby uzyskać więcej informacji, zobacz [jak: implementowanie trybu wirtualnego w kontrolce DataGridView Windows Forms](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md). Sortowanie według niepowiązanych kolumn w trybie związanym nie jest obsługiwane.  
  
## <a name="programmatic-sorting"></a>Sortowanie programistyczne  
 <xref:System.Windows.Forms.DataGridView> można sortować programowo, wywołując metodę <xref:System.Windows.Forms.DataGridView.Sort%2A>.  
  
 `Sort(DataGridViewColumn,ListSortDirection)` Przeciążenie metody <xref:System.Windows.Forms.DataGridView.Sort%2A> przyjmuje <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.ComponentModel.ListSortDirection> wartość wyliczenia jako parametry. To przeciążenie jest przydatne podczas sortowania według kolumn z wartościami, które mogą być uporządkowane w sposób znaczący, ale których nie chcesz konfigurować do automatycznego sortowania. Po wywołaniu tego przeciążenia i przejściu do kolumny o wartości <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> i <xref:System.Windows.Forms.DataGridView.SortOrder%2A> właściwości są ustawiane automatycznie, a odpowiedni symbol sortowania pojawi się w nagłówku kolumny.  
  
> [!NOTE]
> Gdy formant <xref:System.Windows.Forms.DataGridView> jest powiązany z zewnętrznym źródłem danych przez ustawienie właściwości <xref:System.Windows.Forms.DataGridView.DataSource%2A>, Przeciążenie metody `Sort(DataGridViewColumn,ListSortDirection)` nie działa w przypadku kolumn niepowiązanych. Ponadto gdy właściwość <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> jest `true`, można wywołać to Przeciążenie tylko dla kolumn powiązanych. Aby określić, czy kolumna jest powiązana z danymi, sprawdź wartość właściwości <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A>. Sortowanie kolumn niepowiązanych w trybie związanym nie jest obsługiwane.  
  
## <a name="custom-sorting"></a>Sortowanie niestandardowe  
 <xref:System.Windows.Forms.DataGridView> można dostosować, używając `Sort(IComparer)` przeciążenia metody <xref:System.Windows.Forms.DataGridView.Sort%2A> lub przez obsługę zdarzenia <xref:System.Windows.Forms.DataGridView.SortCompare>.  
  
 Przeciążenie metody `Sort(IComparer)` Pobiera wystąpienie klasy implementującej interfejs <xref:System.Collections.IComparer> jako parametr. To przeciążenie jest przydatne, gdy chcesz zapewnić niestandardowe sortowanie; na przykład, gdy wartości w kolumnie nie mają naturalnej kolejności sortowania lub gdy porządek sortowania naturalny jest nieodpowiedni. W takim przypadku nie można użyć automatycznego sortowania, ale możesz nadal sortować użytkowników, klikając nagłówki kolumn. Można wywołać to Przeciążenie w obsłudze zdarzenia <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick>, jeśli nie używasz nagłówków kolumn do wyboru.  
  
> [!NOTE]
> Przeciążenie metody `Sort(IComparer)` działa tylko wtedy, gdy kontrolka <xref:System.Windows.Forms.DataGridView> nie jest powiązana z zewnętrznym źródłem danych, a wartość właściwości <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> to `false`. Aby dostosować sortowanie dla kolumn powiązanych z zewnętrznym źródłem danych, należy użyć operacji sortowania dostarczonych przez źródło danych. W trybie wirtualnym należy zapewnić własne operacje sortowania dla kolumn niepowiązanych.  
  
 Aby użyć przeciążenia metody `Sort(IComparer)`, należy utworzyć własną klasę, która implementuje interfejs <xref:System.Collections.IComparer>. Ten interfejs wymaga, aby Klasa zaimplementował metodę <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType>, do której <xref:System.Windows.Forms.DataGridView> przekazuje obiekty <xref:System.Windows.Forms.DataGridViewRow> jako dane wejściowe, gdy zostanie wywołane Przeciążenie metody `Sort(IComparer)`. Dzięki temu można obliczyć prawidłowe porządkowanie wierszy na podstawie wartości w dowolnej kolumnie.  
  
 Przeciążenie metody `Sort(IComparer)` nie ustawia właściwości <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> i <xref:System.Windows.Forms.DataGridView.SortOrder%2A>, dlatego należy zawsze ustawić właściwość <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>, aby wyświetlić Symbol sortowania.  
  
 Alternatywą dla przeciążenia metody `Sort(IComparer)` można zapewnić niestandardowe sortowanie, implementując procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.SortCompare>. To zdarzenie występuje, gdy użytkownicy klikają nagłówki kolumn skonfigurowane do automatycznego sortowania lub podczas wywoływania `Sort(DataGridViewColumn,ListSortDirection)` przeciążenia metody <xref:System.Windows.Forms.DataGridView.Sort%2A>. Zdarzenie występuje dla każdej pary wierszy w kontrolce, co umożliwia obliczenie prawidłowej kolejności.  
  
> [!NOTE]
> Zdarzenie <xref:System.Windows.Forms.DataGridView.SortCompare> nie występuje, gdy właściwość <xref:System.Windows.Forms.DataGridView.DataSource%2A> jest ustawiona lub gdy wartość właściwości <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> jest `true`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Sortowanie danych w kontrolce DataGridView formularzy Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [Instrukcje: dostosowywanie sortowania w kontrolce DataGridView Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
