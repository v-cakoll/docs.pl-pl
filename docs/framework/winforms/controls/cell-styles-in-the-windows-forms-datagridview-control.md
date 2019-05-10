---
title: Style komórki w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: 98e0ed5f4fe7b0c016b4477ac9f646037b0877ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593434"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Style komórki w formancie DataGridView formularzy systemu Windows
Każda komórka w ramach <xref:System.Windows.Forms.DataGridView> formant może mieć własny styl, na przykład format tekstu, koloru tła, kolor pierwszego planu i czcionki. Zwykle jednak wiele komórek współużytkują właściwości danego stylu.  
  
 Grupy, które współużytkują style komórek może obejmować wszystkie komórki w ramach określonego wierszy lub kolumn, wszystkie komórki zawierające określonej wartości lub wszystkie komórki w formancie. Ponieważ te grupy zachodziły na siebie, każda komórka może uzyskać jego informacje dotyczące stylu z więcej niż jednego miejsca. Na przykład może być każdej komórki <xref:System.Windows.Forms.DataGridView> sterowania za pomocą tego samego czcionki, ale tylko komórki w kolumnach waluty, aby użyć formatu waluty i tylko komórki w walucie liczbami ujemnymi używać czerwonym kolorem.  
  
## <a name="the-datagridviewcellstyle-class"></a>Klasa DataGridViewCellStyle  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Klasa zawiera następujące właściwości związane z stylu wizualnego:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Ta klasa zawiera także następujące właściwości związane z formatowaniem:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Aby uzyskać więcej informacji na temat tych właściwości i inne właściwości stylu komórki, zobacz <xref:System.Windows.Forms.DataGridViewCellStyle> dokumentację referencyjną i tematy wymienione w poniższej sekcji Zobacz też.  
  
## <a name="using-datagridviewcellstyle-objects"></a>Używanie obiektów DataGridViewCellStyle  
 Możesz pobrać <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów z różnych właściwości obiektu <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>, i <xref:System.Windows.Forms.DataGridViewCell> klasy i ich klasy pochodne. Jeśli jedna z tych właściwości nie jeszcze została ustawiona, trwa pobieranie jego wartość zostanie utworzony nowy <xref:System.Windows.Forms.DataGridViewCellStyle> obiektu. Można również utworzyć wystąpienie własne <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów i przypisać je do tych właściwości.  
  
 Możesz uniknąć niepotrzebnego dublowania informacje dotyczące stylu, udostępniając <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów między wieloma <xref:System.Windows.Forms.DataGridView> elementów. Style są ustawione na kontrolki, kolumn i wierszy poziomy odfiltrowywanie przez każdy poziom na poziomie komórki, dlatego możesz uniknąć stylu duplikatów przez ustawienie tych właściwości stylu na każdym poziomie, które różnią się od poziomów powyżej. Jest to opisane bardziej szczegółowo w następnej sekcji dziedziczenie stylów.  
  
 W poniższej tabeli wymieniono podstawowe właściwości, które pobierania lub ustawiania <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów.  
  
|Właściwość|Klasy|Opis|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>i klasy pochodne|Pobiera lub ustawia domyślne style używane przez wszystkie komórki w całej kontrolce (w tym komórki nagłówka), w kolumnie lub w wierszu.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślnych stylów komórek używana przez wszystkich wierszy w formancie. Nie ma komórki nagłówka.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślnych stylów komórek posługują się naprzemiennych wierszy w formancie. Pozwala utworzyć efekt jak rejestr.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślnych stylów komórek używane przez nagłówki wierszy formantu. Zastąpione przez bieżący motyw, włączenie funkcji stylów wizualnych.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślnych stylów komórek posługują się nagłówki kolumn formantu. Zastąpione przez bieżący motyw, włączenie funkcji stylów wizualnych.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell> i klasy pochodne|Pobiera lub ustawia style określone na poziomie komórki. Te style przesłaniają akcje dziedziczone z wyższego poziomu.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow>, <xref:System.Windows.Forms.DataGridViewColumn>i klasy pochodne|Pobiera wszystkie style, które są obecnie stosowany do komórki, wiersza lub kolumny, w tym style dziedziczone z wyższego poziomu.|  
  
 Jak wspomniano powyżej, pobierania wartości właściwości stylu automatycznie tworzy nową <xref:System.Windows.Forms.DataGridViewCellStyle> obiektu, jeśli właściwość nie została wcześniej ustawiona. Aby uniknąć niepotrzebnego tworzenia tych obiektów, klas wiersza i kolumny mają <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> właściwość, którą można sprawdzić, aby określić, czy <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> właściwość została ustawiona. Podobnie, klasy komórki mają <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> właściwość, która wskazuje, czy <xref:System.Windows.Forms.DataGridViewCell.Style%2A> właściwość została ustawiona.  
  
 Każdy z ponownego obliczenia właściwości stylu ma odpowiadające mu *PropertyName* `Changed` zdarzenie na <xref:System.Windows.Forms.DataGridView> kontroli. Dla wierszy, kolumny i właściwości komórki Nazwa zdarzenia rozpoczyna się od "`Row`","`Column`", lub "`Cell`" (na przykład <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>). Każde z tych wydarzeń występuje, gdy odpowiednia właściwość stylu jest ustawiona na inne <xref:System.Windows.Forms.DataGridViewCellStyle> obiektu. Te zdarzenia nie występują po pobraniu <xref:System.Windows.Forms.DataGridViewCellStyle> z właściwości stylu i zmodyfikować wartości właściwości. Aby reagować na zmiany w samych obiektach style komórki, obsługi <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> zdarzeń.  
  
## <a name="style-inheritance"></a>Dziedziczenie stylów  
 Każdy <xref:System.Windows.Forms.DataGridViewCell> pobiera jego wygląd z jego <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> właściwości. <xref:System.Windows.Forms.DataGridViewCellStyle> Obiektu zwróconego przez tę właściwość dziedziczy jej wartości właściwości typu hierarchia <xref:System.Windows.Forms.DataGridViewCellStyle>. Te właściwości są podane poniżej w kolejności, w którym <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> komórek-header uzyskuje jego wartości.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (tylko w przypadku komórek w wierszach nieparzystych numery indeksu)  
  
4. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Dla wiersza i kolumny komórki nagłówka <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> właściwość jest wypełniana przez wartości z poniższej listy właściwości źródła w podanej kolejności.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Na poniższym diagramie przedstawiono ten proces.  
  
 ![Właściwości typu DataGridViewCellStyle](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "DataGridViewCells diagram dziedziczenia")  
  
 Można także przejść style dziedziczone przez określonych wierszy i kolumn. Kolumna <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> właściwość dziedziczy jej wartości następujących właściwości.  
  
1. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Wiersz <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> właściwość dziedziczy jej wartości następujących właściwości.  
  
1. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (tylko w przypadku komórek w wierszach nieparzystych numery indeksu)  
  
3. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Dla każdej właściwości w <xref:System.Windows.Forms.DataGridViewCellStyle> obiektu zwróconego przez `InheritedStyle` właściwości, wartość właściwości jest uzyskiwana z pierwszym styl komórek na odpowiedniej liście, który ma odpowiedni zestaw właściwości do wartości innych niż <xref:System.Windows.Forms.DataGridViewCellStyle> klasy wartości domyślne.  
  
 W poniższej tabeli przedstawiono sposób, w jaki <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> wartości właściwości dla komórki przykład jest dziedziczony z kolumny zawierającej.  
  
|właściwości typu `DataGridViewCellStyle`|Przykład `ForeColor` wartość dla obiektu pobrany|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 W tym przypadku <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> wartość komórki wiersza jest pierwszym rzeczywistą wartość na liście. Staje się on <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> wartość właściwości komórki <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>.  
  
 Na poniższym diagramie przedstawiono sposób różnych <xref:System.Windows.Forms.DataGridViewCellStyle> właściwości może dziedziczyć ich wartości z różnych miejsc.  
  
 ![Właściwość formantu DataGridView&#45;wartość dziedziczenia](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "DataGridViewCells wartość dziedziczenia diagramu")  
  
 Dzięki wykorzystaniu dziedziczenie stylów, możesz podać odpowiednie style kontrolki całego bez konieczności określania tych samych informacji w kilku miejscach.  
  
 Mimo że komórki nagłówka uczestniczą w dziedziczeniu stylu, zgodnie z opisem, obiekty zwrócone przez <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> właściwości <xref:System.Windows.Forms.DataGridView> kontrolka ma początkowe wartości właściwości, które zastępują wartości właściwości w obiekcie zwracanym przez <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> właściwości. Jeśli chcesz, aby właściwości ustawione dla obiektu zwróconego przez <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> właściwości do zastosowania do nagłówków wierszy i kolumn, należy ustawić odpowiednie właściwości obiektów zwróconych przez <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> wskazanej właściwości do wartości domyślnych Aby uzyskać <xref:System.Windows.Forms.DataGridViewCellStyle> klasy.  
  
> [!NOTE]
>  Po włączeniu funkcji stylów wizualnych nagłówki wierszy i kolumn (z wyjątkiem <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) są automatycznie ich styl, bieżący motyw, zastępując wszystkie style, określony przez te właściwości.  
  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>, <xref:System.Windows.Forms.DataGridViewImageColumn>, I <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> typy również inicjują kilka wartości obiektu zwróconego przez kolumnę <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> właściwości. Aby uzyskać więcej informacji zobacz dokumentację odniesienia dla tych typów.  
  
## <a name="setting-styles-dynamically"></a>Dynamiczne Ustawianie stylów  
 Aby dostosować style komórek przy użyciu określonej wartości, należy zaimplementować obsługi dla <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> zdarzeń. Programy obsługi dla tego zdarzenia otrzymywać argumentu <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> typu. Ten obiekt zawiera właściwości, które pozwalają określić wartość komórki formatowana wraz z jego lokalizację w <xref:System.Windows.Forms.DataGridView> kontroli. Ten obiekt zawiera także <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> właściwości, który jest inicjowany do wartości <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> właściwości komórki formatowana. Można zmodyfikować właściwości stylu komórki, aby określić informacje dotyczące stylu odpowiednie wartości w komórce i lokalizacji.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.RowPrePaint> i <xref:System.Windows.Forms.DataGridView.RowPostPaint> również odbierać zdarzenia <xref:System.Windows.Forms.DataGridViewCellStyle> danych w zdarzeniu obiektu, ale w ich przypadku jest kopię wiersza <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> właściwość tylko do odczytu do celów i zmiany do niego nie wpływają na formant.  
  
 Takie jak również dynamiczne można zmodyfikować style pojedyncze komórki w reakcji na zdarzenia <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> i <xref:System.Windows.Forms.DataGridView.CellMouseLeave> zdarzenia. Na przykład w przypadku obsługi dla <xref:System.Windows.Forms.DataGridView.CellMouseEnter> zdarzeń, może przechowywać bieżącą wartość koloru tła komórek (pobierane w drodze komórki <xref:System.Windows.Forms.DataGridViewCell.Style%2A> właściwości), wówczas ustaw ją na nowy kolor, który wyróżnij komórkę, gdy wskaźnik myszy znajdzie się nad nią. W obsłudze dla <xref:System.Windows.Forms.DataGridView.CellMouseLeave> zdarzenia, można przywrócić kolor tła do oryginalnej wartości.  
  
> [!NOTE]
>  Buforowanie wartości przechowywane w komórce <xref:System.Windows.Forms.DataGridViewCell.Style%2A> właściwość jest ważne, niezależnie od tego, czy ustawiono wartość konkretnego stylu. Jeżeli wymienisz tymczasowo ustawienie style, przywracane do pierwotnego stanu "nie jest ustawiona" zapewnia, że komórki powraca do dziedziczących ustawienie style na wyższy poziom. Jeśli zachodzi potrzeba określenia rzeczywistego stylu dla komórki, niezależnie od tego, czy jest dziedziczona styl, należy użyć komórki <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Ustawianie domyślnych stylów komórki dla kontrolki DataGridView formularzy Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Formatowanie danych w kontrolce DataGridView formularzy Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
