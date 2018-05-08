---
title: 'Wskazówki: Hosting złożonego formantu WPF w Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: a70b71b4f7352226796b711cd1fb956a843d7f82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>Wskazówki: Hosting złożonego formantu WPF w Windows Forms
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępnia bogate środowisko do tworzenia aplikacji. Jednak jeśli masz znaczących inwestycji [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodu, może być bardziej skuteczne rozszerzyć istniejącą [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacja o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zamiast ponownego wpisywania go od początku. Typowy scenariusz obejmuje Aby osadzić jedną lub większą liczbę opcji zaimplementowany przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w aplikacji formularzy systemu Windows. Aby uzyskać więcej informacji na temat dostosowywania formantów WPF, zobacz [Dostosowywanie formantu](../../../../docs/framework/wpf/controls/control-customization.md).  
  
 Ten przewodnik zawiera kroki aplikacji obsługującego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożonych kontrolek w celu wykonania wprowadzania danych w aplikacji formularzy systemu Windows. Formantu złożonego jest dostarczana w bibliotece DLL. Ta procedura ogólne można rozszerzyć do bardziej złożonych aplikacji i formanty. W tym przewodniku została zaprojektowana jako niemal identyczny jak w wyglądu i działania [wskazówki: hostowanie formantu złożonego formularzy systemu Windows na platformie WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md). Podstawowa różnica polega na tym, czy została odwrócona scenariuszu obsługi.  
  
 Instruktaż jest podzielona na dwie sekcje. Pierwsza sekcja krótko opisano wykonania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantu złożonego. Druga sekcja szczegółowo omówiono sposób obsługi złożonych kontrolek w aplikacji formularzy systemu Windows, odbieranie zdarzeń z formantu i uzyskiwać dostęp do niektórych właściwości formantu.  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Wdrażanie złożonych kontrolek WPF.  
  
-   Wdrażanie aplikacji hosta formularzy systemu Windows.  
  
 Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [Hosting formantu złożonego WPF w przykładowym formularzy systemu Windows](http://go.microsoft.com/fwlink/?LinkID=159996).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="implementing-the-wpf-composite-control"></a>Wdrażanie złożonych kontrolek WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Formantu złożonego używana w tym przykładzie jest proste wprowadzania danych formularza, który przyjmuje nazwę użytkownika i adres. Gdy użytkownik kliknie jeden z dwóch przycisków, aby wskazać, że zadanie jest zakończony, formantu zgłasza zdarzenie niestandardowe do zwracania informacji do hosta. Na poniższej ilustracji przedstawiono renderowanych formantu.  
  
 ![Proste kontrolki WPF](../../../../docs/framework/wpf/advanced/media/avaloncontrol.png "AvalonControl")  
WPF złożonych kontrolek  
  
### <a name="creating-the-project"></a>Tworzenie projektu  
 Aby uruchomić projekt:  
  
1.  Uruchom [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], a następnie otwórz **nowy projekt** okno dialogowe.  
  
2.  Visual C# i kategorii systemu Windows, wybierz **Biblioteka kontrolek użytkownika WPF** szablonu.  
  
3.  Nazwa nowego projektu `MyControls`.  
  
4.  Do lokalizacji, określ wygodnie nazwanego folder najwyższego poziomu, takich jak `WindowsFormsHostingWpfControl`. Później należy umieścić w folderze aplikacji hosta.  
  
5.  Kliknij przycisk **OK** Aby utworzyć projekt. Domyślny projekt zawiera jeden formant o nazwie `UserControl1`.  
  
6.  W Eksploratorze rozwiązań, Zmień nazwę `UserControl1` do `MyControl1`.  
  
 Projekt powinien mieć odwołania do następującego systemowej biblioteki dll. Jeśli dowolne te biblioteki DLL nie są włączone domyślnie, dodaj je do projektu.  
  
-   PresentationCore  
  
-   PresentationFramework  
  
-   System  
  
-   WindowsBase  
  
### <a name="creating-the-user-interface"></a>Tworzenie interfejsu użytkownika  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Dla formantu złożonego jest realizowana za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Formantu złożonego [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] składa się z pięciu <xref:System.Windows.Controls.TextBox> elementów. Każdy <xref:System.Windows.Controls.TextBox> ma skojarzony element <xref:System.Windows.Controls.TextBlock> element, który służy jako etykieta. Istnieją dwa <xref:System.Windows.Controls.Button> elementów na dole **OK** i **anulować**. Po kliknięciu przycisku albo kontrolka wywołuje zdarzenie niestandardowe do zwracania informacji do hosta.  
  
#### <a name="basic-layout"></a>Podstawowy układ  
 Różnych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy są zawarte w <xref:System.Windows.Controls.Grid> elementu. Można użyć <xref:System.Windows.Controls.Grid> ułożyć zawartość złożone kontroli w taki sam sposób używasz `Table` elementu w formacie HTML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma również <xref:System.Windows.Documents.Table> elementu, ale <xref:System.Windows.Controls.Grid> jest bardziej lekkie oraz lepsze dopasowanie dla zadań układ prosty.  
  
 Następujące XAML przedstawiono podstawowe układu. Ta XAML definiuje ogólną strukturę formantu, określając liczbę kolumn i wierszy w <xref:System.Windows.Controls.Grid> elementu.  
  
 W MyControl1.xaml Zastąp istniejące XAML następujące XAML.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Dodawanie blok tekstu i elementów pola tekstowego do siatki  
 Możesz umieścić [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementu w siatce przez ustawienie elementu <xref:System.Windows.Controls.Grid.RowProperty> i <xref:System.Windows.Controls.Grid.ColumnProperty> atrybuty do odpowiedniej liczby wierszy i kolumn. Należy pamiętać, że wiersz i kolumnę numerowanie liczony od zera. Może mieć elementu obejmuje wielu kolumn, ustawiając jego <xref:System.Windows.Controls.Grid.ColumnSpanProperty> atrybutu. Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.Grid> elementów, zobacz [utworzyć elementu siatki](../../../../docs/framework/wpf/controls/how-to-create-a-grid-element.md).  
  
 Następujący kod XAML zawiera złożonych kontrolek <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.TextBlock> elementy z ich <xref:System.Windows.Controls.Grid.RowProperty> i <xref:System.Windows.Controls.Grid.ColumnProperty> atrybuty, które są ustawione właściwie umieścić elementów w siatce.  
  
 W MyControl1.xaml, Dodaj następujące XAML w <xref:System.Windows.Controls.Grid> elementu.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Style elementów interfejsu użytkownika  
 Wiele elementów w formularzu wprowadzania danych mają podobne wygląd oznacza, że mają one identyczne ustawienia dla wielu ich właściwości. Zamiast Ustawianie atrybutów każdego elementu oddzielnie, korzysta z poprzednich XAML <xref:System.Windows.Style> elementy do definiowania ustawień standardowe właściwości dla klasy elementów. Takie podejście pozwala ograniczyć złożoność formantu i umożliwia zmienianie wyglądu wielu elementów przy użyciu atrybutu pojedynczy styl.  
  
 <xref:System.Windows.Style> Elementy są zawarte w <xref:System.Windows.Controls.Grid> elementu <xref:System.Windows.FrameworkElement.Resources%2A> właściwości, dzięki mogą być używane przez wszystkie elementy w formancie. Jeśli nosi nazwę stylu, możesz zastosować go do elementu przez dodanie <xref:System.Windows.Style> elementu Ustaw nazwę elementu style. Style, które nie są nazywane stają się domyślny styl elementu. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] style, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Poniżej przedstawiono XAML <xref:System.Windows.Style> elementy dla formantu złożonego. Aby dowiedzieć się, jak style są stosowane do elementów, zobacz poprzednie XAML. Na przykład w ciągu ostatnich <xref:System.Windows.Controls.TextBlock> element ma `inlineText` stylu oraz za ostatni <xref:System.Windows.Controls.TextBox> element używa domyślnego stylu.  
  
 W MyControl1.xaml, Dodaj następujący kod XAML tuż po <xref:System.Windows.Controls.Grid> elementu początkowego.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Dodawanie OK i przyciski Anuluj  
 Końcowe elementy formantu złożonego są **OK** i **anulować** <xref:System.Windows.Controls.Button> elementów, które zajmują pierwsze dwie kolumny ostatni wiersz <xref:System.Windows.Controls.Grid>. Typowe program obsługi zdarzeń, użyj tych elementów `ButtonClicked`, wartością domyślną <xref:System.Windows.Controls.Button> style zdefiniowane w poprzedniej XAML.  
  
 W MyControl1.xaml, należy dodać następujące XAML po ostatniej <xref:System.Windows.Controls.TextBox> elementu. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Część złożonego formantu jest teraz ukończona.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Implementacja pliku CodeBehind  
 Plik CodeBehind MyControl1.xaml.cs, implementuje trzy podstawowe zadania:
  
1.  Obsługuje zdarzenie, gdy użytkownik kliknie jeden z przycisków.  
  
2.  Pobiera dane z <xref:System.Windows.Controls.TextBox> elementów, a następnie umieszcza go w obiekcie argument zdarzenie niestandardowe.  
  
3.  Zgłasza niestandardowego `OnButtonClick` zdarzeń, który powiadamia hosta, czy użytkownik zakończy i przekazuje dane z powrotem na hoście.  
  
 Formant również eksponuje pewną liczbę właściwości kolorów i czcionek, które umożliwiają zmienianie wyglądu. W odróżnieniu od <xref:System.Windows.Forms.Integration.WindowsFormsHost> klasy, która jest używana do hostowania kontrolki formularza systemu Windows, <xref:System.Windows.Forms.Integration.ElementHost> klasa przedstawia formantu <xref:System.Windows.Controls.Panel.Background%2A> tylko właściwości. Aby zachować podobieństwa między w tym przykładzie kodu i przykład omówione w [wskazówki: hostowanie formantu złożonego formularzy systemu Windows na platformie WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md), formantu przedstawia pozostałe właściwości bezpośrednio.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Podstawowa struktura pliku CodeBehind  
 Plik CodeBehind składa się z jednego obszaru nazw, `MyControls`, który będzie zawierać dwie klasy `MyControl1` i `MyControlEventArgs`.  
  
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
  
 To pierwsza klasa `MyControl1`, jest częściowej klasy zawierającego kod, który implementuje funkcje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zdefiniowane w MyControl1.xaml. Podczas analizowania MyControl1.xaml [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest konwertowana na tej samej klasy częściowe i dwie klasy częściowe zostaną scalone skompilowanych formant formularza. Z tego powodu nazwę klasy w pliku CodeBehind musi odpowiadać nazwie klasy przypisane do MyControl1.xaml i musi on dziedziczyć z elementu głównego formantu. Klasa sekundę `MyControlEventArgs`, jest klasą argumentów zdarzenia, który służy do wysyłania danych do hosta.  
  
 Open MyControl1.xaml.cs. Zmień istniejące deklaracji klasy, który ma następujące nazwy i dziedziczy <xref:System.Windows.Controls.Grid>.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Inicjowanie kontrolki  
 Poniższy kod implementuje kilka podstawowych zadań:  
  
-   Deklaruje zdarzenie prywatne, `OnButtonClick`, a jego skojarzony obiektem delegowanym `MyControlEventHandler`.  
  
-   Tworzy kilka prywatnej zmienne globalne, które przechowują dane użytkownika. Te dane są dostępne za pośrednictwem odpowiednie właściwości.  
  
-   Implementuje obsługi, `Init`, dla formantu <xref:System.Windows.FrameworkElement.Loaded> zdarzeń. Ten program obsługi inicjuje zmienne globalne przez przypisywanie ich do wartości określonych w MyControl1.xaml. Aby to zrobić, używa <xref:System.Windows.FrameworkElement.Name%2A> przypisane do typowe <xref:System.Windows.Controls.TextBlock> elementu `nameLabel`, aby uzyskać dostępu do ustawienia właściwości tego elementu.  
  
 Usuń istniejące Konstruktor i Dodaj następujący kod, aby Twoje `MyControl1` klasy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Obsługa przycisków zdarzenia kliknięcia  
 Użytkownik wskazuje zakończenie zadania wprowadzania danych, klikając opcję **OK** przycisk lub **anulować** przycisku. Przyciski używać tego samego <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń, `ButtonClicked`. Przyciski mają nazwy, `btnOK` lub `btnCancel`, obsługi ustalić, który przycisk został kliknięty, sprawdzając wartość, który umożliwia `sender` argumentu. Program obsługi wykonuje następujące czynności:  
  
-   Tworzy `MyControlEventArgs` obiekt, który zawiera dane z <xref:System.Windows.Controls.TextBox> elementów.  
  
-   Jeśli użytkownik kliknął **anulować** przycisk zestawy `MyControlEventArgs` obiektu `IsOK` właściwości `false`.  
  
-   Zgłasza `OnButtonClick` zdarzenia w celu poinformowania do hosta, że zostanie zakończone i przekazuje kopii zebranych danych.  
  
 Dodaj następujący kod do Twojej `MyControl1` klasy po `Init` metody.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Tworzenie właściwości  
 W pozostałej części klasy po prostu udostępnia właściwości, które odpowiadają zmienne globalne omówionych wcześniej. Podczas zmiany właściwości, metody dostępu set modyfikuje wygląd formantu, zmieniając odpowiednie właściwości elementu i aktualizowania podstawowej zmienne globalne.  
  
 Dodaj następujący kod do Twojej `MyControl1` klasy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Wysyłanie danych do hosta  
 Jest ostatnim składnika w pliku `MyControlEventArgs` klasy, która jest używana do odesłania zebranych danych do hosta.  
  
 Dodaj następujący kod do Twojej `MyControls` przestrzeni nazw. Wdrożenie jest proste i nie został omówiony w dalszej.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Skompiluj rozwiązanie. Kompilacja utworzy o nazwie MyControls.dll biblioteki DLL.  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Wdrażanie aplikacji hosta formularzy systemu Windows  
 Formularze systemu Windows hosta aplikacja używa <xref:System.Windows.Forms.Integration.ElementHost> obiektu hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantu złożonego. Uchwyty aplikacji `OnButtonClick` zdarzenia w celu odbierania danych z formantu złożonego. Aplikacja ma również zestaw przycisków opcji, który służy do modyfikowania wyglądu formantu. Na poniższej ilustracji przedstawiono aplikację.  
  
 ![Hostowanie kontrolki Avalon formularza systemu Windows](../../../../docs/framework/wpf/advanced/media/wfhost.png "WFHost")  
WPF formantu złożonego w aplikacji formularzy systemu Windows  
  
### <a name="creating-the-project"></a>Tworzenie projektu  
 Aby uruchomić projekt:  
  
1.  Uruchom [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], a następnie otwórz **nowy projekt** okno dialogowe.  
  
2.  Visual C# i kategorii systemu Windows, wybierz **aplikacji Windows Forms** szablonu.  
  
3.  Nazwa nowego projektu `WFHost`.  
  
4.  W przypadku lokalizacji określ tego samego folderu najwyższego poziomu, który zawiera MyControls projektu.  
  
5.  Kliknij przycisk **OK** Aby utworzyć projekt.  
  
 Należy również dodać odwołania do biblioteki DLL zawierającej `MyControl1` i innych zestawów.  
  
1.  Kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań i wybierz **Dodaj odwołanie**.  
  
2.  Kliknij przycisk **Przeglądaj** karcie i przejdź do folderu, który zawiera MyControls.dll. W ramach tego przewodnika ten folder jest MyControls\bin\Debug.  
  
3.  Wybierz MyControls.dll, a następnie kliknij przycisk **OK**.  
  
4.  Dodaj odwołania do następujących zestawów.  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   System.Xaml  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>Implementacja interfejsu użytkownika dla aplikacji  
 Interfejs użytkownika dla aplikacji formularzy systemu Windows zawiera kilka formantów na współdziałanie z WPF złożonych kontrolek.  
  
1.  Otwórz Form1 w projektanta formularzy systemu Windows.  
  
2.  Powiększa formularza, aby pomieścić kontrolki.  
  
3.  W prawym górnym rogu formularza dodać <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> sterowania, aby pomieścić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantu złożonego.  
  
4.  Dodaj następujące <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> formantów w formularzu.  
  
    |Nazwa|Tekst|  
    |----------|----------|  
    |groupBox1|Kolor tła|  
    |groupBox2|Kolor pierwszego planu|  
    |groupBox3|Rozmiar czcionki|  
    |groupBox4|Rodzina czcionek|  
    |groupBox5|Styl czcionki|  
    |groupBox6|Grubość czcionki|  
    |groupBox7|Dane z formantu|  
  
5.  Dodaj następujące <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> formanty <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> kontrolki.  
  
    |GroupBox|Nazwa|Tekst|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|Oryginał|  
    |groupBox1|radioBackgroundLightGreen|LightGreen|  
    |groupBox1|radioBackgroundLightSalmon|LightSalmon|  
    |groupBox2|radioForegroundOriginal|Oryginał|  
    |groupBox2|radioForegroundRed|czerwony|  
    |groupBox2|radioForegroundYellow|żółty|  
    |groupBox3|radioSizeOriginal|Oryginał|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|Oryginał|  
    |groupBox4|radioFamilyTimes|Georgia|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|Normalny|  
    |groupBox5|radioStyleItalic|Kursywa|  
    |groupBox6|radioWeightOriginal|Oryginał|  
    |groupBox6|radioWeightBold|Bold|  
  
6.  Dodaj następujące <xref:System.Windows.Forms.Label?displayProperty=nameWithType> kontrolki do ostatniego <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>. Formanty wyświetlania danych zwróconych przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantu złożonego.  
  
    |GroupBox|Nazwa|Tekst|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Nazwa:|  
    |groupBox7|lblAddress|Adres:|  
    |groupBox7|lblCity|Miasto:|  
    |groupBox7|lblState|Stan:|  
    |groupBox7|lblZip|Kod pocztowy:|  
  
### <a name="initializing-the-form"></a>Inicjowanie formularza  
 Zazwyczaj zaimplementować hostingu kodu w postaci <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń. Poniższy kod przedstawia <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń, program obsługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantu złożonego <xref:System.Windows.FrameworkElement.Loaded> zdarzeń i deklaracje dla kilku zmiennych globalnych, które są używane później.  
  
 W narzędziu Projektant dla formularzy systemu Windows, kliknij dwukrotnie formularz, aby utworzyć <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń. W górnej części pliku Form1.cs, Dodaj następujący `using` instrukcje.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Zastąp istniejącą zawartość `Form1` klasy następującym kodem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 `Form1_Load` w poprzednim kodzie przedstawiono ogólną procedurę obsługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sterowania:  
  
1.  Utwórz nową <xref:System.Windows.Forms.Integration.ElementHost> obiektu.  
  
2.  Ustawianie formantu <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>.  
  
3.  Dodaj <xref:System.Windows.Forms.Integration.ElementHost> formant <xref:System.Windows.Forms.Panel> formantu <xref:System.Windows.Forms.Control.Controls%2A> kolekcji.  
  
4.  Utwórz wystąpienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantu.  
  
5.  Host złożonych kontrolek w formularzu, przypisując formant <xref:System.Windows.Forms.Integration.ElementHost> formantu <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> właściwości.  
  
 Pozostałe dwa wiersze w `Form1_Load` metody dołączyć obsługi do dwóch zdarzeń kontrolowania:  
  
-   `OnButtonClick` To zdarzenie niestandardowe, które jest wywoływane przez złożonych kontrolek, gdy użytkownik kliknie **OK** lub **anulować** przycisku. Można obsługiwać zdarzenia, aby uzyskać odpowiedzi użytkownika i zbierać dane, które użytkownik określił.  
  
-   <xref:System.Windows.FrameworkElement.Loaded> jest standardowe zdarzenie, które jest wywoływane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroli, gdy zostanie całkowicie załadowany. Zdarzenia jest używany w tym miejscu, ponieważ przykładzie musi zainicjować kilku zmiennych globalnych, przy użyciu właściwości z formantu. W tym czasie w postaci <xref:System.Windows.Forms.Form.Load> zdarzenia formant nie jest w pełni załadowany i te wartości są nadal ustawioną `null`. Należy zaczekać, aż do formantu <xref:System.Windows.FrameworkElement.Loaded> wystąpi zdarzenie w celu uzyskania dostępu do tych właściwości.  
  
 <xref:System.Windows.FrameworkElement.Loaded> Program obsługi zdarzeń jest wyświetlany w powyższym kodzie. `OnButtonClick` Obsługi została szczegółowo opisana w następnej sekcji.  
  
### <a name="handling-onbuttonclick"></a>Obsługa OnButtonClick  
 `OnButtonClick` Zdarzenie wystąpi, gdy użytkownik kliknie **OK** lub **anulować** przycisku.  
  
 Program obsługi zdarzeń sprawdza argument zdarzenia `IsOK` pole, aby określić, który przycisk został kliknięty. `lbl` *Danych* zmienne odpowiadają <xref:System.Windows.Forms.Label> formantów, które zostały wymienione powyżej. Gdy użytkownik kliknie **OK** przycisk danych w formancie <xref:System.Windows.Controls.TextBox> formantów jest przypisany do odpowiednich <xref:System.Windows.Forms.Label> formantu. Gdy użytkownik kliknie **anulować**, <xref:System.Windows.Forms.Label.Text%2A> wartości są ustawiane na domyślne parametry.  
  
 Dodaj poniższy przycisk kliknij kod obsługi zdarzeń do `Form1` klasy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Skompiluj i uruchom aplikację. Dodaj tekst w kontrolce WPF, złożonego, a następnie kliknij przycisk **OK**. Tekst jest wyświetlany w etykiecie. W tym momencie kodu nie dodano do obsługi przycisków radiowych.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Modyfikowanie wygląd formantu  
 <xref:System.Windows.Forms.RadioButton> Kontrolek w formularzu umożliwi użytkownikom na zmianę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] również jako kilka właściwości czcionki koloru tła i pierwszego planu formantu złożonego. Kolor tła jest udostępniany przez <xref:System.Windows.Forms.Integration.ElementHost> obiektu. Pozostałe właściwości są widoczne jako właściwości niestandardowe kontrolki.  
  
 Kliknij dwukrotnie <xref:System.Windows.Forms.RadioButton> kontrolkę w formularzu można utworzyć <xref:System.Windows.Forms.RadioButton.CheckedChanged> procedury obsługi zdarzeń. Zastąp <xref:System.Windows.Forms.RadioButton.CheckedChanged> procedury obsługi zdarzeń z następującym kodem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Skompiluj i uruchom aplikację. Kliknij przycisk różnych opcji, aby zobaczyć efekt na złożonych kontrolek WPF.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Projektant WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Przewodnik: hosting złożonej kontrolki 3D WPF w Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
