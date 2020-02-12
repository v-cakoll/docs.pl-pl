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
ms.openlocfilehash: bce2eed5f0e78c16b85b399e588c3d0d68ce7cb7
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123717"
---
# <a name="dialog-boxes-overview"></a>Okna dialogowe — Omówienie
Aplikacje autonomiczne zwykle mają główne okno, które wyświetla główne dane, nad którymi działa aplikacja, i udostępnia funkcję przetwarzania tych danych za pomocą mechanizmów [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], takich jak paski menu, paski narzędzi i paski stanu. Nieuproszczona aplikacja może również wyświetlać dodatkowe okna, aby wykonać następujące czynności:  
  
- Wyświetl konkretne informacje dla użytkowników.  
  
- Zbierz informacje od użytkowników.  
  
- Wyświetla i zbiera informacje.  
  
 Te typy okien są znane jako *okna dialogowe*, a istnieją dwa typy: modalne i niemodalne.  
  
 *Modalne* okno dialogowe jest wyświetlane przez funkcję, gdy funkcja wymaga dodatkowych danych od użytkownika, aby kontynuować. Ponieważ funkcja jest zależna od modalnego okna dialogowego do zbierania danych, modalne okno dialogowe uniemożliwia również użytkownikowi aktywowanie innych okien w aplikacji, gdy pozostanie otwarte. W większości przypadków modalne okno dialogowe umożliwia użytkownikowi sygnalizowanie po zakończeniu pracy z modalnym oknem dialogowym przez naciśnięcie przycisku **OK** lub **Anuluj** . Naciśnięcie przycisku **OK** oznacza, że użytkownik wprowadził dane i chce, aby funkcja kontynuowała przetwarzanie za pomocą tych danych. Naciśnięcie przycisku **Anuluj** oznacza, że użytkownik chce zatrzymać wykonywanie funkcji całkowicie. Najbardziej typowe przykłady modalnych okien dialogowych są wyświetlane, aby otwierać, zapisywać i drukować dane.  
  
 *Niemodalne* okno dialogowe, z drugiej strony, nie uniemożliwia użytkownikowi aktywowania innych okien, gdy jest otwarty. Na przykład, jeśli użytkownik chce znaleźć wystąpienia określonego wyrazu w dokumencie, okno główne często otwiera okno dialogowe z monitem o wyszukanie użytkownika. Ponieważ znalezienie słowa nie zapobiega edytowaniu dokumentu przez użytkownika, okno dialogowe nie musi być modalne. Niemodalne okno dialogowe z co najmniej udostępnia przycisk **Zamknij** , aby zamknąć okno dialogowe i może udostępnić dodatkowe przyciski do wykonywania określonych funkcji, takich jak przycisk **Znajdź dalej** , aby znaleźć następny wyraz, który pasuje do kryteriów wyszukiwania szukanych wyrazów.  
  
 Windows Presentation Foundation (WPF) umożliwia tworzenie kilku typów okien dialogowych, w tym pól komunikatów, wspólnych okien dialogowych i niestandardowych okien dialogowych. W tym temacie omówiono każdy i [przykład okna dialogowego](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox) zawiera pasujące przykłady.  

<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>Okna komunikatów  
 *Okno komunikatu* to okno dialogowe, za pomocą którego można wyświetlić informacje tekstowe i umożliwić użytkownikom podejmowanie decyzji przy użyciu przycisków. Na poniższej ilustracji przedstawiono okno komunikatu, które wyświetla informacje tekstowe, prosi o pytanie i udostępnia użytkownikowi trzy przyciski, aby odpowiedzieć na pytanie.  
  
 ![Okno dialogowe Edytor tekstów z pytaniem, czy chcesz zapisać zmiany w dokumencie przed zamknięciem aplikacji.](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 Aby utworzyć okno komunikatu, użyj klasy <xref:System.Windows.MessageBox>. <xref:System.Windows.MessageBox> umożliwia skonfigurowanie tekstu, tytułu, ikony i przycisków okna komunikatu przy użyciu kodu, takiego jak poniższy.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Aby wyświetlić okno komunikatu, należy wywołać metodę <xref:System.Windows.MessageBox.Show%2A> `static`, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Gdy kod, który pokazuje okno komunikatu, musi wykryć i przetworzyć decyzję użytkownika (który został naciśnięty przycisk), kod może sprawdzić wynik okna komunikatu, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 Aby uzyskać więcej informacji o korzystaniu z okien komunikatów, zobacz <xref:System.Windows.MessageBox>, [MessageBox Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)i [Box okna dialogowego](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox).  
  
 Mimo że <xref:System.Windows.MessageBox> mogą oferować proste środowisko użytkownika okna dialogowego, zaletą korzystania z <xref:System.Windows.MessageBox> jest to jedyny typ okna, który może być pokazywany przez aplikacje działające w obszarze piaskownicy zabezpieczeń częściowej relacji zaufania (zobacz [zabezpieczenia](../security-wpf.md)), takie jak aplikacje przeglądarki XAML (XBAP).  
  
 Większość okien dialogowych wyświetla i zbiera bardziej złożone dane niż wynik okna komunikatu, w tym tekst, zaznaczenie (pola wyboru), wzajemnie wykluczające się zaznaczenie (przyciski radiowe) i wybór listy (pola listy, pola kombi, pola listy rozwijanej). Dla tych Windows Presentation Foundation (WPF) udostępnia kilka wspólnych okien dialogowych i umożliwia tworzenie własnych okien dialogowych, chociaż korzystanie z nich jest ograniczone do aplikacji działających z pełnym zaufaniem.  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>Wspólne okna dialogowe  
 System Windows implementuje różne okna dialogowe wielokrotnego użytku, które są wspólne dla wszystkich aplikacji, w tym okna dialogowe do otwierania plików, zapisywania plików i drukowania. Ponieważ te okna dialogowe są implementowane przez system operacyjny, mogą być współużytkowane przez wszystkie aplikacje działające w systemie operacyjnym, co pomaga zapewnić spójność środowiska użytkownika. gdy użytkownicy znają korzystanie z okna dialogowego dostarczonego przez system operacyjny w jednej aplikacji, nie muszą dowiedzieć się, jak korzystać z tego okna dialogowego w innych aplikacjach. Ponieważ te okna dialogowe są dostępne dla wszystkich aplikacji, a ponieważ zapewniają spójne środowisko użytkownika, są one znane jako *wspólne okna dialogowe*.  
  
 Windows Presentation Foundation (WPF) hermetyzuje okna dialogowe Otwórz plik, Zapisz plik i Drukuj, które udostępniają je jako klasy zarządzane do użycia w aplikacjach autonomicznych. Ten temat zawiera krótkie omówienie każdego z nich.  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>Otwórz okno dialogowe pliku  
 Okno dialogowe Otwórz plik, pokazane na poniższym rysunku, jest używane przez funkcję otwierania plików do pobrania nazwy pliku do otwarcia.  
  
 ![Otwarte okno dialogowe pokazujące lokalizację, w której ma zostać pobrany plik.](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 Okno dialogowe Common Open File jest zaimplementowane jako Klasa <xref:Microsoft.Win32.OpenFileDialog> i znajduje się w przestrzeni nazw <xref:Microsoft.Win32>. Poniższy kod pokazuje, jak tworzyć, konfigurować i wyświetlać je oraz jak przetwarzać wynik.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Aby uzyskać więcej informacji na temat okna dialogowego Otwórz plik, zobacz <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.  
  
> [!NOTE]
> <xref:Microsoft.Win32.OpenFileDialog> może służyć do bezpiecznego pobierania nazw plików przez aplikacje działające z częściowym zaufaniem (zobacz [zabezpieczenia](../security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>Zapisz Plik — Okno dialogowe  
 Okno dialogowe Zapisz plik, pokazane na poniższym rysunku, jest używane przez funkcję zapisywania plików do pobrania nazwy pliku do zapisania.  
  
 ![Okno dialogowe Zapisz jako z lokalizacją, w której ma zostać zapisany plik.](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 Okno dialogowe często zapisywany plik jest zaimplementowane jako Klasa <xref:Microsoft.Win32.SaveFileDialog> i znajduje się w przestrzeni nazw <xref:Microsoft.Win32>. Poniższy kod pokazuje, jak tworzyć, konfigurować i wyświetlać je oraz jak przetwarzać wynik.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Aby uzyskać więcej informacji na temat okna dialogowego Zapisywanie pliku, zobacz <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>Drukuj — Okno dialogowe

Okno dialogowe Drukowanie, pokazane na poniższym rysunku, jest używane przez funkcję drukowania do wybierania i konfigurowania drukarki, do której użytkownik chce drukować dane.  
  
![Zrzut ekranu przedstawiający okno dialogowe Drukowanie.](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
Wspólne okno dialogowe drukowania jest zaimplementowane jako Klasa <xref:System.Windows.Controls.PrintDialog> i znajduje się w przestrzeni nazw <xref:System.Windows.Controls>. Poniższy kod przedstawia sposób tworzenia, konfigurowania i wyświetlania jednego z nich.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Aby uzyskać więcej informacji na temat okna dialogowego drukowanie, zobacz <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>. Aby uzyskać szczegółowe omówienie drukowania w WPF, zobacz [Omówienie drukowania](../advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>Niestandardowe okna dialogowe

Chociaż wspólne okna dialogowe są przydatne i powinny być używane, jeśli jest to możliwe, nie obsługują wymagań okien dialogowych specyficznych dla domeny. W takich przypadkach należy utworzyć własne okna dialogowe. Jak zobaczymy, okno dialogowe jest oknem z zachowaniem specjalnym. <xref:System.Windows.Window> implementuje te zachowania i, w związku z tym, używasz <xref:System.Windows.Window> do tworzenia niestandardowych modalnych i niemodalnych okien dialogowych.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>Tworzenie modalnego niestandardowego okna dialogowego

W tym temacie pokazano, jak używać <xref:System.Windows.Window> do tworzenia typowej implementacji modalnego okna dialogowego przy użyciu okna dialogowego `Margins` (Zobacz przykład [okna dialogowego](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)). Okno dialogowe `Margins` jest pokazane na poniższym rysunku.  
  
 ![Okno dialogowe marginesów z polami do definiowania lewego marginesu, górnego marginesu, prawego marginesu i dolnego marginesu.](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>Konfigurowanie modalnego okna dialogowego

Interfejs użytkownika typowego okna dialogowego zawiera następujące elementy:  
  
- Różne kontrolki, które są wymagane do zebrania żądanych danych.  
  
- Kliknij przycisk **OK** , aby zamknąć okno dialogowe, Wróć do funkcji i Kontynuuj przetwarzanie.  
  
- Przycisk **Anuluj** kliknięty przez użytkowników, aby zamknąć okno dialogowe i zatrzymać funkcję od dalszej obróbki.  
  
- Przycisk **Zamknij** na pasku tytułu.  
  
- Ikona.  
  
- Przyciski **Minimalizuj**, **Maksymalizuj**i **Przywróć** .  
  
- Menu **systemowe** umożliwiające minimalizowanie, zmaksymalizowanie, przywrócenie i zamknięcie okna dialogowego.  
  
- Pozycja powyżej i w środku okna, które otworzyło okno dialogowe.  
  
- Możliwość zmiany rozmiaru w miarę możliwości, aby zapobiec zbyt małym oknem okna dialogowego i zapewnić użytkownikowi przydatny rozmiar domyślny. Wymaga to ustawienia domyślnego i minimalnego wymiaru.  
  
- Klawisz ESC jako skrót klawiaturowy, który powoduje naciśnięcie przycisku **Anuluj** . W tym celu należy ustawić właściwość <xref:System.Windows.Controls.Button.IsCancel%2A> przycisku **Anuluj** na `true`.  
  
- Klawisz ENTER (lub RETURN) jako skrót klawiaturowy, który powoduje naciśnięcie przycisku **OK** . W tym celu należy ustawić właściwość <xref:System.Windows.Controls.Button.IsDefault%2A> przycisku **OK** `true`.  
  
Poniższy kod ilustruje tę konfigurację.  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
Środowisko użytkownika dla okna dialogowego rozciąga się również na pasek menu okna dialogowego, które otwiera okno dialogowe. Gdy element menu uruchamia funkcję, która wymaga interakcji użytkownika za pomocą okna dialogowego, zanim będzie można kontynuować działanie, element menu dla funkcji będzie miał wielokropek w nagłówku, jak pokazano poniżej.  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
Gdy element menu uruchamia funkcję, która wyświetla okno dialogowe, które nie wymaga interakcji z użytkownikiem, takie jak okno dialogowe informacje, wielokropek nie jest wymagany.  
  
#### <a name="opening-a-modal-dialog-box"></a>Otwieranie modalnego okna dialogowego

Okno dialogowe jest zwykle wyświetlane jako wynik użytkownika, który wybiera element menu do wykonania funkcji specyficznej dla domeny, na przykład ustawiając marginesy dokumentu w edytorze tekstów. Wyświetlanie okna jako okno dialogowe jest podobne do wyświetlania normalnego okna, chociaż wymaga dodatkowej konfiguracji specyficznej dla okna dialogowego. W poniższym kodzie pokazano cały proces tworzenia wystąpienia, konfigurowania i otwierania okna dialogowego.  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

W tym miejscu kod przekazuje domyślne informacje (bieżące marginesy) do okna dialogowego. Ustawia również właściwość <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> z odwołaniem do okna, które jest wyświetlane okno dialogowe. Ogólnie rzecz biorąc, należy zawsze ustawić właściciela dla okna dialogowego, aby podać zachowania związane ze stanem okna, które są wspólne dla wszystkich okien dialogowych (zobacz [Omówienie systemu Windows WPF](wpf-windows-overview.md) , aby uzyskać więcej informacji).

> [!NOTE]
> Musisz podać właściciela, aby obsługiwał automatyzację interfejsu użytkownika (UI) dla okien dialogowych (zobacz [Automatyzacja interfejsu](../../ui-automation/ui-automation-overview.md)użytkownika).

Po skonfigurowaniu okna dialogowego zostanie ono wyświetlone w sposób modalny przez wywołanie metody <xref:System.Windows.Window.ShowDialog%2A>.  
  
#### <a name="validating-user-provided-data"></a>Sprawdzanie poprawności danych dostarczonych przez użytkownika

Gdy okno dialogowe zostanie otwarte, a użytkownik poda wymagane dane, okno dialogowe jest odpowiedzialne za upewnienie się, że podane dane są prawidłowe z następujących powodów:  
  
- Z punktu widzenia zabezpieczeń należy sprawdzić poprawność wszystkich danych wejściowych.  
  
- W perspektywie specyficznej dla domeny weryfikacja danych uniemożliwia przetwarzanie błędnych danych przez kod, co może potencjalnie zgłosić wyjątki.  
  
- Z perspektywy użytkownika, okno dialogowe może ułatwić użytkownikom wyświetlanie, które wprowadzone przez siebie dane są nieprawidłowe.  
  
- Z punktu widzenia wydajności sprawdzanie poprawności danych w aplikacji wielowarstwowej może zmniejszyć liczbę rund między klientem a warstwami aplikacji, zwłaszcza gdy aplikacja składa się z usług sieci Web lub baz danych opartych na serwerze.  

Aby sprawdzić poprawność kontroli powiązanej w WPF, należy zdefiniować regułę walidacji i skojarzyć ją z powiązaniem. Reguła walidacji jest klasą niestandardową, która pochodzi od <xref:System.Windows.Controls.ValidationRule>. W poniższym przykładzie przedstawiono regułę walidacji, `MarginValidationRule`, która sprawdza, czy wartość powiązana jest <xref:System.Double> i znajduje się w określonym zakresie.  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

W tym kodzie logika walidacji reguły walidacji jest implementowana przez zastąpienie metody <xref:System.Windows.Controls.ValidationRule.Validate%2A>, która sprawdza poprawność danych i zwraca odpowiednie <xref:System.Windows.Controls.ValidationResult>.  

Aby skojarzyć regułę walidacji z kontrolką powiązaną, należy użyć następującego znacznika.  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

Po skojarzeniu reguły walidacji program WPF automatycznie zastosuje ją po wprowadzeniu danych do kontrolki powiązanej. Gdy kontrolka zawiera nieprawidłowe dane, WPF wyświetli czerwone obramowanie wokół nieprawidłowej kontrolki, jak pokazano na poniższej ilustracji.  
  
![Okno dialogowe marginesów z czerwonym obramowaniem wokół nieprawidłowej wartości lewego marginesu.](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

Funkcja WPF nie ogranicza użytkownika do nieprawidłowej kontrolki, dopóki nie wprowadzili prawidłowych danych. Jest to dobre zachowanie w przypadku okna dialogowego; Użytkownik powinien mieć możliwość swobodnego nawigowania po kontrolkach w oknie dialogowym, niezależnie od tego, czy dane są prawidłowe. Oznacza to jednak, że użytkownik może wprowadzić nieprawidłowe dane i nacisnąć przycisk **OK** . Z tego powodu kod musi również sprawdzać poprawność wszystkich kontrolek w oknie dialogowym po naciśnięciu przycisku **OK** przez obsługę zdarzenia <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

Ten kod wylicza wszystkie obiekty zależności w oknie i, jeśli którykolwiek z nich jest nieprawidłowy (w wyniku zwrócenia przez <xref:System.Windows.Controls.Validation.GetHasError%2A>, nieprawidłowy formant uzyskuje fokus, Metoda `IsValid` zwróci `false`, a okno zostanie uznane za nieprawidłowe.  
  
Gdy okno dialogowe jest prawidłowe, może je bezpiecznie zamknąć i zwrócić. W ramach procesu powrotu musi zwrócić wynik do funkcji wywołującej.  
  
#### <a name="setting-the-modal-dialog-result"></a>Ustawianie wyniku dialogu modalnego

Otwieranie okna dialogowego przy użyciu <xref:System.Windows.Window.ShowDialog%2A> jest zasadniczo podobne do wywołania metody: kod, który otworzył okno dialogowe przy użyciu <xref:System.Windows.Window.ShowDialog%2A> czeka na <xref:System.Windows.Window.ShowDialog%2A>. Gdy <xref:System.Windows.Window.ShowDialog%2A> zwraca, kod, który wywołał, musi zdecydować, czy kontynuować przetwarzanie czy zatrzymać przetwarzanie, w zależności od tego, czy użytkownik naciśnie przycisk **OK** , czy przycisk **Anuluj** . Aby ułatwić tę decyzję, okno dialogowe musi zwrócić wybór użytkownika jako wartość <xref:System.Boolean>, która jest zwracana z metody <xref:System.Windows.Window.ShowDialog%2A>.  

Po kliknięciu przycisku **OK** <xref:System.Windows.Window.ShowDialog%2A> powinien zwrócić `true`. Jest to osiągane przez ustawienie właściwości <xref:System.Windows.Window.DialogResult%2A> okna dialogowego, gdy kliknięto przycisk **OK** .  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

Należy zauważyć, że ustawienie właściwości <xref:System.Windows.Window.DialogResult%2A> powoduje również Automatyczne zamknięcie okna, co pozwala uniknąć konieczności jawnego wywołania <xref:System.Windows.Window.Close%2A>.  
  
Gdy klikniesz przycisk **Anuluj** , <xref:System.Windows.Window.ShowDialog%2A> powinien zwrócić `false`, co wymaga również ustawienia właściwości <xref:System.Windows.Window.DialogResult%2A>.  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

Gdy właściwość <xref:System.Windows.Controls.Button.IsCancel%2A> przycisku jest ustawiona na `true`, a użytkownik naciśnie przycisk **Anuluj** lub klawisz ESC, <xref:System.Windows.Window.DialogResult%2A> jest automatycznie ustawiana na `false`. Następujący znacznik ma ten sam skutek jak poprzedni kod, bez konieczności obsłużenia zdarzenia <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

Okno dialogowe automatycznie zwraca `false`, gdy użytkownik naciśnie przycisk **Zamknij** na pasku tytułu lub wybierze element menu **Zamknij** z menu **system** .  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Przetwarzanie danych zwróconych z modalnego okna dialogowego  

Gdy <xref:System.Windows.Window.DialogResult%2A> jest ustawiana za pomocą okna dialogowego, funkcja, która otworzyła go, może uzyskać wynik okna dialogowego, sprawdzając Właściwość <xref:System.Windows.Window.DialogResult%2A> po powrocie <xref:System.Windows.Window.ShowDialog%2A>.  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

Jeśli wynik okna dialogowego jest `true`, funkcja używa tej funkcji jako wskaźnika do pobierania i przetwarzania danych dostarczonych przez użytkownika.  
  
> [!NOTE]
> Po powrocie <xref:System.Windows.Window.ShowDialog%2A> nie można otworzyć okna dialogowego. Zamiast tego należy utworzyć nowe wystąpienie.

Jeśli wynik okna dialogowego jest `false`, funkcja powinna zostać odpowiednio zakończona.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>Tworzenie niemodalnego niestandardowego okna dialogowego

Niemodalne okno dialogowe, takie jak okno dialogowe Znajdź pokazane na poniższej ilustracji ma ten sam wygląd, jak modalne okno dialogowe.  

![Zrzut ekranu przedstawiający okno dialogowe Znajdowanie.](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

Zachowanie jest jednak nieco inne, zgodnie z opisem w poniższych sekcjach.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Otwieranie niemodalnego okna dialogowego

Niemodalne okno dialogowe jest otwierane przez wywołanie metody <xref:System.Windows.Window.Show%2A>.  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  
 
[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

W przeciwieństwie do <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> zwraca natychmiast. W związku z tym okno wywołujące nie może stwierdzić, kiedy okno dialogowe niemodalne jest zamknięte i w związku z tym nie wie, kiedy sprawdzać wynik okna dialogowego lub pobrać dane z okna dialogowego w celu dalszej obróbki. Zamiast tego okno dialogowe musi utworzyć alternatywny sposób zwrócenia danych do okna wywołującego w celu przetworzenia.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Przetwarzanie danych zwróconych z niemodalnego okna dialogowego  

W tym przykładzie `FindDialogBox` może zwrócić jeden lub więcej wyników wyszukiwania do okna głównego, w zależności od wyszukiwanego tekstu bez żadnej konkretnej częstotliwości. Podobnie jak w przypadku modalnego okna dialogowego, niemodalne okno dialogowe może zwracać wyniki przy użyciu właściwości. Jednak okno, które jest właścicielem okna dialogowego, musi wiedzieć, kiedy należy sprawdzić te właściwości. Jednym ze sposobów na włączenie tego okna dialogowego jest zaimplementowanie zdarzenia, które jest zgłaszane po każdym znalezieniu tekstu. `FindDialogBox` implementuje w tym celu `TextFoundEvent`, który najpierw wymaga delegata.  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

Za pomocą delegata `TextFoundEventHandler` `FindDialogBox` implementuje `TextFoundEvent`.
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

W związku z tym `Find` może zgłosić zdarzenie po znalezieniu wyniku wyszukiwania.  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

Okno właściciela musi być następnie zarejestrowane w usłudze i obsłużyć to zdarzenie.

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>Zamykanie niemodalnego okna dialogowego

Ponieważ nie trzeba ustawiać <xref:System.Windows.Window.DialogResult%2A>, niemodalne okno dialogowe można zamknąć przy użyciu mechanizmów zapewniania systemu, w tym następujących:  
  
- Kliknij przycisk **Zamknij** na pasku tytułu.  
  
- Naciśnij klawisze ALT + F4.  
  
- Wybierz pozycję **Zamknij** z menu **systemowego** .  
  
Alternatywnie kod może wywoływać <xref:System.Windows.Window.Close%2A> po kliknięciu przycisku **Zamknij** .  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>Zobacz też

- [Okno podręczne — omówienie](../controls/popup-overview.md)
- [Przykład okna dialogowego](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)
