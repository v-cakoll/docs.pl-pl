---
title: "Style komórki w formancie DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: edec8a00aff59195c6c80414eb4b950d68e488da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Style komórki w formancie DataGridView formularzy systemu Windows
Każda komórka w <xref:System.Windows.Forms.DataGridView> formant może mieć własną styl, na przykład format tekstu, kolor tła kolor pierwszego planu i czcionki. Zwykle jednak wiele komórek udostępni właściwości danego stylu.  
  
 Grupy komórek, style może obejmować wszystkie komórki w szczególności wierszy lub kolumn, wszystkich komórek zawierających wartości określonego lub wszystkie komórki w formancie. Ponieważ nakładają się tych grup, każda komórka może zostać jego elementy z więcej niż jednym miejscu. Na przykład może być każdej komórki <xref:System.Windows.Forms.DataGridView> formantu za pomocą tej samej czcionki, ale tylko komórki w kolumnach walutę do użycia w formacie waluty i tylko komórki waluty ujemne można użyć czerwonym kolorem.  
  
## <a name="the-datagridviewcellstyle-class"></a>Klasa DataGridViewCellStyle  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Klasa zawiera następujące właściwości powiązanych z stylów wizualnych:  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>i<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A>i<xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Ta klasa zawiera także następujące właściwości związane z formatowaniem:  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>i<xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A>i<xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Aby uzyskać więcej informacji o tych właściwości i inne właściwości stylu komórki, zobacz <xref:System.Windows.Forms.DataGridViewCellStyle> dokumentacji i tematy wymienione w poniższej sekcji Zobacz też.  
  
## <a name="using-datagridviewcellstyle-objects"></a>Przy użyciu obiektów DataGridViewCellStyle  
 Możesz pobrać <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów z różnych właściwości <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>, i <xref:System.Windows.Forms.DataGridViewCell> klasy i ich pochodne. Jeśli jeden z tych właściwości ma nie został ustawiony, pobierania jej wartość spowoduje utworzenie nowej <xref:System.Windows.Forms.DataGridViewCellStyle> obiektu. Można również utworzyć wystąpienie własne <xref:System.Windows.Forms.DataGridViewCellStyle> obiekty i przypisać je do tych właściwości.  
  
 Można uniknąć niepotrzebnego dublowania informacji o stylu za pomocą udostępniania <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów między wieloma <xref:System.Windows.Forms.DataGridView> elementów. Ponieważ style formantu, kolumny i filtru poziomy wiersz w dół za pośrednictwem każdy poziom na poziomie komórki, można uniknąć duplikowania styl przez ustawienie tych właściwości stylu na każdym poziomie z poziomami powyżej. Jest to opisane bardziej szczegółowo w poniższej sekcji Style dziedziczenia.  
  
 W poniższej tabeli wymieniono właściwości podstawowego, get lub set <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów.  
  
|Właściwość|Klasy|Opis|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>i klasy pochodne|Pobiera lub ustawia domyślne style używane przez wszystkie komórki w całej formantu (w tym komórki nagłówka), w kolumnie lub w wierszu.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślnych stylów komórek używany przez wszystkie wiersze w formancie. Nie ma komórki nagłówka.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślnych stylów komórek używanych przez naprzemiennych wierszy w formancie. Pozwala utworzyć efekt księgi podobne.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślnych stylów komórek używanych przez nagłówki wierszy formantu. Zastąpione przez bieżącego motywu, jeżeli style wizualne są włączone.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Pobiera lub ustawia domyślnych stylów komórek używanych przez nagłówki kolumn formantu. Zastąpione przez bieżącego motywu, jeżeli style wizualne są włączone.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell>i klasy pochodne|Pobiera lub ustawia style określone na poziomie komórki. Te style przesłaniają dziedziczone z wyższego poziomu.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow>, <xref:System.Windows.Forms.DataGridViewColumn>i klasy pochodne|Pobiera wszystkie style, które są aktualnie zastosowanych komórkę, wiersz lub kolumnę, w tym style dziedziczone z wyższego poziomu.|  
  
 Jak wspomniano powyżej, pobierania wartości właściwości stylu automatycznie tworzy nową <xref:System.Windows.Forms.DataGridViewCellStyle> obiektu, jeśli właściwość nie została wcześniej ustawiona. Aby uniknąć niepotrzebnego tworzenia tych obiektów, klas wierszy i kolumn ma <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> właściwość, którą można sprawdzić, aby określić, czy <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> właściwość została ustawiona. Podobnie klasy komórki mają <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> właściwość, która wskazuje, czy <xref:System.Windows.Forms.DataGridViewCell.Style%2A> właściwość została ustawiona.  
  
 Każdej z właściwości stylu ma odpowiadające mu *PropertyName* `Changed` zdarzenia w <xref:System.Windows.Forms.DataGridView> formantu. Dla wierszy, kolumny i właściwości komórki Nazwa zdarzenia rozpoczyna się od "`Row`","`Column`", lub "`Cell`" (na przykład <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>). Każde z tych wydarzeń występuje, gdy odpowiednia właściwość stylu jest ustawiona na inny <xref:System.Windows.Forms.DataGridViewCellStyle> obiektu. Te zdarzenia nie następują po pobraniu <xref:System.Windows.Forms.DataGridViewCellStyle> obiektu z właściwością styl i modyfikowania jej wartości właściwości. Aby odpowiedzieć na zmiany w samych obiektach stylu komórki, obsługi <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> zdarzeń.  
  
## <a name="style-inheritance"></a>Styl dziedziczenia  
 Każdy <xref:System.Windows.Forms.DataGridViewCell> pobiera jego wygląd z jego <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> właściwości. <xref:System.Windows.Forms.DataGridViewCellStyle> Obiektu zwróconego przez tę właściwość dziedziczy wartości z hierarchii właściwości typu <xref:System.Windows.Forms.DataGridViewCellStyle>. Te właściwości są podane poniżej w kolejności, w którym <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> dla komórek nagłówka nie uzyskuje jego wartości.  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(tylko dla komórek w wierszach nieparzystych numery indeksu)  
  
4.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Dla komórek nagłówka wiersza i kolumny <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> właściwości jest wprowadzana przez wartości z poniższej listy właściwości źródeł w podanej kolejności.  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType>lub<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Na poniższym diagramie przedstawiono ten proces.  
  
 ![Właściwości typu DataGridViewCellStyle](../../../../docs/framework/winforms/controls/media/datagridviewcells1.gif "DataGridViewCells1")  
  
 Można także przejść style dziedziczone przez określonych wierszy i kolumn. Kolumna <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> właściwości dziedziczy wartości następujących właściwości.  
  
1.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Wiersz <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> właściwości dziedziczy wartości następujących właściwości.  
  
1.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(tylko dla komórek w wierszach nieparzystych numery indeksu)  
  
3.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Dla każdej właściwości w <xref:System.Windows.Forms.DataGridViewCellStyle> obiektu zwróconego przez `InheritedStyle` właściwości, wartość właściwości są uzyskiwane z pierwszego stylu komórki na odpowiedniej liście mającej odpowiednią właściwość, ustaw wartość innych niż <xref:System.Windows.Forms.DataGridViewCellStyle> klasy wartości domyślnych.  
  
 W poniższej tabeli przedstawiono sposób <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> wartości właściwości dla komórki przykład jest dziedziczona z jego zawierające kolumny.  
  
|Właściwości typu`DataGridViewCellStyle`|Przykład `ForeColor` wartość dla obiekt pobrane|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 W takim przypadku <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> wartość z zakresu od wiersza komórki jest pierwszym rzeczywistą wartość na liście. Staje się on <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> wartość właściwości komórki <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>.  
  
 Na poniższym diagramie przedstawiono sposób różnych <xref:System.Windows.Forms.DataGridViewCellStyle> właściwości mogą dziedziczyć ich wartości z różnych miejscach.  
  
 ![DataGridView — właściwość &#45; dziedziczenie wartości](../../../../docs/framework/winforms/controls/media/datagridviewcells2.gif "DataGridViewCells2")  
  
 Dzięki wykorzystaniu dziedziczenia stylów, możesz podać odpowiednie style dla całego formantu bez konieczności określania tych samych informacji w kilku miejscach.  
  
 Mimo że komórek nagłówka uczestniczyć w dziedziczeniu stylu, zgodnie z opisem, obiekty zwrócone przez <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> właściwości <xref:System.Windows.Forms.DataGridView> formant ma początkowe wartości właściwości przesłaniające wartości właściwości w obiekcie zwracanym przez <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> właściwości. Jeśli chcesz, aby właściwości ustawione dla obiekt zwrócony przez <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> właściwości do zastosowania do nagłówki wierszy i kolumn, należy ustawić odpowiednie właściwości obiektów zwróconych przez <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> wskazanej właściwości domyślne Aby uzyskać <xref:System.Windows.Forms.DataGridViewCellStyle> klasy.  
  
> [!NOTE]
>  Jeżeli style wizualne są włączone, nagłówki wierszy i kolumn (z wyjątkiem <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) są automatycznie wstawiony przez bieżącego motywu, zastępowanie wszystkie style, określony przez te właściwości.  
  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>, <xref:System.Windows.Forms.DataGridViewImageColumn>, I <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> typy również zainicjować niektórych wartości obiektu zwracanego przez kolumnę <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> właściwości. Aby uzyskać więcej informacji zobacz dokumentację odwołania dla tych typów.  
  
## <a name="setting-styles-dynamically"></a>Ustawianie stylów dynamicznie  
 Aby dostosować styl komórek o określonej wartości, należy zaimplementować program obsługi <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> zdarzeń. Programy obsługi dla tego zdarzenia odbierania argument <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> typu. Ten obiekt zawiera właściwości, które pozwalają określić wartość komórki formatowanego wraz z jego lokalizacji w <xref:System.Windows.Forms.DataGridView> formantu. Ten obiekt zawiera także <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> właściwość, która jest ustawiana na wartość <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> właściwości formatowania komórki. Można zmodyfikować właściwości stylu komórki, aby określić odpowiednie wartości w komórce i lokalizacja informacji o stylu.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.RowPrePaint> i <xref:System.Windows.Forms.DataGridView.RowPostPaint> również odbierać zdarzenia <xref:System.Windows.Forms.DataGridViewCellStyle> dane zdarzeń obiektu, ale w ich przypadku jest kopią wiersza <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> właściwości do celów tylko do odczytu, a zmiany nie wpływają na formantu.  
  
 Można również dynamicznie zmodyfikować style pojedynczych komórek w odpowiedzi na zdarzenia takich jak <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> i <xref:System.Windows.Forms.DataGridView.CellMouseLeave> zdarzenia. Na przykład w procedurze obsługi dla <xref:System.Windows.Forms.DataGridView.CellMouseEnter> zdarzeń, można przechowywać bieżącą wartość komórki kolor tła (pobierane w drodze komórki <xref:System.Windows.Forms.DataGridViewCell.Style%2A> właściwości), jest ustawiony na nowy kolor, który będzie zaznacz komórki, gdy mysz znajduje się nad nim. W procedurze obsługi dla <xref:System.Windows.Forms.DataGridView.CellMouseLeave> zdarzeń, będzie można przywrócić kolor tła do oryginalnej wartości.  
  
> [!NOTE]
>  Buforowanie wartościami przechowywanymi w komórce <xref:System.Windows.Forms.DataGridViewCell.Style%2A> właściwość jest ważne, niezależnie od tego, czy ustawiono wartość określonego stylu. Jeśli tymczasowo zastąpić ustawienie stylu, przywracając jego oryginalny stan "nie jest ustawiona" gwarantuje, że komórki zostanie przywrócona dziedziczenie ustawienie stylu z wyższego poziomu. Jeśli trzeba określić rzeczywistego stylu dla komórki niezależnie od tego, czy styl jest dziedziczone, należy używać tej komórki <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>  
 [Podstawowe formatowanie i style w oknach formantu DataGridView formularzy](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Porady: Ustawianie domyślnych stylów komórki dla formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 [Formatowanie danych w oknie formantu DataGridView formularzy](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)
