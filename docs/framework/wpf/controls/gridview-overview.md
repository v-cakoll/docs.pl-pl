---
title: GridView — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 6da556296679de1161f609a7731c6fbf14e94730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966471"
---
# <a name="gridview-overview"></a>GridView — Przegląd
<xref:System.Windows.Controls.GridView>Tryb widoku jest jednym z trybów widoku dla <xref:System.Windows.Controls.ListView> kontrolki. <xref:System.Windows.Controls.GridView> Klasa i jej klasy pomocnicze umożliwiają Ci i użytkownikom wyświetlanie kolekcji elementów w tabeli, która zwykle używa przycisków jako interaktywnych nagłówków kolumn. W <xref:System.Windows.Controls.GridView> tym temacie przedstawiono klasę i opisano jej użycie.  

<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>Co to jest widok GridView?  
 Tryb <xref:System.Windows.Controls.GridView> widoku Wyświetla listę elementów danych według powiązań pól danych do kolumn i wyświetlając nagłówek kolumny w celu zidentyfikowania pola. Styl domyślny <xref:System.Windows.Controls.GridView> implementuje przyciski jako nagłówki kolumn. Za pomocą przycisków nagłówków kolumn, można zaimplementować ważne funkcje interakcji użytkownika. na przykład użytkownicy mogą kliknąć nagłówek kolumny, aby sortować <xref:System.Windows.Controls.GridView> dane zgodnie z zawartością konkretnej kolumny.  
  
> [!NOTE]
> Kontrolki przycisku, <xref:System.Windows.Controls.GridView> które są używane dla nagłówków kolumn, <xref:System.Windows.Controls.Primitives.ButtonBase>są wyprowadzane z.  
  
 Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView> widok zawartości.  
    
 ![Zrzut ekranu pokazujący widok GridView zawartości elementu ListView.](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>kolumny są reprezentowane przez <xref:System.Windows.Controls.GridViewColumn> obiekty, które mogą automatycznie zmieniać rozmiar zawartości. Opcjonalnie można jawnie ustawić <xref:System.Windows.Controls.GridViewColumn> określoną szerokość. Można zmienić rozmiar kolumn, przeciągając uchwyt między nagłówkami kolumn. Można również dynamicznie dodawać, usuwać, zamieniać i zmieniać kolejność kolumn, ponieważ ta funkcja jest wbudowana <xref:System.Windows.Controls.GridView>w. <xref:System.Windows.Controls.GridView> Nie można jednak bezpośrednio zaktualizować wyświetlanych danych.  
  
 Poniższy przykład pokazuje <xref:System.Windows.Controls.GridView> , jak zdefiniować, który wyświetla dane pracownika. W tym przykładzie <xref:System.Windows.Controls.ListView> `EmployeeInfoDataSource` definiuje jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Definicje <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> właściwości powiązanej <xref:System.Windows.Controls.GridViewColumn> zawartości z `EmployeeInfoDataSource` kategoriami danych.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Na poniższej ilustracji przedstawiono tabelę, która została utworzona w poprzednim przykładzie. Kontrolka GridView wyświetla dane z obiektu ItemsSource:
    
 ![Zrzut ekranu pokazujący widok ListView z danymi wyjściowymi GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>Układ i styl widoku GridView  
 Komórki kolumn i nagłówek <xref:System.Windows.Controls.GridViewColumn> kolumny mają taką samą szerokość. Domyślnie każda kolumna zmienia rozmiar szerokości w celu dopasowania jej do zawartości. Opcjonalnie możesz ustawić kolumnę o stałej szerokości.  
  
 Zawartość pokrewnych danych jest wyświetlana w poziomych wierszach. Na przykład na poprzedniej ilustracji, nazwisko każdego pracownika, imię i numer IDENTYFIKACYJNy są wyświetlane jako zestaw, ponieważ pojawiają się one w poziomym wierszu.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>Definiowanie i Określanie stylu kolumn w widoku GridView  
 Podczas <xref:System.Windows.Controls.GridViewColumn>definiowania pola danych, które mają być wyświetlane w, należy <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>użyć właściwości, <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>lub. <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Właściwość ma pierwszeństwo przed właściwościami szablonu.  
  
 Aby określić wyrównanie zawartości w kolumnie a <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>Zdefiniuj. Nie należy używać <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> właściwości i <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> dla <xref:System.Windows.Controls.ListView> zawartości, która jest wyświetlana przy użyciu <xref:System.Windows.Controls.GridView>.  
  
 Aby określić właściwości szablonu i stylu dla nagłówków kolumn, użyj <xref:System.Windows.Controls.GridView>klas, <xref:System.Windows.Controls.GridViewColumn>i. <xref:System.Windows.Controls.GridViewColumnHeader> Aby uzyskać więcej informacji, zobacz [Omówienie stylów i szablonów nagłówka kolumny GridView](gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>Dodawanie elementów wizualnych do widoku GridView  
 Aby dodać elementy wizualne, takie jak <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.Button> kontrolki, do <xref:System.Windows.Controls.GridView> trybu widoku, użyj szablonów lub stylów.  
  
 Jeśli jawnie zdefiniujesz element wizualny jako element danych, może on pojawić się tylko jeden raz w <xref:System.Windows.Controls.GridView>. To ograniczenie istnieje, ponieważ element może mieć tylko jeden element nadrzędny i w związku z tym może wystąpić tylko raz w drzewie wizualnym.  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>Style wierszy w widoku GridView  
 Użyj klas <xref:System.Windows.Controls.GridViewHeaderRowPresenter> <xref:System.Windows.Controls.GridView>i do formatowania i wyświetlania wierszy. <xref:System.Windows.Controls.GridViewRowPresenter> Aby zapoznać się z przykładem stylu wierszy w <xref:System.Windows.Controls.GridView> trybie widoku, zobacz [Style a wiersz w ListView, który implementuje GridView](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>Problemy z wyrównaniami w przypadku korzystania z ItemContainerStyle  
 Aby zapobiec wyrównaniu problemów między nagłówkami kolumn i komórkami, nie ustawiaj właściwości ani określ szablon, który wpływa na szerokość elementu w <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Na <xref:System.Windows.FrameworkElement.Margin%2A> przykład nie należy ustawiać właściwości ani <xref:System.Windows.Controls.ControlTemplate> określić <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> , że dodaje <xref:System.Windows.Controls.CheckBox> do, który jest zdefiniowany w <xref:System.Windows.Controls.ListView> kontrolce. Zamiast tego należy określić właściwości i szablony, które mają wpływ na szerokość kolumny bezpośrednio w klasach, które definiują <xref:System.Windows.Controls.GridView> tryb widoku.  
  
 Na przykład, <xref:System.Windows.Controls.CheckBox> aby dodać do wierszy w <xref:System.Windows.Controls.GridView> trybie <xref:System.Windows.Controls.CheckBox> widok <xref:System.Windows.DataTemplate>, Dodaj do, a następnie ustaw <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> Właściwość <xref:System.Windows.DataTemplate>na wartość.  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>Interakcje użytkownika z elementem GridView  
 Gdy używasz <xref:System.Windows.Controls.GridView> w aplikacji, użytkownicy mogą korzystać z i modyfikować formatowanie <xref:System.Windows.Controls.GridView>. Na przykład użytkownicy mogą zmieniać kolejność kolumn, zmienić rozmiar kolumny, wybierać elementy w tabeli i przewijać zawartość. Można także zdefiniować procedurę obsługi zdarzeń, która reaguje, gdy użytkownik kliknie przycisk nagłówka kolumny. Procedura obsługi zdarzeń może wykonywać operacje, takie jak sortowanie danych, które są wyświetlane <xref:System.Windows.Controls.GridView> w zależności od zawartości kolumny.  
  
 Poniższa lista zawiera bardziej szczegółowe możliwości korzystania <xref:System.Windows.Controls.GridView> ze współdziałania z użytkownikiem:  
  
- **Zmień kolejność kolumn za pomocą metody przeciągania i upuszczania.**  
  
     Użytkownicy mogą zmieniać kolejność kolumn w a <xref:System.Windows.Controls.GridView> , naciskając lewym przyciskiem myszy nad nagłówkiem kolumny, a następnie przeciągając tę kolumnę do nowej pozycji. Gdy użytkownik przeciągnie nagłówek kolumny, zostanie wyświetlona przestawna wersja nagłówka, a także pełna Czarna linia pokazująca, gdzie wstawić kolumnę.  
  
     Jeśli chcesz zmodyfikować domyślny styl dla zmiennoprzecinkowej wersji nagłówka, określ <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.GridViewColumnHeader> dla typu, <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> który jest wyzwalany, gdy właściwość jest ustawiona na <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>. Aby uzyskać więcej informacji, zobacz [Tworzenie stylu dla przeciągniętego nagłówka kolumny GridView](how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
- **Zmień rozmiar kolumny na jej zawartość.**  
  
     Użytkownicy mogą dwukrotnie kliknąć uchwyt z prawej strony nagłówka kolumny, aby zmienić rozmiar kolumny w celu dopasowania jej do zawartości.  
  
    > [!NOTE]
    > Można ustawić <xref:System.Windows.Controls.GridViewColumn.Width%2A> `Double.NaN` właściwość na, aby utworzyć ten sam efekt.  
  
- **Zaznacz elementy wierszy.**  
  
     Użytkownicy mogą wybrać jeden lub więcej elementów w <xref:System.Windows.Controls.GridView>.  
  
     Jeśli chcesz zmienić <xref:System.Windows.Style> wybrany element, zobacz [Używanie wyzwalaczy do stylu wybranych elementów w elemencie ListView](how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
- **Przewiń, aby wyświetlić zawartość, która nie jest początkowo widoczna na ekranie.**  
  
     Jeśli rozmiar <xref:System.Windows.Controls.GridView> nie jest wystarczająco duży, aby wyświetlić wszystkie elementy, użytkownicy mogą przewijać w poziomie lub w pionie przy użyciu pasków przewijania, które są udostępniane <xref:System.Windows.Controls.ScrollViewer> przez formant. Element <xref:System.Windows.Controls.Primitives.ScrollBar> jest ukryty, jeśli cała zawartość jest widoczna w określonym kierunku. Nagłówki kolumn nie są przewijane pionowym paskiem przewijania, ale przewinięcie w poziomie.  
  
- **Korzystając z kolumn, kliknij przyciski nagłówka kolumny.**  
  
     Gdy użytkownik kliknie przycisk nagłówka kolumny, może sortować dane, które są wyświetlane w kolumnie, jeśli podano algorytm sortowania.  
  
     Możesz obsłużyć <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie dla przycisków nagłówka kolumny, aby zapewnić funkcje takie jak algorytm sortowania. Aby obsłużyć <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie dla pojedynczego nagłówka kolumny, ustaw procedurę obsługi zdarzeń <xref:System.Windows.Controls.GridViewColumnHeader>na. Aby ustawić procedurę obsługi zdarzeń, która obsługuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie dla wszystkich nagłówków kolumn, ustaw procedurę obsługi <xref:System.Windows.Controls.ListView> na kontrolce.  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>Uzyskiwanie innych widoków niestandardowych  
 Klasa, która jest pochodną <xref:System.Windows.Controls.ViewBase> klasy abstrakcyjnej, jest tylko jednym z <xref:System.Windows.Controls.ListView> możliwych trybów wyświetlania klasy. <xref:System.Windows.Controls.GridView> Można utworzyć inne niestandardowe widoki dla <xref:System.Windows.Controls.ListView> , wyprowadzając je <xref:System.Windows.Controls.ViewBase> z klasy. Aby zapoznać się z przykładem trybu widoku niestandardowego, zobacz [Tworzenie niestandardowego trybu widoku dla elementu ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>Klasy pomocnicze GridView  
 Poniższe klasy obsługują <xref:System.Windows.Controls.GridView> tryb widoku.  
  
- <xref:System.Windows.Controls.GridViewColumn>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GridViewRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewColumnCollection>  
  
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Controls.GridViewColumn>
- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.ViewBase>
- [ListView — omówienie](listview-overview.md)
- [Sortowanie kolumny GridView po kliknięciu nagłówka](how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Tematy z instrukcjami](listview-how-to-topics.md)
