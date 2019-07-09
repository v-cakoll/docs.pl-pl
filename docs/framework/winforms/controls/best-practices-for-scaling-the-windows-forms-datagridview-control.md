---
title: Najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
ms.openlocfilehash: 65afd73c166332f08003c3b3bfcc70e488d0373a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663554"
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>Najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows

<xref:System.Windows.Forms.DataGridView> Kontroli zaprojektowano w celu zapewnienia maksymalnej skalowalności. Jeśli zachodzi potrzeba wyświetlenia dużych ilości danych, możesz postępuj zgodnie z wytycznymi opisany w tym temacie, aby uniknąć zużywa bardzo dużą ilość pamięci lub ograniczanie czasu odpowiedzi interfejsu użytkownika (UI). W tym temacie omówiono następujące zagadnienia:

- Efektywne używanie style komórek

- Efektywne używanie menu skrótów

- Za pomocą automatycznej zmiany rozmiaru efektywnie

- Efektywne używanie wybranych kolekcji komórek, wierszy i kolumn

- Za pomocą udostępnione wiersze

- Uniemożliwienie staje się anulować wierszy

W przypadku potrzeb związanych z wydajnością specjalne możesz Implementowanie trybu wirtualnego i podać własne operacji zarządzania danymi. Aby uzyskać więcej informacji, zobacz [tryby wyświetlania danych w formancie DataGridView formularzy Windows](data-display-modes-in-the-windows-forms-datagridview-control.md).

## <a name="using-cell-styles-efficiently"></a>Efektywne używanie style komórek

Każdy komórek, wierszy i kolumn może mieć własne informacje dotyczące stylu. Styl informacje są przechowywane w <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów. Tworzenia obiektów style komórki dla poszczególnych wiele <xref:System.Windows.Forms.DataGridView> elementy mogą być mało wydajne, szczególnie w przypadku pracy z dużymi ilościami danych. Aby uniknąć wpływu na wydajność, należy użyć następujących wytycznych:

- Należy unikać ustawiania właściwości stylów komórki dla poszczególnych <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewRow> obiektów. Obejmuje to obiekt wiersza określonego przez <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> właściwości. Każdy nowy wiersz, który został sklonowany z szablonu wiersza otrzyma własną kopię obiektu style komórki tego szablonu. Dla maksymalnej skalowalności, należy ustawić właściwości style komórki w <xref:System.Windows.Forms.DataGridView> poziom. Na przykład ustawić <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> właściwości zamiast <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> właściwości.

- Jeśli niektóre komórki wymagają innych niż domyślne formatowanie formatowania, należy używać tego samego <xref:System.Windows.Forms.DataGridViewCellStyle> wystąpienia w grupach komórek, wierszy lub kolumn. Należy unikać bezpośrednio ustawiania właściwości typu <xref:System.Windows.Forms.DataGridViewCellStyle> na poszczególnych komórek, wierszy i kolumn. Na przykład udostępniania style komórki zobacz [jak: Ustawianie domyślnych stylów komórki dla formantu DataGridView formularzy Windows](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Można zapobiec spadek wydajności podczas ustawiania stylów komórki indywidualnie obsługi <xref:System.Windows.Forms.DataGridView.CellFormatting> programu obsługi zdarzeń. Aby uzyskać przykład, zobacz [jak: Dostosowywanie formatowania danych w formancie DataGridView formularzy Windows](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).

- Podczas określania stylu komórki, użyj <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType> właściwości zamiast <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> właściwości. Uzyskiwanie dostępu do <xref:System.Windows.Forms.DataGridViewCell.Style%2A> właściwości tworzy nowe wystąpienie klasy <xref:System.Windows.Forms.DataGridViewCellStyle> klasy, jeśli właściwość nie jest już używana. Ponadto ten obiekt może nie zawierać informacji pełną style komórki, jeśli niektóre style są dziedziczone z wierszy, kolumny lub formantu. Aby uzyskać więcej informacji na temat dziedziczenie stylów komórki, zobacz [style komórki w formancie DataGridView formularzy Windows](cell-styles-in-the-windows-forms-datagridview-control.md).

## <a name="using-shortcut-menus-efficiently"></a>Efektywne używanie menu skrótów

Każdy komórek, wierszy i kolumn może mieć własną menu skrótów. Menu skrótów w <xref:System.Windows.Forms.DataGridView> kontrolki są reprezentowane przez <xref:System.Windows.Forms.ContextMenuStrip> kontrolki. Podobnie jak w przypadku obiektów style komórki, tworzenie menu skrótów dla poszczególnych wiele <xref:System.Windows.Forms.DataGridView> elementy zostaną niekorzystnie wpłynąć na wydajność. Aby uniknąć tej opłaty karnej, użyj następujących wytycznych:

- Unikaj tworzenia menu skrótów dla poszczególnych komórek i wierszy. Obejmuje to szablon wiersza, który został sklonowany wraz z jego menu skrótów, gdy nowe wiersze są dodawane do formantu. Maksymalnej skalowalności, należy użyć tylko kontrolki <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwości w celu określenia menu skrótów jednego dla całego kontroli.

- Jeśli potrzebujesz wielu menu skrótów dla wielu wierszy lub komórki obsługi <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> lub <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded> zdarzenia. Zdarzenia te umożliwiają zarządzanie obiektami menu skrótów samodzielnie, dzięki czemu można dostrajanie wydajności.

## <a name="using-automatic-resizing-efficiently"></a>Za pomocą automatycznej zmiany rozmiaru efektywnie

Wiersze, kolumny i nagłówki można automatycznie zmienić rozmiar zgodnie ze zmianami zawartości komórki tak, aby cała zawartość komórki są wyświetlane bez przycinania. Zmiana trybów zmieniania rozmiaru można również zmienić rozmiar wiersze, kolumny i nagłówki. Aby określić odpowiedni rozmiar <xref:System.Windows.Forms.DataGridView> kontroli należy sprawdzić wartość każdej komórki, która musi sobie radzić. Podczas pracy z dużymi zestawami danych, ta analiza może niekorzystnie wpłynąć na wydajność kontrolki sytuacji automatyczną zmianę rozmiaru. Aby uniknąć spadku wydajności, użyj następujących wytycznych:

- Unikaj używania automatycznej zmiany rozmiaru w <xref:System.Windows.Forms.DataGridView> kontrolki z dużym zestawem wierszy. Jeśli używasz automatycznej zmiany rozmiaru, tylko zmiany rozmiaru na podstawie wyświetlanych wierszy. Użyj tylko wierszy wyświetlanych w trybie wirtualnym, jak również.

  - W przypadku wierszy i kolumn, użyj `DisplayedCells` lub `DisplayedCellsExceptHeaders` pole <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>, <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>, i <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> wyliczenia.

  - Nagłówki wierszy, można użyć <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders> lub <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader> pole <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> wyliczenia.

- Maksymalnej skalowalności Wyłącz opcję automatycznej zmiany rozmiaru i użyj programowe Zmienianie rozmiaru.

Aby uzyskać więcej informacji, zobacz [opcje ustalania rozmiaru w formancie DataGridView formularzy Windows](sizing-options-in-the-windows-forms-datagridview-control.md).

## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>Efektywne używanie wybranych komórek, wierszy i kolumn kolekcji

<xref:System.Windows.Forms.DataGridView.SelectedCells%2A> Kolekcji nie wykonuje efektywnie przy użyciu opcji dużych. <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> kolekcje nieoptymalne, mimo że do mniejszym stopniu ponieważ dużo mniej wierszy niż komórek w typowej <xref:System.Windows.Forms.DataGridView> kontroli i wiele mniejszą liczbę kolumn niż wierszy. Aby uniknąć spadku wydajności podczas pracy z tymi kolekcjami, użyj następujących wytycznych:

- Aby określić, czy wszystkie komórki w <xref:System.Windows.Forms.DataGridView> wybrano, aby dostęp do zawartości <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> kolekcji, sprawdź wartość zwracaną przez <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metody. Należy jednak pamiętać, że ta metoda może spowodować wierszy, które mają stać się nieudostępnionych. Aby uzyskać więcej informacji, zobacz następną sekcję.

- Unikaj używania <xref:System.Collections.ICollection.Count%2A> właściwość <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType> do określenia liczby zaznaczonych komórek. Zamiast tego należy użyć <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType> metody i przekaż <xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType> wartość. Podobnie, użyj <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType> metody w celu określenia liczby wybranych elementów, a nie dostęp do wybranych kolekcji wierszy i kolumn.

- Należy unikać tryby wyboru na podstawie komórki. Zamiast tego należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> właściwości <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.

## <a name="using-shared-rows"></a>Używana jest udostępniona wierszy

Wykorzystanie pamięci wydajność jest osiągana w <xref:System.Windows.Forms.DataGridView> sterowanie za pośrednictwem udostępnione wiersze. Wiersze współużytkują jak najwięcej informacji o ich wygląd i zachowanie, udostępniając wystąpień <xref:System.Windows.Forms.DataGridViewRow> klasy.

Podczas udostępniania wystąpienia wiersza zużycie pamięci, wiersze mogą łatwo stać się nieudostępnionych. Na przykład zawsze wtedy, gdy użytkownik wchodzi w interakcję bezpośrednio z komórki, jego wiersz staje się nieudostępnionych. Ponieważ nie można uniknąć, wskazówek zawartych w tym temacie są przydatne tylko wtedy, gdy praca z dużymi ilościami danych i tylko wtedy, gdy użytkownicy będą korzystać z niewielką część danych każdorazowo, gdy program jest uruchamiany.

Wiersz nie może być udostępniane w niepowiązanych <xref:System.Windows.Forms.DataGridView> kontroli, jeśli którakolwiek z jej komórek zawiera wartości. Gdy <xref:System.Windows.Forms.DataGridView> kontrolka jest powiązana z zewnętrznego źródła danych lub Implementowanie trybu wirtualnego i zapewnić źródła danych, wartości komórek są przechowywane poza kontrolą, a nie w obiektach komórki, dzięki czemu wierszy, które mają być udostępniane.

Obiekt wiersza może być współużytkowany tylko, jeśli można ustalić stanu jej komórek na podstawie stanu wiersza i Stany kolumny zawierające komórki. Jeśli zmienisz stan komórki, dzięki czemu można określić już ze stanu jego wiersza i kolumny, wiersz nie może być współużytkowana.

Na przykład wiersz nie może być współużytkowana w następujących sytuacjach:

- Wiersz zawiera pojedynczy zaznaczonej komórki, który nie znajduje się w zaznaczonej kolumnie.

- Wiersz zawiera komórki z jego <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> lub <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A> zestawu właściwości.

- Wiersz zawiera <xref:System.Windows.Forms.DataGridViewComboBoxCell> z jego <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A> zestawu właściwości.

W trybie powiązanej lub wirtualnych, możesz podać etykietki narzędzi i menu skrótów pojedyncze komórki obsługi <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> i <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> zdarzenia.

<xref:System.Windows.Forms.DataGridView> Formant będzie automatycznie próbować użyć udostępnione wiersze, jeśli wiersze są dodawane do <xref:System.Windows.Forms.DataGridViewRowCollection>. Aby upewnić się, że wiersze są udostępniane, skorzystaj z poniższych wskazówek:

- Należy unikać wywoływania `Add(Object[])` przeciążenia <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> metody i `Insert(Object[])` przeciążenia <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> metody <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> kolekcji. Taka przeciążona funkcja sprawdza automatycznie tworzyć nieudostępnionych wierszy.

- Upewnij się, że określono w wiersza <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> właściwości mogą być współużytkowane w następujących przypadkach:

  - Podczas wywoływania `Add()` lub `Add(Int32)` przeciążenia <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> metody lub `Insert(Int32,Int32)` przeciążenia <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> metody <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> kolekcji.

  - Gdy zwiększenie wartości <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType> właściwości.

  - Podczas ustawiania <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType> właściwości.

- Upewnij się, że w wierszu wskazywanym przez `indexSource` parametru może być współużytkowany podczas wywoływania <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>, i <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> metody <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> kolekcji.

- Pamiętaj, że określony wiersz lub wiersze mogą być współdzielone, podczas wywoływania `Add(DataGridViewRow)` przeciążenia <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> metody <xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A> metody `Insert(Int32,DataGridViewRow)` przeciążenia <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> metody i <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> metoda <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>kolekcji.

Aby określić, czy wiersza jest współużytkowany, użyj <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> metodę, aby pobrać obiekt wiersza, a następnie sprawdź obiektu <xref:System.Windows.Forms.DataGridViewBand.Index%2A> właściwości. Udostępnione wiersze zawsze mieć <xref:System.Windows.Forms.DataGridViewBand.Index%2A> właściwości wartości -1.

## <a name="preventing-rows-from-becoming-unshared"></a>Uniemożliwienie staje się anulować wierszy

Udostępnione wiersze mogą stać się nieudostępnionych wyniku kodu lub akcji użytkownika. Aby uniknąć wpływu na wydajność, należy unikać, powodując wierszy, które mają stać się nieudostępnionych. Podczas tworzenia aplikacji, które ułatwią Ci obsługę <xref:System.Windows.Forms.DataGridView.RowUnshared> zdarzenia w celu określenia, kiedy wierszy stają się nieudostępnionych. Jest to przydatne podczas debugowania problemów z udostępnianiem wiersza.

Aby zapobiec sytuacji, w której wiersze staje się anulować, użyj następujących wytycznych:

- Należy unikać indeksowania <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji lub iteracja ją za pomocą `foreach` pętli. Nie zwykle konieczne będzie bezpośredni dostęp wierszy. <xref:System.Windows.Forms.DataGridView> metody, które działają w wierszach zająć argumenty Indeks wiersza, a nie wystąpienia wiersza. Ponadto programy obsługi zdarzeń związanych z wiersza pojawić obiekty argumentu zdarzenia z właściwościami wiersza, które umożliwiają manipulowanie wierszami bez powodowania by nieudostępnionych.

- Jeśli potrzebujesz dostępu do obiektu wiersz, użyj <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> metody i przekazać w rzeczywistych indeks wiersza. Należy jednak pamiętać, że modyfikowanie obiektu wierszu udostępnionym pobierane za pośrednictwem tej metody zmodyfikuje wszystkie wiersze, które współużytkują ten obiekt. Wiersza dla nowych rekordów nie jest udostępniony za pomocą innych wierszy, więc go nie zostaną zmienione po zmodyfikowaniu innych wierszy. Należy zauważyć, że różne wiersze reprezentowanego przez wiersz udostępniony może mieć inny skrót menu. Aby pobrać menu skrótów poprawne z wystąpienia wiersza udostępnionego, użyj <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> metody i przekazać w rzeczywistych indeks wiersza. Jeśli uzyskujesz dostęp do udostępnionego wiersza <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> właściwości zamiast tego użyje indeks wiersza udostępnionego,-1 i nie będą pobierane z menu skrótów poprawne.

- Należy unikać indeksowania <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType> kolekcji. Uzyskiwanie dostępu do komórki bezpośrednio spowoduje, że wiersz jego nadrzędnego w taki sposób, aby stać się nieudostępnionych tworzenia wystąpienia nowego <xref:System.Windows.Forms.DataGridViewRow>. Programy obsługi zdarzeń związanych z komórki otrzymują obiekty argumentu zdarzenia za pomocą właściwości komórki, które służą do manipulowania komórek bez powodowania wierszy, które mają stać się nieudostępnionych. Można również użyć <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> właściwość służąca do pobierania wiersza i kolumny indeksów bieżącej komórki bez uzyskiwania dostępu do komórki bezpośrednio.

- Należy unikać tryby wyboru na podstawie komórki. Te tryby spowodować, że wiersze, aby stać się nieudostępnionych. Zamiast tego należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> właściwości <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.

- Nie obsługują <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType> zdarzenia. Te zdarzenia, że wiersze, aby stać się nieudostępnionych. Ponadto nie należy wywoływać metody <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType> metody, które wywołania tych zdarzeń.

- Nie <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType> kolekcji podczas <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> wartość właściwości jest <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>, lub <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>. Powoduje to, że wszystkie zaznaczone wiersze stać się nieudostępnionych.

- Nie wywołuj <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType> metody. Ta metoda może spowodować wierszy, które mają stać się nieudostępnionych.

- Nie wywołuj <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType> metody podczas <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> wartość właściwości jest <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>. To powoduje, że wszystkie wiersze stać się nieudostępnionych.

- Nie należy ustawiać <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> lub <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> właściwości komórki do `false` Jeśli odpowiednie właściwości w jej kolumna jest równa `true`. To powoduje, że wszystkie wiersze stać się nieudostępnionych.

- Nie <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType> właściwości. To powoduje, że wszystkie wiersze stać się nieudostępnionych.

- Nie wywołuj `Sort(IComparer)` przeciążenia <xref:System.Windows.Forms.DataGridView.Sort%2A> metody. Sortowanie za pomocą niestandardowego modułu porównującego powoduje, że wszystkie wiersze stać się nieudostępnionych.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Ustawianie domyślnych stylów komórki dla kontrolki DataGridView formularzy Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Opcje ustalania rozmiaru w kontrolce DataGridView formularzy Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md)
