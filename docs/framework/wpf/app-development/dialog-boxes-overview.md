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
ms.openlocfilehash: 649d60a2d50237827d5f334e934103b234a42724
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506337"
---
# <a name="dialog-boxes-overview"></a>Przegląd okien dialogowych
Aplikacje autonomiczne zwykle mają okno główne, czy oba powoduje wyświetlenie danych głównych, względem której aplikacja działa i uwidacznia funkcje przetwarzania tych danych za pośrednictwem [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] mechanizmów, takich jak pasek menu, paski narzędzi i pasków stanu. — Prosta aplikacja może również wyświetlić dodatkowe okna, wykonaj następujące czynności:  
  
-   Wyświetl szczegółowe informacje dla użytkowników.  
  
-   Zbierz informacje od użytkowników.  
  
-   Wyświetlanie i zbierania informacji.  
  
 Tego rodzaju systemu windows, są znane jako *okna dialogowe*, istnieją dwa typy: modalne i niemodalne.  
  
 A *modalne* zostanie wyświetlone okno dialogowe przez funkcję, gdy funkcja będzie potrzebowała dodatkowych danych od użytkownika, aby kontynuować. Ponieważ funkcja jest zależna od modalne okno dialogowe na potrzeby zbierania danych, okno modalne okno dialogowe zapobiega także użytkownika aktywowanie innych okien w aplikacji, gdy pozostaje on otwartych. W większości przypadków modalne okno dialogowe pozwala użytkownikowi na sygnał, gdy została zakończona z modalne okno dialogowe, naciskając klawisz albo **OK** lub **anulować** przycisku. Naciśnięcie klawisza **OK** przycisk wskazuje, że użytkownik wprowadził dane i chce, aby z funkcji, aby kontynuować przetwarzanie za pomocą tych danych. Naciśnięcie klawisza **anulować** przycisk oznacza, że użytkownik chce, aby zatrzymać funkcji wykonywania całkowicie. Najbardziej typowe przykłady modalne okna dialogowe są wyświetlane na otwieranie, zapisywanie i drukowanie danych.  
  
 A *niemodalne* okno dialogowe z drugiej strony, nie uniemożliwia użytkownikowi aktywowanie inne okna, gdy jest on otwarty. Na przykład jeśli użytkownik chce wyszukać wystąpienia określonego wyrazu w dokumencie, okno główne często otworzy okno dialogowe, aby poprosić użytkownika programu word, które szukają. Od znajdowanie słowo nie uniemożliwia użytkownikowi edytowania dokumentu, jednak okno dialogowe nie musi być modalne. Co najmniej zapewnia niemodalnego okna dialogowego **Zamknij** przycisk, aby zamknąć okno dialogowe i mogą dostarczać dodatkowych przycisków do wykonania określonych funkcji, takich jak **Znajdź następny** przycisk, aby znaleźć następnego word, który odpowiadającego kryteriom wyszukiwania, wyszukiwania programu word.  
  
 Windows Presentation Foundation (WPF) pozwala utworzyć kilka typów okien dialogowych, w tym okna komunikatów, wspólne okna dialogowe i niestandardowych okien dialogowych. W tym temacie omówiono poszczególnych usług i [przykładowe okno dialogowe](https://go.microsoft.com/fwlink/?LinkID=159984) zawiera przykłady dopasowania.  
  
 
  
<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>Okna komunikatów  
 A *okno komunikatu* to okno dialogowe, który może służyć do wyświetlania informacji tekstowych i Zezwalaj użytkownikom na podejmowanie decyzji za pomocą przycisków. Na poniższej ilustracji przedstawiono okno komunikatu, który wyświetla informacje tekstowe, zadaje pytanie i zapewnia użytkownikowi dostęp do trzech przycisków, aby znaleźć odpowiedź na pytanie.  
  
 ![Okno dialogowe Edytor tekstów](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure1.png "DialogBoxesOverviewFigure1")  
  
 Aby utworzyć okno komunikatu, należy użyć <xref:System.Windows.MessageBox> klasy. <xref:System.Windows.MessageBox> Umożliwia skonfigurowanie tekst okno komunikatu, tytuł, ikona i przyciski, za pomocą kodu, jak pokazano poniżej.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Aby wyświetlić okno komunikatu, należy wywołać `static` <xref:System.Windows.MessageBox.Show%2A> metody, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Gdy kod, który wyświetli okno wiadomości musi wykrywania i przetwarzania przez użytkownika decyzji (który przycisk został naciśnięty), ten kod można sprawdzić wynik okno komunikatu, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 Aby uzyskać więcej informacji na temat korzystania z okna komunikatów, zobacz <xref:System.Windows.MessageBox>, [przykładowe MessageBox](https://go.microsoft.com/fwlink/?LinkID=160023), i [przykładowe okno dialogowe](https://go.microsoft.com/fwlink/?LinkID=159984).  
  
 Mimo że <xref:System.Windows.MessageBox> mogą oferować interfejs użytkownika okno dialogowe prosty, zaletą korzystania z <xref:System.Windows.MessageBox> jest to jedyny typ okna, które mogą być wyświetlane przez aplikacje, które są uruchamiane w piaskownicy zabezpieczenia częściowej relacji zaufania (zobacz [zabezpieczeń](../../../../docs/framework/wpf/security-wpf.md)), takich jak [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
 Większość okien dialogowych wyświetlania i zbieranie danych bardziej skomplikowane niż suma okno komunikatu, łącznie z tekstem, wybór (pola wyboru) wzajemnie wykluczających się zaznaczenie (przycisków radiowych) i listy wyboru (pola listy, pola kombi, pola listy rozwijanej). W tym przypadku Windows Presentation Foundation (WPF) zawiera kilka typowych okien dialogowych i pozwala na tworzenie własnych okien dialogowych, mimo że używanie jednego jest ograniczony do aplikacji działających z pełnym zaufaniem.  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>Wspólne okna dialogowe  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] implementuje wiele okien dialogowych wielokrotnego użytku, które są wspólne dla wszystkich aplikacji, w tym okna dialogowe Otwieranie plików, zapisywanie plików i drukowania. Ponieważ te okna dialogowe są implementowane przez system operacyjny, mogą być współdzielone wśród wszystkich aplikacji działających w systemie operacyjnym, co pomaga użytkownikom środowisko spójności; w przypadku znanych przy użyciu okna dialogowego dostarczane przez system operacyjny, w jednej aplikacji użytkownicy nie muszą dowiedzieć się, jak za pomocą tego okna dialogowego w innych aplikacjach. Ponieważ te okna dialogowe są dostępne dla wszystkich aplikacji, a ponieważ pomagają zapewnić spójne środowisko użytkownika, są znane jako *wspólne okna dialogowe*.  
  
 Windows Presentation Foundation (WPF) hermetyzuje otwartego pliku, Zapisz plik i drukowanie wspólnych okien dialogowych i udostępnia je jako zarządzanych klas do użycia w aplikacji autonomicznej. Ten temat zawiera krótkie omówienie każdego z nich.  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>Okno dialogowe Otwieranie pliku  
 Okno dialogowe Otwieranie pliku pokazano na poniższym rysunku, służy funkcji otwierania pliku do pobierania nazwę pliku, aby otworzyć.  
  
 ![Okno dialogowe Otwieranie](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure2.png "DialogBoxesOverviewFigure2")  
  
 Wspólne okno dialogowe Otwieranie pliku jest implementowany jako <xref:Microsoft.Win32.OpenFileDialog> klasy i znajduje się w <xref:Microsoft.Win32> przestrzeni nazw. Poniższy kod przedstawia sposób tworzenia, konfigurowania i jeden oraz sposób przetwarzania wyniku.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Aby uzyskać więcej informacji w oknie dialogowym otwartego pliku, zobacz <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog> może służyć do bezpiecznego pobierania nazwy plików według działających z częściowej relacji zaufania (zobacz [zabezpieczeń](../../../../docs/framework/wpf/security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>Zapisz plik, okno dialogowe  
 Zapisz plik, okno dialogowe, pokazane na poniższej ilustracji jest używany przez funkcje zapisywania pliku pobrać nazwy pliku do zapisywania.  
  
 ![Okno dialogowe Zapisz jako](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure3.png "DialogBoxesOverviewFigure3")  
  
 Typowe, Zapisz plik, okno dialogowe jest implementowany jako <xref:Microsoft.Win32.SaveFileDialog> klasy i znajduje się w <xref:Microsoft.Win32> przestrzeni nazw. Poniższy kod przedstawia sposób tworzenia, konfigurowania i jeden oraz sposób przetwarzania wyniku.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Aby uzyskać więcej informacji na temat zapisywania pliku okno dialogowe, zobacz <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>Okno dialogowe drukowania  
 Okno dialogowe drukowania, pokazano na poniższym rysunku, służy funkcja drukowania można wybrać i skonfigurować drukarki, użytkownik chce drukowanie danych do.  
  
 ![Okno dialogowe drukowania](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure4.png "DialogBoxesOverviewFigure4")  
  
 Wspólne okno dialogowe drukowania jest implementowany jako <xref:System.Windows.Controls.PrintDialog> klasy i znajduje się w <xref:System.Windows.Controls> przestrzeni nazw. Poniższy kod przedstawia sposób tworzenia, konfigurowania i jeden.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Aby uzyskać więcej informacji na temat okna dialogowego drukowania, zobacz <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>. Aby uzyskać szczegółowe omówienie drukowania w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zobacz [Omówienie drukowania](../../../../docs/framework/wpf/advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>Niestandardowych okien dialogowych  
 Natomiast wspólne okna dialogowe są przydatne, jeśli jest to możliwe, należy użyć, nie obsługują one wymagania okna dialogowe specyficznego dla domeny. W takich przypadkach należy utworzyć własne okna dialogowe. Jak zobaczymy, okno dialogowe jest oknem za pomocą zachowań specjalnych. <xref:System.Windows.Window> implementuje te zachowania i w związku z tym, możesz użyć <xref:System.Windows.Window> do tworzenia niestandardowych modalne i Niemodalne okna dialogowe.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>Tworzenie modalnych niestandardowe okno dialogowe  
 W tym temacie pokazano, jak używać <xref:System.Windows.Window> do utworzenia z implementacją okno typowej modalnego okna dialogowego za pomocą `Margins` okno dialogowe, na przykład (zobacz [przykładowe okno dialogowe](https://go.microsoft.com/fwlink/?LinkID=159984)). `Margins` Na poniższej ilustracji przedstawiono okno dialogowe.  
  
 ![Okno dialogowe marginesy](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure5.png "DialogBoxesOverviewFigure5")  
  
#### <a name="configuring-a-modal-dialog-box"></a>Konfigurowanie modalne okno dialogowe  
 Interfejs użytkownika dla typowych okno dialogowe obejmuje następujące funkcje:  
  
-   Różne formanty, które są wymagane, aby zebrać pożądane dane.  
  
-   Wyświetlanie **OK** przycisku przez użytkowników, kliknij, aby zamknąć okno dialogowe, wróć do funkcji i kontynuować przetwarzanie.  
  
-   Wyświetlanie **anulować** przycisku, który użytkownicy kliknąć, aby zamknąć okno dialogowe i zatrzymać funkcji z dalszego przetwarzania.  
  
-   Wyświetlanie **Zamknij** przycisk na pasku tytułu.  
  
-   Wyświetlanie ikony.  
  
-   Wyświetlanie **Minimalizuj**, **Maksymalizuj**, i **przywrócić** przycisków.  
  
-   Wyświetlanie **systemu** menu Minimalizuj, Maksymalizuj, przywracania i zamknąć okno dialogowe.  
  
-   Otwieranie w górę i w środku okna, które są otwarte okno dialogowe.  
  
-   Okna dialogowe powinien być odpowiednio o zmiennym rozmiarze, gdzie to możliwe, tak aby uniemożliwić okna dialogowego za mały i udostępniać użytkownikom o rozmiarze przydatna, musisz ustawić zarówno domyślny, jak i co najmniej wymiarów.  
  
-   Naciśnięcie klawisza ESC powinna być skonfigurowana jako skrót klawiaturowy, który powoduje, że **anulować** naciśnięcia przycisku. Jest to osiągane przez ustawienie <xref:System.Windows.Controls.Button.IsCancel%2A> właściwość **anulować** przycisk, aby `true`.  
  
-   Naciśnięcie klawisza ENTER (lub RETURN) powinna być skonfigurowana jako skrót klawiaturowy, który powoduje, że **OK** naciśnięcia przycisku. Jest to osiągane przez ustawienie <xref:System.Windows.Controls.Button.IsDefault%2A> właściwość **OK** przycisk `true`.  
  
 Poniższy kod przedstawia tę konfigurację.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup2)]  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind2)]  
  
 Środowisko użytkownika dla okna dialogowego również rozszerza się na pasku menu, okna, które otwiera okno dialogowe. Po uruchomieniu funkcji, która wymaga interakcji z użytkownikiem za pomocą okna dialogowego, zanim będzie można kontynuować funkcji elementu menu element menu dla funkcji mają wielokropek w jej nagłówku, jak pokazano poniżej.  
  
 [!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup1)]  
[!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup2)]  
  
 Wielokropek element menu działa funkcja, która wyświetla okno dialogowe, które nie wymaga interakcji użytkownika, takich jak okno dialogowe informacje, nie jest wymagana.  
  
#### <a name="opening-a-modal-dialog-box"></a>Otwieranie modalne okno dialogowe  
 Okno dialogowe zwykle znajduje się w wyniku użytkownika, wybierając element menu do wykonywania funkcji specyficznych dla domeny, takie jak ustawianie marginesów dokumentu w edytorze tekstu. Wyświetlanie okna jako okno dialogowe przypomina przedstawiający okno normalne, mimo że wymaga konfiguracji specyficznej dla okno dialogowe dodatkowe. Cały proces tworzenia wystąpienia, konfigurowanie i otwiera okno dialogowe przedstawiono w poniższym kodzie.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind4)]  
  
 W tym miejscu kod przechodzi domyślne informacje (bieżący marginesy) do okna dialogowego. Jest również ustawienie <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> właściwości z odwołaniem do okna, które jest wyświetlane okno dialogowe. Ogólnie rzecz biorąc, zawsze należy ustawić właściciela dla okna dialogowego, aby zapewnić związanych z zachowania okna, które są wspólne dla wszystkich oknach dialogowych (zobacz [Przegląd Windows WPF](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md) Aby uzyskać więcej informacji).  
  
> [!NOTE]
>  Należy dostarczyć właściciela do obsługi [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] automatyzacji dla okien dialogowych (zobacz [Przegląd automatyzacji interfejsu użytkownika](../../../../docs/framework/ui-automation/ui-automation-overview.md)).  
  
 Po skonfigurowaniu okno dialogowe wyświetleniem trybie modalnym przez wywołanie metody <xref:System.Windows.Window.ShowDialog%2A> metody.  
  
#### <a name="validating-user-provided-data"></a>Sprawdzanie poprawności danych wprowadzonych przez użytkownika  
 Gdy zostanie otwarte okno dialogowe, a użytkownik udostępnia wymaganych danych, okno dialogowe jest odpowiedzialny za zapewnienie, że podane dane są prawidłowe, z następujących powodów:  
  
-   Z punktu widzenia zabezpieczeń wszystkie dane wejściowe powinny być weryfikowane.  
  
-   Z punktu widzenia specyficzne dla domeny sprawdzanie poprawności danych zapobiega błędne dane przetwarzane przez kod, który potencjalnie może zgłaszać wyjątki.  
  
-   Z punktu widzenia środowisko użytkownika okno dialogowe może pomóc użytkownikom, pokazując, dane, które wprowadzono jest nieprawidłowy.  
  
-   Z punktu widzenia wydajności sprawdzania poprawności danych w aplikacji wielowarstwowej pozwala zmniejszyć liczbę wystąpień komunikacji dwustronnej między klientem i warstwy aplikacji, szczególnie w przypadku, gdy aplikacja składa się z usługami sieci Web lub na serwerze baz danych.  
  
 Aby sprawdzić poprawność powiązanej kontrolki w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], należy zdefiniować reguły sprawdzania poprawności i skojarzyć go z powiązania. Reguła poprawności jest klasę niestandardową, która pochodzi od klasy <xref:System.Windows.Controls.ValidationRule>. W poniższym przykładzie pokazano reguły sprawdzania poprawności `MarginValidationRule`, która sprawdza, czy jest wiązana wartość <xref:System.Double> i znajduje się w określonym zakresie.  
  
 [!code-csharp[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs#marginvalidationrulecode)]
 [!code-vb[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb#marginvalidationrulecode)]  
  
 W tym kodzie logikę walidacji reguły sprawdzania poprawności jest implementowany przez zastąpienie <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody, która sprawdza poprawność danych i zwraca odpowiednią <xref:System.Windows.Controls.ValidationResult>.  
  
 Aby skojarzyć regułę sprawdzania poprawności z powiązanej kontrolki, należy użyć następujących znaczników.  
  
 [!code-xaml[DialogBoxSample#MarginsValidationMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup2)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup3)]  
  
 Po skojarzeniu, reguła sprawdzania poprawności [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] spowoduje automatyczne zastosowanie go po wprowadzeniu danych do powiązanej kontrolki. Gdy kontrolka zawiera nieprawidłowe dane [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zostaną wyświetlone czerwone obramowanie wokół nieprawidłowej kontrolki, jak pokazano na poniższej ilustracji.  
  
 ![Nieprawidłowy lewy margines](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure7.png "DialogBoxesOverviewFigure7")  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nie ogranicza użytkownika do nieprawidłowej kontrolki, dopóki ich zostały wprowadzone prawidłowe dane. Jest to dobry zachowanie dla okna dialogowego; Użytkownik powinien móc swobodnie Przejdź formantów w oknie dialogowym, czy dane są prawidłowe. Oznacza to jednak użytkownik może wprowadzić nieprawidłowe dane, a następnie naciśnij klawisz **OK** przycisku. Z tego powodu kod musi także sprawdzić poprawność wszystkich kontrolek w oknie dialogowym przypadku **OK** naciśnięciu przycisku obsługi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind3)]  
  
 Ten kod wylicza wszystkie obiekty zależności, w oknie i, jeśli są nieprawidłowe (zwrócone przez <xref:System.Windows.Controls.Validation.GetHasError%2A>, nieprawidłowy formant uzyskuje fokus, `IsValid` metoda zwraca `false`, i okno jest uznawane za nieprawidłowe.  
  
 Gdy okno dialogowe jest prawidłowy, można bezpiecznie zamknąć i wrócić. W ramach procesu zwrotu musi ona zwrócony wynik do funkcji wywołującej.  
  
#### <a name="setting-the-modal-dialog-result"></a>Ustawianie wyniku modalne okno dialogowe  
 Otwierając okno dialogowe przy użyciu <xref:System.Windows.Window.ShowDialog%2A> to zasadniczo, takie jak wywołanie metody: kod, który otwierane przy użyciu okno dialogowe <xref:System.Windows.Window.ShowDialog%2A> czeka, aż do <xref:System.Windows.Window.ShowDialog%2A> zwraca. Gdy <xref:System.Windows.Window.ShowDialog%2A> zwraca, kod, który wymaga o nazwie zdecydować, czy kontynuować przetwarzanie lub zatrzymać przetwarzanie, na podstawie od tego, czy użytkownik nacisnął klawisz **OK** przycisk lub **anulować** przycisku. W celu ułatwienia tej decyzji, okno dialogowe musi zwracać wybrany przez użytkownika jako <xref:System.Boolean> wartość, która jest zwracana z <xref:System.Windows.Window.ShowDialog%2A> metody.  
  
 Gdy **OK** kliknięto przycisk <xref:System.Windows.Window.ShowDialog%2A> powinna zwrócić `true`. Jest to osiągane przez ustawienie <xref:System.Windows.Window.DialogResult%2A> właściwości okna dialogowego pole, kiedy **OK** przycisku.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind3)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind4)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind4)]  
  
 Należy pamiętać, że ustawienie <xref:System.Windows.Window.DialogResult%2A> właściwości również powoduje, że okna zamknięte automatycznie, która eliminuje potrzebę jawnego wywoływania <xref:System.Windows.Window.Close%2A>.  
  
 Gdy **anulować** kliknięto przycisk <xref:System.Windows.Window.ShowDialog%2A> powinna zwrócić `false`, co wymaga także ustawienia <xref:System.Windows.Window.DialogResult%2A> właściwości.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind3)]  
  
 Gdy przycisk <xref:System.Windows.Controls.Button.IsCancel%2A> właściwość jest ustawiona na `true` i użytkownik naciśnie opcję **anulować** przycisku lub klawisz ESC <xref:System.Windows.Window.DialogResult%2A> jest automatycznie ustawiana na `false`. Następujące znaczniki ma taki sam skutek jak kod powyżej, bez konieczności obsługi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogDefaultCancelMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogdefaultcancelmarkup)]  
  
 Okno dialogowe jest automatycznie zwraca `false` po naciśnięciu klawisza **Zamknij** przycisk na pasku tytułu lub wybierze **Zamknij** element menu z **systemu** menu.  
  
#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Przetwarzanie danych zwróconych z modalne okno dialogowe  
 Gdy <xref:System.Windows.Window.DialogResult%2A> jest ustawiony przez okno dialogowe funkcji, który je otworzył można uzyskać wyniku okna dialogowego, sprawdzając <xref:System.Windows.Window.DialogResult%2A> właściwości podczas <xref:System.Windows.Window.ShowDialog%2A> zwraca.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind4)]  
  
 Jeśli w wyniku okna dialogowego `true`, funkcja używa, jako wskaźnik do pobierania i przetwarzania danych przez użytkownika.  
  
> [!NOTE]
>  Po <xref:System.Windows.Window.ShowDialog%2A> zostanie zwrócone, nie można ponownie otworzyć okno dialogowe. Zamiast tego należy utworzyć nowe wystąpienie.  
  
 Jeśli w wyniku okna dialogowego `false`, funkcja powinien kończyć się odpowiednio przetwarzania.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>Tworzenie niemodalnego okna dialogowego niestandardowe  
 Niemodalne okno dialogowe, takie jak pokazano na poniższym rysunku, okno dialogowe Znajdź ma taki sam wygląd podstawowe jako modalne okno dialogowe.  
  
 ![Okno dialogowe Znajdź](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure6.PNG "DialogBoxesOverviewFigure6")  
  
 Jednak to zachowanie jest nieco inna, zgodnie z opisem w poniższych sekcjach.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Otwieranie niemodalnego okna dialogowego  
 Niemodalne okno dialogowe jest otwarty przez wywołanie metody <xref:System.Windows.Window.Show%2A> metody.  
  
 [!code-xaml[DialogBoxSample#OpenFindDialogMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#openfinddialogmarkup1)]  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind3)]  
  
 W odróżnieniu od <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> zwraca natychmiast. W związku z tym wywoływania okna nie wiadomo, kiedy niemodalnego okna dialogowego jest zamknięty i, w związku z tym, nie może określić, kiedy należy sprawdzić wyniku okna dialogowego lub pobieranie danych z okna dialogowego do dalszego przetwarzania. Okno dialogowe musi utworzyć alternatywny sposób, aby zwrócić dane do wywoływania okna do przetworzenia.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Przetwarzanie dane zwrócone z niemodalnego okna dialogowego  
 W tym przykładzie `FindDialogBox` może zwracać jedną lub więcej Znajdź wyniki do głównego okna, w zależności od tekstu wyszukane bez żadnych szczególnych częstotliwość. Podobnie jak w przypadku modalne okno dialogowe, niemodalne okno dialogowe może zwrócić wyniki za pomocą właściwości. Jednak okno, które jest właścicielem okna dialogowego musi wiedzieć, kiedy mają być sprawdzane tych właściwości. Jest jednym ze sposobów, aby włączyć tę opcję dla okna dialogowego zaimplementować zdarzenie, które jest wywoływane zawsze wtedy, gdy zostanie znaleziony tekst. `FindDialogBox` implementuje `TextFoundEvent` w tym celu, który po raz pierwszy wymaga delegata.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs#textfoundeventhandlercode)]
 [!code-vb[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb#textfoundeventhandlercode)]  
  
 Za pomocą `TextFoundEventHandler` delegować, `FindDialogBox` implementuje `TextFoundEvent`.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind2)]  
  
 W związku z tym `Find` może zgłosić zdarzenie, gdy zostanie znaleziony w wynikach wyszukiwania.  
  
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
  
 Okno właściciela musi zarejestrować się i obsługiwać to zdarzenie.  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind2)]  
  
#### <a name="closing-a-modeless-dialog-box"></a>Zamykanie niemodalnego okna dialogowego  
 Ponieważ <xref:System.Windows.Window.DialogResult%2A> musi być ustawiony, może zostać zamknięty niemodalnego okna dialogowego za pomocą systemu zapewniają mechanizmy, w tym następujące:  
  
-   Klikając **Zamknij** przycisk na pasku tytułu.  
  
-   Naciskając klawisze ALT + F4.  
  
-   Wybieranie **Zamknij** z **systemu** menu.  
  
 Alternatywnie, można wywołać kod <xref:System.Windows.Window.Close%2A> podczas **Zamknij** przycisku.  
  
 [!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind1)]
 [!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind1)]  
[!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind2)]
[!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Okno podręczne — omówienie](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [Przykładowe okno dialogowe](https://go.microsoft.com/fwlink/?LinkID=159984)  
 [Próbka formantów niestandardowych ColorPicker](https://go.microsoft.com/fwlink/?LinkID=159977)
