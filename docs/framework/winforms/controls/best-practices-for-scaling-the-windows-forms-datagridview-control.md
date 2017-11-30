---
title: "Najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bfefd41a4773c81757f73e725095057f988cef2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>Najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Formantu ma na celu zapewnienie maksymalnej skalowalności. Jeśli konieczne jest wyświetlenie dużych ilości danych, powinny postępuj zgodnie z wytycznymi, opisane w tym temacie, aby uniknąć zużywa duże ilości pamięci lub pogorszenia jakości związku czasu odpowiedzi interfejsu użytkownika (UI). W tym temacie omówiono następujące zagadnienia:  
  
-   Wydajne użycie style komórek  
  
-   Wydajne użycie menu skrótów  
  
-   Przy użyciu automatyczną zmianę rozmiaru wydajnie  
  
-   Wydajne użycie wybranych kolekcji komórek, wierszy i kolumn  
  
-   Przy użyciu udostępnione wiersze  
  
-   Uniemożliwia staje się anulować wierszy  
  
 Jeśli masz potrzeby w zakresie wydajności specjalne można Implementowanie trybu wirtualnego i podać własne operacje zarządzania danych. Aby uzyskać więcej informacji, zobacz [tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-cell-styles-efficiently"></a>Wydajne użycie style komórek  
 Każdy komórek, wierszy i kolumn może mieć własną informacji o stylu. Styl informacje są przechowywane w <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów. Tworzenie obiektów stylów komórki dla poszczególnych wiele <xref:System.Windows.Forms.DataGridView> elementów może być mało wydajne, szczególnie w przypadku pracy z dużą ilością danych. Aby uniknąć wpływu na wydajność, skorzystaj z następujących wskazówek:  
  
-   Unikaj ustawiania właściwości stylu komórki dla poszczególnych <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewRow> obiektów. Obejmuje to obiekt wiersza określony przez <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> właściwości. Każdego nowego wiersza, który został sklonowany z szablonu wiersza otrzyma on osobną kopię obiektu style komórki w szablonie. Maksymalna skalowalności ustawionych właściwości stylu komórki w <xref:System.Windows.Forms.DataGridView> poziom. Na przykład ustawić <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> właściwości zamiast <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> właściwości.  
  
-   Jeśli niektóre komórki wymagają formatowania innych niż domyślne formatowanie, należy używać tego samego <xref:System.Windows.Forms.DataGridViewCellStyle> wystąpienia między grupami komórek, wierszy i kolumn. Unikaj bezpośrednio ustawiania właściwości typu <xref:System.Windows.Forms.DataGridViewCellStyle> na pojedynczych komórek, wierszy i kolumn. Przykład stylu komórki do udostępniania, zobacz [porady: Ustawianie domyślne style komórki dla formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Również można uniknąć spadek wydajności podczas ustawiania style komórki indywidualnie Obsługa <xref:System.Windows.Forms.DataGridView.CellFormatting> obsługi zdarzeń. Na przykład zobacz [porady: dostosowywanie formatowania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
-   Podczas określania stylu komórki, użyj <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType> właściwości zamiast <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> właściwości. Uzyskiwanie dostępu do <xref:System.Windows.Forms.DataGridViewCell.Style%2A> właściwości tworzy nowe wystąpienie klasy <xref:System.Windows.Forms.DataGridViewCellStyle> klasy, jeśli właściwość nie jest już używana. Ponadto ten obiekt może nie zawierać informacji o pełną stylu komórki, jeśli niektóre style są dziedziczone z wierszy, kolumny lub formantu. Aby uzyskać więcej informacji na temat dziedziczenia stylu komórki, zobacz [style komórki w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-shortcut-menus-efficiently"></a>Wydajne użycie menu skrótów  
 Każdy komórek, wierszy i kolumn może mieć własną menu skrótów. Menu skrótów w <xref:System.Windows.Forms.DataGridView> formantu są reprezentowane przez <xref:System.Windows.Forms.ContextMenuStrip> kontrolki. Tak jak w przypadku obiektów stylu komórki, tworzenie menu skrótów dla poszczególnych wiele <xref:System.Windows.Forms.DataGridView> elementy ujemnie wpływa na wydajność. Aby uniknąć tego kar, użyj następujących wytycznych:  
  
-   Unikaj tworzenia menu skrótów do pojedynczych komórek i wierszy. W tym szablonu wiersza, który został sklonowany wraz z jego menu skrótów po dodaniu nowych wierszy do formantu. Maksymalna skalowalności, użyj tylko formantu <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwości w celu określenia menu skrótów pojedynczego całego formantu.  
  
-   Jeśli potrzebujesz wielu menu skrótów dla wielu komórek lub wierszy obsługi <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> lub <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded> zdarzenia. Zdarzenia te umożliwiają zarządzanie obiektów menu skrótów samodzielnie, umożliwiając dostrajania wydajności.  
  
## <a name="using-automatic-resizing-efficiently"></a>Przy użyciu automatyczną zmianę rozmiaru wydajnie  
 Wiersze, kolumny i nagłówki można zmieniany automatycznie jako zmiany zawartości komórki tak, aby cała zawartość komórki są wyświetlane bez przycinania. Zmiana rozmiaru tryby można również zmienić rozmiar wierszy, kolumny i nagłówków. Aby określić odpowiedni rozmiar <xref:System.Windows.Forms.DataGridView> kontroli należy sprawdzić wartość każdej komórki, które należy uwzględnić go. Podczas pracy z dużych zestawów danych, analiza może niekorzystnie wpłynąć na wydajność formantu, gdy wystąpi automatyczną zmianę rozmiaru. Aby uniknąć spadku wydajności, skorzystaj z następujących wskazówek:  
  
-   Unikaj używania automatycznej zmiany rozmiaru w <xref:System.Windows.Forms.DataGridView> formantu o dużych zestawów wierszy. Jeśli używasz automatycznej zmiany rozmiaru, tylko zmiany rozmiaru wyświetlanych wierszy. Użyj tylko wyświetlanych wierszy w trybie wirtualnym, a także.  
  
    -   Dla wierszy i kolumn, użyj `DisplayedCells` lub `DisplayedCellsExceptHeaders` pole <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>, <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>, i <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> wyliczenia.  
  
    -   Nagłówki wierszy, można użyć <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders> lub <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader> pole <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> wyliczenia.  
  
-   Maksymalna skalowalność Wyłącz tryb automatycznej zmiany rozmiaru i używać programowe zmiany rozmiaru.  
  
 Aby uzyskać więcej informacji, zobacz [opcje rozmiaru w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>Wydajne użycie wybranych komórek, wierszy i kolumn kolekcji  
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> Kolekcji nie przeprowadza wydajnie z opcjami duże. <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> kolekcje nieoptymalne, mimo że do mniejszym stopniu ponieważ istnieje wiele mniej wierszy niż komórek w przypadku typowych <xref:System.Windows.Forms.DataGridView> kontroli i wiele mniejszą liczbę kolumn niż wierszy. Aby uniknąć spadku wydajności podczas pracy z tymi kolekcjami, skorzystaj z następujących wskazówek:  
  
-   Aby określić, czy wszystkie komórki w <xref:System.Windows.Forms.DataGridView> wybrano, aby uzyskać dostęp do zawartości <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> kolekcji, sprawdzić wartość zwrotną z <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metody. Należy jednak pamiętać, że ta metoda może spowodować wierszy, które mają stać się nieudostępnionych. Aby uzyskać więcej informacji, zobacz następną sekcję.  
  
-   Unikaj używania <xref:System.Collections.ICollection.Count%2A> właściwości <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType> do określenia liczby zaznaczonych komórek. Zamiast tego należy użyć <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType> — metoda i przekaż <xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType> wartość. Podobnie, użyj <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType> metody, aby określić liczbę wybranych elementów, a nie dostęp do wybranych kolekcji wierszy i kolumn.  
  
-   Unikaj tryby wyboru na podstawie komórki. Zamiast tego należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> właściwości <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.  
  
## <a name="using-shared-rows"></a>Używanie udostępnionego wierszy  
 Wykorzystanie pamięci wydajne odbywa się w <xref:System.Windows.Forms.DataGridView> sterowanie za pośrednictwem udostępnione wiersze. Wiersze udostępni te informacje o ich wyglądu i działania, jak to możliwe dzięki udostępnieniu wystąpień <xref:System.Windows.Forms.DataGridViewRow> klasy.  
  
 Podczas udostępniania wystąpienia wiersza oszczędzić pamięć, wiersze można łatwo stają się nieudostępnionych. Na przykład zawsze, gdy użytkownik użyje bezpośrednio komórki, jego wiersz staje się nieudostępnionych. Ponieważ nie można uniknąć, wskazówki zawarte w tym temacie są przydatne tylko w przypadku pracy z bardzo dużych ilości danych, i tylko wtedy, gdy użytkownicy będzie wchodzić w interakcje niewielka część danych zawsze, gdy program jest uruchamiany.  
  
 Wiersz nie może zostać udostępniony w niezwiązanego <xref:System.Windows.Forms.DataGridView> kontroli, jeśli którakolwiek z komórek zawiera wartości. Gdy <xref:System.Windows.Forms.DataGridView> kontrolka jest powiązana z zewnętrznego źródła danych lub gdy Implementowanie trybu wirtualnego, a następnie podaj źródła danych, wartości komórek są przechowywane poza kontrolą, a nie w obiektach komórki, dzięki czemu wierszy, które mają być udostępniane.  
  
 Obiekt wiersza może być udostępniony tylko, jeśli stan jej komórek można ustalić na podstawie stanu wiersza i stanów kolumny zawierającej komórki. Jeśli zmienisz stan komórki, dzięki czemu można określić już ze stanu jego wiersza i kolumny, nie może być współużytkowana wiersza.  
  
 Na przykład wiersz nie może być współużytkowana w następujących sytuacjach:  
  
-   Wiersz zawiera pojedynczy zaznaczonej komórki, który nie znajduje się w zaznaczonej kolumnie.  
  
-   Wiersz zawiera komórki z jego <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> lub <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A> zestawu właściwości.  
  
-   Wiersz zawiera <xref:System.Windows.Forms.DataGridViewComboBoxCell> z jego <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A> zestawu właściwości.  
  
 W trybie powiązane lub w trybie wirtualnym, można zapewnić etykietki narzędzi i menu skrótów pojedynczych komórek Obsługa <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> i <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> zdarzenia.  
  
 <xref:System.Windows.Forms.DataGridView> Formant automatycznie podejmie próbę użycia udostępnione wiersze, jeśli wiersze są dodawane do <xref:System.Windows.Forms.DataGridViewRowCollection>. Aby upewnić się, że wiersze są udostępniane, skorzystaj z poniższych wskazówek:  
  
-   Unikaj wywoływania `Add(Object[])` przeciążenia z <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> — metoda i `Insert(Object[])` przeciążenia z <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> metody <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> kolekcji. Te przeciążenia automatycznie utworzyć nieudostępnionych wierszy.  
  
-   Upewnij się, że określona w wierszu <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> właściwości mogą być udostępniane w następujących przypadkach:  
  
    -   Podczas wywoływania metody `Add()` lub `Add(Int32)` overloads z <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> metody lub `Insert(Int32,Int32)` przeciążenia z <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> metody <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> kolekcji.  
  
    -   Gdy zwiększenie wartości <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType> właściwości.  
  
    -   Podczas ustawiania <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType> właściwości.  
  
-   Upewnij się, że wiersz wskazuje `indexSource` parametru może być udostępniony podczas wywoływania metody <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>, i <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> metody <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> kolekcji.  
  
-   Pamiętaj, że określony wiersz lub wierszy można udostępniać podczas wywoływania metody `Add(DataGridViewRow)` przeciążenia z <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> metody <xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A> metody, `Insert(Int32,DataGridViewRow)` przeciążenia z <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> metody i <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> metody <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>kolekcji.  
  
 Aby określić, czy wiersz jest udostępniony, użyj <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> metodę, aby pobrać obiekt wiersza, a następnie sprawdź obiektu <xref:System.Windows.Forms.DataGridViewBand.Index%2A> właściwości. Udostępnione wiersze zawsze mieć <xref:System.Windows.Forms.DataGridViewBand.Index%2A> właściwości wartości -1.  
  
## <a name="preventing-rows-from-becoming-unshared"></a>Uniemożliwia staje się anulować wierszy  
 Udostępnione wiersze może stać się nieudostępnionych wyniku kodu lub akcji użytkownika. Aby uniknąć wpływu na wydajność, należy unikać powoduje wierszy, które mają stać się nieudostępnionych. Podczas tworzenia aplikacji, można obsługiwać <xref:System.Windows.Forms.DataGridView.RowUnshared> zdarzenia w celu określenia, kiedy nieudostępnionych zaczynają wierszy. Jest to przydatne podczas rozwiązywania problemów udostępnianie wierszy.  
  
 Aby zapobiec przekształceniu cofnięto wierszy, skorzystaj z następujących wskazówek:  
  
-   Unikaj indeksowania <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji lub za pomocą iteracja `foreach` pętli. Nie zazwyczaj należy uzyskać bezpośredni dostęp wierszy. <xref:System.Windows.Forms.DataGridView>metody, które pracują na wiersze wykonać argumentów Indeks wiersza, zamiast kilku wystąpień wiersza. Ponadto programy obsługi dla zdarzenia związane z wiersza wyświetlany obiektów argument zdarzenia z właściwościami wiersza, które służy do manipulowania wierszy bez powodowania je, aby stać się nieudostępnionych.  
  
-   Jeśli potrzebujesz dostępu do obiektu wiersza, użyj <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> — metoda i przekazać w indeksie rzeczywisty wiersza. Należy jednak pamiętać, że modyfikowanie obiektu udostępnionego wiersza pobrać za pomocą tej metody spowoduje jej modyfikacji wszystkie wiersze, które współużytkują ten obiekt. Wiersz dla nowych rekordów nie są udostępniane innych wierszy, dzięki czemu nie będzie można zmian podczas modyfikowania innych wierszy. Należy pamiętać, że różne wiersze reprezentowany przez udostępnionego wiersza może mieć menu skrótów inny. Aby pobrać menu skrótów poprawne z wystąpienia wierszu udostępnionym, należy użyć <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> — metoda i przekazać w indeksie rzeczywisty wiersza. Jeśli dostęp do udostępnionego wiersza <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> właściwości zamiast tego użyje indeksu udostępnionego wiersza-1 i nie będą pobierane z menu skrótów poprawne.  
  
-   Unikaj indeksowania <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType> kolekcji. Bezpośrednie uzyskiwanie dostępu do komórki spowoduje, że jego wiersza nadrzędnego jako nieudostępnionych uruchamianiu nową <xref:System.Windows.Forms.DataGridViewRow>. Programy obsługi dla zdarzenia związane z komórki odbierać obiektów argument zdarzenia z właściwości komórki, które służą do manipulowania komórek bez powodowania wierszy, które mają stać się nieudostępnionych. Można również użyć <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> właściwości można pobrać indeksów wierszy i kolumn bieżącej komórki bez uzyskiwania dostępu do komórki bezpośrednio.  
  
-   Unikaj tryby wyboru na podstawie komórki. Te tryby spowodować wierszy, które mają stać się nieudostępnionych. Zamiast tego należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> właściwości <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.  
  
-   Nie obsługują <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType> zdarzenia. Te zdarzenia spowodować wierszy, które mają stać się nieudostępnionych. Ponadto nie należy wywoływać <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType> metody, które wywołania tych zdarzeń.  
  
-   Nie ma dostępu <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType> kolekcji po <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> wartość właściwości jest <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>, lub <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>. Powoduje to, że wszystkie zaznaczone wiersze stać się nieudostępnionych.  
  
-   Nie wywołuj <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType> metody. Ta metoda może spowodować wierszy, które mają stać się nieudostępnionych.  
  
-   Nie wywołuj <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType> metody podczas <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> wartość właściwości jest <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>. Powoduje to, że wszystkie wiersze stać się nieudostępnionych.  
  
-   Nie ustawiaj <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> lub <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> właściwości komórki do `false` Jeśli odpowiadających im właściwości w jej kolumna jest równa `true`. Powoduje to, że wszystkie wiersze stać się nieudostępnionych.  
  
-   Nie ma dostępu <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType> właściwości. Powoduje to, że wszystkie wiersze stać się nieudostępnionych.  
  
-   Nie wywołuj `Sort(IComparer)` przeciążenia z <xref:System.Windows.Forms.DataGridView.Sort%2A> metody. Sortowania z niestandardowej funkcji porównującej powoduje, że wszystkie wiersze stać się nieudostępnionych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 [Dostrajanie wydajności w systemu Windows do formantu DataGridView formularzy](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Tryb wirtualny w systemie Windows do formantu DataGridView formularzy](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [Tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 [Style komórki w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Porady: Ustawianie domyślnych stylów komórki dla formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 [Opcje rozmiaru w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)
