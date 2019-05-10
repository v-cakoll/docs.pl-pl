---
title: GridView — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: d1b9efb4016fbc3c4f7e14ea4a1c63308d992504
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649174"
---
# <a name="gridview-overview"></a>GridView — Przegląd
<xref:System.Windows.Controls.GridView> tryb widoku to jeden z trybów wyświetlania dla <xref:System.Windows.Controls.ListView> kontroli. <xref:System.Windows.Controls.GridView> Klasy i jej klasy pomocnicze umożliwiają Ty i Twoi użytkownicy elementu przeglądać kolekcje w tabeli, która zwykle używa przyciski jako nagłówków kolumn interaktywne. W tym temacie przedstawiono <xref:System.Windows.Controls.GridView> klasy i opisano jego użycia.  

<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>Co to jest widok GridView  
 <xref:System.Windows.Controls.GridView> Widoku tryb Wyświetla listę elementów danych przez powiązanie pola danych do kolumn i wyświetlając nagłówek kolumny w celu identyfikacji pola. Wartość domyślna <xref:System.Windows.Controls.GridView> styl implementuje przyciski jako nagłówków kolumn. Za pomocą przycisków dla nagłówków kolumn, można zaimplementować możliwości interakcji użytkownika ważne; na przykład użytkownicy będą mogli kliknąć nagłówek kolumny, aby posortować <xref:System.Windows.Controls.GridView> danych zgodnie z zawartością określonej kolumny.  
  
> [!NOTE]
>  Formanty przycisków, które <xref:System.Windows.Controls.GridView> zastosowań nagłówki kolumn są uzyskiwane z <xref:System.Windows.Controls.Primitives.ButtonBase>.  
  
 Poniższa ilustracja przedstawia <xref:System.Windows.Controls.GridView> widoku <xref:System.Windows.Controls.ListView> zawartości.  
    
 ![Zrzut ekranu przedstawiający widok GridView zawartości ListView.](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView> kolumny są reprezentowane przez <xref:System.Windows.Controls.GridViewColumn> obiektów, które można automatycznie rozmiar do ich zawartości. Opcjonalnie można jawnie ustawić <xref:System.Windows.Controls.GridViewColumn> określonej szerokości. Można zmienić rozmiar kolumn przez przeciągnięcie uchwytu między nagłówków kolumn. Możesz również dynamicznie dodać, usunąć, Zastąp i zmienić kolejność kolumn, ponieważ ta funkcja jest wbudowana w <xref:System.Windows.Controls.GridView>. Jednak <xref:System.Windows.Controls.GridView> bezpośrednio nie można zaktualizować danych, który jest wyświetlany.  
  
 Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.GridView> wyświetlającą dane pracowników. W tym przykładzie <xref:System.Windows.Controls.ListView> definiuje `EmployeeInfoDataSource` jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Definicje właściwości <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> powiązać <xref:System.Windows.Controls.GridViewColumn> zawartości `EmployeeInfoDataSource` kategorii danych.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Na poniższej ilustracji przedstawiono tabelę w poprzednim przykładzie tworzona. W kontrolce GridView wyświetla dane z obiektu ItemsSource:
    
 ![Zrzut ekranu pokazujący ListView z danymi wyjściowymi GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>Styl i układ widoku GridView  
 Komórek kolumny i nagłówek <xref:System.Windows.Controls.GridViewColumn> mają taką samą szerokość. Domyślnie każda kolumna o rozmiarach jego szerokość, do jego zawartości. Opcjonalnie można ustawić kolumny stałej szerokości.  
  
 Powiązane dane zawartości są wyświetlane w poziomie wierszy. Na przykład na poprzedniej ilustracji, numer identyfikacyjny, imię i nazwisko każdego pracownika są wyświetlane jako zestaw ponieważ pojawiają się na poziomie wiersza.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>Definiowanie i style kolumny w widoku GridView  
 Podczas definiowania pola danych do wyświetlenia w <xref:System.Windows.Controls.GridViewColumn>, użyj <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>, <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>, lub <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> właściwości. <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Właściwość ma pierwszeństwo przed albo we właściwościach szablonu.  
  
 Aby określić wyrównanie zawartości w kolumnie <xref:System.Windows.Controls.GridView>, zdefiniuj <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>. Nie używaj <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> i <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> właściwości <xref:System.Windows.Controls.ListView> zawartość, która jest wyświetlana przy użyciu <xref:System.Windows.Controls.GridView>.  
  
 Aby określić właściwości szablonu i style nagłówków kolumn, użyj <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn>, i <xref:System.Windows.Controls.GridViewColumnHeader> klasy. Aby uzyskać więcej informacji, zobacz [omówienie szablony i style nagłówków kolumn GridView](gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>Dodawanie elementów wizualnych w kontrolce GridView  
 Aby dodać elementy wizualne, takie jak <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.Button> kontrolki do <xref:System.Windows.Controls.GridView> trybu wyświetlania, należy użyć szablonów i stylów.  
  
 Jeśli element graficzny jest jawnie zdefiniować jako element danych, może być wyświetlany tylko jeden raz w <xref:System.Windows.Controls.GridView>. To ograniczenie istnieje, ponieważ element może mieć tylko jedną jednostkę nadrzędną i dlatego może znajdować się tylko jeden raz w drzewie wizualnym.  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>Style wierszy w widoku GridView  
 Użyj <xref:System.Windows.Controls.GridViewRowPresenter> i <xref:System.Windows.Controls.GridViewHeaderRowPresenter> klasy formatowania i wyświetlania wierszy <xref:System.Windows.Controls.GridView>. Na przykład, jak do wierszy stylu w <xref:System.Windows.Controls.GridView> trybu wyświetlania, zobacz [styl wierszowi w ListView implementuje czy GridView](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>Wyrównanie w problemy podczas używania ItemContainerStyle  
 Aby zapobiec problemom wyrównanie między nagłówki kolumn i komórki, nie ustawiaj właściwości lub Określ szablon, który wpływa na szerokość elementu w <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Na przykład nie należy ustawiać <xref:System.Windows.FrameworkElement.Margin%2A> właściwości lub określ <xref:System.Windows.Controls.ControlTemplate> dodająca <xref:System.Windows.Controls.CheckBox> do <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> zdefiniowanego na <xref:System.Windows.Controls.ListView> kontroli. Zamiast tego należy określić właściwości i szablony, które wpływają na szerokość kolumny bezpośrednio w klasach, które definiują <xref:System.Windows.Controls.GridView> trybu wyświetlania.  
  
 Na przykład, aby dodać <xref:System.Windows.Controls.CheckBox> do wierszy w <xref:System.Windows.Controls.GridView> trybu wyświetlania, dodawania <xref:System.Windows.Controls.CheckBox> do <xref:System.Windows.DataTemplate>, a następnie ustaw <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> właściwość, która <xref:System.Windows.DataTemplate>.  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>Interakcję użytkownika z GridView  
 Kiedy używasz <xref:System.Windows.Controls.GridView> w aplikacji, użytkownicy mogą wchodzić w interakcje z i zmodyfikować formatowanie <xref:System.Windows.Controls.GridView>. Na przykład użytkownicy mogą zmienić kolejność kolumn, zmiana rozmiaru kolumny, wybierz elementy w tabeli i przewijanie zawartości. Można również zdefiniować program obsługi zdarzeń, które reaguje, gdy użytkownik kliknie przycisk nagłówka kolumny. Program obsługi zdarzeń można wykonać operacji, takich jak sortowanie danych, która jest wyświetlana w <xref:System.Windows.Controls.GridView> zgodnie z zawartością kolumny.  
  
 Poniższa lista w tym artykule omówiono bardziej szczegółowo możliwości korzystania z <xref:System.Windows.Controls.GridView> do interakcji z użytkownikiem:  
  
- **Zmienianie kolejności kolumn przy użyciu metody przeciągania i upuszczania.**  
  
     Użytkownicy mogą zmienić kolejność kolumn w <xref:System.Windows.Controls.GridView> , naciskając klawisze lewy przycisk myszy jest przemieszczany nad nagłówek kolumny, a następnie przeciągając tę kolumnę do nowej pozycji. Gdy użytkownik przeciągnie nagłówek kolumny, zmiennoprzecinkowy wersję nagłówka jest wyświetlany oraz linia ciągła czarny, pokazujący miejsca do wstawienia w kolumnie.  
  
     Jeśli chcesz zmodyfikować domyślny styl zmiennoprzecinkowy wersji nagłówka, należy określić <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.GridViewColumnHeader> typ wyzwalane, gdy <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>. Aby uzyskać więcej informacji, zobacz [Tworzenie stylu dla nagłówka kolumny GridView przeciągnąć](how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
- **Zmień rozmiar kolumny do jego zawartości.**  
  
     Użytkownicy, można kliknąć dwukrotnie uchwytu z prawej strony nagłówka kolumny, aby można było zmienić rozmiar kolumny w celu dopasowania do jego zawartości.  
  
    > [!NOTE]
    >  Możesz ustawić <xref:System.Windows.Controls.GridViewColumn.Width%2A> właściwość `Double.NaN` aby wygenerować ten sam efekt.  
  
- **Wybierz elementy wierszy.**  
  
     Użytkownicy mogą wybrać jeden lub więcej elementów w <xref:System.Windows.Controls.GridView>.  
  
     Jeśli chcesz zmienić <xref:System.Windows.Style> wybranego elementu, zobacz [używanie wyzwalaczy do zaznaczonego elementu w ListView, styl](how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
- **Przewiń do wyświetlania zawartości, który nie jest początkowo widoczne na ekranie.**  
  
     Jeśli rozmiar <xref:System.Windows.Controls.GridView> jest zbyt mały, aby wyświetlić wszystkie elementy, użytkownicy mogą być przewijane w poziomie lub pionie za pomocą paski przewijania, które są dostarczane przez <xref:System.Windows.Controls.ScrollViewer> kontroli. Element <xref:System.Windows.Controls.Primitives.ScrollBar> jest ukryta, jeśli cała zawartość jest widoczna w określonym kierunku. Nagłówki kolumn przewijane pionowy pasek przewijania, ale być przewijane w poziomie.  
  
- **Za pomocą przycisków nagłówka kolumny wchodzić w interakcje z kolumnami.**  
  
     Gdy użytkownik kliknie przycisk nagłówka kolumny, posortuj dane, które jest wyświetlane w kolumnie, jeśli podano algorytmu sortowania.  
  
     Może obsługiwać <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń dla przycisków nagłówek kolumny w celu zapewnienia funkcji, takich jak algorytmu sortowania. Aby obsłużyć <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia dla nagłówka jedną kolumnę, ustawić programu obsługi zdarzeń dla <xref:System.Windows.Controls.GridViewColumnHeader>. Aby ustawić program obsługi zdarzeń, który obsługuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia dla wszystkich nagłówków kolumn, ustawić programu obsługi na <xref:System.Windows.Controls.ListView> kontroli.  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>Uzyskiwanie innych widoków niestandardowych  
 <xref:System.Windows.Controls.GridView> Klasy, która jest pochodną <xref:System.Windows.Controls.ViewBase> abstrakcyjna klasa, jest to tylko jeden z trybów widok dla <xref:System.Windows.Controls.ListView> klasy. Można utworzyć inne widoki niestandardowe dotyczące <xref:System.Windows.Controls.ListView> przez pochodząca od <xref:System.Windows.Controls.ViewBase> klasy. Na przykład niestandardowy tryb widoku zobacz [Tworzenie niestandardowego trybu widoku dla ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>Klasy obsługi widoku GridView  
 Następujące klasy pomocy technicznej <xref:System.Windows.Controls.GridView> trybu wyświetlania.  
  
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
