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
ms.openlocfilehash: 110e42fea8d5586e471ae36ead46bed304cf9f48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dialog-boxes-overview"></a>Przegląd okien dialogowych
Aplikacje autonomiczne zwykle mają okno główne zarówno powoduje wyświetlenie głównego danych za pośrednictwem której aplikacja działa i udostępnia funkcje do przetwarzania danych za pośrednictwem [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] mechanizmów, takich jak paski menu, pasków narzędzi i paski stanu. — Prosta aplikacja może również wyświetlić dodatkowe okna, aby wykonać następujące czynności:  
  
-   Wyświetlać określone informacje dla użytkowników.  
  
-   Zbieranie informacji od użytkowników.  
  
-   Zarówno Wyświetl i zbierać informacje.  
  
 Tego rodzaju systemu windows są określane jako *okien dialogowych*, i istnieją dwa typy: modalne i niemodalne.  
  
 A *modalne* okno dialogowe jest wyświetlane przez funkcję, gdy funkcja wymaga dodatkowych danych od użytkownika, aby kontynuować. Ponieważ funkcja jest zależna od modalne okno dialogowe do zbierania danych, modalnego okna dialogowego również uniemożliwia użytkownikowi aktywowanie innych okien w aplikacji, gdy zostanie zamknięte. W większości przypadków modalne okno dialogowe umożliwia użytkownikowi sygnału po zakończeniu ich z modalnego okna dialogowego przez naciśnięcie przycisku albo **OK** lub **anulować** przycisku. Naciśnięcie przycisku **OK** przycisk oznacza, że użytkownik ma wprowadzonych danych oczekuje, że funkcja kontynuować przetwarzanie z tymi danymi. Naciśnięcie przycisku **anulować** przycisk oznacza, że użytkownik chce, aby zatrzymać funkcji wykonywania całkowicie. Najbardziej typowe przykłady modalne okna dialogowe są wyświetlane otworzyć, zapisywania i drukowania danych.  
  
 A *niemodalne* okno dialogowe z drugiej strony, nie zapobiega użytkownika aktywacji innych systemu windows, gdy jest otwarty. Na przykład jeśli użytkownik chce, aby wyszukać wystąpienia określonego wyrazu w dokumencie, okno główne będzie często otworzyć okno dialogowe poprosić użytkownika programu word, jakie szukają. Ponieważ wyszukiwanie wyrazu nie zapobiec edycji dokumentu przez użytkownika, jednak okna dialogowego nie musi być modalne. Niemodalne okna dialogowe co najmniej zapewnia **zamknąć** przycisk, aby zamknąć okno dialogowe i mogą dostarczać dodatkowych przycisków do wykonywania określonych funkcji, takich jak **Znajdź następny** przycisk, aby znaleźć następne programu word, który kryteria znajdowania wyszukiwania programu word.  
  
 Windows Presentation Foundation (WPF) umożliwia tworzenie wielu typów okien dialogowych, w tym pola wiadomości, wspólne okna dialogowe i niestandardowych okien dialogowych. W tym temacie omówiono poszczególnych usług i [przykładowe okno dialogowe](http://go.microsoft.com/fwlink/?LinkID=159984) przykłady dopasowania.  
  
 
  
<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>Pola komunikatów  
 A *komunikat* to okno dialogowe, który może służyć do wyświetlania informacji tekstowych i umożliwiają podejmowanie decyzji o przycisków. Na poniższej ilustracji przedstawiono okno komunikatu, która wyświetla informacji tekstowych, zadaje pytanie i dostarcza użytkownikowi trzy przyciski udzielenia odpowiedzi na pytanie.  
  
 ![Okno dialogowe Edytor tekstów](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure1.png "DialogBoxesOverviewFigure1")  
  
 Aby utworzyć okno komunikatu, należy użyć <xref:System.Windows.MessageBox> klasy. <xref:System.Windows.MessageBox> Umożliwia skonfigurowanie tekst pola wiadomości, tytuł, ikony i przyciski, za pomocą kodu podobne do następujących.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Aby wyświetlić okno komunikatu, należy wywołać `static` <xref:System.Windows.MessageBox.Show%2A> metody, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Gdy kod, który pokazuje okno komunikatu musi wykrywania i przetwarzania decyzja użytkownika (który przycisk został naciśnięty), kod sprawdzić wynik okno komunikatu, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 Aby uzyskać więcej informacji na temat używania pól komunikatu, zobacz <xref:System.Windows.MessageBox>, [próbki MessageBox](http://go.microsoft.com/fwlink/?LinkID=160023), i [przykładowe okno dialogowe](http://go.microsoft.com/fwlink/?LinkID=159984).  
  
 Mimo że <xref:System.Windows.MessageBox> mogą oferować prostego okna dialogowego pole użytkowników, zaletą korzystania z <xref:System.Windows.MessageBox> jest to jedyny typ okna, które mogą być wyświetlane w aplikacji działających w częściowej relacji zaufania piaskownicy zabezpieczeń (zobacz [zabezpieczeń](../../../../docs/framework/wpf/security-wpf.md)), takich jak [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
 Większość okien dialogowych Wyświetl i zbierania danych bardziej złożone niż wynik okno komunikatu, łącznie z tekstem, wybór (pola wyboru), wybór wykluczają się wzajemnie (przyciski radiowe) i listy wyboru (pola listy, pola kombi, pola listy rozwijanej). W tym przypadku Windows Presentation Foundation (WPF) zawiera kilka wspólne okna dialogowe i służy do tworzenia własnych okien dialogowych, mimo że korzystanie z albo jest ograniczony do aplikacji działających przy pełnym zaufaniu.  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>Wspólne okna dialogowe  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] implementuje wiele okien dialogowych wielokrotnego użytku, które są wspólne dla wszystkich aplikacji, w tym okien dialogowych służących do otwarcia plików, zapisywanie plików i drukowania. Ponieważ tych okien dialogowych są implementowane przez system operacyjny, mogły być udostępniane między wszystkich aplikacji uruchomionych w systemie operacyjnym, co pomaga spójności; interfejs użytkownika gdy użytkownicy zapoznali się przy użyciu okna dialogowego dostarczane przez system operacyjny w jednej aplikacji, nie muszą dowiedzieć się, jak używać tego okna dialogowego w innych aplikacjach. Ponieważ okna te są dostępne dla wszystkich aplikacji, a ponieważ one zapewnić spójny interfejs użytkownika, są określane jako *wspólne okna dialogowe*.  
  
 Otwórz plik hermetyzuje Windows Presentation Foundation (WPF), Zapisz plik i drukowanie wspólnych okien dialogowych i udostępnia je jako zarządzanych klas do użycia w aplikacjach autonomicznych. Ten temat zawiera krótkie omówienie każdego z nich.  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>Okno dialogowe Otwieranie pliku  
 Okno dialogowe Otwieranie pliku pokazano na poniższej ilustracji, jest używana przez plik otwieranie funkcji pobrać nazwy pliku do otwarcia.  
  
 ![Okno dialogowe Otwieranie](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure2.png "DialogBoxesOverviewFigure2")  
  
 Wspólne okna dialogowe Otwieranie pliku jest zaimplementowany jako <xref:Microsoft.Win32.OpenFileDialog> klasy i znajduje się w <xref:Microsoft.Win32> przestrzeni nazw. Poniższy kod przedstawia sposób tworzenia, konfigurowania i jeden oraz sposób przetwarzania wynik.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Aby uzyskać więcej informacji, otwórz plik — okno dialogowe, zobacz <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog> można bezpiecznie pobrać nazwy pliku przez aplikacje działające z częściowa relacja zaufania (zobacz [zabezpieczeń](../../../../docs/framework/wpf/security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>Zapisz plik — okno dialogowe  
 Zapisz plik — okno dialogowe, pokazane na poniższej ilustracji, jest używany przez funkcje zapisywania pliku pobrać nazwy pliku do zapisania.  
  
 ![Okno dialogowe Zapisz jako](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure3.png "DialogBoxesOverviewFigure3")  
  
 Typowe Zapisz plik — okno dialogowe jest zaimplementowany jako <xref:Microsoft.Win32.SaveFileDialog> klasy i znajduje się w <xref:Microsoft.Win32> przestrzeni nazw. Poniższy kod przedstawia sposób tworzenia, konfigurowania i jeden oraz sposób przetwarzania wynik.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Aby uzyskać więcej informacji na temat zapisywania pliku — okno dialogowe, zobacz <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>Drukuj — okno dialogowe  
 Okno dialogowe drukowania, co pokazano na poniższej ilustracji służy funkcja drukowania można wybrać i skonfigurować drukarki, które użytkownik chce danych do drukowania.  
  
 ![Okno dialogowe drukowania](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure4.png "DialogBoxesOverviewFigure4")  
  
 Okno dialogowe drukowania wspólnej jest zaimplementowany jako <xref:System.Windows.Controls.PrintDialog> klasy i znajduje się w <xref:System.Windows.Controls> przestrzeni nazw. Poniższy kod przedstawia sposób tworzenia, konfigurowania i jeden.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Aby uzyskać więcej informacji w oknie dialogowym, zobacz <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>. Szczegółowe omówienie drukowania w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zobacz [Omówienie drukowania](../../../../docs/framework/wpf/advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>Niestandardowych okien dialogowych  
 Wspólne okna dialogowe są przydatne, i powinien być używany, gdy jest to możliwe, które nie obsługują wymagania właściwe dla domeny okien dialogowych. W takich przypadkach musisz utworzyć własne okien dialogowych. Jak zajmiemy się tym, okno dialogowe jest okno programu przy użyciu specjalnego zachowania. <xref:System.Windows.Window> implementuje te zachowania i w związku z tym, użyj <xref:System.Windows.Window> do tworzenia niestandardowych modalne i Niemodalne okna dialogowe.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>Tworzenie modalnych niestandardowe okno dialogowe  
 W tym temacie przedstawiono sposób użycia <xref:System.Windows.Window> do utworzenia implementacji pole typowe modalnego okna dialogowego za pomocą `Margins` okno dialogowe jako przykład (zobacz [przykładowe okno dialogowe](http://go.microsoft.com/fwlink/?LinkID=159984)). `Margins` Okno dialogowe jest wyświetlane na poniższej ilustracji.  
  
 ![Okno dialogowe marginesy](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure5.png "DialogBoxesOverviewFigure5")  
  
#### <a name="configuring-a-modal-dialog-box"></a>Konfigurowanie modalne okno dialogowe  
 Interfejs użytkownika dla typowych okno dialogowe obejmuje następujące funkcje:  
  
-   Różnych formantów, które są wymagane do zbierania żądanych danych.  
  
-   Wyświetlanie **OK** przycisku, że użytkownicy kliknij, aby zamknąć okno dialogowe, wróć do funkcji i kontynuować przetwarzania.  
  
-   Wyświetlanie **anulować** przycisku, który użytkownicy kliknij, aby zamknąć okno dialogowe i zatrzymać dalsze przetwarzanie funkcji.  
  
-   Wyświetlanie **Zamknij** przycisku w pasku tytułu.  
  
-   Wyświetlanie ikon.  
  
-   Wyświetlanie **Minimalizuj**, **Maksymalizuj**, i **przywrócić** przycisków.  
  
-   Wyświetlanie **systemu** menu, aby zminimalizować, zmaksymalizować, przywracania i zamknąć okno dialogowe.  
  
-   Otwieranie w górę i w środku okna otwarte okno dialogowe.  
  
-   Okna dialogowe powinien być odpowiednio wymiarów o zmiennych rozmiarach, jeśli jest to możliwe, tak aby uniemożliwić okna dialogowego za mały, a aby przyznać użytkownikowi o rozmiarze przydatna, należy określić zarówno domyślny, jak i co najmniej.  
  
-   Naciśnięcie klawisza ESC powinna być skonfigurowana jako skrót klawiaturowy, który powoduje, że **anulować** przycisk jest naciśnięty. Jest to osiągane przez ustawienie <xref:System.Windows.Controls.Button.IsCancel%2A> właściwość **anulować** przycisk, aby `true`.  
  
-   Naciśnięcie klawisza ENTER (lub RETURN) powinna być skonfigurowana jako skrót klawiaturowy, który powoduje, że **OK** przycisk jest naciśnięty. Jest to osiągane przez ustawienie <xref:System.Windows.Controls.Button.IsDefault%2A> właściwość **OK** przycisk `true`.  
  
 Poniższy kod ilustruje tę konfigurację.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup2)]  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind2)]  
  
 Środowisko użytkownika dla okna dialogowego rozszerzają na pasku menu okna, które otwiera okno dialogowe. Po uruchomieniu funkcji, która wymaga interakcji z użytkownikiem za pomocą okna dialogowego, zanim będzie można kontynuować funkcji elementu menu element menu dla funkcji ma wielokropek w jej nagłówku, jak pokazano poniżej.  
  
 [!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup1)]  
[!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup2)]  
  
 Wielokropek element menu działa funkcja, która wyświetla okno dialogowe, które nie wymagają interakcji użytkownika, na przykład okno dialogowe informacje, nie jest wymagane.  
  
#### <a name="opening-a-modal-dialog-box"></a>Otwieranie modalne okno dialogowe  
 Okno dialogowe zazwyczaj znajduje się w wyniku użytkownikowi wybranie elementu menu do wykonywania funkcji specyficznego dla domeny, takie jak ustawienie marginesów dokumentu w edytorze tekstów. Przedstawiający okno jako okno dialogowe przypomina przedstawiający okno normalne, chociaż wymagane dodatkowe okno pole konfiguracyjne. Cały proces tworzenia wystąpienia, konfigurowanie i otwierając okno dialogowe jest wyświetlane w poniższym kodzie.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind4)]  
  
 W tym miejscu kod jest przekazanie informacji domyślnych (bieżące marginesy) do okna dialogowego. Jest również ustawienie <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> właściwości z odwołaniem do okna, które jest wyświetlane okno dialogowe. Ogólnie rzecz biorąc, zawsze należy ustawić właściciela dla okna dialogowego zapewnienie związanych z zachowania okna, które są wspólne dla wszystkich okien dialogowych (zobacz [WPF systemu Windows — omówienie](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md) Aby uzyskać więcej informacji).  
  
> [!NOTE]
>  Należy dostarczyć właściciela do obsługi [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] automatyzacji dla okien dialogowych (zobacz [Przegląd automatyzacji interfejsu użytkownika](../../../../docs/framework/ui-automation/ui-automation-overview.md)).  
  
 Po skonfigurowaniu okno dialogowe, jest ona wyświetlana trybie modalnym, wywołując <xref:System.Windows.Window.ShowDialog%2A> metody.  
  
#### <a name="validating-user-provided-data"></a>Sprawdzanie poprawności danych dostarczane przez użytkownika  
 Gdy zostanie otwarte okno dialogowe, a użytkownik podaje wymagane dane, okno dialogowe jest odpowiedzialny za zapewnienie, że podane dane są prawidłowe, z następujących powodów:  
  
-   Z punktu widzenia zabezpieczeń wszystkie dane wejściowe powinny być weryfikowane.  
  
-   Z punktu widzenia specyficznego dla domeny sprawdzanie poprawności danych uniemożliwia błędnych danych przetwarzanych przez kod, który może potencjalnie zgłaszają wyjątki.  
  
-   Z punktu widzenia środowiska użytkownika okno dialogowe umożliwia użytkownikom, zmniejszając wprowadzony danych jest nieprawidłowa.  
  
-   Z punktu widzenia wydajności sprawdzania poprawności danych w wielowarstwowej aplikacji można zmniejszyć liczby rund między klientem i warstwy aplikacji, szczególnie w przypadku, gdy aplikacja składa się z usług sieci Web lub na serwerze baz danych.  
  
 Aby sprawdzić poprawność powiązanej kontrolki w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], należy zdefiniować reguły sprawdzania poprawności i skojarzyć go z powiązaniem. Reguły sprawdzania poprawności jest niestandardowej klasy, która jest pochodną <xref:System.Windows.Controls.ValidationRule>. W poniższym przykładzie przedstawiono regułę walidacji `MarginValidationRule`, która sprawdza, czy jest wiązana wartość <xref:System.Double> i znajduje się w określonym zakresie.  
  
 [!code-csharp[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs#marginvalidationrulecode)]
 [!code-vb[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb#marginvalidationrulecode)]  
  
 W tym kodzie logiki sprawdzania poprawności reguły sprawdzania poprawności jest implementowany przez zastępowanie <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodę, która sprawdza poprawność danych i zwraca odpowiednie <xref:System.Windows.Controls.ValidationResult>.  
  
 Aby skojarzyć reguły weryfikacji z powiązanej kontrolki, należy użyć następujących znaczników.  
  
 [!code-xaml[DialogBoxSample#MarginsValidationMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup2)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup3)]  
  
 Gdy reguła sprawdzania poprawności jest skojarzony, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] automatycznie spowoduje ich zastosowania, podczas wprowadzania danych do powiązania kontrolki. Jeśli formant zawiera nieprawidłowe dane [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wyświetli czerwonym obramowaniem nieprawidłowej kontrolki, jak pokazano na poniższej ilustracji.  
  
 ![Nieprawidłowy lewy margines](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure7.png "DialogBoxesOverviewFigure7")  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nie ogranicza użytkownika do nieprawidłowej kontrolki, aż do ich zostały wprowadzone prawidłowe dane. Jest to dobry zachowanie dla okna dialogowego; Użytkownik powinien móc za darmo Przejdź formantów w oknie dialogowym, czy dane są prawidłowe. Oznacza to jednak użytkownik może wprowadzić nieprawidłowe dane i naciśnij klawisz **OK** przycisku. Z tego powodu kodu również wymagane jest sprawdzenie wszystkich kontrolek w oknie dialogowym dialogowe **OK** przycisku Obsługa <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind3)]  
  
 Ten kod wylicza wszystkie obiekty zależności w oknie i, jeśli są nieprawidłowe (zwrócony przez <xref:System.Windows.Controls.Validation.GetHasError%2A>, nieprawidłowy formant uzyska fokus, `IsValid` metoda zwraca `false`, i okna jest uznawane za nieprawidłowe.  
  
 Gdy okno dialogowe jest prawidłowy, można bezpiecznie zamknięte i ponownie. Jako część procesu zwracany musi zwracać wynik wywołania funkcji.  
  
#### <a name="setting-the-modal-dialog-result"></a>Ustawianie wyniku modalnego okna dialogowego  
 Otwieranie okna dialogowe za pomocą <xref:System.Windows.Window.ShowDialog%2A> jest zasadniczo takie jak wywołania metody: kod, który otwartego przy użyciu — okno dialogowe <xref:System.Windows.Window.ShowDialog%2A> czekać na <xref:System.Windows.Window.ShowDialog%2A> zwraca. Gdy <xref:System.Windows.Window.ShowDialog%2A> zwraca, kod, który wymaga o nazwie zdecydować, czy kontynuować przetwarzania lub zatrzymać przetwarzanie, na podstawie od tego, czy użytkownik nacisnął klawisz **OK** przycisk lub **anulować** przycisku. W celu ułatwienia tej decyzji, okno dialogowe musi zwracać wybór użytkownika jako <xref:System.Boolean> wartość zwracana z <xref:System.Windows.Window.ShowDialog%2A> metody.  
  
 Gdy **OK** kliknięciu przycisku <xref:System.Windows.Window.ShowDialog%2A> powinien zwrócić `true`. Jest to osiągane przez ustawienie <xref:System.Windows.Window.DialogResult%2A> dialogowe Właściwości okna dialogowego **OK** kliknięciu przycisku.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind3)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind4)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind4)]  
  
 Należy pamiętać, że ustawienie <xref:System.Windows.Window.DialogResult%2A> właściwości powoduje również okno, aby zamknąć automatycznie, która eliminuje potrzebę jawnie wywołać <xref:System.Windows.Window.Close%2A>.  
  
 Gdy **anulować** kliknięciu przycisku <xref:System.Windows.Window.ShowDialog%2A> powinien zwrócić `false`, co wymaga także ustawienia <xref:System.Windows.Window.DialogResult%2A> właściwości.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind3)]  
  
 Jeśli przycisk <xref:System.Windows.Controls.Button.IsCancel%2A> właściwość jest ustawiona na `true` , a użytkownik naciśnie albo **anulować** klawisz ESC, lub przycisk <xref:System.Windows.Window.DialogResult%2A> jest automatycznie ustawiana `false`. Następujący kod znaczników ma ten sam efekt co poprzedni kod, bez konieczności obsługi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogDefaultCancelMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogdefaultcancelmarkup)]  
  
 Okno dialogowe automatycznie zwraca `false` po naciśnięciu klawisza **Zamknij** przycisku w pasku tytułu lub wybierze **Zamknij** element menu z **systemu** menu.  
  
#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Przetwarzanie danych zwróconych z modalne okno dialogowe  
 Gdy <xref:System.Windows.Window.DialogResult%2A> jest ustawiony przez okno dialogowe, funkcji, który je można uzyskać wyników okno dialogowe, sprawdzając <xref:System.Windows.Window.DialogResult%2A> właściwości podczas <xref:System.Windows.Window.ShowDialog%2A> zwraca.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind4)]  
  
 Jeśli w wyniku okna dialogowego `true`, funkcja użyty jako wskaźnik do pobrania i przetwarzania danych przez użytkownika.  
  
> [!NOTE]
>  Po <xref:System.Windows.Window.ShowDialog%2A> zwrócił nie można ponownie otworzyć okno dialogowe. Zamiast tego należy utworzyć nowe wystąpienie.  
  
 Jeśli w wyniku okna dialogowego `false`, funkcja powinna kończyć odpowiednio przetwarzania.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>Tworzenie niemodalnego niestandardowe okno dialogowe  
 Okno dialogowe niemodalne, takich jak pokazano na poniższej ilustracji, okno dialogowe Znajdź ma taki sam wygląd podstawowych jako modalnego okna dialogowego.  
  
 ![Znajdź okno dialogowe](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure6.PNG "DialogBoxesOverviewFigure6")  
  
 Jednak to zachowanie różni się nieznacznie, zgodnie z opisem w poniższych sekcjach.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Otwieranie niemodalne okno dialogowe  
 Niemodalne okno dialogowe jest otwarty przez wywołanie metody <xref:System.Windows.Window.Show%2A> metody.  
  
 [!code-xaml[DialogBoxSample#OpenFindDialogMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#openfinddialogmarkup1)]  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind3)]  
  
 W odróżnieniu od <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> natychmiast kończy pracę. W rezultacie wywoływania okna nie wiadomo, gdy Niemodalne okna dialogowe zostanie zamknięte, a w związku z tym nie może określić, kiedy należy sprawdzić, czy wynik okno dialogowe lub pobieranie danych z okna dialogowego dla dalszego przetwarzania. Okno dialogowe musi utworzyć alternatywny sposób, aby powrócić do wywoływania okna do przetwarzania danych.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Przetwarzanie dane zwrócone z niemodalnego okna dialogowego  
 W tym przykładzie `FindDialogBox` może zwracać jedną lub więcej znaleźć wyników do głównego okna, w zależności od tekst wyszukane bez żadnych szczególnych częstotliwości. Podobnie jak w przypadku modalne okno dialogowe, niemodalne okno dialogowe może zwrócić wyniki za pomocą właściwości. Jednak okna, który jest właścicielem okna dialogowego musi wiedzieć, kiedy należy sprawdzić te właściwości. Jest jednym ze sposobów włączyć tę opcję w oknie dialogowym zaimplementować zdarzenie jest zgłaszane, gdy zostanie znaleziony tekst. `FindDialogBox` implementuje `TextFoundEvent` w tym celu, który po raz pierwszy wymaga delegata.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs#textfoundeventhandlercode)]
 [!code-vb[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb#textfoundeventhandlercode)]  
  
 Przy użyciu `TextFoundEventHandler` delegować, `FindDialogBox` implementuje `TextFoundEvent`.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind2)]  
  
 W rezultacie `Find` może zgłosić zdarzenie, gdy zostanie znaleziony wynik wyszukiwania.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind2)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind3)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind3)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind4)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind4)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind5)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind5)]  
  
 Okno właściciela następnie musi zarejestrować się i obsługa tego zdarzenia.  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind2)]  
  
#### <a name="closing-a-modeless-dialog-box"></a>Zamykanie niemodalne okno dialogowe  
 Ponieważ <xref:System.Windows.Window.DialogResult%2A> musi być ustawiona, niemodalne okno dialogowe można zamknąć przy użyciu systemu zapewniają mechanizmy, takie jak:  
  
-   Kliknięcie przycisku **Zamknij** przycisku w pasku tytułu.  
  
-   Naciśnięcie klawisza ALT + F4.  
  
-   Wybieranie **Zamknij** z **systemu** menu.  
  
 Alternatywnie można wywołać kodu <xref:System.Windows.Window.Close%2A> podczas **Zamknij** kliknięciu przycisku.  
  
 [!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind1)]
 [!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind1)]  
[!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind2)]
[!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Okno podręczne — omówienie](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [Przykładowe okno dialogowe](http://go.microsoft.com/fwlink/?LinkID=159984)  
 [Próbka formantów niestandardowych ColorPicker](http://go.microsoft.com/fwlink/?LinkID=159977)
