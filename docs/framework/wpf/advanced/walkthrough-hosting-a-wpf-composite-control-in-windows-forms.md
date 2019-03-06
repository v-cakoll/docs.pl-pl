---
title: 'Przewodnik: Hosting złożonego formantu WPF w formularzach Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: 257462cea4d4926ce5ad22a9d97a3a56e1d6c2a1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368275"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>Przewodnik: Hosting złożonego formantu WPF w formularzach Windows Forms
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferuje rozbudowane środowisko do tworzenia aplikacji. Jednak jeśli masz znaczne inwestycje [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodu, może być bardziej efektywne rozszerzyć istniejącą [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacji za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , a nie do jego przepisania od podstaw. Jest to typowy scenariusz, gdy chcesz osadzić jedną lub większą liczbę opcji implementowane za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w aplikacji Windows Forms. Aby uzyskać więcej informacji na temat dostosowywania kontrolek WPF, zobacz [niestandardowe Dostosowywanie formantu](../controls/control-customization.md).  
  
 Ten przewodnik przeprowadzi Cię przez aplikację obsługujący [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożonego formantu, aby wykonać wprowadzanie danych w aplikacji Windows Forms. Złożonej kontrolki jest dostarczana w bibliotece DLL. Ta procedura ogólne można rozszerzyć do bardziej złożonych aplikacji i formantów. Ten przewodnik jest przeznaczony do niemal identyczne w wyglądu i działania [instruktażu: Hosting Windows złożonego formantu formularzy na platformie WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md). Podstawowa różnica polega na tym, że scenariusza hostingu została odwrócona.  
  
 Ekran instruktażu jest podzielony na dwie sekcje. Pierwsza sekcja krótko opisano implementację [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożonego formantu. Druga sekcja w tym artykule omówiono szczegółowo sposób hostowania złożonej kontrolki w aplikacji Windows Forms, odbieranie zdarzeń z kontrolki i uzyskiwać dostęp do niektórych właściwości formantu.  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Implementowanie złożonego formantu WPF.  
  
-   Wdrażanie aplikacji hosta Windows Forms.  
  
 Lista zadań przedstawione w niniejszym przewodniku kompletny kod znajduje się [Hosting złożonego formantu WPF w Windows Forms przykładzie](https://go.microsoft.com/fwlink/?LinkID=159996).  
  
## <a name="prerequisites"></a>Wymagania wstępne  

Potrzebujesz programu Visual Studio w celu przeprowadzenia tego instruktażu.  
  
## <a name="implementing-the-wpf-composite-control"></a>Implementowanie złożonej kontrolki WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Złożonej kontrolki używane w tym przykładzie jest formularz proste wprowadzanie danych, który przyjmuje nazwę użytkownika i adres. Gdy użytkownik kliknie jeden z dwóch przycisków, aby wskazać, że zadanie jest zakończone, formant zgłasza zdarzenie niestandardowe do zwracania tych informacji do hosta. Poniższa ilustracja przedstawia renderowanych kontroli.  
  
 ![Proste kontrolki WPF](./media/avaloncontrol.png "AvalonControl")  
Złożonej kontrolki WPF  
  
### <a name="creating-the-project"></a>Tworzenie projektu  
 Aby uruchomić projekt:  
  
1.  Uruchom [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], a następnie otwórz **nowy projekt** okno dialogowe.  
  
2.  W Visual C# i kategorii Windows, wybierz **Biblioteka kontrolek użytkownika WPF** szablonu.  
  
3.  Nazwa nowego projektu `MyControls`.  
  
4.  Dla lokalizacji, określ wygodnie nazwane folder najwyższego poziomu, takie jak `WindowsFormsHostingWpfControl`. Później należy umieścić aplikacji hosta w tym folderze.  
  
5.  Kliknij przycisk **OK** do tworzenia projektu. Domyślny projekt zawiera jeden formant o nazwie `UserControl1`.  
  
6.  W Eksploratorze rozwiązań, zmienianie nazwy `UserControl1` do `MyControl1`.  
  
 Projekt powinien mieć odwołania do następujących systemowych bibliotek DLL. Jeśli dowolny z tych bibliotek DLL nie są włączone domyślnie, należy je dodać do projektu.  
  
-   PresentationCore  
  
-   PresentationFramework  
  
-   System  
  
-   WindowsBase  
  
### <a name="creating-the-user-interface"></a>Tworzenie interfejsu użytkownika  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Dla złożonego formantu jest implementowane za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Złożonej kontrolki [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] składa się z pięciu <xref:System.Windows.Controls.TextBox> elementów. Każdy <xref:System.Windows.Controls.TextBox> element ma skojarzony <xref:System.Windows.Controls.TextBlock> element, który służy jako etykieta. Istnieją dwa <xref:System.Windows.Controls.Button> elementy u dołu **OK** i **anulować**. Po kliknięciu przycisku albo kontrolki wywołuje zdarzenie niestandardowe do zwracania informacji do hosta.  
  
#### <a name="basic-layout"></a>Układ podstawowy  
 Różne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów są zawarte w <xref:System.Windows.Controls.Grid> elementu. Możesz użyć <xref:System.Windows.Controls.Grid> rozmieścić zawartość złożonego kontrolować w taki sam sposób należy użyć `Table` elementu w formacie HTML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma również <xref:System.Windows.Documents.Table> elementu, ale <xref:System.Windows.Controls.Grid> jest uproszczone i lepszym rozwiązaniem w przypadku układu prostego zadania.  
  
 Następujące XAML zawiera podstawowy układ. Ta XAML definiuje ogólną strukturę kontrolki, określając liczbę kolumn i wierszy w <xref:System.Windows.Controls.Grid> elementu.  
  
 W MyControl1.xaml Zastąp istniejące XAML następujące XAML.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Dodawanie TextBlock i pole tekstowe elementów do siatki  
 Możesz umieścić [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementu w siatce, ustawiając element <xref:System.Windows.Controls.Grid.RowProperty> i <xref:System.Windows.Controls.Grid.ColumnProperty> atrybuty do odpowiedniej liczby wierszy i kolumn. Należy pamiętać, że wierszy i kolumn numerowanie liczony od zera. Może mieć elementu obejmuje wielu kolumn, ustawiając jego <xref:System.Windows.Controls.Grid.ColumnSpanProperty> atrybutu. Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.Grid> elementów, zobacz [Utwórz Element siatki](../controls/how-to-create-a-grid-element.md).  
  
 Następujące XAML zawiera kontrolek złożonych <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.TextBlock> elementów przy użyciu ich <xref:System.Windows.Controls.Grid.RowProperty> i <xref:System.Windows.Controls.Grid.ColumnProperty> atrybuty, które są ustawione poprawnie umieszcza elementy w siatce.  
  
 W MyControl1.xaml, Dodaj następujące XAML w ramach <xref:System.Windows.Controls.Grid> elementu.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Ustawianie stylów elementów interfejsu użytkownika  
 Wiele elementów w formularzu wprowadzania danych mają podobne wygląd, co oznacza, że identycznymi ustawieniami dla kilku ich właściwości. Zamiast ustawiać osobno każdy element atrybuty, korzysta z poprzednim XAML <xref:System.Windows.Style> elementów do definiowania ustawień właściwości standardowych klas elementów. Takie podejście zmniejsza złożoność kontrolki i umożliwia zmianę wyglądu wiele elementów za pomocą atrybutu pojedynczy styl.  
  
 <xref:System.Windows.Style> Elementów są zawarte w <xref:System.Windows.Controls.Grid> elementu <xref:System.Windows.FrameworkElement.Resources%2A> właściwości, dzięki czemu może służyć przez wszystkie elementy w kontrolce. Jeśli w nazwie stylu zastosowania do elementu, dodając <xref:System.Windows.Style> element ustawiony na nazwę stylu. Style, które nie są nazywane stają się domyślnego stylu dla elementu. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] style, zobacz [Tworzenie szablonów i stylów](../controls/styling-and-templating.md).  
  
 Pokazano w poniższym XAML <xref:System.Windows.Style> elementy dla złożonego formantu. Aby dowiedzieć się, jak style są stosowane do elementów, zobacz poprzednie XAML. Na przykład ostatniego <xref:System.Windows.Controls.TextBlock> element ma `inlineText` styl, a ostatnia <xref:System.Windows.Controls.TextBox> element używa domyślnego stylu.  
  
 W MyControl1.xaml, Dodaj następujące XAML tuż za <xref:System.Windows.Controls.Grid> elementu początkowego.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Dodawanie OK i przyciski Anuluj  
 Końcowe elementy w złożonej kontrolki są **OK** i **anulować** <xref:System.Windows.Controls.Button> elementy, które zajmuje pierwsze dwie kolumny ostatni wiersz <xref:System.Windows.Controls.Grid>. Te elementy, użyj wspólnej procedury obsługi zdarzeń `ButtonClicked`i domyślnie <xref:System.Windows.Controls.Button> style zdefiniowane w poprzednim XAML.  
  
 W MyControl1.xaml, Dodaj następujące XAML po ostatnim <xref:System.Windows.Controls.TextBox> elementu. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Część złożonej kontrolki jest teraz ukończona.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Wdrażanie pliku związanego z kodem  
 Plik związany z kodem, MyControl1.xaml.cs, implementuje trzy podstawowe zadania:
  
1.  Obsługuje zdarzenie, który występuje, gdy użytkownik kliknie jeden z przycisków.  
  
2.  Pobiera dane z <xref:System.Windows.Controls.TextBox> elementów, a następnie umieszcza go w obiekcie argumentu zdarzenia niestandardowego.  
  
3.  Wywołuje niestandardowy `OnButtonClick` zdarzeń, która powiadamia hosta, że użytkownik jest gotowy i przekazuje dane z powrotem do hosta.  
  
 Kontrolka udostępnia również wiele właściwości kolorów i czcionek, które umożliwiają użytkownikowi zmienianie wyglądu. W odróżnieniu od <xref:System.Windows.Forms.Integration.WindowsFormsHost> klasy, która jest używana do obsługi formantu Windows Forms, <xref:System.Windows.Forms.Integration.ElementHost> klasa udostępnia kontrolki <xref:System.Windows.Controls.Panel.Background%2A> tylko właściwości. Aby zachować podobieństwa między ten przykładowy kod i przykład omówione w [instruktażu: Hostowanie kontrolki złożonej Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md), formant udostępnia pozostałe właściwości bezpośrednio.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Podstawowa struktura pliku związanego z kodem  
 Plik związany z kodem, który składa się z jednej przestrzeni nazw `MyControls`, które będzie zawierać dwie klasy `MyControl1` i `MyControlEventArgs`.  
  
```  
namespace MyControls  
{  
  public partial class MyControl1 : Grid  
  {  
    //...  
  }  
  public class MyControlEventArgs : EventArgs  
  {  
    //...  
  }  
}  
```  
  
 Pierwsza klasa `MyControl1`, to klasę częściową zawierający kod, który implementuje funkcje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zdefiniowane w MyControl1.xaml. Gdy MyControl1.xaml zostanie przetworzona, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest konwertowana na tej samej klasy częściowe i dwie klasy częściowe są scalane, skompilowany kontrolka formularz. Z tego powodu nazwę klasy w pliku związanym z kodem musi odpowiadać nazwie klasy przypisane do MyControl1.xaml i musi on dziedziczyć z elementem głównym formantu. Druga klasa, `MyControlEventArgs`, to klasa argumentów zdarzenia, który służy do wysyłania danych z powrotem do hosta.  
  
 Open MyControl1.xaml.cs. Zmień istniejącej deklaracji klasy, który ma następujące nazwy i dziedziczy <xref:System.Windows.Controls.Grid>.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Inicjowanie kontrolki  
 Poniższy kod implementuje kilka podstawowych zadań:  
  
-   Deklaruje zdarzenie prywatne, `OnButtonClick`i jego skojarzone delegata `MyControlEventHandler`.  
  
-   Tworzy kilka prywatnej zmienne globalne, które przechowują dane użytkownika. Te dane są prezentowane za pomocą odpowiednich właściwości.  
  
-   Implementuje obsługi `Init`, dla formantu <xref:System.Windows.FrameworkElement.Loaded> zdarzeń. Ten program obsługi inicjuje zmienne globalne przez przypisywanie ich do wartości określonych w MyControl1.xaml. Aby to zrobić, używa <xref:System.Windows.FrameworkElement.Name%2A> przypisane do typowej <xref:System.Windows.Controls.TextBlock> elementu `nameLabel`, aby uzyskać dostęp ustawienia właściwości tego elementu.  
  
 Usuń istniejące Konstruktor i Dodaj następujący kod, aby Twoje `MyControl1` klasy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Przyciski obsługi zdarzenia kliknięcia  
 Użytkownik wskazuje, że zakończenia zadania wprowadzanie danych przez kliknięcie dowolnej **OK** przycisk lub **anulować** przycisku. Przyciski używać tego samego <xref:System.Windows.Controls.Primitives.ButtonBase.Click> programu obsługi zdarzeń `ButtonClicked`. Przyciski mają nazwy `btnOK` lub `btnCancel`, umożliwiającej program obsługi określić, której przycisk został kliknięty, sprawdzając wartość `sender` argumentu. Program obsługi wykonuje następujące czynności:  
  
-   Tworzy `MyControlEventArgs` obiekt, który zawiera dane z <xref:System.Windows.Controls.TextBox> elementów.  
  
-   Jeśli użytkownik kliknął element **anulować** przycisk zestawy `MyControlEventArgs` obiektu `IsOK` właściwość `false`.  
  
-   Wywołuje `OnButtonClick` zdarzenie, które wskazuje na hoście, że zostanie zakończone i przekazuje kopii zebranych danych.  
  
 Dodaj następujący kod, aby Twoje `MyControl1` klasy po `Init` metody.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Tworzenie właściwości  
 W pozostałej części klasy po prostu udostępnia właściwości, które odnoszą się do zmiennych globalnych omówionych wcześniej. Podczas zmiany właściwości, metody dostępu set modyfikuje wygląd kontrolki poprzez zmianę odpowiednich właściwości elementu i aktualizowanie bazowego zmienne globalne.  
  
 Dodaj następujący kod, aby Twoje `MyControl1` klasy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Wysyłania danych z powrotem do hosta  
 Jest ostateczny składnika w pliku `MyControlEventArgs` klasy, która służy do wysyłania zebrane dane z powrotem do hosta.  
  
 Dodaj następujący kod, aby Twoje `MyControls` przestrzeni nazw. Wdrożenie jest proste i nie zostało omówione w dalszej.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Skompiluj rozwiązanie. Kompilacja generuje biblioteki DLL o nazwie MyControls.dll.  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Wdrażanie aplikacji hosta Windows Forms  
 Formularze Windows hostowanie aplikacji używa <xref:System.Windows.Forms.Integration.ElementHost> obiektu hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożonego formantu. Uchwyty aplikacji `OnButtonClick` zdarzenia w celu odbierania danych z złożonego formantu. Aplikacja ma również zestaw przycisków opcji, które można użyć w celu zmodyfikowania wyglądu formantu. Na poniższej ilustracji przedstawiono aplikację.  
  
 ![Formularz Windows Hosting kontrolki Avalon](./media/wfhost.png "WFHost")  
Hostowany w aplikacji Windows Forms złożonej kontrolki WPF  
  
### <a name="creating-the-project"></a>Tworzenie projektu  
 Aby uruchomić projekt:  
  
1.  Uruchom [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], a następnie otwórz **nowy projekt** okno dialogowe.  
  
2.  W Visual C# i kategorii Windows, wybierz **aplikacja interfejsu Windows Forms** szablonu.  
  
3.  Nazwa nowego projektu `WFHost`.  
  
4.  Dla lokalizacji należy określić ten sam folder najwyższego poziomu, który zawiera projekt MyControls.  
  
5.  Kliknij przycisk **OK** do tworzenia projektu.  
  
 Należy również dodać odwołania do biblioteki DLL, która zawiera `MyControl1` i innych zestawów.  
  
1.  Kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań, a następnie wybierz pozycję **Dodaj odwołanie**.  
  
2.  Kliknij przycisk **Przeglądaj** , a następnie przejdź do folderu, który zawiera MyControls.dll. W tym przewodniku ten folder jest MyControls\bin\Debug.  
  
3.  Wybierz MyControls.dll, a następnie kliknij przycisk **OK**.  
  
4.  Dodaj odwołania do następujących zestawów.  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   System.Xaml  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>Implementowanie interfejsu użytkownika dla aplikacji  
 W interfejsie użytkownika dla aplikacji Windows formularza zawiera kilka formantów do interakcji z złożonego formantu WPF.  
  
1.  Otwórz formularz Form1 w Projektancie formularza Windows.  
  
2.  Powiększ formularza, aby pomieścić kontrolki.  
  
3.  W prawym górnym rogu formularza Dodaj <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> formantu do przechowywania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożonego formantu.  
  
4.  Dodaj następujący kod <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> formantów do formularza.  
  
    |Nazwa|Tekst|  
    |----------|----------|  
    |groupBox1|Kolor tła|  
    |groupBox2|Kolor pierwszego planu|  
    |groupBox3|Rozmiar czcionki|  
    |groupBox4|Rodzina czcionek|  
    |groupBox5|Styl czcionki|  
    |groupBox6|Grubość czcionki|  
    |groupBox7|Dane z formantu|  
  
5.  Dodaj następujący kod <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> mające na celu <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> kontrolki.  
  
    |GroupBox|Nazwa|Tekst|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|Oryginał|  
    |groupBox1|radioBackgroundLightGreen|LightGreen|  
    |groupBox1|radioBackgroundLightSalmon|LightSalmon|  
    |groupBox2|radioForegroundOriginal|Oryginał|  
    |groupBox2|radioForegroundRed|Czerwony|  
    |groupBox2|radioForegroundYellow|Żółty|  
    |groupBox3|radioSizeOriginal|Oryginał|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|Oryginał|  
    |groupBox4|radioFamilyTimes|Georgia|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|Normalne|  
    |groupBox5|radioStyleItalic|Kursywa|  
    |groupBox6|radioWeightOriginal|Oryginał|  
    |groupBox6|radioWeightBold|Bold|  
  
6.  Dodaj następujący kod <xref:System.Windows.Forms.Label?displayProperty=nameWithType> kontrolki do ostatniego <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>. Te kontrolki wyświetlanie danych zwróconych przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożonego formantu.  
  
    |GroupBox|Nazwa|Tekst|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Nazwa:|  
    |groupBox7|lblAddress|Adres:|  
    |groupBox7|lblCity|Miasto:|  
    |groupBox7|lblState|Stan:|  
    |groupBox7|lblZip|Kod pocztowy:|  
  
### <a name="initializing-the-form"></a>Inicjowanie formularza  
 Ogólnie zaimplementować kod hostingu w postaci <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń. Poniższy kod przedstawia <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń, procedura obsługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożonej kontrolki <xref:System.Windows.FrameworkElement.Loaded> zdarzeń i deklaracje dla kilku zmiennych globalnych, które są używane w dalszej części.  
  
 W Windows Forms Designer, kliknij dwukrotnie formularz, aby utworzyć <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń. W górnej części Form1.cs, Dodaj następujący kod `using` instrukcji.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Zastąp zawartość istniejącego `Form1` klasy z następującym kodem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 `Form1_Load` w poprzednim kodzie przedstawiono ogólna procedura obsługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sterowania:  
  
1.  Utwórz nową <xref:System.Windows.Forms.Integration.ElementHost> obiektu.  
  
2.  Ustaw dla formantu <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>.  
  
3.  Dodaj <xref:System.Windows.Forms.Integration.ElementHost> kontrolę <xref:System.Windows.Forms.Panel> kontrolki <xref:System.Windows.Forms.Control.Controls%2A> kolekcji.  
  
4.  Utwórz wystąpienie obiektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroli.  
  
5.  Hostowanie złożonego formantu w formularzu, przypisując kontrolki <xref:System.Windows.Forms.Integration.ElementHost> kontrolki <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> właściwości.  
  
 Pozostałe dwa wiersze w `Form1_Load` metoda dołączyć obsługi do dwóch zdarzeń formantów:  
  
-   `OnButtonClick` To zdarzenie niestandardowe, które jest wywoływane przez złożonej kontrolki, gdy użytkownik kliknie **OK** lub **anulować** przycisku. Obsługi zdarzeń uzyskania odpowiedzi użytkownika i zbierać dowolne dane, określonej przez użytkownika.  
  
-   <xref:System.Windows.FrameworkElement.Loaded> To zdarzenie standardowe, który jest wywoływany przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolować znajduje się w pełni załadowane. Zdarzenie jest używane w tym miejscu ponieważ przykład musi zainicjować wiele zmiennych globalnych przy użyciu właściwości z formantu. W czasie w postaci <xref:System.Windows.Forms.Form.Load> zdarzenie, formant nie jest w pełni załadowany i te wartości są nadal równa `null`. Musisz czekać do momentu formantu <xref:System.Windows.FrameworkElement.Loaded> wystąpi zdarzenie, aby korzystać z tych właściwości.  
  
 <xref:System.Windows.FrameworkElement.Loaded> Program obsługi zdarzeń jest wyświetlany w poprzednim kodzie. `OnButtonClick` Obsługi została omówiona w następnej sekcji.  
  
### <a name="handling-onbuttonclick"></a>Obsługa OnButtonClick  
 `OnButtonClick` Zdarzenie występuje, gdy użytkownik kliknie **OK** lub **anulować** przycisku.  
  
 Program obsługi zdarzeń sprawdza argumentu zdarzenia `IsOK` pole, aby określić, której przycisk został kliknięty. `lbl` *Danych* zmienne odpowiadają <xref:System.Windows.Forms.Label> formantów, które zostały opisane wcześniej. Jeśli użytkownik kliknie **OK** przycisk danych w formancie <xref:System.Windows.Controls.TextBox> kontrolki jest przypisany do odpowiednich <xref:System.Windows.Forms.Label> kontroli. Jeśli użytkownik kliknie **anulować**, <xref:System.Windows.Forms.Label.Text%2A> wartości są ustawiane na domyślne parametry.  
  
 Dodaj poniższy przycisk kliknij kod obsługi zdarzeń do `Form1` klasy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Skompiluj i uruchom aplikację. Dodaj tekst w złożonej kontrolki WPF, a następnie kliknij przycisk **OK**. Tekst jest wyświetlany w etykietach. W tym momencie kod nie dodano do obsługi przycisków radiowych.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Modyfikowanie wyglądu formantu  
 <xref:System.Windows.Forms.RadioButton> Kontrolek w formularzu umożliwi użytkownikowi na zmianę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożonej kontrolki pierwszego planu i tła kolorów również jako kilka właściwości czcionki. Kolor tła jest uwidaczniany przez <xref:System.Windows.Forms.Integration.ElementHost> obiektu. Pozostałe właściwości są widoczne jako właściwości niestandardowe kontrolki.  
  
 Kliknij dwukrotnie <xref:System.Windows.Forms.RadioButton> kontrolkę w formularzu, aby utworzyć <xref:System.Windows.Forms.RadioButton.CheckedChanged> procedury obsługi zdarzeń. Zastąp <xref:System.Windows.Forms.RadioButton.CheckedChanged> procedury obsługi zdarzeń z następującym kodem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Skompiluj i uruchom aplikację. Kliknij przyciski radiowe różnych, aby zobaczyć efekt na złożonego formantu WPF.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Przewodnik: Hostowanie kontrolki złożonej Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: Hosting złożonego formantu 3D WPF w formularzach Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
