---
title: Opcje ustalania rozmiaru w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sizing
- data grids [Windows Forms], column sizing
- DataGridView control [Windows Forms], column sizing
- DataGridView control [Windows Forms], sizing options
- data grids [Windows Forms], row sizing
- data grids [Windows Forms], sizing options
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
ms.openlocfilehash: 2f76bbca3d4b6e642c0eec2129c4a2abee752655
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197844"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Opcje ustalania rozmiaru w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> wiersze, kolumny i nagłówki można zmienić rozmiar wyniku wiele różnych wystąpień. W poniższej tabeli przedstawiono te wystąpienia.  
  
|Wystąpienie|Opis|  
|----------------|-----------------|  
|Zmiana rozmiaru użytkownika|Użytkownicy mogą wprowadzać zmiany rozmiaru, przeciągając lub klikając dwukrotnie separator wierszy, kolumny lub nagłówek.|  
|Zmień rozmiar kontrolki|W tryb wypełniania kolumny zmienić szerokość formantu zmienia; szerokości kolumn na przykład, gdy formant jest zadokowany do jego formularza nadrzędnego i użytkownik zmienia rozmiar formularza.|  
|Zmiana wartości komórki|W trybach automatycznej zmiany rozmiaru na podstawie zawartości rozmiary zmienić Dopasuj nowe wartości wyświetlania.|  
|Wywołanie metody|Programowy rozmiaru na podstawie zawartości pozwala wprowadzać zmiany rozmiaru oportunistyczne na podstawie wartości komórek w momencie wywołania metody.|  
|Ustawienie właściwości|Można również ustawić wartości szerokości i wysokości.|  
  
 Domyślnie zmiana rozmiaru użytkownika jest włączona, automatycznej zmiany rozmiaru jest wyłączona i powoduje wartości komórek, które są większe niż kolumn.  
  
 W poniższej tabeli przedstawiono scenariusze, w której można dostosować domyślne zachowanie lub użyj opcji określonych rozmiarów, aby uzyskać efekty określonej.  
  
|Scenariusz|Implementacja|  
|--------------|--------------------|  
|Tryb wypełniania kolumny Użyj do wyświetlania mieć podobny rozmiar danych w stosunkowo małej liczby kolumn, które zajmują całą szerokość kontrolki bez wyświetlania poziomego paska przewijania.|Ustaw <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> właściwość <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>.|  
|Tryb wypełniania kolumny użycia za pomocą wyświetlania wartości o różnych rozmiarach.|Ustaw <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> właściwość <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Inicjowanie szerokości kolumn względną, ustawiając kolumnę <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> właściwości lub przez wywołanie formantu <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> metody wypełnianie kontrolki z danymi.|  
|Tryb wypełniania kolumny za pomocą wartości różnej znaczenie.|Ustaw <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> właściwość <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Wartość large <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> wartości dla kolumny, które muszą zawsze wyświetlić ich dane lub użyć innych niż opcję zmiany rozmiaru wypełnienia tryb określone kolumny.|  
|Tryb wypełniania kolumny umożliwia zapobiec wyświetlaniu tła formantu.|Ustaw <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> właściwości ostatniej kolumny do <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> i użyć innych opcji rozmiaru dla pozostałych kolumn. Użycie innych kolumn zbyt dużej ilości dostępnego miejsca, ustaw <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> właściwości ostatniej kolumnie.|  
|Wyświetl kolumnę o stałej szerokości, takich jak ikony lub kolumna Identyfikatora.|Ustaw <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> do <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> i <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> do <xref:System.Windows.Forms.DataGridViewTriState.False> dla kolumny. Zainicjuj jego szerokość, ustawiając <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> właściwości lub przez wywołanie formantu <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> metody wypełnianie kontrolki z danymi.|  
|Automatycznie Dostosuj rozmiary po każdym wprowadzeniu zmiany zawartości komórki, należy unikać przycinania i zoptymalizować wykorzystanie miejsca.|Ustaw właściwość automatycznej zmiany rozmiaru na wartość, która reprezentuje tryb ustalania rozmiaru na podstawie zawartości. Aby uniknąć spadek wydajności, podczas pracy z dużymi ilościami danych, użyj tryb zmiany rozmiaru, który oblicza wyświetlane tylko wiersze.|  
|Dopasowywanie rozmiarów do określonych wartości w wierszach wyświetlanych, aby uniknąć spadku wydajności podczas pracy z wielu wierszy.|Za pomocą wartości odpowiednich wyliczenia tryb zmiany rozmiaru automatycznego lub programowy rozmiaru. Aby dostosować rozmiarów do określonych wartości w wierszach nowo wyświetlanego podczas przewijania, wywołaj metodę zmiany rozmiaru w <xref:System.Windows.Forms.DataGridView.Scroll> programu obsługi zdarzeń. Aby dostosować kliknij dwukrotnie użytkownika zmiany rozmiaru tak, aby tylko wartości w wierszach wyświetlanych określają nowe rozmiary Wywołaj zmiany rozmiaru metodę w <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> lub <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick> programu obsługi zdarzeń.|  
|Dopasowywanie rozmiarów do określonych zawartość komórki tylko w określonych godzinach, aby uniknąć spadku wydajności lub Włącz opcję zmiany rozmiaru użytkownika.|Wywołaj metodę zmiany rozmiaru na podstawie zawartości w obsłudze zdarzeń. Na przykład użyć <xref:System.Windows.Forms.DataGridView.DataBindingComplete> zdarzenie, aby zainicjować rozmiary po powiązaniu i obsłużyć <xref:System.Windows.Forms.DataGridView.CellValidated> lub <xref:System.Windows.Forms.DataGridView.CellValueChanged> zdarzenie, aby dopasować rozmiary pokrycie użytkownik dokona edycji lub zmiany w źródle powiązane dane.|  
|Dopasuj wysokość wierszy dla zawartości komórki wielowierszowe.|Upewnij się, że szerokości kolumn są odpowiednie do wyświetlania akapitów tekstu i umożliwia dostosowanie wysokości rozmiaru automatycznego lub programowy wierszy na podstawie zawartości. Upewnij się również wyświetlana z zawartością wielowierszowy przy użyciu <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> komórki wartość stylu <xref:System.Windows.Forms.DataGridViewTriState.True>.<br /><br /> Zazwyczaj użyje tryb zmiany rozmiaru kolumn do obsługiwania szerokości kolumn i ustaw je na określonej szerokości, zanim zostaną dopasowane wysokości wierszy.|  
  
## <a name="resizing-with-the-mouse"></a>Zmiana rozmiaru za pomocą myszy  
 Domyślnie użytkownicy mogą zmieniać rozmiar wiersze, kolumny i nagłówki, które nie korzystają z Tryb automatycznej zmiany rozmiaru na podstawie wartości komórek. Aby uniemożliwić użytkownikom zmianę rozmiaru za pomocą innych metod, takich jak tryb wypełniania kolumny, ustawić jedną lub więcej z następujących <xref:System.Windows.Forms.DataGridView> właściwości:  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 Użytkownik może również uniemożliwić użytkownikom zmiany rozmiaru poszczególnych wierszy lub kolumn, ustawiając ich <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> właściwości. Domyślnie <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> wartość właściwości jest oparta na <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> wartości właściwości dla kolumn i <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> wartości właściwości dla wierszy. Jeśli jawnie ustawić <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> do <xref:System.Windows.Forms.DataGridViewTriState.True> lub <xref:System.Windows.Forms.DataGridViewTriState.False>, jednak zastąpienia określonej wartości, wartość kontrolki jest dla tego wiersza lub kolumny. Ustaw <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> do <xref:System.Windows.Forms.DataGridViewTriState.NotSet> do przywrócenia dziedziczenia.  
  
 Ponieważ <xref:System.Windows.Forms.DataGridViewTriState.NotSet> przywraca dziedziczenie wartości <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> właściwość nigdy nie będzie zwracać <xref:System.Windows.Forms.DataGridViewTriState.NotSet> wartości, chyba że wiersza lub kolumny nie został dodany do <xref:System.Windows.Forms.DataGridView> kontroli. Jeśli zachodzi potrzeba określenia czy <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> wartość właściwości wiersza lub kolumny jest dziedziczone, sprawdź jego <xref:System.Windows.Forms.DataGridViewElement.State%2A> właściwości. Jeśli <xref:System.Windows.Forms.DataGridViewElement.State%2A> wartość obejmuje <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet> flagi <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> wartość właściwości nie jest dziedziczony.  
  
## <a name="automatic-sizing"></a>Automatycznej zmiany rozmiaru  
 Istnieją dwa rodzaje automatycznej zmiany rozmiaru w <xref:System.Windows.Forms.DataGridView> kontroli: tryb wypełniania kolumny i na podstawie zawartości automatycznej zmiany rozmiaru.  
  
 Tryb wypełniania kolumny powoduje, że widocznych kolumn w formancie do wypełnienia szerokości obszaru wyświetlania kontrolki. Aby uzyskać więcej informacji na temat tego trybu, zobacz [trybu wypełnienia kolumn w formancie DataGridView formularzy Windows](column-fill-mode-in-the-windows-forms-datagridview-control.md).  
  
 Można również skonfigurować wiersze, kolumny i nagłówki, aby automatycznie dopasowywać ich rozmiary, do ich zawartości komórki. W tym przypadku sposób korekty rozmiaru występuje po każdym wprowadzeniu zmiany zawartości komórki.  
  
> [!NOTE]
>  Jeśli zachować wartości komórek w pamięci podręcznej danych niestandardowych przy użyciu wirtualny Tryb automatycznej zmiany rozmiaru występuje, gdy użytkownik edytuje wartość komórki, ale nie występuje, gdy zmienia wartość w pamięci podręcznej poza <xref:System.Windows.Forms.DataGridView.CellValuePushed> programu obsługi zdarzeń. W takim przypadku wywołania <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> metodę wymuszania kontroli, aby zaktualizować wyświetlane komórki i zastosować bieżące tryby automatycznej zmiany rozmiaru.  
  
 Po włączeniu automatycznej zmiany rozmiaru na podstawie zawartości dla tylko jednego wymiaru —, jest, dla wierszy, ale nie kolumny lub kolumn, ale nie wiersze — i <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> jest również włączone, rozmiar dopasowania występuje także w każdym przypadku, gdy zmieni się innego wymiaru. Na przykład, jeśli wierszy, ale nie kolumny, które są skonfigurowane dla automatycznej zmiany rozmiaru i <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> jest włączona, użytkownicy mogą przeciągnij separator kolumn, aby zmienić szerokość kolumny i wysokość wierszy spowoduje automatyczne dopasowanie w celu wyświetlenia zawartości komórki są nadal w pełni.  
  
 Jeśli skonfigurujesz wierszy i kolumn do automatycznej zmiany rozmiaru na podstawie zawartości i <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> jest włączona, <xref:System.Windows.Forms.DataGridView> kontroli skoryguje rozmiarów, za każdym razem zawartość komórki zmienione i będzie używać współczynnika wysokości szerokości idealne komórek podczas obliczania nowe rozmiary.  
  
 Aby skonfigurować tryb zmiany rozmiaru, nagłówki i wiersze i kolumny, które nie zastępują wartości kontrolki, należy ustawić co najmniej jeden z następujących <xref:System.Windows.Forms.DataGridView> właściwości:  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 Aby przesłonić kontrolki tryb zmiany rozmiaru kolumn dla poszczególnych kolumn, ustaw jego <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> właściwości na wartość inną niż <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>. Tryb zmiany rozmiaru kolumny faktycznie jest określana przez jego <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> właściwości. Wartość tej właściwości zależy od kolumny <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> wartość właściwości, chyba że ta wartość jest <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>, w którym to przypadku formantu <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> wartość jest dziedziczona.  
  
 Za pomocą opartego na zawartości automatyczną zmianę rozmiaru ostrożnie podczas pracy z dużymi ilościami danych. Aby uniknąć spadku wydajności, należy użyć tryby automatycznej zmiany rozmiaru, które obliczenia rozmiarów, oparte tylko na wyświetlanych wierszy, a nie analizowanie każdego wiersza w formancie. Aby osiągnąć najwyższą wydajność Użyj programowe zmiany rozmiaru zamiast tego, aby rozmiar można zmieniać w określonym czasie, takie jak natychmiast po nowe dane są ładowane.  
  
 Tryby automatycznej zmiany rozmiaru na podstawie zawartości nie wpływają na wiersze, kolumny lub wiersze nagłówków, które zostały ukryte, ustawiając wiersz lub kolumnę <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> właściwości lub kontrolki <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> lub <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> właściwości `false`. Na przykład jeśli kolumna jest ukryta, po jego jest automatycznie dopasowywany do dopasowania wartości komórki dużych, ukryta kolumna nie zmieni jego rozmiar usunięcie wiersz zawierający wartość komórki dużych. Automatycznej zmiany rozmiaru nie występuje po zmianie widoczności, więc zmiana kolumny <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> właściwości z powrotem do `true` nie wymusi jej ponownie obliczyć jego rozmiar, w oparciu o jego zawartość.  
  
 Programowy rozmiaru na podstawie zawartości ma wpływ wiersze, kolumny i nagłówków, niezależnie od ich widoczności.  
  
## <a name="programmatic-resizing"></a>Programowe zmienianie rozmiaru  
 Po wyłączeniu automatycznej zmiany rozmiaru programowo ustawić dokładnie szerokość lub wysokość wierszy, kolumny lub wiersze nagłówków za pośrednictwem następujących właściwości:  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 Możesz też programowo zmienić rozmiar wiersze, kolumny i nagłówków w celu dopasowania do ich zawartości przy użyciu następujących metod:  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 Tych metod będzie rozmiar wierszy, kolumny lub nagłówki raz zamiast konfigurowania ich do zmiany rozmiaru ciągłe. Nowe rozmiary są automatycznie obliczane, aby wyświetlić całą zawartość komórki bez przycinania. Podczas programowego zmiany rozmiaru kolumn, które mają <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> wartości właściwości <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>, jednak obliczeniowe szerokości na podstawie zawartości są używane do proporcjonalnie dopasować kolumny <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości właściwości i szerokości kolumn faktycznie następnie obliczana te nowe proporcje tak, aby wszystkie kolumny wypełnienia obszaru wyświetlania dostępne kontrolki.  
  
 Programowe zmienianie rozmiaru jest przydatna, aby uniknąć spadku wydajności o zmienionych rozmiarach ciągłe. Jest to również przydatne w celu zapewnienia początkowe rozmiary o zmiennym rozmiarze użytkownika wiersze, kolumny i nagłówki i tryb wypełniania kolumny.  
  
 Zazwyczaj wywoła metody zmiany rozmiaru programistyczne w określonym czasie. Na przykład może programowo rozmiar wszystkich kolumn od razu po załadowaniu danych lub może programowo zmiany rozmiaru określonego wiersza po zmodyfikowaniu wartości określonego komórki.  
  
## <a name="customizing-content-based-sizing-behavior"></a>Dostosowywanie zachowania dotyczącego ustalania rozmiaru na podstawie zawartości  
 Można dostosować rozmiaru zachowania podczas pracy z pochodnych <xref:System.Windows.Forms.DataGridView> komórek, wierszy i kolumn typów poprzez zastąpienie <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>, lub <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType> metody lub przez wywołanie metody chronione zmiany rozmiaru przeciążenia metody w pochodnej <xref:System.Windows.Forms.DataGridView> formant. Chronione zmiany rozmiaru przeciążenia metody zostały zaprojektowane do pracy w parach, aby osiągnąć Współczynnik wysokości szerokości idealne komórki, unikając nadmiernie szerokość lub wysokość komórki. Na przykład, jeśli wywołasz `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` przeciążenia <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> metody i przekazać wartość `false` dla <xref:System.Boolean> parametru przeciążenia obliczy idealne wysokości i szerokości dla komórki w wierszu, ale będzie go dostosować wysokość wierszy tylko. Następnie należy wywołać <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> metodę, aby dostosować szerokości kolumn do obliczeniową idealne rozwiązanie.  
  
## <a name="content-based-sizing-options"></a>Opcje ustalania rozmiaru na podstawie zawartości  
 Wyliczenia używane przez właściwości ustalania rozmiaru i metody mają podobne wartości do ustalania rozmiaru na podstawie zawartości. Te wartości można ograniczyć komórki, które są używane do obliczania preferowany rozmiar. Dla wszystkich rozmiarów wyliczenia wartości z nazwami, które odwołują się do komórek w kolumnie wyświetlane ograniczyć ich obliczeń do komórek w wyświetlanych wierszach. Wykluczanie wierszy jest przydatna, aby uniknąć spadek wydajności, podczas pracy z dużą liczbę wierszy. Można również ograniczyć obliczeń do wartości komórek w nagłówku lub zawierająca komórek.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [Zmiana rozmiaru wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Tryb wypełniania kolumn w kontrolce DataGridView formularzy Windows Forms](column-fill-mode-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Ustawianie trybów zmieniania rozmiaru kontrolki DataGridView formularzy Windows Forms](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
