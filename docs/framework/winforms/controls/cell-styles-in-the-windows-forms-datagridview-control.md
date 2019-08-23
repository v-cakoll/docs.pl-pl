---
title: Style komórki w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: be4c47db5c56685a84153a9ae4a9a2fe14c6adad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917758"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Style komórki w formancie DataGridView formularzy systemu Windows
Każda komórka w <xref:System.Windows.Forms.DataGridView> kontrolce może mieć własny styl, taki jak format tekstu, kolor tła, kolor pierwszego planu i czcionka. Zwykle jednak wiele komórek będzie współużytkować konkretne charakterystyki stylu.  
  
 Grupy komórek, które współużytkują style mogą obejmować wszystkie komórki w określonych wierszach lub kolumnach, wszystkie komórki zawierające określone wartości lub wszystkie komórki w formancie. Ponieważ te grupy nakładają się na siebie, każda komórka może uzyskać informacje o stylu z więcej niż jednego miejsca. Na przykład możesz chcieć, aby każda komórka w <xref:System.Windows.Forms.DataGridView> kontrolce używała tej samej czcionki, ale tylko komórki w kolumnach walutowych używały formatu waluty i tylko komórki walutowe z liczbami ujemnymi, aby użyć koloru czerwonego pierwszego planu.  
  
## <a name="the-datagridviewcellstyle-class"></a>Klasa DataGridViewCellStyle  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Klasa zawiera następujące właściwości związane z stylem wizualnym:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Ta klasa zawiera również następujące właściwości związane z formatowaniem:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Aby uzyskać więcej informacji o tych właściwościach i innych właściwościach stylu komórki, <xref:System.Windows.Forms.DataGridViewCellStyle> Zobacz dokumentację referencyjną i tematy wymienione w sekcji Zobacz też.  
  
## <a name="using-datagridviewcellstyle-objects"></a>Korzystanie z obiektów DataGridViewCellStyle  
 Można pobrać <xref:System.Windows.Forms.DataGridViewCellStyle> obiekty z różnych właściwości <xref:System.Windows.Forms.DataGridView>klas, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>, i <xref:System.Windows.Forms.DataGridViewCell> ich klas pochodnych. Jeśli jedna z tych właściwości nie została jeszcze ustawiona, pobranie jej wartości spowoduje utworzenie nowego <xref:System.Windows.Forms.DataGridViewCellStyle> obiektu. Można również tworzyć wystąpienia własnych <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów i przypisywać je do tych właściwości.  
  
 Można uniknąć niepotrzebnego duplikowania informacji o stylu <xref:System.Windows.Forms.DataGridViewCellStyle> przez udostępnianie obiektów <xref:System.Windows.Forms.DataGridView> między wieloma elementami. Ze względu na to, że style ustawione na poziomach formantu, kolumny i wiersza są filtrowane w dół na poziomie komórki, można również uniknąć duplikowania stylu przez ustawienie tylko tych właściwości stylu na każdym poziomie, które różnią się od powyższych poziomów. Opisano to szczegółowo w sekcji dziedziczenie stylów poniżej.  
  
 W poniższej tabeli wymieniono podstawowe właściwości, które pobierają <xref:System.Windows.Forms.DataGridViewCellStyle> lub ustawiają obiekty.  
  
|Właściwość|Klasy|Opis|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn> ,<xref:System.Windows.Forms.DataGridViewRow>i klasy pochodne|Pobiera lub ustawia domyślne style używane przez wszystkie komórki w całej kontrolce (w tym komórki nagłówka), w kolumnie lub w wierszu.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślne style komórek używane przez wszystkie wiersze w kontrolce. Nie obejmuje to komórek nagłówka.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślne style komórek używane przez przemienne wiersze w kontrolce. Służy do tworzenia efektu przypominającego finanse.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślne style komórek używane przez nagłówki wierszy formantu. Zastępowany przez bieżący motyw, jeśli style wizualizacji są włączone.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślne style komórek używane przez nagłówki kolumn formantu. Zastępowany przez bieżący motyw, jeśli style wizualizacji są włączone.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell>i klasy pochodne|Pobiera lub ustawia style określone na poziomie komórki. Te style zastępują te dziedziczone z wyższego poziomu.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow> ,<xref:System.Windows.Forms.DataGridViewColumn>i klasy pochodne|Pobiera wszystkie style, które są aktualnie stosowane do komórki, wiersza lub kolumny, włącznie z stylami dziedziczonymi z wyższego poziomu.|  
  
 Jak wspomniano powyżej, pobranie wartości właściwości style automatycznie tworzy wystąpienie nowego <xref:System.Windows.Forms.DataGridViewCellStyle> obiektu, jeśli właściwość nie została wcześniej ustawiona. Aby uniknąć niepotrzebnego tworzenia tych obiektów, klasy wierszy i kolumn mają <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> właściwość, którą można sprawdzić, aby określić, <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> czy właściwość została ustawiona. Podobnie klasy komórek mają <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> właściwość, która wskazuje, <xref:System.Windows.Forms.DataGridViewCell.Style%2A> czy właściwość została ustawiona.  
  
 Każda właściwość stylu ma odpowiednie zdarzenie *PropertyName* `Changed` na <xref:System.Windows.Forms.DataGridView> formancie. Dla właściwości wiersza, kolumny i komórki Nazwa zdarzenia`Row`rozpoczyna się od "", "`Column`" lub "`Cell`" (na przykład <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>). Każde z tych zdarzeń występuje, gdy odpowiednia właściwość stylu jest ustawiona na inny <xref:System.Windows.Forms.DataGridViewCellStyle> obiekt. Te zdarzenia nie występują, gdy pobierasz <xref:System.Windows.Forms.DataGridViewCellStyle> obiekt z właściwości style i modyfikujesz jego wartości właściwości. Aby reagować na zmiany obiektów stylu komórki, należy obsłużyć <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> zdarzenie.  
  
## <a name="style-inheritance"></a>Dziedziczenie stylów  
 Każdy <xref:System.Windows.Forms.DataGridViewCell> z nich pobiera swój wygląd <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> z jego właściwości. Obiekt zwrócony przez tę właściwość dziedziczy wartości z hierarchii właściwości typu <xref:System.Windows.Forms.DataGridViewCellStyle>. <xref:System.Windows.Forms.DataGridViewCellStyle> Te właściwości są wymienione poniżej w kolejności, w której <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> w przypadku komórek niebędących nagłówkami uzyskują swoje wartości.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(tylko w przypadku komórek w wierszach z nieparzystymi numerami indeksu)  
  
4. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 W przypadku komórek <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> nagłówka wiersza i kolumny właściwość jest wypełniana wartościami z poniższej listy właściwości źródła w danej kolejności.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Na poniższym diagramie przedstawiono ten proces.  
  
 ![Właściwości typu DataGridViewCellStyle](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "Diagram dziedziczeń elementów DataGridViewCell")  
  
 Możesz również uzyskać dostęp do stylów dziedziczonych przez określone wiersze i kolumny. Właściwość Column <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> dziedziczy wartości z następujących właściwości.  
  
1. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Właściwość Row <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> dziedziczy wartości z następujących właściwości.  
  
1. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(tylko w przypadku komórek w wierszach z nieparzystymi numerami indeksu)  
  
3. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Dla każdej właściwości w <xref:System.Windows.Forms.DataGridViewCellStyle> obiekcie zwracanym `InheritedStyle` przez właściwość wartość właściwości jest uzyskiwana z pierwszego stylu komórki na odpowiedniej liście, która ma odpowiadającą jej Właściwość ustawioną na wartość inną niż <xref:System.Windows.Forms.DataGridViewCellStyle> wartości domyślne klasy.  
  
 W poniższej tabeli przedstawiono sposób, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> w jaki wartość właściwości dla przykładowej komórki jest dziedziczona z kolumny zawierającej.  
  
|Właściwość typu`DataGridViewCellStyle`|Przykładowa `ForeColor` wartość dla pobranego obiektu|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 W takim przypadku <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> wartość z wiersza komórki to pierwsza wartość rzeczywista na liście. Jest to <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>wartość właściwości.<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
 Na poniższym diagramie przedstawiono sposób, <xref:System.Windows.Forms.DataGridViewCellStyle> w jaki różne właściwości mogą dziedziczyć wartości z różnych miejsc.  
  
 ![Dziedziczenie&#45;wartości właściwości DataGridView](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "Diagram dziedziczenia wartości elementów DataGridViewCell")  
  
 Dzięki wykorzystaniu dziedziczenia stylu można zapewnić odpowiednie style dla całej kontrolki bez konieczności określania tych samych informacji w wielu miejscach.  
  
 Mimo że komórki nagłówka uczestniczą w dziedziczeniu stylu zgodnie z opisem, obiekty <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> zwrócone <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> przez i właściwości <xref:System.Windows.Forms.DataGridView> formantu mają początkowe wartości właściwości, które zastępują wartości właściwości obiektu zwróconego przez <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> właściwość. Jeśli chcesz, aby właściwości zostały ustawione dla obiektu zwróconego przez <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> właściwość w celu zastosowania do nagłówków wierszy i kolumn, należy ustawić odpowiednie właściwości obiektów zwracanych <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> przez i <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> właściwości do wskazanych wartości domyślnych. <xref:System.Windows.Forms.DataGridViewCellStyle> dla klasy.  
  
> [!NOTE]
> Jeśli style wizualizacji są włączone, nagłówki wierszy i kolumn (z wyjątkiem <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) są automatycznie wzorowane przez bieżący motyw, zastępując style określone przez te właściwości.  
  
 ,, I <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> typy inicjują również niektóre wartości obiektu zwróconego przez Właściwość Column. <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> <xref:System.Windows.Forms.DataGridViewImageColumn> <xref:System.Windows.Forms.DataGridViewButtonColumn> Aby uzyskać więcej informacji, zobacz dokumentację referencyjną dla tych typów.  
  
## <a name="setting-styles-dynamically"></a>Dynamiczne ustawianie stylów  
 Aby dostosować style komórek o określonych wartościach, zaimplementuj procedurę obsługi dla <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> zdarzenia. Programy obsługi dla tego zdarzenia otrzymują argument <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> typu. Ten obiekt zawiera właściwości pozwalające określić wartość sformatowanej komórki wraz z jej lokalizacją w <xref:System.Windows.Forms.DataGridView> kontrolce. Ten obiekt zawiera <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> również właściwość, która została zainicjowana do wartości <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> właściwości sformatowanej komórki. Możesz zmodyfikować właściwości stylu komórki, aby określić informacje o stylu odpowiednie dla wartości komórki i lokalizacji.  
  
> [!NOTE]
> Zdarzenia <xref:System.Windows.Forms.DataGridView.RowPrePaint> i <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> odbierają <xref:System.Windows.Forms.DataGridViewCellStyle> także obiekt w danych zdarzenia, ale w ich przypadku jest to kopia właściwości wiersza do celów tylko do odczytu, a zmiany w nim nie wpływają na <xref:System.Windows.Forms.DataGridView.RowPostPaint> kontrolkę.  
  
 Możesz również dynamicznie modyfikować style poszczególnych komórek w odpowiedzi na zdarzenia, takie jak <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> zdarzenia i. <xref:System.Windows.Forms.DataGridView.CellMouseLeave> Na przykład w procedurze obsługi dla <xref:System.Windows.Forms.DataGridView.CellMouseEnter> zdarzenia można przechowywać bieżącą wartość koloru tła komórki (pobieraną za pośrednictwem <xref:System.Windows.Forms.DataGridViewCell.Style%2A> właściwości komórki), a następnie ustawić ją na nowy kolor, który będzie wyróżniać komórkę, gdy wskaźnik myszy jest przesuwany nad nią. W procedurze obsługi <xref:System.Windows.Forms.DataGridView.CellMouseLeave> zdarzenia można przywrócić pierwotną wartość koloru tła.  
  
> [!NOTE]
> Buforowanie wartości przechowywanych we <xref:System.Windows.Forms.DataGridViewCell.Style%2A> właściwości komórki jest ważne niezależnie od tego, czy ustawiono określoną wartość stylu. Jeśli tymczasowo zastąpisz ustawienie stylu, przywrócenie jego oryginalnego stanu "nie ustawiono" spowoduje, że komórka powróci do dziedziczenia ustawienia stylu z wyższego poziomu. Jeśli konieczne jest określenie rzeczywistego stylu dla komórki bez względu na to, czy styl jest dziedziczony, użyj <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> właściwości komórki.  
  
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
- [Instrukcje: Ustawianie domyślnych stylów komórek dla kontrolki DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Formatowanie danych w kontrolce DataGridView formularzy Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
