---
title: 'Wskazówki: hosting złożonego formantu Windows Forms w WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: 5868ee8c5b781d5af75349a5950f7e1e1680d74d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>Wskazówki: hosting złożonego formantu Windows Forms w WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępnia bogate środowisko do tworzenia aplikacji. Jeśli masz znaczących inwestycji [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodu, może być bardziej skuteczne ponownie użyć co najmniej części kodu w Twojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji zamiast ponownego wpisywania go od początku. Najbardziej typowym scenariuszem jest w przypadku istniejących formantów formularzy systemu Windows. W niektórych przypadkach nie jeszcze masz dostęp do kodu źródłowego dla tych kontrolek. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera proste procedury obsługi tych kontrolek w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Na przykład można użyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dla większości sieci programowania podczas hosting sieci specjalne <xref:System.Windows.Forms.DataGridView> kontrolki.  
  
 Ten przewodnik zawiera kroki aplikacji, która obsługuje formantu złożonego formularzy systemu Windows do wykonywania wprowadzania danych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Formantu złożonego jest dostarczana w bibliotece DLL. Ta procedura ogólne można rozszerzyć do bardziej złożonych aplikacji i formanty. W tym przewodniku została zaprojektowana jako niemal identyczny jak w wyglądu i działania [wskazówki: hostowanie formantu złożonego WPF w formularzach systemu Windows](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md). Podstawowa różnica polega na tym, czy została odwrócona scenariuszu obsługi.  
  
 Instruktaż jest podzielona na dwie sekcje. Pierwsza sekcja zawiera krótki opis implementacji złożonego formantu formularzy systemu Windows. Druga sekcja omówiono szczegółowo do obsługi złożonych kontrolek w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, odbieranie zdarzeń z formantu i uzyskiwać dostęp do niektórych właściwości formantu.  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Wdrażanie złożonych kontrolek formularzy systemu Windows.  
  
-   Wdrażanie aplikacji hosta WPF.  
  
 Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [Hosting formantu złożonego formularzy systemu Windows w przykładowym WPF](http://go.microsoft.com/fwlink/?LinkID=159999).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="implementing-the-windows-forms-composite-control"></a>Implementowanie złożonego formantu formularzy systemu Windows  
 Złożonych kontrolek formularzy systemu Windows używane w tym przykładzie jest formularzem wprowadzania danych w prostych. Ten formularz przyjmuje nazwę użytkownika i adres, a następnie używa niestandardowych zdarzeń do zwracania informacji do hosta. Na poniższej ilustracji przedstawiono renderowanych formantu.  
  
 ![Formant formularzy systemu Windows proste](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")  
Złożonego formantu formularzy systemu Windows  
  
### <a name="creating-the-project"></a>Tworzenie projektu  
 Aby uruchomić projekt:  
  
1.  Uruchom [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], a następnie otwórz **nowy projekt** okno dialogowe.  
  
2.  W oknie kategorii, wybierz **Biblioteka formantów formularzy systemu Windows** szablonu.  
  
3.  Nazwa nowego projektu `MyControls`.  
  
4.  Do lokalizacji, określ wygodnie nazwanego folder najwyższego poziomu, takich jak `WpfHostingWindowsFormsControl`. Później należy umieścić w folderze aplikacji hosta.  
  
5.  Kliknij przycisk **OK** Aby utworzyć projekt. Domyślny projekt zawiera jeden formant o nazwie `UserControl1`.  
  
6.  W Eksploratorze rozwiązań, Zmień nazwę `UserControl1` do `MyControl1`.  
  
 Projekt powinien mieć odwołania do następującego systemowej biblioteki dll. Jeśli dowolne te biblioteki DLL nie są włączone domyślnie, dodaj je do projektu.  
  
-   System  
  
-   System.Data  
  
-   System.Drawing  
  
-   System.Windows.Forms  
  
-   System.Xml  
  
### <a name="adding-controls-to-the-form"></a>Dodawanie formantów do formularza  
 Do dodawania formantów do formularza:  
  
-   Otwórz `MyControl1` w projektancie.  
  
 Dodaj pięć <xref:System.Windows.Forms.Label> kontrolek i odpowiednie <xref:System.Windows.Forms.TextBox> formantów, wielkości i tak jak znajdują się na poprzedniej ilustracji w formularzu. W tym przykładzie <xref:System.Windows.Forms.TextBox> formanty są o nazwie:  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 Dodaj dwa <xref:System.Windows.Forms.Button> formantów z etykietą **OK** i **anulować**. W tym przykładzie są nazwy przycisków `btnOK` i `btnCancel`odpowiednio.  
  
### <a name="implementing-the-supporting-code"></a>Implementowanie obsługi kodu  
 Otwórz formularz w widoku kodu. Formant zwraca zebranych danych do jej hosta podnosząc niestandardowego `OnButtonClick` zdarzeń. Dane są zawarte w obiekt argument zdarzenia. Poniższy kod przedstawia deklaracja zdarzenia a obiektem delegowanym.  
  
 Dodaj następujący kod do `MyControl1` klasy.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]  
  
 `MyControlEventArgs` Klasa zawiera informacje, które ma zostać zwrócona do hosta.  
  
 Dodaj następujące klasy w formularzu.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]  
  
 Po kliknięciu przez użytkownika **OK** lub **anulować** przycisku <xref:System.Windows.Forms.Control.Click> tworzenie obsługi zdarzeń `MyControlEventArgs` obiekt, który zawiera dane i zgłasza `OnButtonClick` zdarzeń. Argument zdarzenia jest jedyną różnicą między dwóch metod obsługi `IsOK` właściwości. Ta właściwość umożliwia hosta określić, który przycisk został kliknięty. Ma ustawioną wartość `true` dla **OK** przycisk, a `false` dla **anulować** przycisku. Poniższy kod przedstawia programy obsługi dwóch przycisków.  
  
 Dodaj następujący kod do `MyControl1` klasy.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]  
  
### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>Nadanie silnej nazwy zestawu i kompilowania zestawu  
 Dla tego zestawu można odwoływać się [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, musi mieć silnej nazwy. Aby utworzyć silnej nazwy, Utwórz plik klucza o Sn.exe i dodaj go do projektu.  
  
1.  Otwórz [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] wiersza polecenia. Aby to zrobić, kliknij przycisk **Start** menu, a następnie wybierz **wszystkie programy/Microsoft Studio 2010/Visual Studio Tools/Visual Studio wiersz polecenia programu Visual**. Spowoduje to uruchomienie ze zmiennymi dostosowane środowisko okna konsoli.  
  
2.  W wierszu polecenia, użyj `cd` polecenie, aby przejść do folderu projektu.  
  
3.  Generuj plik klucza o nazwie MyControls.snk, uruchamiając następujące polecenie.  
  
    ```  
    Sn.exe -k MyControls.snk  
    ```  
  
4.  Aby dołączyć plik klucza do projektu, kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań, a następnie kliknij przycisk **właściwości**. W Projektancie projektu kliknij **podpisywanie** wybierz opcję **Podpisz zestaw** zaznacz pole wyboru, a następnie przejdź do pliku klucza.  
  
5.  Skompiluj rozwiązanie. Kompilacja utworzy o nazwie MyControls.dll biblioteki DLL.  
  
## <a name="implementing-the-wpf-host-application"></a>Wdrażanie aplikacji hosta WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Hosta aplikacja używa <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantu do hosta `MyControl1`. Uchwyty aplikacji `OnButtonClick` zdarzeń do odbierania danych z formantu. Ma również zbiór przycisków opcji, które umożliwiają zmianę niektórych właściwości formantu z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Na poniższej ilustracji przedstawiono Zakończono aplikacji.  
  
 ![Formantu osadzonego w stronie WPF](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")  
Kompletna aplikacja przedstawiający formantu osadzonego w aplikacji WPF  
  
### <a name="creating-the-project"></a>Tworzenie projektu  
 Aby uruchomić projekt:  
  
1.  Otwórz [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]i wybierz **nowy projekt**.  
  
2.  W oknie kategorii, wybierz **aplikacji WPF** szablonu.
  
3.  Nazwa nowego projektu `WpfHost`.  
  
4.  W przypadku lokalizacji określ tego samego folderu najwyższego poziomu, który zawiera MyControls projektu.  
  
5.  Kliknij przycisk **OK** Aby utworzyć projekt.  
  
 Należy również dodać odwołania do biblioteki DLL zawierającej `MyControl1` i innych zestawów.  
  
1.  Kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań i wybierz **Dodaj odwołanie**.  
  
2.  Kliknij przycisk **Przeglądaj** karcie i przejdź do folderu, który zawiera MyControls.dll. W ramach tego przewodnika ten folder jest MyControls\bin\Debug.  
  
3.  Wybierz MyControls.dll, a następnie kliknij przycisk **OK**.  
  
4.  Dodaj odwołanie do zestawu WindowsFormsIntegration, o nazwie WindowsFormsIntegration.dll.  
  
### <a name="implementing-the-basic-layout"></a>Podstawowe układu Implementowanie  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Hosta aplikacji jest zaimplementowana w MainWindow.xaml. Ten plik zawiera [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kod znaczników, który definiuje układ i obsługuje formantu formularzy systemu Windows. Aplikacja jest podzielona na trzy obszary:  
  
-   **Właściwości formantu** panelu, które zawiera kolekcję przycisków opcji, które służy do modyfikowania różnych właściwości obsługiwanego formantu.  
  
-   **Danych z formantu** panelu, które zawiera kilka <xref:System.Windows.Controls.TextBlock> elementów, które przedstawiają dane zwrócone z obsługiwanego formantu.  
  
-   Hostowanej samego formantu.  
  
 Podstawowy układ przedstawiono w następujących XAML. Kod znaczników, który jest wymagany do hosta `MyControl1` pominięto w tym przykładzie, ale zostanie dokładnie omówione później.  
  
 Zamień XAML w MainWindow.xaml poniżej. Jeśli używasz programu Visual Basic, Zmień klasę, aby `x:Class="MainWindow"`.  
  
 [!code-xaml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]  
  
 Pierwszy <xref:System.Windows.Controls.StackPanel> element zawiera kilka zestawów <xref:System.Windows.Controls.RadioButton> formantów, które umożliwiają modyfikowanie różnych właściwości domyślne obsługiwanego formantu. Którym następuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementów, których hostów `MyControl1`. Ostatni <xref:System.Windows.Controls.StackPanel> element zawiera kilka <xref:System.Windows.Controls.TextBlock> elementów, które przedstawiają dane zwracane przez obsługiwanego formantu. Kolejność elementów i <xref:System.Windows.Controls.DockPanel.Dock%2A> i <xref:System.Windows.FrameworkElement.Height%2A> ustawienia atrybutu osadzić obsługiwanego formantu do okna bez przerw i zakłóceń.  
  
#### <a name="hosting-the-control"></a>Hosting kontrolki  
 Następująca wersja edytowanego poprzednie XAML skupia się wokół elementów, które są wymagane do hosta `MyControl1`.  
  
 [!code-xaml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]  
[!code-xaml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]  
  
 `xmlns` Atrybutu mapowania przestrzeni nazw tworzy odwołanie do `MyControls` przestrzeni nazw, która zawiera obsługiwanego formantu. To mapowanie umożliwia reprezentują `MyControl1` w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako `<mcl:MyControl1>`.  
  
 Dwa elementy w kodzie XAML obsługi hostingu:  
  
-   `WindowsFormsHost` reprezentuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, który umożliwia hostowanie kontrolki formularza systemu Windows, w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
-   `mcl:MyControl1`, która reprezentuje `MyControl1`, jest dodawany do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu podrzędnej kolekcji. W związku z tym renderowania tego formantu formularzy systemu Windows jako część [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , a następnie może komunikować się z urządzeniem za pomocą aplikacji.  
  
### <a name="implementing-the-code-behind-file"></a>Implementacja pliku CodeBehind  
 Plik CodeBehind, MainWindow.xaml.vb lub MainWindow.xaml.cs, zawiera kod procedury, która implementuje funkcje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] omówione w poprzedniej sekcji. Podstawowe zadania są:  
  
-   Dołączanie do obsługi zdarzeń `MyControl1`w `OnButtonClick` zdarzeń.  
  
-   Modyfikowanie właściwości różnych `MyControl1`, zależności od konfiguracji kolekcji przycisków opcji.  
  
-   Wyświetlanie danych zebranych przez formant.  
  
#### <a name="initializing-the-application"></a>Inicjowanie aplikacji  
 Kod inicjujący znajduje się w obsłudze zdarzeń w oknie <xref:System.Windows.FrameworkElement.Loaded> zdarzeń i dołącza program obsługi zdarzeń do formantu `OnButtonClick` zdarzeń.  
  
 W MainWindow.xaml.vb lub MainWindow.xaml.cs, Dodaj następujący kod, aby `MainWindow` klasy.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]  
  
 Ponieważ [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] omówione uprzednio dodanych `MyControl1` do <xref:System.Windows.Forms.Integration.WindowsFormsHost> kolekcji elementów podrzędnych elementu, można rzutować <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> można pobrać odwołania do `MyControl1`. Następnie służy odwołujące się do dołączenia do obsługi zdarzeń `OnButtonClick`.  
  
 Oprócz zapewnienia odwołanie do samej kontrolce, <xref:System.Windows.Forms.Integration.WindowsFormsHost> przedstawia liczbę właściwości formantu, które można manipulować, korzystając z aplikacji. Kod inicjujący przypisuje tych wartości do prywatnego zmienne globalne do późniejszego użytku w aplikacji.  
  
 Tak, aby mogli łatwo uzyskiwać dostęp typu `MyControls` biblioteki DLL, Dodaj następujący `Imports` lub `using` instrukcji na początku pliku.  
  
```vb  
Imports MyControls  
```  
  
```csharp  
using MyControls;  
```  
  
#### <a name="handling-the-onbuttonclick-event"></a>Obsługa zdarzeń OnButtonClick  
 `MyControl1` zgłasza `OnButtonClick` zdarzenie, gdy użytkownik kliknie jeden z przycisków kontrolki.  
  
 Dodaj następujący kod do `MainWindow` klasy.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]  
  
 Spakowane dane w polach tekstowych w `MyControlEventArgs` obiektu. Gdy użytkownik kliknie **OK** przycisku, program obsługi zdarzeń wyodrębnia dane i wyświetla je w panelu poniżej `MyControl1`.  
  
#### <a name="modifying-the-controls-properties"></a>Modyfikowanie właściwości formantu  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element udostępnia kilka właściwości domyślne obsługiwanego formantu. W związku z tym można zmienić wygląd formantu, aby lepiej pasuje styl aplikacji. Zestawy przycisków opcji znajdujących się w lewym panelu zezwolić użytkownikowi na modyfikowanie kilka właściwości kolorów i czcionek. Każdy zestaw przycisków ma obsługi dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie, które wykrywa przycisk Opcje użytkownika i zmienia odpowiadających im właściwości w formancie.  
  
 Dodaj następujący kod do `MainWindow` klasy.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Skompiluj i uruchom aplikację. Dodaj część tekstu w złożonych kontrolek formularzy systemu Windows, a następnie kliknij przycisk **OK**. Tekst jest wyświetlany w etykiecie. Kliknij przyciski różnych opcji, aby zobaczyć efekt w formancie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Projektant WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Przewodnik: hosting kontrolki Windows Forms w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
