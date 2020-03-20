---
title: GridView — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 98bc7985172cabeab19469af4b4c21e13a6bce73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181899"
---
# <a name="gridview-overview"></a>GridView — Przegląd
<xref:System.Windows.Controls.GridView>tryb widoku jest jednym z trybów wyświetlania formantu. <xref:System.Windows.Controls.ListView> Klasa <xref:System.Windows.Controls.GridView> i jej klasy pomocnicze umożliwiają tobie i użytkownikom wyświetlanie kolekcji elementów w tabeli, która zazwyczaj używa przycisków jako interaktywnych nagłówków kolumn. W tym temacie <xref:System.Windows.Controls.GridView> przedstawiono klasę i przedstawiono jej użycie.  

<a name="DefiningaListViewthatusesGridViewView"></a>
## <a name="what-is-a-gridview-view"></a>Co to jest widok gridview?  
 W <xref:System.Windows.Controls.GridView> trybie widoku wyświetlana jest lista elementów danych przez powiązanie pól danych z kolumnami i wyświetlanie nagłówka kolumny w celu zidentyfikowania pola. Styl <xref:System.Windows.Controls.GridView> domyślny implementuje przyciski jako nagłówki kolumn. Za pomocą przycisków dla nagłówków kolumn, można zaimplementować ważne możliwości interakcji użytkownika; na przykład użytkownicy mogą kliknąć <xref:System.Windows.Controls.GridView> nagłówek kolumny, aby sortować dane zgodnie z zawartością określonej kolumny.  
  
> [!NOTE]
> Formanty <xref:System.Windows.Controls.GridView> przycisku używane dla nagłówków <xref:System.Windows.Controls.Primitives.ButtonBase>kolumn są uzyskiwane z .  
  
 Na poniższej <xref:System.Windows.Controls.GridView> ilustracji <xref:System.Windows.Controls.ListView> przedstawiono widok zawartości.  

 ![Zrzut ekranu przedstawiający widok GridView zawartości ListView.](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>kolumny są reprezentowane <xref:System.Windows.Controls.GridViewColumn> przez obiekty, które mogą automatycznie rozmiar do ich zawartości. Opcjonalnie można jawnie ustawić <xref:System.Windows.Controls.GridViewColumn> na określoną szerokość. Rozmiar kolumn można zmienić, przeciągając uchwyt między nagłówkami kolumn. Można również dynamicznie dodawać, usuwać, zamieniać i zmieniać kolejność <xref:System.Windows.Controls.GridView>kolumn, ponieważ ta funkcja jest wbudowana w program . Jednak <xref:System.Windows.Controls.GridView> nie można bezpośrednio zaktualizować dane, które wyświetla.  
  
 W poniższym <xref:System.Windows.Controls.GridView> przykładzie pokazano, jak zdefiniować dane pracownika. W tym <xref:System.Windows.Controls.ListView> przykładzie `EmployeeInfoDataSource` definiuje <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>jako . Definicje właściwości <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> zawartości <xref:System.Windows.Controls.GridViewColumn> powiązania `EmployeeInfoDataSource` z kategoriami danych.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Na poniższej ilustracji przedstawiono tabelę, którą tworzy poprzedni przykład. Formant GridView wyświetla dane z obiektu ItemsSource:

 ![Zrzut ekranu przedstawiający widok list z wyjściem GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>
## <a name="gridview-layout-and-style"></a>Układ i styl widoku siatki  
 Komórki kolumny i nagłówek kolumny <xref:System.Windows.Controls.GridViewColumn> mają taką samą szerokość. Domyślnie każda kolumna ma rozmiar szerokości, aby dopasować ją do zawartości. Opcjonalnie można ustawić kolumnę na stałą szerokość.  
  
 Powiązana zawartość danych jest wyświetlana w wierszach poziomych. Na przykład na poprzedniej ilustracji nazwisko, imię i numer identyfikatora każdego pracownika są wyświetlane jako zestaw, ponieważ są wyświetlane w wierszu poziomym.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>
### <a name="defining-and-styling-columns-in-a-gridview"></a>Definiowanie i stylizowanie kolumn w widoku gridview  
 Podczas definiowania pola danych do <xref:System.Windows.Controls.GridViewColumn>wyświetlenia <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>w <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> , użyj , lub właściwości. Właściwość <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> ma pierwszeństwo przed jedną z właściwości szablonu.  
  
 Aby określić wyrównanie zawartości w <xref:System.Windows.Controls.GridView>kolumnie <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>, zdefiniuj plik . Nie należy <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> używać <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> właściwości <xref:System.Windows.Controls.ListView> i dla zawartości, która <xref:System.Windows.Controls.GridView>jest wyświetlana za pomocą pliku .  
  
 Aby określić właściwości szablonu i stylu <xref:System.Windows.Controls.GridView>dla <xref:System.Windows.Controls.GridViewColumn>nagłówków kolumn, należy użyć przycisku , i <xref:System.Windows.Controls.GridViewColumnHeader> klas. Aby uzyskać więcej informacji, zobacz [GridView Column Header Styles and Templates Overview](gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>
### <a name="adding-visual-elements-to-a-gridview"></a>Dodawanie elementów wizualnych do widoku siatki  
 Aby dodać elementy wizualne, takie jak <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.Button> formanty, do trybu <xref:System.Windows.Controls.GridView> widoku, użyj szablonów lub stylów.  
  
 Jeśli element wizualny zostanie jawnie zdefiniowany jako element danych, <xref:System.Windows.Controls.GridView>może on pojawić się tylko jeden raz w pliku . To ograniczenie istnieje, ponieważ element może mieć tylko jeden element nadrzędny i dlatego może pojawić się tylko jeden raz w drzewie wizualnym.  
  
<a name="StylingRowsinaGridViewView"></a>
### <a name="styling-rows-in-a-gridview"></a>Stylowanie wierszy w widoku gridview  
 Użyj <xref:System.Windows.Controls.GridViewRowPresenter> klas <xref:System.Windows.Controls.GridViewHeaderRowPresenter> i, aby sformatować <xref:System.Windows.Controls.GridView>i wyświetlić wiersze pliku . Na przykład sposobu stylowania wierszy <xref:System.Windows.Controls.GridView> w trybie widoku zobacz [Styl wiersza w widoku ListView, który implementuje widok gridview](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>Problemy z wyrównaniem podczas używania elementuContainerStyle  
 Aby zapobiec problemom wyrównania między nagłówkami kolumn i komórkami, nie należy ustawiać <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>właściwości ani określać szablonu, który wpływa na szerokość elementu w pliku . Na przykład nie należy <xref:System.Windows.FrameworkElement.Margin%2A> ustawiać <xref:System.Windows.Controls.ControlTemplate> właściwości lub <xref:System.Windows.Controls.CheckBox> określić, który dodaje <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> do, który jest zdefiniowany na <xref:System.Windows.Controls.ListView> formancie. Zamiast tego należy określić właściwości i szablony, które wpływają <xref:System.Windows.Controls.GridView> na szerokość kolumny bezpośrednio na klasy, które definiują tryb widoku.  
  
 Na przykład, aby <xref:System.Windows.Controls.CheckBox> dodać a <xref:System.Windows.Controls.GridView> do wierszy <xref:System.Windows.Controls.CheckBox> w <xref:System.Windows.DataTemplate>trybie widoku, <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> dodaj <xref:System.Windows.DataTemplate>do , a następnie ustaw właściwość do tego .  
  
<a name="InteractingwithaGridViewControl"></a>
## <a name="user-interactions-with-a-gridview"></a>Interakcje użytkownika z widokiem na siatkę  
 Podczas korzystania <xref:System.Windows.Controls.GridView> z aplikacji użytkownicy mogą wchodzić w interakcje <xref:System.Windows.Controls.GridView>z formatowaniem programu . Na przykład użytkownicy mogą zmienić kolejność kolumn, zmienić rozmiar kolumny, zaznaczyć elementy w tabeli i przewijać zawartość. Można również zdefiniować program obsługi zdarzeń, który odpowiada, gdy użytkownik kliknie przycisk nagłówka kolumny. Program obsługi zdarzeń może wykonywać operacje, takie jak <xref:System.Windows.Controls.GridView> sortowanie danych, które są wyświetlane w zależności od zawartości kolumny.  
  
 Na poniższej liście omówiono bardziej szczegółowo <xref:System.Windows.Controls.GridView> możliwości korzystania z interakcji z użytkownikiem:  
  
- **Zamieść kolejność kolumn przy użyciu metody przeciągania i upuszczania.**  
  
     Użytkownicy mogą zamiesz <xref:System.Windows.Controls.GridView> było zamie według nazwy kolumn, naciskając lewy przycisk myszy, gdy znajduje się nad nagłówkiem kolumny, a następnie przeciągając tę kolumnę w nowe miejsce. Podczas przeciągania nagłówka kolumny wyświetlana jest pływająca wersja nagłówka, a także pełna czarna linia, która pokazuje, gdzie wstawić kolumnę.  
  
     Jeśli chcesz zmodyfikować domyślny styl dla przestawnej <xref:System.Windows.Controls.ControlTemplate> wersji <xref:System.Windows.Controls.GridViewColumnHeader> nagłówka, określ <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> typ wyzwalany, gdy właściwość jest ustawiona na <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>. Aby uzyskać więcej informacji, zobacz [Tworzenie stylu dla przeciągniętego nagłówka kolumny GridView](how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
- **Zmienić rozmiar kolumny do jej zawartości.**  
  
     Użytkownicy mogą dwukrotnie kliknąć uchwyt po prawej stronie nagłówka kolumny, aby zmienić rozmiar kolumny w celu dopasowania jej zawartości.  
  
    > [!NOTE]
    > Można ustawić <xref:System.Windows.Controls.GridViewColumn.Width%2A> właściwość, aby `Double.NaN` uzyskać ten sam efekt.  
  
- **Zaznacz elementy wiersza.**  
  
     Użytkownicy mogą wybrać jeden <xref:System.Windows.Controls.GridView>lub więcej elementów w pliku .  
  
     Aby zmienić <xref:System.Windows.Style> zaznaczony element, zobacz [Używanie wyzwalaczy do stylowania wybranych elementów w widoku listy](how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
- **Przewiń, aby wyświetlić zawartość, która początkowo nie jest widoczna na ekranie.**  
  
     Jeśli rozmiar <xref:System.Windows.Controls.GridView> nie jest wystarczająco duży, aby wyświetlić wszystkie elementy, użytkownicy mogą przewijać w <xref:System.Windows.Controls.ScrollViewer> poziomie lub w pionie za pomocą pasków przewijania, które są dostarczane przez formant. A <xref:System.Windows.Controls.Primitives.ScrollBar> jest ukryty, jeśli cała zawartość jest widoczna w określonym kierunku. Nagłówki kolumn nie przewijają się za pomocą pionowego paska przewijania, ale przewijają się w poziomie.  
  
- **Interakcja z kolumnami, klikając przyciski nagłówka kolumny.**  
  
     Gdy użytkownicy klikną przycisk nagłówka kolumny, mogą sortować dane wyświetlane w kolumnie, jeśli podano algorytm sortowania.  
  
     Można obsługiwać <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie dla przycisków nagłówka kolumny w celu zapewnienia funkcji, takich jak algorytm sortowania. Aby obsłużyć <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie dla nagłówka pojedynczej kolumny, ustaw program obsługi zdarzeń na pliku <xref:System.Windows.Controls.GridViewColumnHeader>. Aby ustawić program obsługi zdarzeń, który obsługuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie dla wszystkich <xref:System.Windows.Controls.ListView> nagłówków kolumn, ustaw program obsługi na formancie.  
  
<a name="Obtaining_Other_Custom_Views"></a>
## <a name="obtaining-other-custom-views"></a>Uzyskiwanie innych widoków niestandardowych  
 Klasa, <xref:System.Windows.Controls.GridView> która pochodzi od <xref:System.Windows.Controls.ViewBase> klasy abstrakcyjnej, jest tylko jednym z <xref:System.Windows.Controls.ListView> możliwych trybów widoku dla klasy. Można utworzyć inne widoki <xref:System.Windows.Controls.ListView> niestandardowe, <xref:System.Windows.Controls.ViewBase> wyprowadzając z klasy. Aby zapoznać się z przykładem trybu widoku niestandardowego, zobacz [Tworzenie trybu widoku niestandardowego dla widoku listview](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>
## <a name="gridview-supporting-classes"></a>Klasy pomocnicze GridView  
 Następujące klasy obsługują <xref:System.Windows.Controls.GridView> tryb widoku.  
  
- <xref:System.Windows.Controls.GridViewColumn>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GridViewRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewColumnCollection>  
  
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Controls.GridViewColumn>
- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.ViewBase>
- [ListView — omówienie](listview-overview.md)
- [Sortowanie kolumny GridView po kliknięciu nagłówka](how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Tematy in jakże](listview-how-to-topics.md)
