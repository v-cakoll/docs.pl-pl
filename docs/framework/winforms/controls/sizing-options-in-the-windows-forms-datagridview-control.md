---
title: Opcje ustalania wielkości w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sizing
- data grids [Windows Forms], column sizing
- DataGridView control [Windows Forms], column sizing
- DataGridView control [Windows Forms], sizing options
- data grids [Windows Forms], row sizing
- data grids [Windows Forms], sizing options
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
ms.openlocfilehash: bf1be699a18608bb452bd9fb98cbca1e99f7a9e4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742984"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Opcje ustalania rozmiaru w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> wiersze, kolumny i nagłówki mogą zmieniać rozmiar w wyniku wielu różnych wystąpień. W poniższej tabeli przedstawiono te wystąpienia.  
  
|Jego|Opis|  
|----------------|-----------------|  
|Zmiana rozmiaru użytkownika|Użytkownicy mogą wprowadzać korekty rozmiaru przez przeciąganie lub dwukrotne kliknięcie wierszy, kolumn lub separatorów nagłówków.|  
|Zmień rozmiar kontrolki|W trybie wypełniania kolumn szerokości kolumn zmieniają się, gdy zmieni się szerokość kontrolki; na przykład gdy formant jest zadokowany do jego formularza nadrzędnego, a użytkownik zmienia rozmiar formularza.|  
|Zmiana wartości komórki|W przypadku trybów automatycznego ustalania rozmiaru na podstawie zawartości rozmiary zmieniają się w celu dopasowania do nowych wartości wyświetlania.|  
|Wywołanie metody|Programistyczna zmiana rozmiaru oparta na zawartości umożliwia wykonywanie korekt rozmiaru oportunistycznego na podstawie wartości komórek w czasie wywołania metody.|  
|Ustawienie właściwości|Można również ustawić określone wartości wysokości i szerokości.|  
  
 Domyślnie zmiany rozmiarów użytkownika są włączone, automatyczne ustalanie rozmiarów jest wyłączone, a wartości komórek, które są szersze niż ich kolumny, są przycinane.  
  
 W poniższej tabeli przedstawiono scenariusze, których można użyć do dostosowania zachowania domyślnego lub zastosowania określonych opcji ustalania rozmiarów w celu uzyskania określonych efektów.  
  
|Scenariusz|Implementacja|  
|--------------|--------------------|  
|Użyj trybu wypełnienia kolumn do wyświetlania danych o podobnym rozmiarze w stosunkowo niewielkiej liczbie kolumn, które zajmują całą szerokość formantu bez wyświetlania poziomego paska przewijania.|Ustaw właściwość <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> na <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>.|  
|Użyj trybu wypełniania kolumn z wartościami wyświetlanymi różnych rozmiarów.|Ustaw właściwość <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> na <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Zainicjuj względne szerokości kolumn przez ustawienie kolumny <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> właściwości lub przez wywołanie metody <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> kontrolki po wypełnieniu kontrolki danymi.|  
|Użyj trybu wypełnienia kolumny z wartościami o różnej ważności.|Ustaw właściwość <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> na <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Ustaw duże wartości <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> dla kolumn, które muszą zawsze wyświetlać niektóre z ich danych lub użyć opcji ustalania wielkości innej niż tryb wypełnienia dla określonych kolumn.|  
|Użyj trybu wypełnienia kolumny, aby uniknąć wyświetlania tła formantu.|Ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> ostatniej kolumny na <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> i użyj innych opcji ustalania rozmiarów dla innych kolumn. Jeśli inne kolumny używają zbyt dużej ilości dostępnego miejsca, ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> ostatniej kolumny.|  
|Wyświetlanie kolumny o stałej szerokości, takiej jak ikona lub kolumna identyfikatora.|Ustaw <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> na <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> i <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> na <xref:System.Windows.Forms.DataGridViewTriState.False> dla kolumny. Zainicjuj jego szerokość, ustawiając właściwość <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> lub wywołując metodę <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> formantu po wypełnieniu kontrolki danymi.|  
|Automatycznie dostosowuj rozmiary przy każdej zmianie zawartości komórki, aby uniknąć przycinania i zoptymalizować użycie miejsca.|Ustaw właściwość automatycznej zmiany wartości na wartość reprezentującą tryb ustalania wielkości na podstawie zawartości. Aby uniknąć spadek wydajności podczas pracy z dużymi ilościami danych, należy użyć trybu ustalania rozmiarów, który oblicza tylko wyświetlane wiersze.|  
|Dopasuj rozmiary, dopasowując wartości w wyświetlanych wierszach, aby uniknąć wydajności podczas pracy z wieloma wierszami.|Użyj odpowiednich wartości wyliczenia w trybie zmiany wielkości z automatyczną lub programistyczną zmianą rozmiarów. Aby dostosować rozmiary w celu dopasowania do wartości w nowo wyświetlanych wierszach podczas przewijania, wywołaj metodę zmiany rozmiaru w programie obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.Scroll>. Aby dostosować, kliknij dwukrotnie zmianę rozmiaru przez użytkownika, aby tylko wartości w wyświetlanych wierszach były określane jako nowe rozmiary, wywołaj metodę zmiany rozmiaru w <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> lub <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick> obsłudze zdarzeń.|  
|Dostosuj rozmiary, aby dopasować zawartość komórki tylko w określonych godzinach, aby uniknąć kar za wydajność lub umożliwić zmianę rozmiaru użytkownika.|Wywoływanie metody zmiany wielkości na podstawie zawartości w programie obsługi zdarzeń. Na przykład użyj zdarzenia <xref:System.Windows.Forms.DataGridView.DataBindingComplete>, aby zainicjować rozmiary po powiązaniu i obsłużyć zdarzenie <xref:System.Windows.Forms.DataGridView.CellValidated> lub <xref:System.Windows.Forms.DataGridView.CellValueChanged>, aby dostosować rozmiary, aby zrekompensować modyfikacje lub zmiany użytkowników w powiązanym źródle danych.|  
|Dopasuj wysokość wierszy w przypadku zawartości komórki wielowierszowej.|Upewnij się, że szerokości kolumn są odpowiednie do wyświetlania akapitów tekstu i Użyj automatycznej lub programowanej szerokości wierszy w celu dostosowania wysokości. Upewnij się również, że komórki z zawartością wielowierszową są wyświetlane przy użyciu <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> wartości stylu komórki <xref:System.Windows.Forms.DataGridViewTriState.True>.<br /><br /> Zwykle tryb automatycznego ustalania szerokości kolumny jest używany do zachowywania szerokooci kolumn lub ustawiania określonych szerokości przed dopasowaniem wysokości wierszy.|  
  
## <a name="resizing-with-the-mouse"></a>Zmienianie rozmiarów przy użyciu myszy  
 Domyślnie użytkownicy mogą zmieniać rozmiar wierszy, kolumn i nagłówków, które nie używają trybu automatycznego ustalania rozmiaru na podstawie wartości komórek. Aby uniemożliwić użytkownikom zmianę rozmiarów z innymi trybami, takimi jak tryb wypełniania kolumn, ustaw co najmniej jedną z następujących właściwości <xref:System.Windows.Forms.DataGridView>:  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 Możesz również uniemożliwić użytkownikom zmianę rozmiarów poszczególnych wierszy lub kolumn, ustawiając ich <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> właściwości. Domyślnie wartość właściwości <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> jest oparta na wartości właściwości <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> dla kolumn i wartości właściwości <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> dla wierszy. Jeśli jawnie ustawisz <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> na <xref:System.Windows.Forms.DataGridViewTriState.True> lub <xref:System.Windows.Forms.DataGridViewTriState.False>, określona wartość zastępuje wartość kontrolki dla tego wiersza lub kolumny. Ustaw <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> na <xref:System.Windows.Forms.DataGridViewTriState.NotSet>, aby przywrócić dziedziczenie.  
  
 Ponieważ <xref:System.Windows.Forms.DataGridViewTriState.NotSet> przywraca dziedziczenie wartości, właściwość <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> nigdy nie zwróci wartości <xref:System.Windows.Forms.DataGridViewTriState.NotSet>, chyba że wiersz ani kolumna nie zostały dodane do kontrolki <xref:System.Windows.Forms.DataGridView>. Jeśli musisz określić, czy <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> wartość właściwości wiersza lub kolumny jest dziedziczona, sprawdź jej Właściwość <xref:System.Windows.Forms.DataGridViewElement.State%2A>. Jeśli wartość <xref:System.Windows.Forms.DataGridViewElement.State%2A> zawiera flagę <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>, wartość właściwości <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> nie jest dziedziczona.  
  
## <a name="automatic-sizing"></a>Automatyczne ustalanie rozmiarów  
 Istnieją dwa rodzaje automatycznego ustalania rozmiarów w kontrolce <xref:System.Windows.Forms.DataGridView>: tryb wypełnienia kolumny i automatyczne ustalanie rozmiarów na podstawie zawartości.  
  
 Tryb wypełniania kolumn powoduje, że widoczne kolumny w kontrolce wypełniają szerokość obszaru wyświetlania kontrolki. Aby uzyskać więcej informacji na temat tego trybu, zobacz [tryb wypełniania kolumn w kontrolce DataGridView Windows Forms](column-fill-mode-in-the-windows-forms-datagridview-control.md).  
  
 Możesz również skonfigurować wiersze, kolumny i nagłówki, aby automatycznie dopasować ich rozmiary do zawartości komórki. W takim przypadku korekta rozmiaru występuje zawsze, gdy zmienia się zawartość komórki.  
  
> [!NOTE]
> Jeśli przechowujesz wartości komórek w niestandardowej pamięci podręcznej danych przy użyciu trybu wirtualnego, automatyczne Określanie rozmiarów występuje, gdy użytkownik edytuje wartość komórki, ale nie występuje w przypadku zmiany wartości buforowanej poza procedurę obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.CellValuePushed>. W takim przypadku Wywołaj metodę <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A>, aby wymusić zaktualizowanie przez formant do wyświetlania komórki i zastosować bieżące tryby automatycznego ustalania rozmiarów.  
  
 Jeśli automatyczne ustalanie rozmiaru opartego na zawartości jest włączone tylko dla jednego wymiaru — to znaczy w przypadku wierszy, ale nie kolumn lub dla kolumn, ale nie wierszy — a <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> jest również włączona, korekta rozmiaru występuje również przy każdym zmianie wymiaru. Jeśli na przykład wiersze, ale nie kolumn są skonfigurowane do automatycznego ustalania rozmiarów, a <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> jest włączona, użytkownicy mogą przeciągać rozdzielacze kolumn w celu zmiany szerokości kolumny i wysokości wierszy automatycznie dostosowuje się, tak aby zawartość komórki była nadal w pełni wyświetlana.  
  
 W przypadku skonfigurowania zarówno wierszy, jak i kolumn dla automatycznego ustalania rozmiaru opartego na zawartości, a <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> jest włączone, kontrolka <xref:System.Windows.Forms.DataGridView> dostosowuje rozmiary za każdym razem, gdy zawartość komórki zostanie zmieniona i będzie używać idealnego stosunku do szerokości komórki podczas obliczania nowych rozmiarów.  
  
 Aby skonfigurować tryb ustalania rozmiarów dla nagłówków i wierszy oraz dla kolumn, które nie przesłaniają wartości kontrolki, należy ustawić co najmniej jedną z następujących właściwości <xref:System.Windows.Forms.DataGridView>:  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 Aby przesłonić tryb ustalania szerokości kolumny dla pojedynczej kolumny, ustaw jej Właściwość <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> na wartość inną niż <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>. Tryb ustalania szerokości kolumny jest określany na podstawie właściwości <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>. Wartość tej właściwości jest określana na podstawie wartości właściwości <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> kolumny, chyba że ta wartość jest <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>. w takim przypadku <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> wartość kontrolki jest dziedziczona.  
  
 Podczas pracy z dużymi ilościami danych korzystaj z funkcji automatycznego zmieniania rozmiarów w oparciu o zawartość. Aby uniknąć kar za wydajność, należy użyć trybów automatycznej zmiany rozmiaru, które obliczają rozmiary na podstawie wyświetlanych wierszy zamiast analizować każdy wiersz w kontrolce. W celu uzyskania maksymalnej wydajności należy zamiast tego użyć programistycznej zmiany rozmiaru, aby można było zmienić rozmiar w określonych godzinach, na przykład natychmiast po załadowaniu nowych danych.  
  
 Tryby automatycznego ustalania rozmiarów oparte na zawartości nie mają wpływu na wiersze, kolumny ani nagłówki, które zostały ukryte przez ustawienie właściwości <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> wiersza lub kolumny albo właściwości <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> formantu lub <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> na `false`. Na przykład jeśli kolumna jest ukryta po automatycznym dopasowaniu rozmiaru w celu dopasowania do dużej wartości komórki, Ukryta kolumna nie zmieni jej rozmiaru, jeśli wiersz zawierający wartość dużej komórki zostanie usunięty. Automatyczne określanie rozmiaru nie występuje, gdy widoczność zmienia się, więc zmiana wartości kolumny <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> z powrotem na `true` nie spowoduje wymuszenia ponownego obliczenia rozmiaru w oparciu o jego bieżącą zawartość.  
  
 Programistyczna zmiana rozmiaru oparta na zawartości ma wpływ na wiersze, kolumny i nagłówki niezależnie od ich widoczności.  
  
## <a name="programmatic-resizing"></a>Programowe zmienianie rozmiarów  
 Gdy automatyczne ustalanie rozmiarów jest wyłączone, można programowo ustawić dokładną szerokość lub wysokość wierszy, kolumn lub nagłówków przez następujące właściwości:  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 Możesz również programowo zmienić rozmiar wierszy, kolumn i nagłówków, aby dopasować ich zawartość przy użyciu następujących metod:  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 Te metody spowodują zmianę rozmiaru wierszy, kolumn lub nagłówków, a nie skonfigurowanie ich do ciągłego zmieniania rozmiaru. Nowe rozmiary są automatycznie obliczane do wyświetlania całej zawartości komórki bez przycinania. Podczas programistycznego zmieniania rozmiaru kolumn, które mają <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> wartości właściwości <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>, obliczone szerokości oparte na zawartości są używane do proporcjonalnie Dostosuj wartości właściwości <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> kolumn, a rzeczywiste szerokości kolumn są następnie obliczane zgodnie z tymi nowymi proporcjami, tak aby wszystkie kolumny wypełniły dostępny obszar wyświetlania formantu.  
  
 Programistyczne zmiany rozmiarów są przydatne, aby uniknąć wydajności z ciągłym zmianą rozmiarów. Warto również zapewnić początkowe rozmiary dla wierszy, kolumn i nagłówków o zmiennym rozmiarze, a także tryb wypełniania kolumn.  
  
 Metody zmiany można przywoływać programistycznie w określony sposób. Na przykład możesz programowo zmienić rozmiar wszystkich kolumn po załadowaniu danych lub można programowo zmienić rozmiar określonego wiersza po zmodyfikowaniu określonej wartości komórki.  
  
## <a name="customizing-content-based-sizing-behavior"></a>Dostosowywanie zachowania zmiany wielkości na podstawie zawartości  
 Można dostosować zachowania ustalania wielkości podczas pracy z pochodnymi <xref:System.Windows.Forms.DataGridView> komórek, wierszy i kolumn, zastępując metody <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>lub <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType> lub przez wywołanie chronionych przeciążeń metod w pochodnym formancie <xref:System.Windows.Forms.DataGridView>. Przeciążenia metody chronionej zmiany rozmiarów są przeznaczone do pracy w parach, aby osiągnąć idealny stosunek wysokooci do szerokości komórki, unikając zbyt dużej lub większej liczby komórek. Na przykład, jeśli wywołasz `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` Przeciążenie metody <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> i przekażesz wartość `false` dla parametru <xref:System.Boolean>, Przeciążenie obliczy idealny zakres i szerokości dla komórek w wierszu, ale dopasowuje tylko wysokość wiersza. Następnie należy wywołać metodę <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>, aby dopasować szerokości kolumn do obliczonego idealnego.  
  
## <a name="content-based-sizing-options"></a>Opcje ustalania rozmiarów na podstawie zawartości  
 Wyliczenia używane przez właściwości i metody ustalania rozmiarów mają podobne wartości w przypadku ustalania rozmiarów na podstawie zawartości. Za pomocą tych wartości można ograniczyć, które komórki są używane do obliczania preferowanych rozmiarów. W przypadku wszystkich wyliczeń ustalania rozmiaru wartości z nazwami odwołującymi się do wyświetlanych komórek ograniczają ich obliczenia do komórek w wyświetlanych wierszach. Wyłączenie wierszy jest przydatne, aby uniknąć spadek wydajności podczas pracy z dużą ilością wierszy. Możesz również ograniczyć obliczenia do wartości komórek w nagłówkach lub komórkach nietytułowych.  
  
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
- [Instrukcje: ustawianie trybów zmieniania rozmiaru kontrolki DataGridView formularzy Windows Forms](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
