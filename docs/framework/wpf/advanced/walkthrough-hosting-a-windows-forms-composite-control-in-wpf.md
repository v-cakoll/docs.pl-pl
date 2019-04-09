---
title: 'Przewodnik: hostowanie kontrolki złożonej Windows Forms w WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: f9e0477b2c186ea9b23886f460caf965a5db0244
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174359"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>Przewodnik: hostowanie kontrolki złożonej Windows Forms w WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferuje rozbudowane środowisko do tworzenia aplikacji. Jednak jeśli masz znaczne inwestycje [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodu, może być bardziej efektywne ponownie użyć co najmniej część tego kodu w swojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, a nie do jego przepisania od podstaw. Najbardziej typowym scenariuszem jest w przypadku istniejących kontrolek Windows Forms. W niektórych przypadkach możesz nawet utracić dostęp do kodu źródłowego dla tych formantów. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera procedury prostym do hostowania te kontrolki w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Na przykład, można użyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dla większości programowania w hostujący usługi specjalistyczne <xref:System.Windows.Forms.DataGridView> kontrolki.  
  
 Ten przewodnik przeprowadzi Cię przez aplikację, która obsługuje złożone kontrolkę Windows Forms do wykonywania wprowadzania danych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Złożonej kontrolki jest dostarczana w bibliotece DLL. Ta procedura ogólne można rozszerzyć do bardziej złożonych aplikacji i formantów. Ten przewodnik jest przeznaczony do niemal identyczne w wyglądu i działania [instruktażu: Hosting złożonego formantu WPF w formularzach Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md). Podstawowa różnica polega na tym, że scenariusza hostingu została odwrócona.  
  
 Ekran instruktażu jest podzielony na dwie sekcje. Pierwsza sekcja krótko opisano wykonania złożonego formantu Windows Forms. Druga sekcja w tym artykule omówiono szczegółowo sposobu hostowania złożonej kontrolki w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, odbieranie zdarzeń z kontrolki i uzyskiwać dostęp do niektórych właściwości formantu.  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Implementowanie złożonego formantu Windows Forms.  
  
-   Implementowanie aplikacja hosta WPF.  
  
 Lista zadań przedstawione w niniejszym przewodniku kompletny kod znajduje się [Hosting kontrolki złożonej formularzy Windows w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=159999).  
  
## <a name="prerequisites"></a>Wymagania wstępne  

Potrzebujesz programu Visual Studio w celu przeprowadzenia tego instruktażu.
  
## <a name="implementing-the-windows-forms-composite-control"></a>Implementowanie formantu złożonego programu Windows Forms  
 Kontrolek złożonych Windows Forms używane w tym przykładzie jest formą proste wprowadzanie danych. Ten formularz przyjmuje nazwę użytkownika i adres, a następnie używa niestandardowego zdarzenia w celu zwracania tych informacji do hosta. Poniższa ilustracja przedstawia renderowanych kontroli.  

 Na poniższej ilustracji przedstawiono złożonego formantu Windows Forms:  

 ![Zrzut ekranu, który pokazuje prosty formant Windows Forms.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a>Tworzenie projektu  
 Aby uruchomić projekt:  
  
1.  Uruchom [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], a następnie otwórz **nowy projekt** okno dialogowe.  
  
2.  W kategorii oknie Wybierz **Biblioteka kontrolek formularzy Windows** szablonu.  
  
3.  Nazwa nowego projektu `MyControls`.  
  
4.  Dla lokalizacji, określ wygodnie nazwane folder najwyższego poziomu, takie jak `WpfHostingWindowsFormsControl`. Później należy umieścić aplikacji hosta w tym folderze.  
  
5.  Kliknij przycisk **OK** do tworzenia projektu. Domyślny projekt zawiera jeden formant o nazwie `UserControl1`.  
  
6.  W Eksploratorze rozwiązań, zmienianie nazwy `UserControl1` do `MyControl1`.  
  
 Projekt powinien mieć odwołania do następujących systemowych bibliotek DLL. Jeśli dowolny z tych bibliotek DLL nie są włączone domyślnie, należy je dodać do projektu.  
  
-   System  
  
-   System.Data  
  
-   System.Drawing  
  
-   System.Windows.Forms  
  
-   System.Xml  
  
### <a name="adding-controls-to-the-form"></a>Dodawanie formantów do formularza  
 Aby dodać formanty do formularza:  
  
-   Otwórz `MyControl1` w projektancie.  
  
 Dodaj 5 <xref:System.Windows.Forms.Label> kontrolek i odpowiadające im <xref:System.Windows.Forms.TextBox> formantów, rozmiar i tak jak są one na poprzedniej ilustracji, na formularzu. W tym przykładzie <xref:System.Windows.Forms.TextBox> formantów są nazywane:  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 Dodaj dwie <xref:System.Windows.Forms.Button> przycisk kontrolek oznaczonych **OK** i **anulować**. W tym przykładzie są nazwy przycisków `btnOK` i `btnCancel`, odpowiednio.  
  
### <a name="implementing-the-supporting-code"></a>Implementowanie obsługi kodu  
 Otwórz formularz w widoku kodu. Formant powraca zebranych danych do jej hosta, tworząc niestandardowy `OnButtonClick` zdarzeń. Dane są zawarte w obiekcie argumentu zdarzenia. Poniższy kod przedstawia deklaracji zdarzeń i delegata.  
  
 Dodaj następujący kod do `MyControl1` klasy.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 `MyControlEventArgs` Klasa zawiera informacje, które mają zostać zwrócona do hosta.

 Dodaj poniższą klasę do formularza.

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 Po kliknięciu przez użytkownika **OK** lub **anulować** przycisku <xref:System.Windows.Forms.Control.Click> utworzyć procedury obsługi zdarzeń `MyControlEventArgs` obiekt, który zawiera dane i zgłasza `OnButtonClick` zdarzeń. Jedyną różnicą między dwoma obsługi jest argumentu zdarzenia `IsOK` właściwości. Ta właściwość umożliwia hostowi na określenie, której przycisk został kliknięty. Jest równa `true` dla **OK** przycisku i `false` dla **anulować** przycisku. Poniższy kod przedstawia programy obsługi dwóch przycisków.

 Dodaj następujący kod do `MyControl1` klasy.

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>Zapewniając zestawu z silną nazwą i tworzenia zestawu
 Dla tego zestawu odwoływać się [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji musi mieć silną nazwę. Aby utworzyć silnej nazwy, Utwórz plik klucza o Sn.exe i dodaj go do projektu.

1.  Otwórz [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] wiersza polecenia. Aby to zrobić, kliknij przycisk **Start** menu, a następnie wybierz pozycję **wszystkie programy/Microsoft Visual Studio 2010/Visual Studio narzędzia/Visual Studio Command Prompt**. Spowoduje to uruchomienie okna konsoli za pomocą zmiennych środowiskowych dostosowane.

2.  W wierszu polecenia użyj `cd` polecenie, aby przejść do folderu projektu.

3.  Wygeneruj plik klucza o nazwie MyControls.snk, uruchamiając następujące polecenie.

    ```
    Sn.exe -k MyControls.snk
    ```

4.  Aby dołączyć plik klucza w projekcie, kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań, a następnie kliknij przycisk **właściwości**. W Projektancie projektu kliknij **podpisywanie** zaznacz **Podpisz zestaw** zaznacz pole wyboru, a następnie przejdź do Twojego pliku klucza.

5.  Skompiluj rozwiązanie. Kompilacja generuje biblioteki DLL o nazwie MyControls.dll.

## <a name="implementing-the-wpf-host-application"></a>Implementowanie aplikacja hosta WPF
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Hostowanie aplikacji używa <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolki hosta `MyControl1`. Uchwyty aplikacji `OnButtonClick` zdarzenia w celu odbierania danych z formantu. Ma również zbiór przycisków opcji, które umożliwiają zmianę niektórych właściwości formantu z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Na poniższej ilustracji przedstawiono ukończonej aplikacji.

Na poniższej ilustracji przedstawiono kompletnej aplikacji, w tym formantu osadzonego w aplikacji WPF:

 ![Zrzut ekranu pokazujący kontrolki osadzony na stronie programu WPF.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a>Tworzenie projektu
 Aby uruchomić projekt:

1.  Otwórz [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]i wybierz **nowy projekt**.

2.  W kategorii oknie Wybierz **aplikacji WPF** szablonu.

3.  Nazwa nowego projektu `WpfHost`.

4.  Dla lokalizacji należy określić ten sam folder najwyższego poziomu, który zawiera projekt MyControls.

5.  Kliknij przycisk **OK** do tworzenia projektu.

 Należy również dodać odwołania do biblioteki DLL, która zawiera `MyControl1` i innych zestawów.

1.  Kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań i wybierz **Dodaj odwołanie**.

2.  Kliknij przycisk **Przeglądaj** , a następnie przejdź do folderu, który zawiera MyControls.dll. W tym przewodniku ten folder jest MyControls\bin\Debug.

3.  Wybierz MyControls.dll, a następnie kliknij przycisk **OK**.

4.  Dodaj odwołanie do zestawu WindowsFormsIntegration, która nosi nazwę WindowsFormsIntegration.dll.

### <a name="implementing-the-basic-layout"></a>Implementowanie podstawowy układ
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Hosta aplikacji jest zaimplementowana w pliku MainWindow.xaml. Ten plik zawiera [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] znaczników, który definiuje układ i udostępnia kontrolki Windows Forms. Aplikacja jest podzielony na trzy regiony:

-   **Właściwości kontrolki** panel, który zawiera kolekcję przycisków opcji, które służy do modyfikowania różnych właściwości obiektu obsługiwanego formantu.

-   **Danych z formantu** panel, który zawiera kilka <xref:System.Windows.Controls.TextBlock> elementy, które wyświetlają dane zwrócone w wyniku obsługiwanego formantu.

-   Hostowanej sama kontrolka.

 Układ podstawowy jest wyświetlany w następujących XAML. Kod znaczników, który jest potrzebny do hosta `MyControl1` pominięto w tym przykładzie, ale zostanie dokładnie omówione później.

 Zamień na XAML w pliku MainWindow.xaml poniżej. Jeśli używasz języka Visual Basic, zmień klasy, która ma `x:Class="MainWindow"`.

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 Pierwszy <xref:System.Windows.Controls.StackPanel> element zawiera kilka zestawów <xref:System.Windows.Controls.RadioButton> formantów, które umożliwiają modyfikowanie różne właściwości domyślne obsługiwanego formantu. Które następuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, która hostuje `MyControl1`. Końcowe <xref:System.Windows.Controls.StackPanel> element zawiera kilka <xref:System.Windows.Controls.TextBlock> elementy, które wyświetlają dane, który jest zwracany przez kontrolę hostowanej. Kolejność elementów i <xref:System.Windows.Controls.DockPanel.Dock%2A> i <xref:System.Windows.FrameworkElement.Height%2A> ustawień atrybutów osadzanie obsługiwanego formantu w oknie bez przerw i zakłóceń.

#### <a name="hosting-the-control"></a>Hostowanie kontrolki
 Następująca wersja edytowanych poprzedniego XAML koncentruje się na elementy, które są potrzebne do hosta `MyControl1`.

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 `xmlns` Atrybutu mapowania przestrzeni nazw tworzy odwołanie do `MyControls` przestrzeni nazw, który zawiera formant hostowanej. To mapowanie umożliwia reprezentują `MyControl1` w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako `<mcl:MyControl1>`.

 Dwa elementy w XAML obsługi hostingu:

-   `WindowsFormsHost` reprezentuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, który pozwala na hostowanie kontrolki Windows Forms w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.

-   `mcl:MyControl1`, który reprezentuje `MyControl1`, jest dodawany do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu kolekcji podrzędnej. W wyniku tego formantu Windows Forms jest renderowana jako część [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , a następnie może komunikować się z urządzeniem za pomocą aplikacji.

### <a name="implementing-the-code-behind-file"></a>Wdrażanie pliku związanego z kodem
 Plik związany z kodem, MainWindow.xaml.vb lub MainWindow.xaml.cs, zawiera kod proceduralny, która implementuje funkcje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] omówione w poprzedniej sekcji. Dostępne są następujące podstawowe zadania:

-   Program obsługi zdarzeń do dołączania `MyControl1`firmy `OnButtonClick` zdarzeń.

-   Modyfikowanie właściwości różnych `MyControl1`, zależnie od konfiguracji kolekcję przycisków opcji.

-   Wyświetlanie danych zebranych przez kontrolkę.

#### <a name="initializing-the-application"></a>Inicjowanie aplikacji
 Kod inicjowania znajduje się w obsłudze zdarzeń dla okna <xref:System.Windows.FrameworkElement.Loaded> zdarzeń i dołącza program obsługi zdarzeń do formantu `OnButtonClick` zdarzeń.

 W pliku MainWindow.xaml.vb lub MainWindow.xaml.cs Dodaj następujący kod, aby `MainWindow` klasy.

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 Ponieważ [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] omówionych wcześniej dodano `MyControl1` do <xref:System.Windows.Forms.Integration.WindowsFormsHost> kolekcji elementów podrzędnych elementu, można rzutować <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> można pobrać odwołania do `MyControl1`. Następnie można użyć tego odwołania, można dołączyć program obsługi zdarzeń do `OnButtonClick`.

 Ponadto, aby zapewnić odwołanie do samej kontrolce, <xref:System.Windows.Forms.Integration.WindowsFormsHost> eksponuje pewną liczbę właściwości kontrolki, które można manipulować z aplikacji. Kod inicjowania przypisuje te wartości do prywatnej zmienne globalne do późniejszego użycia w aplikacji.

 Tak, aby mogli łatwo uzyskiwać dostęp z typami w `MyControls` biblioteki DLL, Dodaj następujący kod `Imports` lub `using` instrukcji na górze pliku.

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a>Obsługa zdarzeń OnButtonClick
 `MyControl1` wywołuje `OnButtonClick` zdarzenie, kiedy użytkownik kliknie jeden z przycisków kontrolki.

 Dodaj następujący kod do `MainWindow` klasy.

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 Dane w polach tekstowych są pakowane w `MyControlEventArgs` obiektu. Jeśli użytkownik kliknie **OK** przycisk, program obsługi zdarzeń wyodrębnia dane i wyświetla go w panelu poniżej `MyControl1`.

#### <a name="modifying-the-controls-properties"></a>Modyfikowanie właściwości kontrolki
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Elementu udostępnia kilka właściwości domyślnych obsługiwanego formantu. Co w efekcie można zmienić wygląd formantu większe zbliżenie style aplikacji. Zestawy przycisków opcji znajdujących się w lewym panelu zezwolić użytkownikom na modyfikowanie kilka właściwości kolorów i czcionek. Każdy zestaw przycisków ma program obsługi dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie, które wykrywa przycisk Opcje użytkownika i zmienia odpowiedniej właściwości w formancie.

 Dodaj następujący kod do `MainWindow` klasy.

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Skompiluj i uruchom aplikację. Dodaj tekst w złożonego formantu Windows Forms, a następnie kliknij przycisk **OK**. Tekst jest wyświetlany w etykietach. Kliknij przyciski radiowe różnych, aby zobaczyć efekt na formancie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Przewodnik: hostowanie kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Przewodnik: hostowanie kontrolki złożonej WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
