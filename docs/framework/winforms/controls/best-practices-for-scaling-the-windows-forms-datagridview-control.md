---
title: Najlepsze rozwiązania dotyczące skalowania formantu DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
ms.openlocfilehash: 63500a79def89510b4bc7a436abc4620a7265a79
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744125"
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>Najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows

Kontrolka <xref:System.Windows.Forms.DataGridView> została zaprojektowana w celu zapewnienia maksymalnej skalowalności. Aby wyświetlić duże ilości danych, należy postępować zgodnie z wytycznymi opisanymi w tym temacie, aby uniknąć zużywania dużych ilości pamięci lub obsłużyć czas odpowiedzi interfejsu użytkownika (UI). W tym temacie omówiono następujące zagadnienia:

- Wydajne używanie stylów komórek

- Wydajne korzystanie z menu skrótów

- Wydajne automatyczne zmienianie rozmiarów

- Wydajne używanie wybranych komórek, wierszy i kolekcji kolumn

- Korzystanie z wierszy udostępnionych

- Uniemożliwianie nieudostępnianych wierszy

W przypadku specjalnych potrzeb związanych z wydajnością można zaimplementować tryb wirtualny i zapewnić własne operacje zarządzania danymi. Aby uzyskać więcej informacji, zobacz [tryby wyświetlania danych w kontrolce DataGridView Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md).

## <a name="using-cell-styles-efficiently"></a>Wydajne używanie stylów komórek

Każda komórka, wiersz i kolumna mogą mieć własne informacje o stylu. Informacje o stylu są przechowywane w <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów. Tworzenie obiektów stylów komórek dla wielu pojedynczych elementów <xref:System.Windows.Forms.DataGridView> może być niewydajne, szczególnie podczas pracy z dużymi ilościami danych. Aby uniknąć wpływu na wydajność, należy użyć następujących wytycznych:

- Należy unikać ustawiania właściwości stylu komórki dla pojedynczych <xref:System.Windows.Forms.DataGridViewCell> lub obiektów <xref:System.Windows.Forms.DataGridViewRow>. Obejmuje to obiekt Row określony przez właściwość <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>. Każdy nowy wiersz, który jest sklonowany z szablonu wiersza, otrzyma własną kopię obiektu stylu komórki szablonu. W celu uzyskania maksymalnej skalowalności ustaw właściwości stylu komórki na poziomie <xref:System.Windows.Forms.DataGridView>. Na przykład ustaw właściwość <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>, a nie Właściwość <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>.

- Jeśli niektóre komórki wymagają formatowania innego niż domyślne, użyj tego samego <xref:System.Windows.Forms.DataGridViewCellStyle> wystąpienia w grupach komórek, wierszy lub kolumn. Należy unikać bezpośredniego ustawiania właściwości typu <xref:System.Windows.Forms.DataGridViewCellStyle> dla poszczególnych komórek, wierszy i kolumn. Aby zapoznać się z przykładem udostępniania stylu komórki, zobacz [How to: set default style Cells for the DataGridView Windows Forms Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Można również uniknąć pogorszenia wydajności podczas ustawiania stylów komórek indywidualnie przez obsługę zdarzenia programu <xref:System.Windows.Forms.DataGridView.CellFormatting>. Aby zapoznać się z przykładem, zobacz [How to: Dostosowywanie formatowania danych w kontrolce DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).

- Podczas określania stylu komórki Użyj właściwości <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>, a nie właściwości <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>. Uzyskanie dostępu do właściwości <xref:System.Windows.Forms.DataGridViewCell.Style%2A> tworzy nowe wystąpienie klasy <xref:System.Windows.Forms.DataGridViewCellStyle>, jeśli właściwość nie została jeszcze użyta. Ponadto ten obiekt może nie zawierać pełnych informacji o stylu komórki, jeśli niektóre style są dziedziczone z wiersza, kolumny lub formantu. Aby uzyskać więcej informacji na temat dziedziczenia stylu komórki, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

## <a name="using-shortcut-menus-efficiently"></a>Wydajne korzystanie z menu skrótów

Każda komórka, wiersz i kolumna może mieć własne menu skrótów. Menu skrótów w kontrolce <xref:System.Windows.Forms.DataGridView> są reprezentowane przez kontrolki <xref:System.Windows.Forms.ContextMenuStrip>. Podobnie jak w przypadku obiektów stylu komórki Tworzenie menu skrótów dla wielu pojedynczych elementów <xref:System.Windows.Forms.DataGridView> może negatywnie wpłynąć na wydajność. Aby uniknąć tej kary, Skorzystaj z następujących wskazówek:

- Unikaj tworzenia menu skrótów dla pojedynczych komórek i wierszy. Obejmuje to szablon wiersza, który jest klonowany wraz z menu skrótów po dodaniu nowych wierszy do kontrolki. W celu uzyskania maksymalnej skalowalności Użyj tylko właściwości <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> kontrolki, aby określić pojedyncze menu skrótów dla całej kontrolki.

- Jeśli potrzebujesz wielu menu skrótów dla wielu wierszy lub komórek, obsłużą zdarzenia <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> lub <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>. Te zdarzenia umożliwiają samodzielne zarządzanie obiektami menu skrótów, co pozwala na dostosowanie wydajności.

## <a name="using-automatic-resizing-efficiently"></a>Wydajne automatyczne zmienianie rozmiarów

Rozmiar wierszy, kolumn i nagłówków można zmienić automatycznie jako zmiany zawartości komórki, tak aby cała zawartość komórek była wyświetlana bez wycinków. Zmienianie trybów ustalania rozmiaru może również zmieniać rozmiar wierszy, kolumn i nagłówków. Aby określić poprawny rozmiar, formant <xref:System.Windows.Forms.DataGridView> musi sprawdzić wartość każdej komórki, którą musi obsłużyć. Podczas pracy z dużymi zestawami danych ta analiza może mieć negatywny wpływ na wydajność kontroli w przypadku wystąpienia automatycznej zmiany rozmiarów. Aby uniknąć kar za wydajność, należy przestrzegać następujących wytycznych:

- Unikaj używania automatycznego ustalania rozmiarów w kontrolce <xref:System.Windows.Forms.DataGridView> z dużym zestawem wierszy. Jeśli używasz automatycznej zmiany rozmiaru, Zmień rozmiar wyłącznie na podstawie wyświetlanych wierszy. Używaj również tylko wyświetlanych wierszy w trybie wirtualnym.

  - W przypadku wierszy i kolumn Użyj pola `DisplayedCells` lub `DisplayedCellsExceptHeaders` w wyliczeniach <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>, <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>i <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>.

  - W przypadku nagłówków wierszy Użyj pola <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders> lub <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader> wyliczenia <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>.

- W celu uzyskania maksymalnej skalowalności należy wyłączyć automatyczne ustalanie rozmiarów i zmieniać rozmiar programistyczny.

Aby uzyskać więcej informacji, zobacz [Opcje ustalania rozmiarów w kontrolce DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).

## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>Wydajne używanie wybranych komórek, wierszy i kolekcji kolumn

Kolekcja <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> nie działa wydajnie z dużymi zaznaczeniami. Kolekcje <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> mogą być również niewydajne, ale w mniejszym stopniu, ponieważ zawiera wiele wierszy niż komórki w typowym formancie <xref:System.Windows.Forms.DataGridView> i wiele kolumn niż wierszy. Aby uniknąć spadku wydajności podczas pracy z tymi kolekcjami, należy przestrzegać następujących wytycznych:

- Aby określić, czy wszystkie komórki w <xref:System.Windows.Forms.DataGridView> zostały wybrane przed uzyskaniem dostępu do zawartości kolekcji <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, sprawdź wartość zwracaną metody <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>. Należy jednak zauważyć, że ta metoda może spowodować nieudostępnianie wierszy. Aby uzyskać więcej informacji, zobacz następną sekcję.

- Należy unikać używania właściwości <xref:System.Collections.ICollection.Count%2A> <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType>, aby określić liczbę zaznaczonych komórek. Zamiast tego należy użyć metody <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType> i przekazać wartość <xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType>. Podobnie Użyj metod <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType>, aby określić liczbę wybranych elementów, a nie dostęp do wybranych kolekcji wierszy i kolumn.

- Unikaj trybów wyboru opartych na komórce. Zamiast tego należy ustawić właściwość <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.

## <a name="using-shared-rows"></a>Korzystanie z wierszy udostępnionych

Wydajne użycie pamięci jest uzyskiwane w kontrolce <xref:System.Windows.Forms.DataGridView> za pomocą wspólnych wierszy. Wiersze będą udostępniać jak najwięcej informacji o ich wyglądzie i zachowaniu, jak to możliwe, udostępniając wystąpienia klasy <xref:System.Windows.Forms.DataGridViewRow>.

Podczas udostępniania wystąpień wierszy oszczędność pamięci, wiersze mogą być w łatwy sposób nieudostępniane. Na przykład za każdym razem, gdy użytkownik współdziała bezpośrednio z komórką, jego wiersz zostanie nieudostępniony. Ponieważ nie można tego uniknąć, wskazówki zawarte w tym temacie są przydatne tylko w pracy z bardzo dużymi ilościami danych i tylko wtedy, gdy użytkownicy będą korzystać z stosunkowo niewielkiej części danych za każdym razem, gdy program jest uruchomiony.

Nie można udostępnić wiersza w niepowiązanej kontrolce <xref:System.Windows.Forms.DataGridView>, jeśli żadna z jej komórek zawiera wartości. Gdy kontrolka <xref:System.Windows.Forms.DataGridView> jest powiązana z zewnętrznym źródłem danych lub w przypadku zaimplementowania trybu wirtualnego i zapewnienia własnego źródła danych, wartości komórek są przechowywane poza kontrolką, a nie w obiektach komórek, co umożliwia udostępnianie wierszy.

Obiekt Row może być współużytkowany tylko wtedy, gdy stan wszystkich jego komórek może być określony na podstawie stanu wiersza i Stanów kolumn zawierających komórki. Jeśli zmienisz stan komórki tak, aby nie można było jej już ustalić ze stanu jej wiersza i kolumny, nie będzie można udostępnić wiersza.

Na przykład wiersz nie może być współużytkowany w żadnej z następujących sytuacji:

- Wiersz zawiera pojedynczą wybraną komórkę, która nie znajduje się w zaznaczonej kolumnie.

- Wiersz zawiera komórkę z ustawionymi właściwościami <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> lub <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A>.

- Wiersz zawiera <xref:System.Windows.Forms.DataGridViewComboBoxCell> z zestawem właściwości <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A>.

W trybie związanym lub w trybie wirtualnym można udostępniać etykietki narzędzi i menu skrótów dla poszczególnych komórek, obsługując <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> i <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> zdarzenia.

Formant <xref:System.Windows.Forms.DataGridView> automatycznie podejmie próbę użycia udostępnionych wierszy przy każdym dodawaniu wierszy do <xref:System.Windows.Forms.DataGridViewRowCollection>. Skorzystaj z poniższych wskazówek, aby upewnić się, że wiersze są udostępniane:

- Należy unikać wywoływania `Add(Object[])` przeciążenia metody <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> i `Insert(Object[])` przeciążenia metody <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> kolekcji <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>. Te przeciążenia automatycznie tworzą nieudostępniane wiersze.

- Upewnij się, że wiersz określony we właściwości <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> może być współużytkowany w następujących przypadkach:

  - Podczas wywoływania `Add()` lub `Add(Int32)` overloads metody <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> lub `Insert(Int32,Int32)` przeciążenia metody <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> kolekcji <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>.

  - Podczas zwiększania wartości właściwości <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType>.

  - Podczas ustawiania właściwości <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>.

- Upewnij się, że wiersz wskazywany przez `indexSource` parametr może być współużytkowany podczas wywoływania <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>i <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> metod kolekcji <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>.

- Upewnij się, że określony wiersz lub wiersze mogą być współużytkowane podczas wywoływania `Add(DataGridViewRow)` przeciążenia metody <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, metody <xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A>, przeciążenia `Insert(Int32,DataGridViewRow)` metody <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> oraz metody <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> kolekcji <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>.

Aby określić, czy wiersz jest współużytkowany, użyj metody <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType>, aby pobrać obiekt Row, a następnie sprawdź Właściwość <xref:System.Windows.Forms.DataGridViewBand.Index%2A> obiektu. Wiersze udostępnione zawsze mają wartość właściwości <xref:System.Windows.Forms.DataGridViewBand.Index%2A>-1.

## <a name="preventing-rows-from-becoming-unshared"></a>Uniemożliwianie nieudostępnianych wierszy

Wiersze udostępnione mogą stać się nieudostępniane w wyniku działania kodu lub użytkownika. Aby uniknąć wpływu na wydajność, należy unikać wyświetlania wierszy, które nie są udostępniane. Podczas tworzenia aplikacji można obsłużyć zdarzenie <xref:System.Windows.Forms.DataGridView.RowUnshared>, aby określić, kiedy wiersze staną się nieudostępnione. Jest to przydatne w przypadku debugowania problemów z udostępnianiem wierszy.

Aby uniemożliwić nieudostępnianie wierszy, użyj następujących wytycznych:

- Należy unikać indeksowania kolekcji <xref:System.Windows.Forms.DataGridView.Rows%2A> lub iterować za pomocą pętli `foreach`. Zwykle nie ma potrzeby bezpośredniego dostępu do wierszy. Metody <xref:System.Windows.Forms.DataGridView>, które działają na wierszach, przyjmują argumenty indeksu wierszy, a nie wystąpienia wierszy. Ponadto programy obsługi dla zdarzeń związanych z wierszem odbierają obiekty argumentów zdarzeń z właściwościami wiersza, których można użyć do manipulowania wierszami bez powodowania, że staną się nieudostępniane.

- Jeśli musisz uzyskać dostęp do obiektu wiersza, użyj metody <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> i przekaż rzeczywisty indeks wiersza. Należy jednak pamiętać, że zmodyfikowanie udostępnionego obiektu wiersza pobranego za pomocą tej metody spowoduje zmodyfikowanie wszystkich wierszy, które współużytkują ten obiekt. Wiersz dla nowych rekordów nie jest współużytkowany z innymi wierszami, więc nie wpłynie to na zmiany w żadnym innym wierszu. Należy zauważyć, że różne wiersze reprezentowane przez wiersz współużytkowany mogą mieć inne menu skrótów. Aby pobrać poprawne menu skrótów z wystąpienia wiersza udostępnionego, użyj metody <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> i przekaż rzeczywisty indeks wiersza. Jeśli zamiast tego uzyskasz dostęp do właściwości <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> w wierszu udostępnionym, zostanie użyty indeks wiersza udostępnionego-1 i nie będzie on pobierał poprawnego menu skrótów.

- Należy unikać indeksowania kolekcji <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType>. Bezpośredni dostęp do komórki spowoduje, że jego wiersz nadrzędny stanie się nieudostępniony, tworząc wystąpienie nowego <xref:System.Windows.Forms.DataGridViewRow>. Programy obsługi dla zdarzeń związanych z komórkami otrzymują obiekty argumentów zdarzeń z właściwościami komórki, których można użyć do manipulowania komórkami bez powodowania, że wiersze staną się nieudostępnione. Można również użyć właściwości <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> do pobrania indeksów wierszy i kolumn bieżącej komórki bez bezpośredniego uzyskiwania dostępu do komórki.

- Unikaj trybów wyboru opartych na komórce. Te tryby powodują, że wiersze stają się nieudostępniane. Zamiast tego należy ustawić właściwość <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.

- Nie obsługuj zdarzeń <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType> ani <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType>. Te zdarzenia powodują, że wiersze stają się nieudostępnione. Ponadto nie należy wywoływać metod <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType> ani <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType>, które zgłaszają te zdarzenia.

- Nie uzyskuj dostępu do kolekcji <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType>, gdy wartość właściwości <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>lub <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>. Powoduje to, że wszystkie zaznaczone wiersze staną się nieudostępnione.

- Nie wywołuj metody <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType>. Ta metoda może spowodować, że wiersze staną się nieudostępnione.

- Nie wywołuj metody <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType>, gdy wartość właściwości <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> jest <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>. Powoduje to, że wszystkie wiersze staną się nieudostępnione.

- Nie ustawiaj właściwości <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> ani <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> komórki na `false`, gdy odpowiadająca jej właściwość w jej kolumnie jest ustawiona na `true`. Powoduje to, że wszystkie wiersze staną się nieudostępnione.

- Nie uzyskuj dostępu do właściwości <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType>. Powoduje to, że wszystkie wiersze staną się nieudostępnione.

- Nie wywołuj `Sort(IComparer)` przeciążenia metody <xref:System.Windows.Forms.DataGridView.Sort%2A>. Sortowanie za pomocą niestandardowej metody porównującej powoduje, że wszystkie wiersze stają się nieudostępnione.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: ustawianie domyślnych stylów komórki dla kontrolki DataGridView formularzy Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Opcje ustalania rozmiaru w kontrolce DataGridView formularzy Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md)
