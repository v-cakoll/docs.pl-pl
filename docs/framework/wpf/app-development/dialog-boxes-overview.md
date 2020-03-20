---
title: Przegląd okien dialogowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- modeless dialog boxes [WPF]
- dialog boxes [WPF]
- message boxes [WPF]
- modal dialog boxes [WPF]
ms.assetid: 0d23d544-a393-4a02-a3aa-d8cd5d3d6511
ms.openlocfilehash: c98d6a45d151d4b683a21e48eaeb5f4a19eaadb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187455"
---
# <a name="dialog-boxes-overview"></a>Omówienie okien dialogowych
Aplikacje autonomiczne zazwyczaj mają okno główne, które wyświetla zarówno główne dane, za pośrednictwem których aplikacja [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] działa i udostępnia funkcje do przetwarzania tych danych za pośrednictwem mechanizmów, takich jak paski menu, paski narzędzi i paski stanu. Nietrywialna aplikacja może również wyświetlać dodatkowe okna, aby wykonać następujące czynności:  
  
- Wyświetlanie określonych informacji użytkownikom.  
  
- Zbieraj informacje od użytkowników.  
  
- Zarówno wyświetlanie, jak i zbieranie informacji.  
  
 Te typy okien są nazywane *oknami dialogowymi*i istnieją dwa typy: modalny i niemodalny.  
  
 *Modalne* okno dialogowe jest wyświetlane przez funkcję, gdy funkcja potrzebuje dodatkowych danych od użytkownika, aby kontynuować. Ponieważ funkcja zależy od modalnego okna dialogowego do zbierania danych, modalne okno dialogowe uniemożliwia również użytkownikowi aktywowanie innych okien w aplikacji, gdy pozostaje otwarta. W większości przypadków modalne okno dialogowe umożliwia użytkownikowi sygnalizowanie po zakończeniu pracy z **OK** modalnym **Cancel** ok. Naciśnięcie przycisku **OK** wskazuje, że użytkownik wprowadził dane i chce, aby funkcja kontynuowała przetwarzanie z tymi danymi. Naciśnięcie przycisku **Anuluj** oznacza, że użytkownik chce całkowicie uniemożliwić wykonanie funkcji. Najbardziej typowe przykłady modalnych okien dialogowych są wyświetlane do otwierania, zapisywania i drukowania danych.  
  
 Z drugiej *strony, niemodless* okno dialogowe nie uniemożliwia użytkownikowi aktywowania innych okien, gdy jest otwarty. Na przykład jeśli użytkownik chce znaleźć wystąpienia określonego wyrazu w dokumencie, okno główne często otwiera okno dialogowe, aby zapytać użytkownika, jakiego słowa szukają. Ponieważ znalezienie wyrazu nie uniemożliwia użytkownikowi edytowania dokumentu, okno dialogowe nie musi być modalne. Niemodowe okno dialogowe zawiera co najmniej przycisk **Zamknij,** aby zamknąć okno dialogowe, i może dostarczyć dodatkowych przycisków do wykonywania określonych funkcji, takich jak przycisk **Znajdź następny,** aby znaleźć następny wyraz, który spełnia kryteria wyszukiwania słów.  
  
 Windows Presentation Foundation (WPF) umożliwia utworzenie kilku typów okien dialogowych, w tym okien komunikatów, typowych okien dialogowych i niestandardowych okien dialogowych. W tym temacie omówiono każdy, a [przykład okna dialogowego](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox) zawiera pasujące przykłady.  

<a name="Message_Boxes"></a>
## <a name="message-boxes"></a>Pola komunikatów  
 *Okno komunikatu* to okno dialogowe, za pomocą którego można wyświetlać informacje tekstowe i umożliwiać użytkownikom podejmowanie decyzji za pomocą przycisków. Na poniższej ilustracji przedstawiono okno komunikatu, w które są wyświetlane informacje tekstowe, zadaje pytanie i udostępnia użytkownikowi trzy przyciski, aby odpowiedzieć na pytanie.  
  
 ![Okno dialogowe Edytor tekstu z pytaniem, czy chcesz zapisać zmiany w dokumencie przed zamknięciem aplikacji.](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 Aby utworzyć okno komunikatu, <xref:System.Windows.MessageBox> należy użyć klasy. <xref:System.Windows.MessageBox>umożliwia skonfigurowanie tekstu, tytułu, ikony i przycisków okna komunikatu przy użyciu kodu podobnego do poniższego.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Aby wyświetlić okno komunikatu, należy wywołać `static` <xref:System.Windows.MessageBox.Show%2A> metodę, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Gdy kod, który pokazuje okno komunikatu musi wykryć i przetworzyć decyzję użytkownika (który przycisk został naciśnięty), kod można sprawdzić wynik okna komunikatu, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 Aby uzyskać więcej informacji na <xref:System.Windows.MessageBox>temat korzystania z okien komunikatów, zobacz , [Przykładowybox wiadomości](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)i [Przykład okna dialogowego](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox).  
  
 Chociaż <xref:System.Windows.MessageBox> może oferować proste środowisko użytkownika okna <xref:System.Windows.MessageBox> dialogowego, zaletą używania jest to, że jest to jedyny typ okna, które mogą być wyświetlane przez aplikacje uruchamiane w częściowym polu izolowanym zabezpieczeń zaufania (zobacz [Zabezpieczenia](../security-wpf.md)), takie jak aplikacje przeglądarki XAML (XBAPs).  
  
 Większość okien dialogowych wyświetla i zbiera bardziej złożone dane niż wynik okna komunikatu, w tym tekst, zaznaczenie (pola wyboru), wzajemnie wykluczające się zaznaczenie (przyciski radiowe) i wybór listy (pola listy, pola kombi, pola listy rozwijanej). W tym celu program Windows Presentation Foundation (WPF) udostępnia kilka typowych okien dialogowych i umożliwia tworzenie własnych okien dialogowych, chociaż użycie jednego z nich jest ograniczone do aplikacji działających z pełnym zaufaniem.  
  
<a name="Common_Dialogs"></a>
## <a name="common-dialog-boxes"></a>Typowe okna dialogowe  
 System Windows implementuje wiele okien dialogowych wielokrotnego użytku, które są wspólne dla wszystkich aplikacji, w tym okna dialogowe do otwierania plików, zapisywania plików i drukowania. Ponieważ te okna dialogowe są implementowane przez system operacyjny, mogą być współużytkowane przez wszystkie aplikacje uruchamiane w systemie operacyjnym, co pomaga spójności środowiska użytkownika; gdy użytkownicy są zaznajomieni z używaniem okna dialogowego dostarczonego przez system operacyjny w jednej aplikacji, nie muszą uczyć się, jak używać tego okna dialogowego w innych aplikacjach. Ponieważ te okna dialogowe są dostępne dla wszystkich aplikacji i pomagają zapewnić spójne środowisko użytkownika, są one znane jako *typowe okna dialogowe*.  
  
 Windows Presentation Foundation (WPF) hermetyzuje otwarty plik, zapisz plik i wydrukować typowe okna dialogowe i udostępnia je jako klasy zarządzane do użycia w aplikacjach autonomicznych. Ten temat zawiera krótki przegląd każdego z nich.  
  
<a name="Open_File_Dialog"></a>
### <a name="open-file-dialog"></a>Okno dialogowe Otwórz plik  
 Okno dialogowe otwierania pliku, pokazane na poniższej ilustracji, jest używane przez funkcję otwierania plików do pobierania nazwy pliku do otwarcia.  
  
 ![Okno dialogowe Otwórz pokazujące lokalizację pobierania pliku.](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 Typowe okno dialogowe otwartego pliku <xref:Microsoft.Win32.OpenFileDialog> jest implementowane <xref:Microsoft.Win32> jako klasa i znajduje się w obszarze nazw. Poniższy kod pokazuje, jak utworzyć, skonfigurować i pokazać jeden i jak przetworzyć wynik.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Aby uzyskać więcej informacji na temat <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>okna dialogowego otwierania pliku, zobacz .  
  
> [!NOTE]
> <xref:Microsoft.Win32.OpenFileDialog>można bezpiecznie pobierać nazwy plików przez aplikacje z częściowym zaufaniem (patrz [Zabezpieczenia).](../security-wpf.md)  
  
<a name="Save_File_Dialog"></a>
### <a name="save-file-dialog-box"></a>Zapisz Plik — Okno dialogowe  
 Okno dialogowe zapisywania pliku, pokazane na poniższej ilustracji, jest używane przez funkcję zapisywania plików w celu pobrania nazwy pliku do zapisania.  
  
 ![Okno dialogowe Zapisywanie jako przedstawiające lokalizację zapisywania pliku.](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 Typowe okno dialogowe zapisywania pliku <xref:Microsoft.Win32.SaveFileDialog> jest implementowane jako <xref:Microsoft.Win32> klasa i znajduje się w obszarze nazw. Poniższy kod pokazuje, jak utworzyć, skonfigurować i pokazać jeden i jak przetworzyć wynik.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Aby uzyskać więcej informacji na temat <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>okna dialogowego zapisywania pliku, zobacz .  
  
<a name="Print_Dialog"></a>
### <a name="print-dialog-box"></a>Drukuj — Okno dialogowe

Okno dialogowe drukowania, pokazane na poniższym rysunku, jest używane przez funkcję drukowania w celu wybrania i skonfigurowania drukarki, na którą użytkownik chciałby drukować dane.  
  
![Zrzut ekranu przedstawiający okno dialogowe Drukowanie.](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
Typowe okno dialogowe drukowania <xref:System.Windows.Controls.PrintDialog> jest implementowane jako <xref:System.Windows.Controls> klasa i znajduje się w obszarze nazw. Poniższy kod pokazuje, jak utworzyć, skonfigurować i pokazać jeden.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Aby uzyskać więcej informacji na <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>temat okna dialogowego drukowania, zobacz . Szczegółowe omówienie drukowania w [Printing Overview](../advanced/printing-overview.md)chciwym ekskopie w U.  
  
<a name="Custom_Dialog_Boxes"></a>
## <a name="custom-dialog-boxes"></a>Niestandardowe okna dialogowe

Chociaż typowe okna dialogowe są przydatne i powinny być używane, gdy jest to możliwe, nie obsługują wymagań okien dialogowych specyficznych dla domeny. W takich przypadkach należy utworzyć własne okna dialogowe. Jak zobaczymy, okno dialogowe jest oknem ze specjalnymi zachowaniami. <xref:System.Windows.Window>implementuje te zachowania i w związku <xref:System.Windows.Window> z tym służy do tworzenia niestandardowych modalnych i modnych okien dialogowych.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>
### <a name="creating-a-modal-custom-dialog-box"></a>Tworzenie niestandardowego okna dialogowego modalnego

W tym temacie <xref:System.Windows.Window> pokazano, jak użyć do utworzenia `Margins` typowej implementacji modalnego okna dialogowego, używając okna dialogowego jako przykładu (zobacz [Przykład okna dialogowego](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)). Okno `Margins` dialogowe jest pokazane na poniższej ilustracji.  
  
 ![Okno dialogowe Marginesy z polami definiuuuuujymidajego marginesu, górnego marginesu, prawego marginesu i dolnego marginesu.](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>Konfigurowanie modalnego okna dialogowego

Interfejs użytkownika dla typowego okna dialogowego zawiera następujące elementy:  
  
- Różne formanty, które są wymagane do zbierania żądanych danych.  
  
- Przycisk **OK,** który użytkownicy klikają, aby zamknąć okno dialogowe, powrócić do funkcji i kontynuować przetwarzanie.  
  
- Przycisk **Anuluj,** który użytkownicy klikają, aby zamknąć okno dialogowe i zatrzymać dalsze przetwarzanie funkcji.  
  
- Przycisk **Zamknij** na pasku tytułu.  
  
- Ikona.  
  
- **Minimalizuj** **przyciski , Maksymalizuj**i **Przywróć.**  
  
- Menu **System w** celu zminimalizowania, maksymalizacji, przywrócenia i zamknięcia okna dialogowego.  
  
- Położenie powyżej i na środku okna, które otworzyło okno dialogowe.  
  
- Możliwość ponownego rozmiaru w miarę możliwości, aby zapobiec zbyt małe okno dialogowe i zapewnić użytkownikowi przydatny rozmiar domyślny. Wymaga to ustawienia zarówno wymiarów domyślnych, jak i minimalnych.  
  
- Klawisz ESC jako skrót klawiaturowy, który powoduje naciśnięcie przycisku **Anuluj.** Można to zrobić, <xref:System.Windows.Controls.Button.IsCancel%2A> ustawiając właściwość `true`przycisku **Anuluj** na .  
  
- Klawisz ENTER (lub RETURN) jako skrót klawiaturowy, który powoduje naciśnięcie przycisku **OK.** Można to zrobić, <xref:System.Windows.Controls.Button.IsDefault%2A> ustawiając właściwość przycisku `true` **OK** .  
  
Poniższy kod demonstruje tę konfigurację.  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
Środowisko użytkownika okna dialogowego rozciąga się również na pasek menu okna, które otwiera okno dialogowe. Gdy element menu uruchamia funkcję, która wymaga interakcji użytkownika za pośrednictwem okna dialogowego, zanim funkcja będzie mogła kontynuować, element menu funkcji będzie miał wielokropek w nagłówku, jak pokazano poniżej.  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
Gdy element menu uruchamia funkcję, która wyświetla okno dialogowe, które nie wymaga interakcji z użytkownikiem, takie jak okno dialogowe Informacje, wielokropek nie jest wymagany.  
  
#### <a name="opening-a-modal-dialog-box"></a>Otwieranie modalnego okna dialogowego

Okno dialogowe jest zazwyczaj wyświetlane w wyniku wybrania przez użytkownika elementu menu w celu wykonania funkcji specyficznej dla domeny, takiej jak ustawianie marginesów dokumentu w edytorze tekstu. Wyświetlanie okna jako okna dialogowego jest podobne do wyświetlania normalnego okna, chociaż wymaga dodatkowej konfiguracji specyficznej dla okna dialogowego. Cały proces tworzenia wystąpienia, konfigurowania i otwierania okna dialogowego jest wyświetlany w poniższym kodzie.  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

W tym miejscu kod przekazuje informacje domyślne (bieżące marginesy) do okna dialogowego. Ustawia również <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> właściwość z odwołaniem do okna, które jest wyświetlane w oknie dialogowym. Ogólnie rzecz biorąc należy zawsze ustawić właściciela okna dialogowego, aby zapewnić zachowania związane ze stanem okna, które są wspólne dla wszystkich okien dialogowych (zobacz [Omówienie systemu Windows WPF,](wpf-windows-overview.md) aby uzyskać więcej informacji).

> [!NOTE]
> Należy podać właściciela do obsługi automatyzacji interfejsu użytkownika (UI) dla okien dialogowych (zobacz [Omówienie automatyzacji interfejsu użytkownika](../../ui-automation/ui-automation-overview.md)).

Po skonfigurowaniu okna dialogowego jest ono wyświetlane <xref:System.Windows.Window.ShowDialog%2A> modnie przez wywołanie metody.  
  
#### <a name="validating-user-provided-data"></a>Sprawdzanie poprawności danych dostarczonych przez użytkownika

Po otwarciu okna dialogowego i udostępnieniu wymaganych danych okno dialogowe jest odpowiedzialne za zapewnienie, że podane dane są prawidłowe z następujących powodów:  
  
- Z punktu widzenia zabezpieczeń wszystkie dane wejściowe powinny zostać zweryfikowane.  
  
- Z punktu widzenia specyficznego dla domeny sprawdzanie poprawności danych zapobiega przetwarzania błędnych danych przez kod, co może potencjalnie zgłaszać wyjątki.  
  
- Z punktu widzenia środowiska użytkownika okno dialogowe może pomóc użytkownikom, pokazując im, które wprowadzone dane są nieprawidłowe.  
  
- Z punktu widzenia wydajności sprawdzanie poprawności danych w aplikacji wielowarstwowej można zmniejszyć liczbę rund między klientem a warstwami aplikacji, szczególnie gdy aplikacja składa się z usług sieci Web lub baz danych opartych na serwerze.  

Aby sprawdzić poprawność powiązanego formantu w WPF, należy zdefiniować regułę sprawdzania poprawności i skojarzyć ją z powiązaniem. Reguła sprawdzania poprawności jest klasą <xref:System.Windows.Controls.ValidationRule>niestandardową, która wywodzi się z . Poniższy przykład przedstawia regułę sprawdzania poprawności, która `MarginValidationRule` <xref:System.Double> sprawdza, czy wartość powiązana jest i mieści się w określonym zakresie.  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

W tym kodzie logika sprawdzania poprawności reguły sprawdzania <xref:System.Windows.Controls.ValidationRule.Validate%2A> poprawności jest implementowana przez zastąpienie <xref:System.Windows.Controls.ValidationResult>metody, która sprawdza poprawność danych i zwraca odpowiedni plik .  

Aby skojarzyć regułę sprawdzania poprawności z formantem powiązanym, należy użyć następującego znaczników.  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

Po skojarzeniu reguły sprawdzania poprawności WPF automatycznie zastosuje ją po wprowadzeniu danych do formantu powiązanego. Gdy formant zawiera nieprawidłowe dane, WPF WPF wyświetli czerwone obramowanie wokół nieprawidłowego formantu, jak pokazano na poniższym rysunku.  
  
![Okno dialogowe Marginesy z czerwonym obramowaniem wokół nieprawidłowej wartości lewego marginesu.](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

WPF WPF nie ogranicza użytkownika do nieprawidłowego formantu, dopóki nie wprowadzi prawidłowych danych. Jest to dobre zachowanie dla okna dialogowego; użytkownik powinien mieć możliwość swobodnego poruszania się po formanty w oknie dialogowym, czy dane są prawidłowe. Oznacza to jednak, że użytkownik może wprowadzić nieprawidłowe dane i nacisnąć przycisk **OK.** Z tego powodu kod musi również sprawdzić poprawność wszystkich formantów w oknie <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dialogowym po naciśnięciu przycisku **OK,** obsługując zdarzenie.  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

Ten kod wylicza wszystkie obiekty zależności w oknie i, jeśli <xref:System.Windows.Controls.Validation.GetHasError%2A>istnieją są nieprawidłowe (jak zwraca, nieprawidłowy formant pobiera fokus, `IsValid` metoda zwraca `false`, a okno jest uważane za nieprawidłowe.  
  
Gdy okno dialogowe jest prawidłowe, można bezpiecznie zamknąć i powrócić. W ramach procesu zwracania musi zwrócić wynik funkcji wywołującej.  
  
#### <a name="setting-the-modal-dialog-result"></a>Ustawianie wyniku modalnego okna dialogowego

Otwieranie okna <xref:System.Windows.Window.ShowDialog%2A> dialogowego przy użyciu jest zasadniczo jak wywołanie <xref:System.Windows.Window.ShowDialog%2A> metody: <xref:System.Windows.Window.ShowDialog%2A> kod, który otworzył okno dialogowe przy użyciu oczekiwania, aż powróci. Po <xref:System.Windows.Window.ShowDialog%2A> powrocie kod, który go wywoływał, musi zdecydować, czy kontynuować przetwarzanie, czy zatrzymać przetwarzanie, w zależności od tego, czy użytkownik nacisnął przycisk **OK,** czy przycisk **Anuluj.** Aby ułatwić tę decyzję, okno dialogowe musi zwrócić <xref:System.Boolean> wybór użytkownika jako <xref:System.Windows.Window.ShowDialog%2A> wartość, która jest zwracana z metody.  

Po **OK** kliknięciu przycisku <xref:System.Windows.Window.ShowDialog%2A> OK `true`należy zwrócić . Osiąga się to poprzez <xref:System.Windows.Window.DialogResult%2A> ustawienie właściwości okna dialogowego po kliknięciu przycisku **OK.**  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

Należy zauważyć, <xref:System.Windows.Window.DialogResult%2A> że ustawienie właściwości powoduje również automatyczne zamknięcie okna, co łagodzi potrzebę jawnego wywołania <xref:System.Windows.Window.Close%2A>.  
  
Po kliknięciu przycisku <xref:System.Windows.Window.ShowDialog%2A> **Anuluj,** powinien zwrócić <xref:System.Windows.Window.DialogResult%2A> `false`, co również wymaga ustawienia właściwości.  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

Gdy właściwość <xref:System.Windows.Controls.Button.IsCancel%2A> przycisku jest `true` ustawiona, a użytkownik naciśnie przycisk **Anuluj** lub klawisz ESC, <xref:System.Windows.Window.DialogResult%2A> jest automatycznie ustawiany na `false`. Poniższy znacznik ma taki sam efekt jak poprzedni kod, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> bez konieczności obsługi zdarzenia.  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

Okno dialogowe zostanie `false` automatycznie przywrócone, gdy użytkownik naciśnie przycisk **Zamknij** na pasku tytułu lub wybierze element menu **Zamknij** z menu **System.**  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Przetwarzanie danych zwróconych z okna dialogowego modalnego  

Gdy <xref:System.Windows.Window.DialogResult%2A> jest ustawiona przez okno dialogowe, funkcja, która go otworzyła, może uzyskać wynik okna dialogowego, sprawdzając <xref:System.Windows.Window.DialogResult%2A> właściwość podczas <xref:System.Windows.Window.ShowDialog%2A> zwracania.  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

Jeśli wynik okna `true`dialogowego jest , funkcja używa tego jako sygnał do pobierania i przetwarzania danych dostarczonych przez użytkownika.  
  
> [!NOTE]
> Po <xref:System.Windows.Window.ShowDialog%2A> powrocie nie można ponownie otworzyć okna dialogowego. Zamiast tego należy utworzyć nowe wystąpienie.

Jeśli wynik okna `false`dialogowego jest , funkcja powinna zakończyć przetwarzania odpowiednio.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>
### <a name="creating-a-modeless-custom-dialog-box"></a>Tworzenie niestandardowego okna dialogowego bez trybu

Niemodalne okno dialogowe, takie jak okno dialogowe Znajdowanie pokazane na poniższym rysunku, ma taki sam wygląd podstawowy jak okno dialogowe modalne.  

![Zrzut ekranu przedstawiający okno dialogowe Znajdowanie.](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

Jednak zachowanie jest nieco inna, jak opisano w poniższych sekcjach.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Otwieranie niemodytowego okna dialogowego

Niemodowe okno dialogowe jest <xref:System.Windows.Window.Show%2A> otwierane przez wywołanie metody.  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  

[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

W <xref:System.Windows.Window.ShowDialog%2A> <xref:System.Windows.Window.Show%2A> przeciwieństwie do , zwraca natychmiast. W związku z tym okno wywołujące nie może stwierdzić, kiedy niemodless okno dialogowe jest zamknięty i dlatego nie wie, kiedy sprawdzić wynik okna dialogowego lub uzyskać dane z okna dialogowego do dalszego przetwarzania. Zamiast tego okno dialogowe musi utworzyć alternatywny sposób zwracania danych do okna wywołującego do przetwarzania.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Przetwarzanie danych zwróconych z niemodalessowego okna dialogowego  

W tym przykładzie `FindDialogBox` może zwrócić jeden lub więcej wyników wyszukiwania do okna głównego, w zależności od tekstu wyszukiwane bez określonej częstotliwości. Podobnie jak w przypadku modalnego okna dialogowego, niemodalne okno dialogowe może zwracać wyniki przy użyciu właściwości. Jednak okno, które jest właścicielem okna dialogowego musi wiedzieć, kiedy sprawdzić te właściwości. Jednym ze sposobów włączenia tego jest dla okna dialogowego do zaimplementowania zdarzenia, które jest wywoływane, gdy tekst zostanie znaleziony. `FindDialogBox``TextFoundEvent` w tym celu, co najpierw wymaga delegata.  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

Za `TextFoundEventHandler` pomocą `FindDialogBox` delegata, `TextFoundEvent`implementuje .
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

W związku `Find` z tym można podnieść zdarzenie po znalezieniu wyniku wyszukiwania.  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

Okno właściciela następnie musi zarejestrować się i obsługiwać to zdarzenie.

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>Zamykanie niemodytowego okna dialogowego

Ponieważ <xref:System.Windows.Window.DialogResult%2A> nie trzeba ustawiać, niemodless okno dialogowe można zamknąć za pomocą systemu zapewniają mechanizmy, w tym następujące:  
  
- Kliknięcie przycisku **Zamknij** na pasku tytułu.  
  
- Naciśnięcie klawisza ALT+F4.  
  
- Wybranie **opcji Zamknij** z menu **System.**  
  
Alternatywnie kod można <xref:System.Windows.Window.Close%2A> wywołać po kliknięciu przycisku **Zamknij.**  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>Zobacz też

- [Okno podręczne — omówienie](../controls/popup-overview.md)
- [Przykład okna dialogowego](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)
