---
title: "Wskazówki: Pierwszy WPF pulpitu aplikację"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: "71"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 16ed99181f8462e805638b5d3881464b16f21177
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Wskazówki: Pierwszy WPF pulpitu aplikację
Ten przewodnik zawiera wprowadzenie do rozwoju [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] aplikacji, która zawiera elementy, które są wspólne dla większości [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji: [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] znaczników, związane z kodem, definicji aplikacji, kontrolki, układ Powiązanie danych i style. 
  
 Ten przewodnik zawiera informacje rozwoju prostą [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, wykonując następujące kroki. 
  
-   Definiowanie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do projektowania wyglądu aplikacji [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. 
  
-   Pisanie kodu do kompilacji zachowania aplikacji. 
  
-   Tworzenie definicji aplikacji, aby zarządzać aplikacją. 
  
-   Dodawanie formantów i tworzenie układu utworzenie aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. 
  
-   Tworzenie stylów, aby utworzyć spójny wygląd aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. 
  
-   Powiązanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] danych zarówno wypełnić [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z danych i Zachowaj dane i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zsynchronizowane. 
  
 Do końca tego przewodnika, dlatego zostanie utworzone autonomiczny [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] aplikacji, która umożliwia użytkownikom wyświetlanie raportów wydatków dla wybranych użytkowników. Aplikacja będzie składać się z kilku [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] stron, które znajdują się w oknie stylu przeglądarki. 
  
 Przykładowy kod, który jest używany do tworzenia tego przewodnika jest dostępny dla obu [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] i [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] w [wprowadzenie do tworzenia aplikacji WPF](http://go.microsoft.com/fwlink/?LinkID=160008). 

## <a name="prerequisites"></a>Wymagania wstępne  

- [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]lub nowszy

Aby uzyskać więcej informacji na temat instalowania najnowszej wersji programu Visual Studio, zobacz [program Visual Studio](/visualstudio/install/install-visual-studio).
  
## <a name="creating-the-application-project"></a>Tworzenie projektu aplikacji  
 W tej sekcji utworzysz infrastruktury aplikacji, w tym definicji aplikacji, dwie strony i obrazu. 
  
1. Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub Visual C# o nazwie `ExpenseIt`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego projektu aplikacji WPF](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82). 
  
    > [!NOTE]
    >  W tym przewodniku zastosowano <xref:System.Windows.Controls.DataGrid> formant, który jest dostępny w .NET Framework 4. Należy się upewnić, że projekt jest przeznaczony dla programu .NET Framework 4 lub nowszej. Aby uzyskać więcej informacji, zobacz[porady: wersja docelowa platformy .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework). 
  
2. Otwórz Application.xaml (Visual Basic) lub App.xaml (C#). 
  
     To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik definiuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji i wszystkie zasoby aplikacji. Ten plik możesz również użyć do określenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] które automatycznie pokazuje podczas uruchamiania aplikacji; w takim przypadku MainWindow.xaml. 
  
     Twoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] powinna wyglądać następująco w języku Visual Basic:  
  
    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     Lub podobny do tego w języku C#:  
  
    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3. Open MainWindow.xaml. 
  
     To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik jest w głównym oknie aplikacji i wyświetla zawartości dla strony. <xref:System.Windows.Window> Klasa definiuje właściwości okna, takie jak jego tytuł, rozmiaru lub ikona i obsługuje zdarzenia, takie jak zamknięcie lub ukrywanie. 
  
4. Zmień <xref:System.Windows.Window> elementu <xref:System.Windows.Navigation.NavigationWindow>. 
  
     Ta aplikacja przejdzie do innej zawartości w zależności od interakcji z użytkownikiem. W związku z tym głównym <xref:System.Windows.Window> musi zostać zmienione w celu <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow>dziedziczy wszystkie właściwości <xref:System.Windows.Window>. <xref:System.Windows.Navigation.NavigationWindow> Elementu w pliku XAML tworzy wystąpienie <xref:System.Windows.Navigation.NavigationWindow> klasy. Aby uzyskać więcej informacji, zobacz [omówienie nawigacji](../../../../docs/framework/wpf/app-development/navigation-overview.md). 
  
5. Zmień następujące właściwości na <xref:System.Windows.Navigation.NavigationWindow> elementu:  
  
    -   Ustaw <xref:System.Windows.Window.Title%2A> dla właściwości "Programu ExpenseIt". 
  
    -   Ustaw <xref:System.Windows.FrameworkElement.Width%2A> właściwości do 500 pikseli. 
  
    -   Ustaw <xref:System.Windows.FrameworkElement.Height%2A> właściwości 350 pikseli. 
  
    -   Usuń <xref:System.Windows.Controls.Grid> elementy między <xref:System.Windows.Navigation.NavigationWindow> tagów. 
  
     Twoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] powinna wyglądać następująco w języku Visual Basic:  
  
    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     Lub podobny do tego w języku C#:  
  
    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6. Otwórz MainWindow.xaml.vb lub MainWindow.xaml.cs. 
  
     Ten plik jest plikiem CodeBehind, zawierającego kod obsługujący zdarzenia zadeklarowany w MainWindow.xaml. Ten plik zawiera klasę częściową dla okna zdefiniowany w języku XAML. 
  
7. Jeśli używasz języka C#, zmień `MainWindow` pochodzi od klasy <xref:System.Windows.Navigation.NavigationWindow>. 
  
     W języku Visual Basic odbywa się to automatycznie po zmianie okna w języku XAML. 
  
     Kod powinien wyglądać następująco. 
  
    [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
    [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
## <a name="adding-files-to-the-application"></a>Dodawanie plików do aplikacji  
 W tej sekcji możesz dodać dwie strony i obraz do aplikacji. 
  
1. Dodawanie nowej strony (WPF) do projektu o nazwie `ExpenseItHome.xaml`. Aby uzyskać więcej informacji, zobacz [porady: dodawanie nowych elementów do projektu WPF](http://msdn.microsoft.com/library/17e6b238-fc32-4385-98ef-2f66ca09d9ad). 
  
     Ta strona jest pierwszą stroną, która jest wyświetlana, gdy aplikacja jest uruchamiana. Pojawi się lista osób, z którego użytkownik może wybrać osobę, aby wyświetlić raport wydatków dla. 
  
2. Open ExpenseItHome.xaml. 
  
3. Ustaw <xref:System.Windows.Controls.Page.Title%2A> do programu "ExpenseIt — strona główna". 
  
     Twoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] powinna wyglądać następująco w języku Visual Basic:  
  
    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     Lub to w języku C#:  
  
    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4. Open MainWindow.xaml. 
  
5. Ustaw <xref:System.Windows.Navigation.NavigationWindow.Source%2A> właściwość <xref:System.Windows.Navigation.NavigationWindow> do "ExpenseItHome.xaml". 
  
     To ustawienie ExpenseItHome.xaml się na pierwszej stronie otwarty podczas uruchamiania aplikacji. Twoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] powinna wyglądać następująco w języku Visual Basic:  
  
    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     Lub to w języku C#:  
  
    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6. Dodawanie nowej strony (WPF) do projektu o nazwie `ExpenseReportPage.xaml`. 
  
     Ta strona będzie przedstawiał raportu wydatków wybranego na ExpenseItHome.xaml osoby. 
  
7. Open ExpenseReportPage.xaml. 
  
8. Ustaw <xref:System.Windows.Controls.Page.Title%2A> do programu "ExpenseIt — widok wydatków". 
  
     Twoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] powinna wyglądać następująco w języku Visual Basic:  
  
    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     Lub to w języku C#:  
  
    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. Otwórz ExpenseItHome.xaml.vb i ExpenseReportPage.xaml.vb, lub ExpenseItHome.xaml.cs i ExpenseReportPage.xaml.cs. 
  
     Visual Studio automatycznie tworzy w kodzie pliku, podczas tworzenia nowego pliku strony. Te pliki związane z kodem obsługi logiki w odpowiedzi na dane wejściowe użytkownika. 
  
     Kod powinien wyglądać następująco. 
  
    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. Dodaj obraz o nazwie watermark.png do projektu. Można utworzyć własny obraz lub skopiuj plik z przykładowym kodzie. Aby uzyskać więcej informacji, zobacz [NIB: porady: Dodawanie istniejących elementów do projektu](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3). 

## <a name="building-and-running-the-application"></a>Tworzenie i uruchamianie aplikacji  
 W tej sekcji możesz skompilować i uruchomić aplikację. 
  
1. Tworzenie i uruchamianie aplikacji, naciskając klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu. 
  
     Na poniższej ilustracji przedstawiono aplikację z <xref:System.Windows.Navigation.NavigationWindow> przycisków. 
  
     ![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
2. Zamknij aplikację, aby powrócić do [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]. 
  
## <a name="creating-the-layout"></a>Tworzenie układu  
 Układ zapewnia uporządkowanej sposób umieść [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów i zarządza także rozmiar i położenie tych elementów podczas [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] rozmiar jest zmieniany. Jeden z poniższych formantów układu są zwykle Utwórz układ:  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 Każdy z tych kontrolek układu obsługuje specjalny rodzaj układu jego elementów podrzędnych. Można zmienić rozmiar strony programu ExpenseIt i każdego strona zawiera elementy, które są rozmieszczone w poziomie i w pionie równolegle z innymi elementami. W rezultacie <xref:System.Windows.Controls.Grid> jest elementem układu idealne dla aplikacji. 
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.Panel> elementów, zobacz [omówienie panele](../../../../docs/framework/wpf/controls/panels-overview.md). Aby uzyskać więcej informacji o układzie, zobacz [układu](../../../../docs/framework/wpf/advanced/layout.md). 
  
 W sekcji tworzenia jednokolumnową tabelę z trzy wiersze i margines 10 pikseli, dodając definicje kolumn i wierszy do <xref:System.Windows.Controls.Grid> w ExpenseItHome.xaml. 
  
1. Open ExpenseItHome.xaml. 
  
2. Ustaw <xref:System.Windows.FrameworkElement.Margin%2A> właściwość <xref:System.Windows.Controls.Grid> elementu "10,0,10,10", co odpowiada po lewej, górnej, prawej i dolnego marginesu. 
  
3. Dodaj następujące [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] między <xref:System.Windows.Controls.Grid> tagi do tworzenia definicji wierszy i kolumn. 
  
    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     <xref:System.Windows.Controls.RowDefinition.Height%2A> Dwa wiersze jest ustawiony na wartość <xref:System.Windows.GridLength.Auto%2A> podstawowa co oznacza, że będzie ustalany wiersze w zawartości w wierszach. Wartość domyślna <xref:System.Windows.Controls.RowDefinition.Height%2A> jest <xref:System.Windows.GridUnitType.Star> zmiany rozmiaru, co oznacza, że wiersz będzie ważona część dostępnego miejsca. Na przykład mieć dwa wiersze wysokość "*", miało wysokości połowy dostępnego miejsca.  
  
     Twoje <xref:System.Windows.Controls.Grid> powinna wyglądać tak jak XAML następujące:  
  
    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
## <a name="adding-controls"></a>Dodawanie formantów  
 W tej sekcji, strony głównej [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jest aktualizowany, aby wyświetlić listę osób, że użytkownicy mogą wybierać z do wyświetlenia raportu z wydatków dla wybranej osoby. Formanty są obiektami interfejsu użytkownika, które zezwala użytkownikom na interakcję z aplikacją. Aby uzyskać więcej informacji, zobacz [formanty](../../../../docs/framework/wpf/controls/index.md). 
  
 Aby utworzyć ten [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], następujące elementy są dodawane do ExpenseItHome.xaml:  
  
-   <xref:System.Windows.Controls.ListBox>(Aby uzyskać listę osób). 
  
-   <xref:System.Windows.Controls.Label>(dla nagłówka listy). 
  
-   <xref:System.Windows.Controls.Button>(aby kliknij, aby wyświetlić raport wydatków dla osoby, która jest zaznaczony na liście). 
  
 Każdy formant znajduje się w wierszu <xref:System.Windows.Controls.Grid> przez ustawienie <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> dołączona właściwość. Aby uzyskać więcej informacji na temat dołączone właściwości, zobacz [dołączony Przegląd właściwości](../../../../docs/framework/wpf/advanced/attached-properties-overview.md). 
  
1. Open ExpenseItHome.xaml. 
  
2. Dodaj następujące [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] między <xref:System.Windows.Controls.Grid> tagów. 
  
    [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3. Skompiluj i uruchom aplikację. 
  
 Na poniższej ilustracji przedstawiono formantów, które zostały utworzone przy użyciu języka XAML w tej sekcji. 
  
 ![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
## <a name="adding-an-image-and-a-title"></a>Dodawanie obrazu i tytuł  
 W tej sekcji, strony głównej [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] został zaktualizowany o obrazu i tytuł strony. 
  
1. Open ExpenseItHome.xaml. 
  
2. Dodaj inną kolumnę do <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> ze stałym <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pikseli. 
  
    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3. Dodaj nowy wiersz do <xref:System.Windows.Controls.Grid.RowDefinitions%2A>. 
  
    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4. Przenieś formanty do drugiej kolumny przez ustawienie <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> do 1. Przesuń kontrolkę każdy wiersz w dół przez odpowiednie zwiększenie <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> o 1. 
  
    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5. Ustaw <xref:System.Windows.Controls.Panel.Background%2A> z <xref:System.Windows.Controls.Grid> jako watermark.png pliku obrazu. 
  
    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6. Przed <xref:System.Windows.Controls.Border>, Dodaj <xref:System.Windows.Controls.Label> z zawartością "Wyświetl raport o wydatkach" jako tytuł strony. 
  
    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7. Skompiluj i uruchom aplikację. 
  
 Na poniższej ilustracji przedstawiono wyniki w tej sekcji. 
  
 ![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
## <a name="adding-code-to-handle-events"></a>Dodawanie kodu do obsługi zdarzeń  
  
1. Open ExpenseItHome.xaml. 
  
2. Dodaj <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń do <xref:System.Windows.Controls.Button> elementu. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie prostego obsługi zdarzeń](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480). 
  
    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3. Otwórz ExpenseItHome.xaml.vb lub ExpenseItHome.xaml.cs. 
  
4. Dodaj następujący kod do <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń, co powoduje, że okno, aby przejść do pliku ExpenseReportPage.xaml. 
  
    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
## <a name="creating-the-ui-for-expensereportpage"></a>Tworzenie interfejsu użytkownika dla ExpenseReportPage  
 ExpenseReportPage.xaml wyświetla raport wydatków dla osoby, która została wybrana na ExpenseItHome.xaml. W tej sekcji dodaje formantów i tworzy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla ExpenseReportPage.xaml. W tej sekcji dodaje również kolory tła i wypełnienia do różnych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów. 
  
1. Open ExpenseReportPage.xaml. 
  
2. Dodaj następujące XAML między <xref:System.Windows.Controls.Grid> tagów. 
  
     Interfejs ten jest podobny do interfejsu użytkownika utworzone na ExpenseItHome.xaml, z wyjątkiem danych raportu jest wyświetlany w <xref:System.Windows.Controls.DataGrid>. 
  
    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3. Skompiluj i uruchom aplikację. 
  
    > [!NOTE]
    >  Jeśli występuje błąd <xref:System.Windows.Controls.DataGrid> nie został znaleziony lub nie istnieje, upewnij się, że projekt jest przeznaczony dla programu .NET Framework 4 lub nowszej. Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework). 
  
4. Kliknij przycisk **widoku** przycisku. 
  
     Zostanie wyświetlona strona raportu wydatków. 
  
 Na poniższej ilustracji pokazano [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy dodane do ExpenseReportPage.xaml. Zwróć uwagę, że jest włączony przycisk nawigacji Wstecz. 
  
 ![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
## <a name="styling-controls"></a>Style formantów  
 Wygląd różnych elementów często może być taka sama dla wszystkich elementów tego samego typu w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]używa style aby wygląd wielokrotnego użytku przez wiele elementów. Możliwość ponownego wykorzystania stylów pozwala uprościć [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tworzenie i zarządzanie nimi. Aby uzyskać więcej informacji na temat stylów, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md). W tej sekcji zastępuje atrybutów na elementów, które zostały zdefiniowane w poprzednich krokach przy użyciu stylów. 
  
1. Otwórz Application.xaml lub pliku App.xaml. 
  
2. Dodaj następujące XAML między <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tagów:  
  
    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dodaje następujące style:  
  
    -  `headerTextStyle`: Aby sformatować tytuł strony <xref:System.Windows.Controls.Label>. 
  
    -  `labelStyle`: Do formatowania <xref:System.Windows.Controls.Label> kontrolki. 
  
    -  `columnHeaderStyle`: Do formatowania <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>. 
  
    -  `listHeaderStyle`: Do formatowania nagłówków <xref:System.Windows.Controls.Border> kontrolki. 
  
    -  `listHeaderTextStyle`: Do formatowania nagłówków <xref:System.Windows.Controls.Label>. 
  
    -  `buttonStyle`: Do formatowania <xref:System.Windows.Controls.Button> na ExpenseItHome.xaml. 
  
     Style są zasobów i elementy podrzędne <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elementu właściwości. W tej lokalizacji style są stosowane do wszystkich elementów w aplikacji. Przykład użycia zasobów w [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplikacji, zobacz [wykorzystania zasobów aplikacji](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md). 
  
3. Open ExpenseItHome.xaml. 
  
4. Zastąp wszystko pomiędzy <xref:System.Windows.Controls.Grid> elementy o następujących XAML. 
  
    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     Właściwości, takie jak <xref:System.Windows.VerticalAlignment> i <xref:System.Windows.Media.FontFamily> definiujących wygląd każdej kontrolki usunięty i zastąpiony, stosując style. Na przykład `headerTextStyle` jest stosowany do "Wyświetl raport wydatków" <xref:System.Windows.Controls.Label>. 
  
5. Open ExpenseReportPage.xaml. 
  
6. Zastąp wszystko pomiędzy <xref:System.Windows.Controls.Grid> elementy o następujących XAML. 
  
    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     Spowoduje to dodanie stylów <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Border> elementy. 
  
7. Skompiluj i uruchom aplikację. 
  
     Po dodaniu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w tej sekcji aplikacji wygląda tak samo jak przed aktualizowany przy użyciu stylów. 
  
## <a name="binding-data-to-a-control"></a>Wiązanie danych do formantu  
 W tej sekcji utworzysz [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] danych, który jest powiązany z różnych formantów. 
  
1. Open ExpenseItHome.xaml. 
  
2. Po otwarciu <xref:System.Windows.Controls.Grid> elementu, Dodaj następujący kod XAML, aby utworzyć <xref:System.Windows.Data.XmlDataProvider> dla każdej osoby, która zawiera dane. 
  
     Dane są tworzone jako <xref:System.Windows.Controls.Grid> zasobów. Zwykle będzie to być ładowane jako plik, ale dla uproszczenia dane są dodawane wbudowanego. 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3. W <xref:System.Windows.Controls.Grid> zasobów, Dodaj następujący <xref:System.Windows.DataTemplate>, który definiuje sposób wyświetlania danych w <xref:System.Windows.Controls.ListBox>. Aby uzyskać więcej informacji na temat szablonów danych, zobacz [omówienie tworzenia szablonów danych](../../../../docs/framework/wpf/data/data-templating-overview.md). 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4. Zastąp istniejące <xref:System.Windows.Controls.ListBox> z następujących XAML. 
  
    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     Wiąże się to XAML <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ListBox> ze źródłem danych i stosuje szablon danych jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>. 
  
## <a name="connecting-data-to-controls"></a>Łączenie danych z formantami  
 W tej sekcji napisać kod, który pobiera bieżący element jest zaznaczony na liście osób na stronie ExpenseItHome.xaml i przekazuje jego odwołania do konstruktora obiektu `ExpenseReportPage` podczas tworzenia wystąpienia. `ExpenseReportPage`Ustawia jego kontekst danych o elemencie przekazany jest formanty zdefiniowanych w ExpenseReportPage.xaml zostanie z nim powiązane. 
  
1. Otwórz ExpenseReportPage.xaml.vb lub ExpenseReportPage.xaml.cs. 
  
2. Dodaj Konstruktor pobierający obiekt, więc można przekazać dane raportu wydatków wybranego użytkownika. 
  
    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3. Otwórz ExpenseItHome.xaml.vb lub ExpenseItHome.xaml.cs. 
  
4. Zmień <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obsługi zdarzeń do wywołania konstruktora new przekazywanie danych raportu wydatków wybrane osoby. 
  
    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
## <a name="styling-data-with-data-templates"></a>Style danych za pomocą szablonów danych  
 W tej sekcji możesz zaktualizować [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla każdego elementu w danych powiązane listy przy użyciu szablonów danych. 
  
1. Open ExpenseReportPage.xaml. 
  
2. Powiąż z zawartością "Name" i "Dział" <xref:System.Windows.Controls.Label> właściwość źródła elementy do odpowiednich danych. Aby uzyskać więcej informacji na temat wiązania danych, zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md). 
  
    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3. Po otwarciu <xref:System.Windows.Controls.Grid> elementu, Dodaj następujące szablony danych, które określają sposób wyświetlania danych raportu wydatków.  
    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4. Stosować szablony do <xref:System.Windows.Controls.DataGrid> kolumny wyświetlające wydatków danych raportu. 
  
    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5. Skompiluj i uruchom aplikację. 
  
6. Wybierz osoby, a następnie kliknij przycisk **widoku** przycisku. 
  
 Na poniższej ilustracji przedstawiono obie strony aplikacji programu ExpenseIt z formantami, układ, style, powiązania danych i zastosować szablony danych. 
  
 ![Zrzuty ekranu programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
## <a name="best-practices"></a>Najlepsze praktyki  
 Ten przykład przedstawia określoną funkcję WPF i w związku z tym, nie jest zgodna z najlepszych rozwiązań tworzenia aplikacji. Dla kompleksowym omówieniem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] najlepszych rozwiązań tworzenia aplikacji, zgodnie z potrzebami, zobacz następujące tematy:  
  
-   Dostępność — [najlepsze praktyki dotyczące ułatwień dostępu](../../../../docs/framework/ui-automation/accessibility-best-practices.md)  
  
-   Zabezpieczenia — [zabezpieczeń](../../../../docs/framework/wpf/security-wpf.md)  
  
-   Lokalizacja — [omówienie lokalizacja i globalizacja WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)  
  
-   Wydajność — [optymalizacji wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
  
## <a name="whats-next"></a>Co to jest dalej  
 Masz teraz szereg technik dyspozycji użytkownika do tworzenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] przy użyciu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Po wykonaniu pełnego zrozumienia podstawowe bloki konstrukcyjne z danymi [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplikacji. W tym temacie w żadnym wypadku nie jest wyczerpująca, ale miejmy nadzieję, że użytkownik ma teraz również w pewnym sensie niektóre możliwości, które można wykryć samodzielnie poza technik w tym temacie. 
  
 Aby uzyskać więcej informacji o modelach programowanie i architektura WPF zobacz następujące tematy:  
  
-   [Architektura WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [Układ](../../../../docs/framework/wpf/advanced/layout.md)  
  
 Aby uzyskać więcej informacji o tworzeniu aplikacji zobacz następujące tematy:  
  
-   [Projektowanie aplikacji](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [Kontrolki](../../../../docs/framework/wpf/controls/index.md)  
  
-   [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [Grafika i multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## <a name="see-also"></a>Zobacz także  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Szablonowanie danych — omówienie](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Kompilowanie aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [Style i szablony](../../../../docs/framework/wpf/controls/styles-and-templates.md)
