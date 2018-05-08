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
ms.openlocfilehash: 6e3a7786970ef536da4ef7628cd33ae067ba90be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Opcje ustalania rozmiaru w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> wiersze, kolumny i nagłówki, można zmienić rozmiar wiele różnych wystąpień. W poniższej tabeli przedstawiono te wystąpienia.  
  
|Wystąpienie|Opis|  
|----------------|-----------------|  
|Zmiana rozmiaru użytkownika|Użytkowników można dostosować rozmiar przeciągając lub dwukrotnie separator wierszy, kolumny lub nagłówek.|  
|Zmiana rozmiaru formantu|W tryb wypełniania kolumny Zmień zmienia szerokość formantu; szerokości kolumn na przykład, gdy formant jest zadokowany jej formularz nadrzędny i użytkownikowi zmienia rozmiar formularza.|  
|Zmiany wartości komórki|W trybach na podstawie zawartości automatycznej zmiany rozmiaru rozmiary zmienić mieści się nowe wartości wyświetlania.|  
|Wywołanie metody|Na podstawie zawartości programowy rozmiaru pozwala dostosować rozmiar oportunistyczne oparte na wartości komórek w momencie wywołania metody.|  
|Ustawienie właściwości|Można również ustawić wartości szerokości i wysokości.|  
  
 Domyślnie zmiana rozmiaru użytkownika jest włączona, wyłączeniu automatycznej zmiany rozmiaru i powoduje wartości komórek, które są większe niż ich kolumn.  
  
 W poniższej tabeli przedstawiono scenariusze, w której można dostosować zachowanie domyślne lub uzyskać efekty określonego za pomocą opcji określonego rozmiaru.  
  
|Scenariusz|Implementacja|  
|--------------|--------------------|  
|Tryb wypełniania kolumny używana do wyświetlania podobnie wielkości danych w stosunkowo małej liczby kolumn, które zajmują cały szerokość formantu bez wyświetlania poziomego paska przewijania.|Ustaw <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>.|  
|Tryb wypełniania kolumny używana z wyświetlania wartości o różnych rozmiarach.|Ustaw <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Inicjowanie szerokość kolumny przez ustawienie kolumny <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> właściwości lub poprzez wywołanie formantu <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> metody po wypełnieniu formantu z danymi.|  
|Tryb wypełniania kolumny za pomocą wartości różnych znaczenie.|Ustaw <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Ustaw dużych <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> wartości kolumn, które musi zawsze wyświetlić niektórych ich danych lub użyj opcji zmiany rozmiaru innych niż wypełnienia tryb dla określonej kolumny.|  
|Użyj tryb wypełniania kolumny, aby zapobiec wyświetlaniu tła formantu.|Ustaw <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> właściwości ostatniej kolumny do <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> i inne opcje rozmiaru innych kolumn. Użycie innych kolumn zbyt dużą ilość dostępnego miejsca, ustaw <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> właściwości ostatniej kolumny.|  
|Wyświetl kolumnę o stałej szerokości, takich jak ikony lub identyfikator kolumny.|Ustaw <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> do <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> i <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> do <xref:System.Windows.Forms.DataGridViewTriState.False> dla kolumny. Zainicjowanie przez ustawienie szerokości <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> właściwości lub poprzez wywołanie formantu <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> metody po wypełnieniu formantu z danymi.|  
|Automatycznie Dostosuj rozmiary zmianie zawartości komórki, aby uniknąć wycinka i optymalizację wykorzystania miejsca.|Ustaw właściwość automatycznej zmiany rozmiaru na wartość, która reprezentuje tryb na podstawie zawartości zmiany rozmiaru. Aby uniknąć spadek wydajności podczas pracy z dużą ilością danych, użyj tryb ustalania, który oblicza tylko wyświetlanych wierszy.|  
|Dostosuj rozmiary, aby dopasować wartości w wierszach wyświetlanych, aby uniknąć spadku wydajności podczas pracy z wielu wierszy.|Za pomocą wartości wyliczenia tryb ustalania odpowiednie automatyczne lub programowe zmiany rozmiaru. Aby dostosować rozmiary, aby dopasować wartości w nowo wyświetlanych wierszy podczas przewijania, należy wywołać metodę zmiany rozmiaru <xref:System.Windows.Forms.DataGridView.Scroll> obsługi zdarzeń. Aby dostosować kliknij dwukrotnie użytkownika Zmiana rozmiaru, dzięki czemu tylko wartości w wierszach wyświetlanych określić nowe rozmiary wywołania zmiany rozmiaru metody <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> lub <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick> obsługi zdarzeń.|  
|Dopasuj rozmiar do zawartości komórki tylko w określonym czasie, aby uniknąć kar za wydajności lub aby umożliwić zmianę rozmiaru użytkownika.|Wywołanie metody zmiany rozmiaru na podstawie zawartości w obsłudze zdarzeń. Na przykład użyć <xref:System.Windows.Forms.DataGridView.DataBindingComplete> zdarzenie, aby zainicjować rozmiary po powiązaniu i obsługiwać <xref:System.Windows.Forms.DataGridView.CellValidated> lub <xref:System.Windows.Forms.DataGridView.CellValueChanged> zdarzenie, aby dopasować rozmiary pokrycie użytkownika lub zmiany w źródle powiązania danych.|  
|Należy dostosować wysokość wierszy dla zawartości komórki wielowierszowy.|Upewnij się, że szerokości kolumn są odpowiednie do wyświetlania akapitów tekstu i Użyj rozmiaru automatyczne lub programowe na podstawie zawartości wiersza, aby dopasować wysokości. Upewnij się również z zawartością wielowierszowy są wyświetlane, przy użyciu <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> wartości stylu komórki <xref:System.Windows.Forms.DataGridViewTriState.True>.<br /><br /> Zazwyczaj użyje tryb zmiany rozmiaru kolumn do obsługi szerokości kolumn lub ustawienie dla nich wartości określonej szerokości przed wysokości wierszy zostaną skorygowane.|  
  
## <a name="resizing-with-the-mouse"></a>Zmiana rozmiaru przy użyciu myszy  
 Domyślnie użytkownicy mogą zmieniać rozmiar wierszy, kolumny i nagłówki, które nie używają Tryb automatycznej zmiany rozmiaru, na podstawie wartości komórki. Aby uniemożliwić użytkownikom zmienianie rozmiaru w trybach innych, takie jak tryb wypełniania kolumny, ustawić co najmniej jeden z następujących <xref:System.Windows.Forms.DataGridView> właściwości:  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 Możesz również uniemożliwia użytkownikom zmienianie rozmiaru poszczególnych wierszy lub kolumn, ustawiając ich <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> właściwości. Domyślnie <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> wartość właściwości jest oparta na <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> wartości właściwości dla kolumn i <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> wartości właściwości dla wierszy. Jeśli jawnie ustawiona <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> do <xref:System.Windows.Forms.DataGridViewTriState.True> lub <xref:System.Windows.Forms.DataGridViewTriState.False>, jednak zastąpienia określona wartość formantu jest dla tego wiersza lub kolumny. Ustaw <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> do <xref:System.Windows.Forms.DataGridViewTriState.NotSet> do przywrócenia dziedziczenia.  
  
 Ponieważ <xref:System.Windows.Forms.DataGridViewTriState.NotSet> przywraca dziedziczenia wartość <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> nigdy nie zwróci właściwości <xref:System.Windows.Forms.DataGridViewTriState.NotSet> wartości, chyba że wiersz lub kolumnę, nie został dodany do <xref:System.Windows.Forms.DataGridView> formantu. Jeśli chcesz określić, czy <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> jest dziedziczona wartość właściwości wiersz lub kolumnę, sprawdź jego <xref:System.Windows.Forms.DataGridViewElement.State%2A> właściwości. Jeśli <xref:System.Windows.Forms.DataGridViewElement.State%2A> wartość obejmuje <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet> flagę <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> nie dziedziczy wartości właściwości.  
  
## <a name="automatic-sizing"></a>Rozmiar automatyczny  
 Istnieją dwa rodzaje automatycznej zmiany rozmiaru w <xref:System.Windows.Forms.DataGridView> kontroli: tryb wypełniania kolumny i na podstawie zawartości automatycznej zmiany rozmiaru.  
  
 Tryb wypełniania kolumny powoduje, że widocznych kolumn w formancie, aby wypełnić obszar wyświetlania formantu. Aby uzyskać więcej informacji na temat ten tryb, zobacz [trybu wypełnienia kolumn w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md).  
  
 Można również skonfigurować wiersze, kolumny i nagłówków, aby automatycznie dopasowywać ich rozmiary, do ich zawartości komórki. W takim przypadku dostosowanie rozmiaru występuje, gdy zawartość komórki zmienia się.  
  
> [!NOTE]
>  Jeśli zachowasz wartości komórek w pamięci podręcznej danych niestandardowych wirtualnego w trybie automatycznej zmiany rozmiaru występuje, gdy użytkownik edytuje wartość komórki, ale nie występuje, gdy zmienia wartość w pamięci podręcznej poza <xref:System.Windows.Forms.DataGridView.CellValuePushed> obsługi zdarzeń. W takim przypadku wywołania <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> metodę wymuszania sterowania, aby zaktualizować wyświetlane komórki i zastosować bieżący tryb automatycznej zmiany rozmiaru.  
  
 Jeśli na podstawie zawartości automatycznej zmiany rozmiaru jest włączona tylko jeden wymiar — który jest wierszy, ale nie kolumny lub kolumn, ale nie wierszy — i <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> również jest włączone, rozmiar korekty również występuje przy każdej zmianie innego wymiaru. Na przykład, jeśli wierszy, ale kolumn nie są skonfigurowane do automatycznej zmiany rozmiaru i <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> jest włączona, użytkownicy będą mogli przeciągać separatorów kolumny, aby zmienić szerokość kolumny i wysokość wierszy spowoduje automatyczne dopasowanie w celu wyświetlenia zawartości komórki nadal pełni.  
  
 Jeśli skonfigurujesz wierszy i kolumn na podstawie zawartości automatycznej zmiany rozmiaru i <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> jest włączona, <xref:System.Windows.Forms.DataGridView> kontroli dopasuje rozmiary zawsze, gdy zawartość komórki zmienione i użyje stosunek wysokości do szerokości komórki idealne podczas obliczania nowe rozmiary.  
  
 Aby skonfigurować tryb zmiany rozmiaru w nagłówkach i wierszy i kolumn, które nie zastępują wartości formantu, należy ustawić co najmniej jeden z następujących <xref:System.Windows.Forms.DataGridView> właściwości:  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 Aby zastąpić tryb zmiany rozmiaru kolumn formantu dla pojedynczej kolumny, ustaw jej <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> właściwości na wartość inną niż <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>. Tryb zmiany rozmiaru kolumny jest ustalany przez jego <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> właściwości. Wartość tej właściwości jest oparta na kolumnie <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> wartość właściwości, chyba że ta wartość jest <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>, w którym to przypadku formantu <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> wartość jest dziedziczona.  
  
 Użyj na podstawie zawartości automatyczną zmianę rozmiaru ostrożność podczas pracy z dużą ilością danych. Aby uniknąć spadku wydajności, należy użyć obliczenia rozmiary oparty tylko na wyświetlanych wierszy zamiast analizowanie każdego wiersza w formancie tryby automatycznej zmiany rozmiaru. Aby zwiększyć wydajność Użyj programowe zmiany rozmiaru zamiast tego, aby można zmienić rozmiar w określonym czasie, takie jak od razu po nowych danych została załadowana.  
  
 Tryby na podstawie zawartości automatycznej zmiany rozmiaru nie wpływają na wiersze, kolumny lub nagłówki, które zostały ukryte przez ustawienie wiersz lub kolumnę <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> właściwości lub formantu <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> lub <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> właściwości `false`. Na przykład jeśli kolumna jest ukryty po jego jest automatycznie dopasowywany do dopasowania wartości komórki dużych, ukryte kolumny nie spowoduje zmiany rozmiaru usunięcie wiersz zawierający wartość komórki duże. Rozmiar automatyczny nie występuje po zmianie widoczności, więc zmiana kolumny <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> właściwości z powrotem do `true` nie zostanie wymuszone jego ponownego obliczenia rozmiaru oparte na jego zawartość.  
  
 Programowe na podstawie zawartości zmiana rozmiaru ma wpływ wiersze, kolumny i nagłówków, niezależnie od ich widoczności.  
  
## <a name="programmatic-resizing"></a>Zmiana rozmiaru programowe  
 Po wyłączeniu automatycznej zmiany rozmiaru, można programowo ustawić dokładną szerokość lub wysokość wierszy, kolumny lub nagłówki za pomocą następujących właściwości:  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 Możesz również programowo zmienić rozmiar wierszy, kolumny i nagłówki do ich zawartości przy użyciu następujących metod:  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 Te metody zmieni się rozmiar wierszy i kolumn, lub raz nagłówki zamiast ich konfiguracji do zmiany rozmiaru ciągłe. Nowe rozmiary są automatycznie obliczane, aby wyświetlić całą zawartość komórki bez przycinania. Gdy programowo zmieniany jest rozmiar kolumn, które mają <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> wartości właściwości <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>, jednak obliczeniowej szerokości na podstawie zawartości są używane do proporcjonalnie Dostosuj kolumny <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości właściwości i szerokości kolumn faktycznie następnie obliczane na podstawie tych nowych proporcje tak, aby wszystkie kolumny wypełnienia obszaru wyświetlania dostępnych formantu.  
  
 Programowy rozmiaru jest przydatne w celu uniknięcia spadku wydajności z ciągłe Zmienianie rozmiaru. Warto również podać początkowe rozmiary o zmiennym rozmiarze użytkownika wiersze, kolumny i nagłówki i tryb wypełniania kolumny.  
  
 Zwykle wywoła metod programistycznych zmiany rozmiaru w określonym czasie. Na przykład może być programowane Dopasuj rozmiar wszystkich kolumn, natychmiast po podczas ładowania danych lub może być programowane zmiany rozmiaru określonego wiersza po wartość określonej komórki została zmodyfikowana.  
  
## <a name="customizing-content-based-sizing-behavior"></a>Dostosowywanie zachowania rozmiaru na podstawie zawartości  
 Można dostosować zachowania wielkości podczas pracy z pochodne <xref:System.Windows.Forms.DataGridView> typy komórek, wierszy i kolumn przez zastąpienie <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>, lub <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType> metody lub poprzez wywołanie chronione zmiany rozmiaru przeciążenia metody w pochodnym <xref:System.Windows.Forms.DataGridView> formant. Chronionych zmiany rozmiaru przeciążenia metody są przeznaczone do pracy parami osiągnąć Współczynnik wysokości do szerokości idealne komórki, unikając zbyt szerokość lub wysokość komórki. Na przykład, jeśli wywołujesz `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` przeciążenia z <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> — metoda i przekazać wartość `false` dla <xref:System.Boolean> parametru przeciążenia obliczy idealne wysokości i szerokości dla komórki w wierszu, ale będzie dostosować wysokość wierszy tylko. Następnie należy wywołać <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> metodę, aby dostosować szerokości kolumn do idealnym obliczeniowej.  
  
## <a name="content-based-sizing-options"></a>Opcje rozmiaru na podstawie zawartości  
 Wyliczenia używane przez zmiany rozmiaru właściwości i metody mają podobne wartości na podstawie zawartości zmiany rozmiaru. Te wartości można ograniczyć komórek, które są używane do obliczania preferowany rozmiar. Dla wszystkich wyliczenia zmiany rozmiaru wartości za pomocą nazw, które odwołują się do komórek wyświetlanych ograniczyć ich obliczeń do komórek w wyświetlanych wierszy. Z wyjątkiem wierszy jest przydatne w celu uniknięcia spadek wydajności podczas pracy z dużą liczbę wierszy. Można również ograniczyć obliczeń do wartości komórek w nagłówku lub zawierająca komórek.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>  
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>  
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>  
 [Zmiana rozmiaru wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 [Tryb wypełniania kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 [Instrukcje: ustawianie trybów zmieniania rozmiaru kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
