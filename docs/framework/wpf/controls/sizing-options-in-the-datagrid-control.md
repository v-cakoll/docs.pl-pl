---
title: Opcje ustalania rozmiaru w formancie DataGrid
description: Dowiedz się, jak ustawić poszczególne wiersze i kolumny w kontrolce Windows Presentation Foundation DataGrid na rozmiar zawartości lub do określonych wartości.
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
ms.openlocfilehash: 0f10e385cbf18a26989614363ca6cd9f92bc83ec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164743"
---
# <a name="sizing-options-in-the-datagrid-control"></a>Opcje ustalania rozmiaru w formancie DataGrid
Dostępne są różne opcje umożliwiające kontrolowanie sposobu, w jaki <xref:System.Windows.Controls.DataGrid> same rozmiary. <xref:System.Windows.Controls.DataGrid>, I poszczególne wiersze i kolumny w <xref:System.Windows.Controls.DataGrid> , można ustawić na rozmiar automatycznie do ich zawartości lub można ustawić określone wartości. Domyślnie <xref:System.Windows.Controls.DataGrid> zwiększy się i zmniejszy rozmiar zawartości.  
  
## <a name="sizing-the-datagrid"></a>Ustalanie wielkości elementu DataGrid  
  
### <a name="cautions-when-using-automatic-sizing"></a>Przestroga podczas korzystania z automatycznego ustalania wielkości  
 Domyślnie <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> właściwości i <xref:System.Windows.Controls.DataGrid> są ustawione na wartość <xref:System.Double.NaN?displayProperty=nameWithType> (" `Auto` " w języku XAML) i <xref:System.Windows.Controls.DataGrid> dostosowują się do rozmiaru zawartości.  
  
 Po umieszczeniu wewnątrz kontenera, który nie ogranicza rozmiaru jego elementów podrzędnych, takich jak <xref:System.Windows.Controls.Canvas> lub <xref:System.Windows.Controls.StackPanel> , <xref:System.Windows.Controls.DataGrid> rozciąga się poza widoczne granice kontenera i ScrollBars nie będą wyświetlane. Ten stan ma wpływ na działanie i wydajność.  
  
 W przypadku powiązania z zestawem danych, jeśli <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.DataGrid> nie jest ograniczony, będzie nadal dodawać wiersz dla każdego elementu danych w zestawie danych powiązanych. Może to spowodować <xref:System.Windows.Controls.DataGrid> zwiększenie wartości poza widocznymi granicami aplikacji w miarę dodawania wierszy. <xref:System.Windows.Controls.DataGrid>W takim przypadku nie będą wyświetlane paski przewijania, ponieważ <xref:System.Windows.FrameworkElement.Height%2A> będzie ona nadal zwiększać się w celu uwzględnienia nowych wierszy.  
  
 Obiekt jest tworzony dla każdego wiersza w <xref:System.Windows.Controls.DataGrid> . Jeśli pracujesz z dużym zestawem danych i zezwolisz <xref:System.Windows.Controls.DataGrid> na automatyczną zmianę rozmiaru, Tworzenie dużej liczby obiektów może wpłynąć na wydajność aplikacji.  
  
 Aby uniknąć tych problemów podczas pracy z dużymi zestawami danych, zaleca się określenie ustawienia <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.DataGrid> lub umieszczenie go w kontenerze, który ograniczy jego, na przykład <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.Grid> . Gdy <xref:System.Windows.FrameworkElement.Height%2A> jest ograniczony, <xref:System.Windows.Controls.DataGrid> program utworzy tylko wiersze, które zmieszczą się w określonym <xref:System.Windows.FrameworkElement.Height%2A> i odzyskuje te wiersze w miarę potrzeb, aby wyświetlić nowe dane.  
  
### <a name="setting-the-datagrid-size"></a>Ustawianie rozmiaru elementu DataGrid  
 <xref:System.Windows.Controls.DataGrid>Może być ustawiony na automatyczny rozmiar w określonych granicach lub <xref:System.Windows.Controls.DataGrid> może być ustawiony na określony rozmiar. W poniższej tabeli przedstawiono właściwości, które można ustawić, aby kontrolować <xref:System.Windows.Controls.DataGrid> rozmiar.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|Ustawia określoną wysokość dla <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|Ustawia górną granicę dla wysokości <xref:System.Windows.Controls.DataGrid> . <xref:System.Windows.Controls.DataGrid>Zostanie powiększona w pionie, dopóki osiągnie tę wysokość.|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|Ustawia dolną granicę dla wysokości <xref:System.Windows.Controls.DataGrid> . Zmniejsza się w <xref:System.Windows.Controls.DataGrid> pionie, dopóki osiągnie tę wysokość.|  
|<xref:System.Windows.FrameworkElement.Width%2A>|Ustawia określoną szerokość dla <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|Ustawia górną granicę szerokości <xref:System.Windows.Controls.DataGrid> . <xref:System.Windows.Controls.DataGrid>Zostanie powiększony w poziomie do momentu osiągnięcia tej szerokości.|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|Ustawia dolną granicę dla szerokości <xref:System.Windows.Controls.DataGrid> . <xref:System.Windows.Controls.DataGrid>Zmniejszy się w poziomie do osiągnięcia tej szerokości.|  
  
## <a name="sizing-rows-and-row-headers"></a>Ustalanie rozmiarów wierszy i nagłówków wierszy  
  
### <a name="datagrid-rows"></a>Wiersze DataGrid  
 Domyślnie <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.FrameworkElement.Height%2A> Właściwość wiersza jest ustawiona na wartość <xref:System.Double.NaN?displayProperty=nameWithType> (" `Auto` " w języku XAML), a wysokość wiersza zostanie rozwinięta do rozmiaru jego zawartości. Wysokość wszystkich wierszy w tabeli <xref:System.Windows.Controls.DataGrid> może być określona przez ustawienie <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType> właściwości. Użytkownicy mogą zmieniać wysokość wiersza, przeciągając separatory nagłówka wiersza.  
  
### <a name="datagrid-row-headers"></a>Nagłówki wierszy DataGrid  
 Aby wyświetlić nagłówki wierszy, <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> Właściwość musi być ustawiona na <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> lub <xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType> . Domyślnie nagłówki wierszy są wyświetlane, a rozmiary są automatycznie dopasowywane do zawartości. Nagłówki wierszy mogą mieć określoną szerokość przez ustawienie <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="sizing-columns-and-column-headers"></a>Ustalanie rozmiarów kolumn i nagłówków kolumn  
  
### <a name="datagrid-columns"></a>Kolumny DataGrid  
 <xref:System.Windows.Controls.DataGrid>Używa wartości <xref:System.Windows.Controls.DataGridLength> i <xref:System.Windows.Controls.DataGridLengthUnitType> struktury do określania bezwzględnych lub automatycznych trybów zmiany rozmiarów.  
  
 W poniższej tabeli przedstawiono wartości udostępniane przez <xref:System.Windows.Controls.DataGridLengthUnitType> strukturę.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|Domyślny tryb automatycznej zmiany rozmiaru <xref:System.Windows.Controls.DataGrid> kolumn w oparciu o zawartość obydwu komórek i nagłówków kolumn.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|Tryb automatycznego ustalania rozmiaru na podstawie komórek <xref:System.Windows.Controls.DataGrid> w oparciu o zawartość komórek w kolumnie, bez uwzględniania nagłówków kolumn.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|Tryb automatycznej zmiany rozmiaru oparty na nagłówkach <xref:System.Windows.Controls.DataGrid> kolumn na podstawie zawartości tylko nagłówków kolumn.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|Rozmiar kolumn w trybie rozmiaru opartych na pikselach <xref:System.Windows.Controls.DataGrid> na podstawie podanej wartości liczbowej.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|Tryb ustalania wielkości gwiazdki służy do dystrybuowania dostępnego miejsca przez ważone proporcje.<br /><br /> W języku XAML wartości gwiazdek są wyrażane jako n *, gdzie n reprezentuje wartość liczbową. 1 \* jest równoważne \* . Na przykład jeśli dwie kolumny <xref:System.Windows.Controls.DataGrid> \* mają szerokość i 2 \* , pierwsza kolumna otrzyma jedną część dostępnego miejsca, a druga kolumna otrzymuje dwie części dostępnego miejsca.|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter>Klasa może służyć do konwertowania danych między wartościami liczbowymi lub ciągami oraz <xref:System.Windows.Controls.DataGridLength> wartościami.  
  
 Domyślnie <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> Właściwość jest ustawiona na <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A> , a <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType> Właściwość jest ustawiona na <xref:System.Windows.Controls.DataGridLength.Auto%2A> . Gdy tryb ustalania rozmiaru jest ustawiony na <xref:System.Windows.Controls.DataGridLength.Auto%2A> lub <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A> , kolumny będą się zwiększać do szerokości najszerszej widocznej zawartości. Podczas przewijania, te tryby ustalania rozmiaru spowodują, że kolumny zostaną rozwinięte, jeśli zawartość większa niż bieżąca rozmiar kolumny zostanie przewinięty do widoku. Kolumna nie zostanie zmniejszana, gdy zawartość nie zostanie wyświetlona z widoku.  
  
 Kolumny w <xref:System.Windows.Controls.DataGrid> można również ustawić na automatyczne rozmiar tylko w określonych granicach, a kolumny można ustawić na określony rozmiar. W poniższej tabeli przedstawiono właściwości, które można ustawić, aby kontrolować rozmiary kolumn.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|Ustawia górną granicę dla wszystkich kolumn w <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|Ustawia górną granicę dla pojedynczej kolumny. Zastąpień <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType> .|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|Ustawia dolną granicę dla wszystkich kolumn w <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|Ustawia dolną granicę dla pojedynczej kolumny. Zastąpień <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType> .|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|Ustawia określoną szerokość dla wszystkich kolumn w <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|Ustawia określoną szerokość pojedynczej kolumny. Zastąpień <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> .|  
  
### <a name="datagrid-column-headers"></a>Nagłówki kolumn DataGrid  
 Domyślnie <xref:System.Windows.Controls.DataGrid> są wyświetlane nagłówki kolumn. Aby ukryć nagłówki kolumn, <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> Właściwość musi być ustawiona na <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> lub <xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType> . Domyślnie, gdy są wyświetlane nagłówki kolumn, rozmiary są automatycznie dopasowywane do zawartości. Nagłówki kolumn mogą mieć określoną wysokość przez ustawienie <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="resizing-with-the-mouse"></a>Zmienianie rozmiarów przy użyciu myszy  
 Użytkownicy mogą zmieniać rozmiar <xref:System.Windows.Controls.DataGrid> wierszy i kolumn, przeciągając separatory nagłówków wierszy lub kolumn. <xref:System.Windows.Controls.DataGrid>Obsługuje również automatyczną zmianę rozmiarów wierszy i kolumn przez dwukrotne kliknięcie separatora nagłówka wiersza lub kolumny. Aby uniemożliwić użytkownikowi zmianę rozmiarów określonych kolumn, należy ustawić właściwość na <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> `false` dla poszczególnych kolumn. Aby uniemożliwić użytkownikom zmianę rozmiarów wszystkich kolumn, należy ustawić <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> Właściwość na `false` . Aby uniemożliwić użytkownikom zmianę rozmiarów wszystkich wierszy, należy ustawić <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType> Właściwość na `false` .  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGridColumn>
- <xref:System.Windows.Controls.DataGridLength>
- <xref:System.Windows.Controls.DataGridLengthConverter>
