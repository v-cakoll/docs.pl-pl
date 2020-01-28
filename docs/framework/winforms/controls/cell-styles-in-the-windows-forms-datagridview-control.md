---
title: Style komórki w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: fe56033a5adbe7719c64695c8f9ebc4f3644fc65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746156"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Style komórki w formancie DataGridView formularzy systemu Windows
Każda komórka w formancie <xref:System.Windows.Forms.DataGridView> może mieć własny styl, taki jak format tekstu, kolor tła, kolor pierwszego planu i czcionka. Zwykle jednak wiele komórek będzie współużytkować konkretne charakterystyki stylu.  
  
 Grupy komórek, które współużytkują style mogą obejmować wszystkie komórki w określonych wierszach lub kolumnach, wszystkie komórki zawierające określone wartości lub wszystkie komórki w formancie. Ponieważ te grupy nakładają się na siebie, każda komórka może uzyskać informacje o stylu z więcej niż jednego miejsca. Na przykład możesz chcieć, aby każda komórka w kontrolce <xref:System.Windows.Forms.DataGridView> używała tej samej czcionki, ale tylko komórki w kolumnach walutowych używały formatu waluty i tylko komórki walutowe z liczbami ujemnymi, aby użyć koloru czerwonego pierwszego planu.  
  
## <a name="the-datagridviewcellstyle-class"></a>Klasa DataGridViewCellStyle  
 Klasa <xref:System.Windows.Forms.DataGridViewCellStyle> zawiera następujące właściwości związane z stylem wizualnym:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Ta klasa zawiera również następujące właściwości związane z formatowaniem:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Aby uzyskać więcej informacji o tych właściwościach i innych właściwościach stylu komórki, zobacz dokumentację referencyjną <xref:System.Windows.Forms.DataGridViewCellStyle> i tematy wymienione w sekcji Zobacz też.  
  
## <a name="using-datagridviewcellstyle-objects"></a>Korzystanie z obiektów DataGridViewCellStyle  
 Można pobrać <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów z różnych właściwości klas <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>i <xref:System.Windows.Forms.DataGridViewCell> i ich klas pochodnych. Jeśli jedna z tych właściwości nie została jeszcze ustawiona, pobranie jej wartości spowoduje utworzenie nowego obiektu <xref:System.Windows.Forms.DataGridViewCellStyle>. Możesz również utworzyć wystąpienia własnych <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów i przypisać je do tych właściwości.  
  
 Można uniknąć niepotrzebnego duplikowania informacji o stylu przez udostępnienie <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów wśród wielu elementów <xref:System.Windows.Forms.DataGridView>. Ze względu na to, że style ustawione na poziomach formantu, kolumny i wiersza są filtrowane w dół na poziomie komórki, można również uniknąć duplikowania stylu przez ustawienie tylko tych właściwości stylu na każdym poziomie, które różnią się od powyższych poziomów. Opisano to szczegółowo w sekcji dziedziczenie stylów poniżej.  
  
 W poniższej tabeli wymieniono podstawowe właściwości, które pobierają lub ustawiają <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów.  
  
|Właściwość|Klasy|Opis|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>i klasy pochodne|Pobiera lub ustawia domyślne style używane przez wszystkie komórki w całej kontrolce (w tym komórki nagłówka), w kolumnie lub w wierszu.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślne style komórek używane przez wszystkie wiersze w kontrolce. Nie obejmuje to komórek nagłówka.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślne style komórek używane przez przemienne wiersze w kontrolce. Służy do tworzenia efektu przypominającego finanse.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślne style komórek używane przez nagłówki wierszy formantu. Zastępowany przez bieżący motyw, jeśli style wizualizacji są włączone.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślne style komórek używane przez nagłówki kolumn formantu. Zastępowany przez bieżący motyw, jeśli style wizualizacji są włączone.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell> i klasy pochodne|Pobiera lub ustawia style określone na poziomie komórki. Te style zastępują te dziedziczone z wyższego poziomu.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow>, <xref:System.Windows.Forms.DataGridViewColumn>i klasy pochodne|Pobiera wszystkie style, które są aktualnie stosowane do komórki, wiersza lub kolumny, włącznie z stylami dziedziczonymi z wyższego poziomu.|  
  
 Jak wspomniano powyżej, pobieranie wartości właściwości style automatycznie tworzy wystąpienie nowego obiektu <xref:System.Windows.Forms.DataGridViewCellStyle>, jeśli właściwość nie została wcześniej ustawiona. Aby uniknąć niepotrzebnego tworzenia tych obiektów, klasy wierszy i kolumn mają właściwość <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A>, którą można sprawdzić, aby określić, czy właściwość <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> została ustawiona. Podobnie klasy komórek mają właściwość <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A>, która wskazuje, czy właściwość <xref:System.Windows.Forms.DataGridViewCell.Style%2A> została ustawiona.  
  
 Każda właściwość stylu ma odpowiednie zdarzenie *PropertyName*`Changed` na kontrolce <xref:System.Windows.Forms.DataGridView>. Dla właściwości wiersza, kolumny i komórki Nazwa zdarzenia rozpoczyna się od "`Row`", "`Column`" lub "`Cell`" (na przykład <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>). Każde z tych zdarzeń występuje, gdy odpowiednia właściwość stylu jest ustawiona na inny obiekt <xref:System.Windows.Forms.DataGridViewCellStyle>. Te zdarzenia nie występują, gdy pobierasz obiekt <xref:System.Windows.Forms.DataGridViewCellStyle> z właściwości style i modyfikujesz jego wartości właściwości. Aby odpowiedzieć na zmiany obiektów stylu komórki, należy obsłużyć zdarzenie <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged>.  
  
## <a name="style-inheritance"></a>Dziedziczenie stylów  
 Każdy <xref:System.Windows.Forms.DataGridViewCell> pobiera swój wygląd z jego właściwości <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>. Obiekt <xref:System.Windows.Forms.DataGridViewCellStyle> zwrócony przez tę właściwość dziedziczy wartości z hierarchii właściwości typu <xref:System.Windows.Forms.DataGridViewCellStyle>. Te właściwości są wymienione poniżej w kolejności, w której <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> komórek niebędących nagłówkami uzyskują swoje wartości.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (tylko w przypadku komórek w wierszach z nieparzystymi numerami indeksu)  
  
4. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 W przypadku komórek nagłówka wiersza i kolumny Właściwość <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> jest wypełniana wartościami z poniższej listy właściwości źródła w danej kolejności.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Na poniższym diagramie przedstawiono ten proces.  
  
 ![Właściwości typu DataGridViewCellStyle](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "Diagram dziedziczeń elementów DataGridViewCell")  
  
 Możesz również uzyskać dostęp do stylów dziedziczonych przez określone wiersze i kolumny. Właściwość <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> kolumny dziedziczy wartości z następujących właściwości.  
  
1. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Właściwość Row <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> dziedziczy wartości z następujących właściwości.  
  
1. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (tylko w przypadku komórek w wierszach z nieparzystymi numerami indeksu)  
  
3. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Dla każdej właściwości w obiekcie <xref:System.Windows.Forms.DataGridViewCellStyle> zwróconym przez właściwość `InheritedStyle` wartość właściwości jest uzyskiwana z pierwszego stylu komórki na odpowiedniej liście, która ma odpowiadającą mu Właściwość ustawioną na wartość inną niż <xref:System.Windows.Forms.DataGridViewCellStyle> domyślne klasy.  
  
 W poniższej tabeli przedstawiono sposób, w jaki <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> wartość właściwości dla przykładowej komórki jest dziedziczona z kolumny zawierającej.  
  
|Właściwość typu `DataGridViewCellStyle`|Przykład `ForeColor` wartość dla pobranego obiektu|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 W takim przypadku <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> wartością z wiersza komórki jest pierwsza wartość rzeczywista na liście. Zostanie <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> wartość właściwości <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>komórki.  
  
 Na poniższym diagramie przedstawiono sposób, w jaki różne właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> mogą dziedziczyć wartości z różnych miejsc.  
  
 ![Dziedziczenie&#45;wartości właściwości DataGridView](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "Diagram dziedziczenia wartości elementów DataGridViewCell")  
  
 Dzięki wykorzystaniu dziedziczenia stylu można zapewnić odpowiednie style dla całej kontrolki bez konieczności określania tych samych informacji w wielu miejscach.  
  
 Chociaż komórki nagłówka uczestniczą w dziedziczeniu stylu zgodnie z opisem, obiekty zwrócone przez <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> właściwości kontrolki <xref:System.Windows.Forms.DataGridView> mają początkowe wartości właściwości, które zastępują wartości właściwości obiektu zwróconego przez właściwość <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>. Jeśli chcesz, aby właściwości zostały ustawione dla obiektu zwróconego przez właściwość <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> do zastosowania do nagłówków wierszy i kolumn, należy ustawić odpowiednie właściwości obiektów zwracanych przez <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> i właściwości <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> do wartości domyślnych wskazanych dla klasy <xref:System.Windows.Forms.DataGridViewCellStyle>.  
  
> [!NOTE]
> Jeśli style wizualizacji są włączone, nagłówki wierszy i kolumn (z wyjątkiem <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) są automatycznie wzorowane przez bieżący motyw, zastępując style określone przez te właściwości.  
  
 Typy <xref:System.Windows.Forms.DataGridViewButtonColumn>, <xref:System.Windows.Forms.DataGridViewImageColumn>i <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> również inicjują niektóre wartości obiektu zwrócone przez właściwość <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> kolumny. Aby uzyskać więcej informacji, zobacz dokumentację referencyjną dla tych typów.  
  
## <a name="setting-styles-dynamically"></a>Dynamiczne ustawianie stylów  
 Aby dostosować style komórek o określonych wartościach, zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>. Programy obsługi dla tego zdarzenia otrzymują argument typu <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>. Ten obiekt zawiera właściwości pozwalające określić wartość sformatowanej komórki wraz z jej lokalizacją w kontrolce <xref:System.Windows.Forms.DataGridView>. Ten obiekt zawiera również właściwość <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A>, która jest inicjowana do wartości właściwości <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> sformatowanej komórki. Możesz zmodyfikować właściwości stylu komórki, aby określić informacje o stylu odpowiednie dla wartości komórki i lokalizacji.  
  
> [!NOTE]
> Zdarzenia <xref:System.Windows.Forms.DataGridView.RowPrePaint> i <xref:System.Windows.Forms.DataGridView.RowPostPaint> również odbierają obiekt <xref:System.Windows.Forms.DataGridViewCellStyle> w danych zdarzenia, ale w ich przypadku jest to kopia właściwości wiersza <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> dla celów tylko do odczytu, a zmiany w nim nie wpływają na kontrolkę.  
  
 Możesz również dynamicznie modyfikować style poszczególnych komórek w odpowiedzi na zdarzenia, takie jak <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> i <xref:System.Windows.Forms.DataGridView.CellMouseLeave> zdarzenia. Na przykład w obsłudze zdarzenia <xref:System.Windows.Forms.DataGridView.CellMouseEnter> można przechowywać bieżącą wartość koloru tła komórki (pobieraną za pośrednictwem właściwości <xref:System.Windows.Forms.DataGridViewCell.Style%2A> komórki), a następnie ustawić ją na nowy kolor, który będzie wyróżniać komórkę, gdy wskaźnik myszy zostanie umieszczony nad nią. W programie obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellMouseLeave> można przywrócić pierwotną wartość koloru tła.  
  
> [!NOTE]
> Buforowanie wartości przechowywanych w właściwości <xref:System.Windows.Forms.DataGridViewCell.Style%2A> komórki jest ważne niezależnie od tego, czy określona wartość stylu jest ustawiona. Jeśli tymczasowo zastąpisz ustawienie stylu, przywrócenie jego oryginalnego stanu "nie ustawiono" spowoduje, że komórka powróci do dziedziczenia ustawienia stylu z wyższego poziomu. Jeśli konieczne jest określenie rzeczywistego stylu dla komórki bez względu na to, czy styl jest dziedziczony, użyj właściwości <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> komórki.  
  
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
- [Instrukcje: ustawianie domyślnych stylów komórki dla kontrolki DataGridView formularzy Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Formatowanie danych w kontrolce DataGridView formularzy Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
