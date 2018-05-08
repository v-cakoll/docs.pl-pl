---
title: GridView — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 776897d490b2748e240cf7b9a4ea21364284c4c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="gridview-overview"></a>GridView — Przegląd
<xref:System.Windows.Controls.GridView> tryb wyświetlania jest jeden z trybów wyświetlania dla <xref:System.Windows.Controls.ListView> formantu. <xref:System.Windows.Controls.GridView> Klasy i jej klas pomocniczych umożliwiają i użytkowników do wyświetlania elementu kolekcji w tabeli, która zwykle używa przycisków jako nagłówków kolumn interaktywnego. W tym temacie przedstawiono <xref:System.Windows.Controls.GridView> klasy i omówiono jej użycia.  
  
  
  
<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>Co to jest widoku GridView?  
 <xref:System.Windows.Controls.GridView> Widoku trybu zostanie wyświetlona lista elementów danych przez powiązanie pól danych do kolumn i wyświetlając nagłówek kolumny, aby zidentyfikować pola. Wartość domyślna <xref:System.Windows.Controls.GridView> styl implementuje przyciski jako nagłówków kolumn. Za pomocą przycisków dla nagłówków kolumn, można zaimplementować możliwości interakcji użytkownika ważne; na przykład użytkownicy mogą kliknąć nagłówek kolumny, aby posortować <xref:System.Windows.Controls.GridView> danych zgodnie z zawartością określonej kolumny.  
  
> [!NOTE]
>  Przycisk formantów, które <xref:System.Windows.Controls.GridView> zastosowania nagłówki kolumn są uzyskiwane z <xref:System.Windows.Controls.Primitives.ButtonBase>.  
  
 Na poniższej ilustracji pokazano <xref:System.Windows.Controls.GridView> widoku <xref:System.Windows.Controls.ListView> zawartości.  
  
 **Widok GridView zawartości elementu ListView**  
  
 ![Styl elementu ListView](../../../../docs/framework/wpf/controls/media/styledlistview.PNG "StyledListView")  
  
 <xref:System.Windows.Controls.GridView> kolumny są reprezentowane przez <xref:System.Windows.Controls.GridViewColumn> obiektów, które można automatycznie rozmiar do ich zawartości. Opcjonalnie można jawnie ustawić <xref:System.Windows.Controls.GridViewColumn> określonej szerokości. Można zmienić rozmiar kolumn przez przeciągnięcie uchwytu między nagłówki kolumn. Możesz również dynamicznie Dodaj, Usuń, zmienić i zmieniać kolejność kolumn, ponieważ ta funkcja jest wbudowana w <xref:System.Windows.Controls.GridView>. Jednak <xref:System.Windows.Controls.GridView> bezpośrednio nie można zaktualizować danych, który jest wyświetlany.  
  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.GridView> wyświetlający dane pracownika. W tym przykładzie <xref:System.Windows.Controls.ListView> definiuje `EmployeeInfoDataSource` jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Definicje właściwości <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> powiązać <xref:System.Windows.Controls.GridViewColumn> zawartości do `EmployeeInfoDataSource` kategorii danych.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Na poniższej ilustracji przedstawiono tabeli, że w poprzednim przykładzie jest tworzony.  
  
 **Element GridView wyświetlający dane z ItemsSource.**  
  
 ![Element ListView z danych wyjściowych w widoku GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>Widok siatki układu i stylu  
 Komórki kolumny i nagłówek <xref:System.Windows.Controls.GridViewColumn> mieć tej samej szerokości. Domyślnie każda kolumna rozmiary jego szerokość, do jego zawartości. Opcjonalnie można ustawić kolumny o stałej szerokości.  
  
 Wyświetla dane dotyczące zawartości w poziomie wierszy. Na przykład na poprzedniej ilustracji identyfikator, imię i nazwisko każdego pracownika są wyświetlane jako zestaw ponieważ pojawią się one w rzędzie.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>Definiowanie i Style kolumn w widoku GridView  
 Podczas określania w polu danych do wyświetlenia w <xref:System.Windows.Controls.GridViewColumn>, użyj <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>, <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>, lub <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> właściwości. <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Właściwość ma wyższy priorytet niż właściwości szablonu.  
  
 Aby określić wyrównanie zawartości w kolumnie <xref:System.Windows.Controls.GridView>, zdefiniuj <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>. Nie używaj <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> i <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> właściwości <xref:System.Windows.Controls.ListView> zawartości, który jest wyświetlany za pomocą <xref:System.Windows.Controls.GridView>.  
  
 Aby określić właściwości szablonu i styl nagłówków kolumn, użyj <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn>, i <xref:System.Windows.Controls.GridViewColumnHeader> klasy. Aby uzyskać więcej informacji, zobacz [Omówienie szablonów i style nagłówka kolumny w widoku GridView](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>Dodawanie elementów do widoku GridView  
 Aby dodać elementy wizualne, takie jak <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.Button> kontrolki do <xref:System.Windows.Controls.GridView> trybu wyświetlania, za pomocą szablonów lub style.  
  
 Jeśli element wizualny jest jawnie zdefiniować jako element danych, może wystąpić tylko raz w <xref:System.Windows.Controls.GridView>. To ograniczenie istnieje, ponieważ element może mieć tylko jednego zdarzenia nadrzędnego i w związku z tym może występować tylko jeden raz w drzewie wizualnym.  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>Style wierszy w widoku GridView  
 Użyj <xref:System.Windows.Controls.GridViewRowPresenter> i <xref:System.Windows.Controls.GridViewHeaderRowPresenter> klasy, aby sformatować i wyświetlić wiersze <xref:System.Windows.Controls.GridView>. Na przykład jak style wierszy w <xref:System.Windows.Controls.GridView> trybu wyświetlania, zobacz [styl wiersza w implementuje ListView czy element GridView](../../../../docs/framework/wpf/controls/how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>Wyrównanie problemów, gdy używasz ItemContainerStyle  
 Aby zapobiec problemom wyrównania między nagłówki kolumn i komórek, nie ustawiaj właściwości lub Określ szablon, który ma wpływ na szerokość elementu w <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Na przykład nie należy ustawiać <xref:System.Windows.FrameworkElement.Margin%2A> właściwości lub określ <xref:System.Windows.Controls.ControlTemplate> dodaje <xref:System.Windows.Controls.CheckBox> do <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> zdefiniowanego w <xref:System.Windows.Controls.ListView> formantu. Zamiast tego należy określić właściwości oraz szablonów, które mają wpływ na szerokość kolumny bezpośrednio na klasy, które definiują <xref:System.Windows.Controls.GridView> trybu wyświetlania.  
  
 Na przykład, aby dodać <xref:System.Windows.Controls.CheckBox> do wierszy w <xref:System.Windows.Controls.GridView> trybu wyświetlania, Dodaj <xref:System.Windows.Controls.CheckBox> do <xref:System.Windows.DataTemplate>, a następnie ustaw <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> właściwości, do którego <xref:System.Windows.DataTemplate>.  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>Interakcji użytkowników z widoku GridView  
 Jeśli używasz <xref:System.Windows.Controls.GridView> w aplikacji, użytkownicy mogą współpracować z i modyfikować formatowanie <xref:System.Windows.Controls.GridView>. Na przykład użytkownicy mogą zmieniać kolejność kolumn, kolumny, wybierz elementy w tabeli, a następnie przewiń do zawartości. Można również zdefiniować program obsługi zdarzeń, który reaguje, gdy użytkownik kliknie przycisk nagłówka kolumny. Program obsługi zdarzeń mogą wykonywać operacje, takie jak sortowanie danych, która jest wyświetlana w <xref:System.Windows.Controls.GridView> zgodnie z zawartością kolumny.  
  
 Poniżej omówiono bardziej szczegółowo możliwości przy użyciu <xref:System.Windows.Controls.GridView> do interakcji z użytkownikiem:  
  
-   **Zmienianie kolejności kolumn za pomocą metody przeciągania i upuszczania.**  
  
     Użytkownicy mogą zmieniać kolejność kolumn w <xref:System.Windows.Controls.GridView> naciśnięcie przycisku lewego przycisku myszy, gdy znajduje się nad nagłówek kolumny, a następnie przeciągając tej kolumny w nowe położenie. Gdy użytkownik przeciąga nagłówek kolumny, zmiennoprzecinkowych wersji nagłówka jest wyświetlany oraz pełny czarnej linii pokazujący miejsca do wstawienia w kolumnie.  
  
     Jeśli chcesz zmodyfikować domyślny styl przestawne wersji nagłówka, określ <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.GridViewColumnHeader> typ wyzwalane, gdy <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>. Aby uzyskać więcej informacji, zobacz [utworzyć styl nagłówka kolumny widoku GridView przeciągnąć](../../../../docs/framework/wpf/controls/how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
-   **Zmień rozmiar kolumny do jego zawartości.**  
  
     Użytkownicy, można kliknąć dwukrotnie uchwytu z prawej strony nagłówek kolumny, aby zmienić rozmiar kolumny w celu dopasowania do jego zawartości.  
  
    > [!NOTE]
    >  Można ustawić <xref:System.Windows.Controls.GridViewColumn.Width%2A> właściwości `Double.NaN` aby wygenerować ten sam efekt.  
  
-   **Wybierz elementy wiersza.**  
  
     Użytkownicy mogą wybrać co najmniej jeden element w <xref:System.Windows.Controls.GridView>.  
  
     Jeśli chcesz zmienić <xref:System.Windows.Style> wybranego elementu, zobacz [Użyj wyzwalaczy Style wybranych elementów w elemencie ListView](../../../../docs/framework/wpf/controls/how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
-   **Przewiń, aby wyświetlić zawartość, która nie jest początkowo widoczne na ekranie.**  
  
     Jeśli rozmiar <xref:System.Windows.Controls.GridView> jest zbyt mały, aby wyświetlić wszystkie elementy, użytkownicy mogą być przewijane w poziomie lub pionie za pomocą pasków przewijania, które są dostarczane przez <xref:System.Windows.Controls.ScrollViewer> formantu. A <xref:System.Windows.Controls.Primitives.ScrollBar> jest ukryty, jeśli cała zawartość jest widoczna w określonym kierunku. Nagłówki kolumn nie przewijania z pionowego paska przewijania, ale przewijane w poziomie.  
  
-   **Interakcje z kolumn za pomocą przycisków nagłówka kolumny.**  
  
     Gdy użytkownik kliknie przycisk nagłówka kolumny, posortuj dane, które jest wyświetlana w kolumnie, jeśli zostały podane algorytm sortowania.  
  
     Może obsłużyć <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia dla przycisków nagłówka kolumny w celu zapewnienia funkcji takich jak algorytm sortowania. Do obsługi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia dla pojedynczej kolumny nagłówka, Ustaw program obsługi zdarzeń na <xref:System.Windows.Controls.GridViewColumnHeader>. Aby ustawić program obsługi zdarzeń, która obsługuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia dla wszystkich nagłówków kolumn, ustawić programu obsługi na <xref:System.Windows.Controls.ListView> kontroli.  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>Uzyskiwanie innych widoków niestandardowych  
 <xref:System.Windows.Controls.GridView> Klasy, która jest pochodną <xref:System.Windows.Controls.ViewBase> klasę abstrakcyjną, jest tylko jeden z trybów widok dla <xref:System.Windows.Controls.ListView> klasy. Można utworzyć innych widoków dla <xref:System.Windows.Controls.ListView> przez pochodny <xref:System.Windows.Controls.ViewBase> klasy. Na przykład widok niestandardowy tryb zobacz [utworzyć niestandardowy tryb wyświetlania na elemencie ListView](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>Klasy obsługi widoku GridView  
 Następujące klasy pomocy technicznej <xref:System.Windows.Controls.GridView> trybu wyświetlania.  
  
-   <xref:System.Windows.Controls.GridViewColumn>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GridViewRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewColumnCollection>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.ListViewItem>  
 <xref:System.Windows.Controls.GridViewColumn>  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.ViewBase>  
 [ListView — omówienie](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Sortowanie kolumny GridView po kliknięciu nagłówka](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
