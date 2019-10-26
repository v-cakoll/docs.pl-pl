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
ms.openlocfilehash: e30b1bb45cc2dae2783cddf54dda400b742cdf73
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920328"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>Wskazówki: hosting złożonego formantu Windows Forms w WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia rozbudowane środowisko do tworzenia aplikacji. Jeśli jednak masz znaczną inwestycję w kod [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], może być bardziej efektywne ponowne użycie co najmniej jednego kodu w aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], a nie zapisanie go od podstaw. Najczęstszym scenariuszem jest to, że masz istniejące kontrolki Windows Forms. W niektórych przypadkach może nie mieć nawet dostępu do kodu źródłowego dla tych formantów. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia prostą procedurę hostingu takich kontrolek w aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Na przykład można użyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w większości programowania, jednocześnie udostępniając wyspecjalizowane kontrolki <xref:System.Windows.Forms.DataGridView>.  
  
 Ten Instruktaż przeprowadzi Cię przez aplikację, która hostuje Windows Forms formant złożony do wprowadzania danych w aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Formant złożony jest spakowany w bibliotece DLL. Ta ogólna procedura może zostać rozszerzona na bardziej złożone aplikacje i kontrolki. Ten przewodnik został zaprojektowany tak, aby był niemal identyczny w wyglądzie i funkcjach do [przewodnika: hosting złożonego formantu WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md). Podstawowa różnica polega na tym, że scenariusz hostingu jest odwrócony.  
  
 Przewodnik jest podzielony na dwie sekcje. W pierwszej sekcji krótko opisano implementację Windows Formsego formantu złożonego. W drugiej sekcji omówiono szczegółowo, jak hostować formant złożony w aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], odbierać zdarzenia z kontrolki i uzyskiwać dostęp do niektórych właściwości kontrolki.  
  
 Zadania przedstawione w tym instruktażu obejmują:  
  
- Implementowanie Windows Formsgo formantu złożonego.  
  
- Implementowanie aplikacji hosta WPF.  
  
 Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [hostowanie złożonego formantu Windows Forms w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=159999).  
  
## <a name="prerequisites"></a>Wymagania wstępne  

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.
  
## <a name="implementing-the-windows-forms-composite-control"></a>Implementowanie Windows Formsgo formantu złożonego  
 Formant złożony Windows Forms używany w tym przykładzie jest prostym formularzem wprowadzania danych. Ten formularz przyjmuje nazwę i adres użytkownika, a następnie używa zdarzenia niestandardowego, aby zwrócić te informacje do hosta. Poniższa ilustracja przedstawia renderowany formant.  

 Na poniższej ilustracji przedstawiono Windows Forms formant złożony:  

 ![Zrzut ekranu, który pokazuje prosty formant Windows Forms.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a>Tworzenie projektu  
 Aby rozpocząć projekt:  
  
1. Uruchom program Visual Studio i Otwórz okno dialogowe **Nowy projekt** .  
  
2. W kategorii okna wybierz szablon **Biblioteka formantów Windows Forms** .  
  
3. Nadaj nazwę nowemu projektowi `MyControls`.  
  
4. W polu Lokalizacja Określ wygodną nazwę folderu najwyższego poziomu, na przykład `WpfHostingWindowsFormsControl`. Później aplikacja hosta zostanie umieszczona w tym folderze.  
  
5. Kliknij przycisk **OK** , aby utworzyć projekt. Domyślny projekt zawiera pojedynczy formant o nazwie `UserControl1`.  
  
6. W Eksplorator rozwiązań Zmień nazwę `UserControl1` na `MyControl1`.  
  
 Projekt powinien zawierać odwołania do następujących bibliotek DLL systemu. Jeśli dowolna z tych bibliotek DLL nie jest domyślnie dołączona, należy dodać je do projektu.  
  
- System  
  
- System.Data  
  
- System. Drawing  
  
- System. Windows. Forms  
  
- System.Xml  
  
### <a name="adding-controls-to-the-form"></a>Dodawanie kontrolek do formularza  
 Aby dodać kontrolki do formularza:  
  
- Otwórz `MyControl1` w projektancie.  
  
 Dodaj pięć <xref:System.Windows.Forms.Label> kontrolek i odpowiadające im kontrolki <xref:System.Windows.Forms.TextBox>, rozmiar i ułożone w taki sposób, jak na poprzedniej ilustracji, w formularzu. W przykładzie kontrolki <xref:System.Windows.Forms.TextBox> są nazwane:  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 Dodaj dwie kontrolki <xref:System.Windows.Forms.Button> oznaczone jako **OK** i **Anuluj**. W tym przykładzie nazwy przycisków są odpowiednio `btnOK` i `btnCancel`.  
  
### <a name="implementing-the-supporting-code"></a>Implementowanie kodu pomocniczego  
 Otwórz formularz w widoku kodu. Kontrolka zwraca zebrane dane do hosta przez podnoszenie niestandardowego zdarzenia `OnButtonClick`. Dane są zawarte w obiekcie argumentu zdarzenia. Poniższy kod przedstawia deklarację zdarzenia i delegata.  
  
 Dodaj następujący kod do klasy `MyControl1`.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 Klasa `MyControlEventArgs` zawiera informacje, które mają zostać zwrócone do hosta.

 Dodaj następującą klasę do formularza.

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 Gdy użytkownik kliknie przycisk **OK** lub **Anuluj** , programy obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> tworzą obiekt `MyControlEventArgs` zawierający dane i zgłasza zdarzenie `OnButtonClick`. Jedyną różnicą między dwoma uchwytami jest właściwość `IsOK` argumentu zdarzenia. Ta właściwość umożliwia hostowi określenie, który przycisk został kliknięty. Dla przycisku **OK** jest ustawiona wartość `true` i `false` przycisku **Anuluj** . Poniższy kod przedstawia dwa programy obsługi przycisków.

 Dodaj następujący kod do klasy `MyControl1`.

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>Nadawanie zestawowi silnej nazwy i kompilowania zestawu
 Dla tego zestawu, do którego odwołuje się aplikacja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], musi mieć silną nazwę. Aby utworzyć silną nazwę, Utwórz plik klucza z SN. exe i dodaj go do projektu.

1. Otwórz wiersz polecenia programu Visual Studio. Aby to zrobić, kliknij menu **Start** , a następnie wybierz pozycję **wszystkie programy/Microsoft Visual Studio 2010/Visual Studio Tools/wiersz polecenia programu Visual Studio**. Spowoduje to uruchomienie okna konsoli z dostosowanymi zmiennymi środowiskowymi.

2. W wierszu polecenia Użyj polecenia `cd`, aby przejść do folderu projektu.

3. Wygeneruj plik klucza o nazwie SNK, uruchamiając następujące polecenie.

    ```console
    Sn.exe -k MyControls.snk
    ```

4. Aby dołączyć plik klucza w projekcie, kliknij prawym przyciskiem myszy nazwę projektu w Eksplorator rozwiązań a następnie kliknij pozycję **Właściwości**. W projektancie projektu kliknij kartę **podpisywanie** , zaznacz pole wyboru **podpisz zestaw** , a następnie przejdź do pliku klucza.

5. Skompiluj rozwiązanie. Kompilacja spowoduje utworzenie biblioteki DLL o nazwie WebControls. dll.

## <a name="implementing-the-wpf-host-application"></a>Implementowanie aplikacji hosta WPF
 Aplikacja hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa kontrolki <xref:System.Windows.Forms.Integration.WindowsFormsHost> do hostowania `MyControl1`. Aplikacja obsługuje zdarzenie `OnButtonClick`, aby otrzymywać dane z formantu. Zawiera również zbiór przycisków opcji, które umożliwiają zmianę niektórych właściwości kontrolki z aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Na poniższej ilustracji przedstawiono ukończoną aplikację.

Na poniższej ilustracji przedstawiono kompletną aplikację, w tym kontrolkę osadzoną w aplikacji WPF:

 ![Zrzut ekranu, który pokazuje kontrolkę osadzoną na stronie WPF.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a>Tworzenie projektu
 Aby rozpocząć projekt:

1. Otwórz program Visual Studio i wybierz pozycję **Nowy projekt**.

2. W kategorii okno Wybierz szablon **Aplikacja WPF** .

3. Nadaj nazwę nowemu projektowi `WpfHost`.

4. Dla lokalizacji Określ ten sam folder najwyższego poziomu, który zawiera projekt kontrolek.

5. Kliknij przycisk **OK** , aby utworzyć projekt.

 Należy również dodać odwołania do biblioteki DLL, która zawiera `MyControl1` i inne zestawy.

1. Kliknij prawym przyciskiem myszy nazwę projektu w Eksplorator rozwiązań i wybierz polecenie **Dodaj odwołanie**.

2. Kliknij kartę **Przeglądaj** i przejdź do folderu, który zawiera plik. dll. W tym instruktażu ten folder jest MyControls\bin\Debug.

3. Wybierz pozycję Moja Controls. dll, a następnie kliknij przycisk **OK**.

4. Dodaj odwołanie do zestawu WindowsFormsIntegration o nazwie WindowsFormsIntegration. dll.

### <a name="implementing-the-basic-layout"></a>Implementowanie układu podstawowego
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] aplikacji hosta jest zaimplementowana w MainWindow. XAML. Ten plik zawiera [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] znacznik, który definiuje układ i hostuje kontrolkę Windows Forms. Aplikacja została podzielona na trzy regiony:

- Panel **właściwości kontrolki** , który zawiera kolekcję przycisków opcji, których można użyć do modyfikacji różnych właściwości kontrolki hostowanej.

- **Dane z panelu sterowania** , które zawierają kilka <xref:System.Windows.Controls.TextBlock> elementów, które wyświetlają dane zwrócone przez obsługiwaną kontrolę.

- Kontrolka hostowana.

 Podstawowy układ jest przedstawiony w poniższym kodzie XAML. Znaczniki, które są potrzebne do hostowania `MyControl1`, są pomijane w tym przykładzie, ale zostaną omówione później.

 Zamień kod XAML w MainWindow. XAML na następujący. Jeśli używasz Visual Basic, Zmień klasę na `x:Class="MainWindow"`.

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 Pierwszy <xref:System.Windows.Controls.StackPanel> element zawiera kilka zestawów formantów <xref:System.Windows.Controls.RadioButton>, które umożliwiają modyfikowanie różnych domyślnych właściwości kontrolki hostowanej. Następuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, który hostuje `MyControl1`. Końcowy element <xref:System.Windows.Controls.StackPanel> zawiera kilka elementów <xref:System.Windows.Controls.TextBlock>, które wyświetlają dane zwracane przez hostowaną kontrolkę. Kolejność elementów oraz ustawienia atrybutów <xref:System.Windows.Controls.DockPanel.Dock%2A> i <xref:System.Windows.FrameworkElement.Height%2A> Osadź formant hostowany w oknie bez przerw ani zniekształceń.

#### <a name="hosting-the-control"></a>Hostowanie kontrolki
 Następująca edytowana wersja poprzedniego języka XAML koncentruje się na elementach, które są konieczne do hostowania `MyControl1`.

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 Atrybut mapowania przestrzeni nazw `xmlns` tworzy odwołanie do przestrzeni nazw `MyControls`, która zawiera hostowaną kontrolkę. To mapowanie umożliwia reprezentowanie `MyControl1` w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako `<mcl:MyControl1>`.

 Dwa elementy w kodzie XAML obsługują hosting:

- `WindowsFormsHost` reprezentuje element <xref:System.Windows.Forms.Integration.WindowsFormsHost>, który umożliwia hostowanie kontrolki Windows Forms w aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

- `mcl:MyControl1`, która reprezentuje `MyControl1`, jest dodawany do kolekcji podrzędnej <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. W efekcie ten formant Windows Forms jest renderowany jako część okna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i można komunikować się z kontrolką z poziomu aplikacji.

### <a name="implementing-the-code-behind-file"></a>Implementowanie pliku związanego z kodem
 Plik związany z kodem, MainWindow. XAML. vb lub MainWindow.xaml.cs, zawiera kod proceduralny implementujący funkcje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] omówione w poprzedniej sekcji. Zadania podstawowe są następujące:

- Dołączanie programu obsługi zdarzeń do zdarzenia `OnButtonClick` `MyControl1`.

- Modyfikowanie różnych właściwości `MyControl1`w zależności od tego, jak kolekcja przycisków opcji jest ustawiona.

- Wyświetlanie danych zebranych przez formant.

#### <a name="initializing-the-application"></a>Inicjowanie aplikacji
 Kod inicjalizacji jest zawarty w obsłudze zdarzeń dla zdarzenia <xref:System.Windows.FrameworkElement.Loaded> okna i dołącza procedurę obsługi zdarzeń do zdarzenia `OnButtonClick` formantu.

 W MainWindow. XAML. vb lub MainWindow.xaml.cs Dodaj następujący kod do klasy `MainWindow`.

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 Ponieważ [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] omówione wcześniej `MyControl1` do kolekcji elementów podrzędnych <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, można rzutować <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>, aby uzyskać odwołanie do `MyControl1`. Następnie można użyć tego odwołania, aby dołączyć procedurę obsługi zdarzeń do `OnButtonClick`.

 Oprócz podawania odniesienia do samego formantu, <xref:System.Windows.Forms.Integration.WindowsFormsHost> uwidacznia szereg właściwości kontrolki, które można manipulować z poziomu aplikacji. Kod inicjalizacji przypisuje te wartości do prywatnych zmiennych globalnych do późniejszego użycia w aplikacji.

 Dzięki temu można łatwo uzyskać dostęp do typów w `MyControls` DLL, Dodaj następującą instrukcję `Imports` lub `using` na początku pliku.

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a>Obsługa zdarzenia OnButtonClick
 `MyControl1` wywołuje zdarzenie `OnButtonClick`, gdy użytkownik kliknie jeden z przycisków kontrolki.

 Dodaj następujący kod do klasy `MainWindow`.

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 Dane w polach tekstowych są pakowane do obiektu `MyControlEventArgs`. Jeśli użytkownik kliknie przycisk **OK** , program obsługi zdarzeń wyodrębni dane i wyświetli je w panelu poniżej `MyControl1`.

#### <a name="modifying-the-controls-properties"></a>Modyfikowanie właściwości kontrolki
 Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> uwidacznia kilka właściwości domyślnych kontrolki hostowanej. W związku z tym można zmienić wygląd formantu tak, aby pasował do stylu aplikacji. Zestawy przycisków opcji w lewym panelu umożliwiają użytkownikowi modyfikowanie kilku właściwości koloru i czcionki. Każdy zestaw przycisków ma procedurę obsługi dla zdarzenia <xref:System.Windows.Controls.Primitives.ButtonBase.Click>, które wykrywa wybór przycisku opcji użytkownika i zmienia odpowiednią właściwość w formancie.

 Dodaj następujący kod do klasy `MainWindow`.

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Skompiluj i uruchom aplikację. Dodaj tekst do kontrolki złożonej Windows Forms, a następnie kliknij przycisk **OK**. Tekst zostanie wyświetlony w etykietach. Kliknij różne przyciski radiowe, aby zobaczyć efekt na kontrolce.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Przewodnik: hosting kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
