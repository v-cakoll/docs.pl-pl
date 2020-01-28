---
title: Hostowanie złożonego formantu WPF w Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: 59243e1810757ff0ff58a60ac3eb007bbc227be0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742683"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>Wskazówki: Hosting złożonego formantu WPF w Windows Forms
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia rozbudowane środowisko do tworzenia aplikacji. Jeśli jednak masz znaczną inwestycję w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodzie, może być bardziej efektywne, aby zwiększyć swoją istniejącą aplikację [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], a nie od początku. Typowym scenariuszem jest osadzenie co najmniej jednej kontrolki zaimplementowanej przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w aplikacji Windows Forms. Aby uzyskać więcej informacji na temat dostosowywania formantów WPF, zobacz [Dostosowywanie kontroli](../controls/control-customization.md).  
  
 W tym instruktażu przedstawiono krok po kroku przez aplikację, która hostuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formant złożony do wprowadzania danych w aplikacji Windows Forms. Formant złożony jest spakowany w bibliotece DLL. Ta ogólna procedura może zostać rozszerzona na bardziej złożone aplikacje i kontrolki. Ten przewodnik został zaprojektowany tak, aby był niemal identyczny w wyglądzie i funkcji w celu [instruktażu: hostowanie złożonego formantu Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md). Podstawowa różnica polega na tym, że scenariusz hostingu jest odwrócony.  
  
 Przewodnik jest podzielony na dwie sekcje. W pierwszej sekcji krótko opisano implementację [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ego formantu złożonego. W drugiej sekcji omówiono szczegółowo, jak hostować formant złożony w aplikacji Windows Forms, odbierać zdarzenia z kontrolki i uzyskiwać dostęp do niektórych właściwości kontrolki.  
  
 Zadania przedstawione w tym instruktażu obejmują:  
  
- Implementowanie kontrolki złożonej WPF.  
  
- Implementowanie aplikacji hosta Windows Forms.  
  
 Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [hosting złożonego formantu WPF w Windows Forms przykładzie](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WindowsFormsHostingWpfControl).  
  
## <a name="prerequisites"></a>Wymagania wstępne  

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.  
  
## <a name="implementing-the-wpf-composite-control"></a>Implementowanie kontrolki złożonej WPF  
 Formant złożony [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używany w tym przykładzie to prosty formularz wprowadzania danych, który pobiera nazwę i adres użytkownika. Gdy użytkownik kliknie jeden z dwóch przycisków, aby wskazać, że zadanie zostało zakończone, formant wywołuje zdarzenie niestandardowe, aby zwrócić te informacje do hosta. Poniższa ilustracja przedstawia renderowany formant. 

 Na poniższej ilustracji przedstawiono formant złożony WPF: 

 ![Zrzut ekranu, który pokazuje prostą kontrolkę WPF.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>Tworzenie projektu  
 Aby rozpocząć projekt:  
  
1. Uruchom program Visual Studio i Otwórz okno dialogowe **Nowy projekt** .  
  
2. W wizualizacji C# i w kategorii Windows wybierz szablon **Biblioteka formantów użytkownika WPF** .  
  
3. Nadaj nazwę nowemu projektowi `MyControls`.  
  
4. W polu Lokalizacja Określ wygodną nazwę folderu najwyższego poziomu, na przykład `WindowsFormsHostingWpfControl`. Później aplikacja hosta zostanie umieszczona w tym folderze.  
  
5. Kliknij przycisk **OK** , aby utworzyć projekt. Domyślny projekt zawiera pojedynczy formant o nazwie `UserControl1`.  
  
6. W Eksplorator rozwiązań Zmień nazwę `UserControl1` na `MyControl1`.  
  
 Projekt powinien zawierać odwołania do następujących bibliotek DLL systemu. Jeśli dowolna z tych bibliotek DLL nie jest domyślnie dołączona, Dodaj je do projektu.  
  
- 'Presentationcore  
  
- Platformie docelowej  
  
- System  
  
- WindowsBase  
  
### <a name="creating-the-user-interface"></a>Tworzenie interfejsu użytkownika  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dla formantu złożonego jest implementowany z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] sterowania złożonego składa się z pięciu <xref:System.Windows.Controls.TextBox> elementów. Każdy element <xref:System.Windows.Controls.TextBox> ma skojarzony <xref:System.Windows.Controls.TextBlock> element, który służy jako etykieta. Na dole znajdują się dwa <xref:System.Windows.Controls.Button> elementy, **OK** i **Anuluj**. Gdy użytkownik kliknie jeden z przycisków, formant wywołuje zdarzenie niestandardowe, aby zwrócić informacje do hosta.  
  
#### <a name="basic-layout"></a>Układ podstawowy  
 Różne elementy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] są zawarte w elemencie <xref:System.Windows.Controls.Grid>. Za pomocą <xref:System.Windows.Controls.Grid> można rozmieścić zawartość kontrolki złożonej w podobny sposób, jak używać elementu `Table` w kodzie HTML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma także element <xref:System.Windows.Documents.Table>, ale <xref:System.Windows.Controls.Grid> jest bardziej lekki i lepszy dla prostych zadań układu.  
  
 Poniższy kod XAML pokazuje podstawowy układ. Ten kod XAML definiuje ogólną strukturę kontrolki, określając liczbę kolumn i wierszy w <xref:System.Windows.Controls.Grid> elemencie.  
  
 W MyControl1. XAML Zastąp istniejący kod XAML następującym XAML.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Dodawanie elementów TextBlock i TextBox do siatki  
 Aby umieścić [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] element w siatce, należy ustawić atrybuty <xref:System.Windows.Controls.Grid.RowProperty> i <xref:System.Windows.Controls.Grid.ColumnProperty> elementu na odpowiedni wiersz i numer kolumny. Należy pamiętać, że numery wierszy i kolumn są numerowane od zera. Element może zawierać wiele kolumn, ustawiając jego atrybut <xref:System.Windows.Controls.Grid.ColumnSpanProperty>. Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.Grid> elementów, zobacz [Tworzenie elementu siatki](../controls/how-to-create-a-grid-element.md).  
  
 Poniższy kod XAML pokazuje <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.TextBlock> elementów formantu złożonego z ich <xref:System.Windows.Controls.Grid.RowProperty> i <xref:System.Windows.Controls.Grid.ColumnProperty> atrybutami, które są ustawione tak, aby elementy były prawidłowo umieszczane w siatce.  
  
 W pliku MyControl1. XAML Dodaj następujący kod XAML w obrębie elementu <xref:System.Windows.Controls.Grid>.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Określanie stylu elementów interfejsu użytkownika  
 Wiele elementów w formularzu wprowadzania danych ma podobny wygląd, co oznacza, że mają identyczne ustawienia dla kilku właściwości. Zamiast oddzielnie ustawić atrybuty każdego elementu, poprzedni kod XAML używa <xref:System.Windows.Style> elementów do definiowania standardowych ustawień właściwości dla klas elementów. Takie podejście zmniejsza złożoność kontrolki i umożliwia zmianę wyglądu wielu elementów za pomocą jednego atrybutu stylu.  
  
 Elementy <xref:System.Windows.Style> są zawarte we właściwości <xref:System.Windows.FrameworkElement.Resources%2A> elementu <xref:System.Windows.Controls.Grid>, dzięki czemu mogą być używane przez wszystkie elementy w formancie. Jeśli styl ma nazwę, należy zastosować go do elementu przez dodanie elementu <xref:System.Windows.Style> zestawu do nazwy stylu. Style, które nie są nazwane, stają się stylem domyślnym elementu. Aby uzyskać więcej informacji na temat stylów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz Style [i tworzenia szablonów](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
 Poniższy kod XAML pokazuje elementy <xref:System.Windows.Style> dla formantu złożonego. Aby zobaczyć, jak style są stosowane do elementów, zobacz poprzedni kod XAML. Na przykład ostatni element <xref:System.Windows.Controls.TextBlock> ma styl `inlineText`, a ostatni element <xref:System.Windows.Controls.TextBox> używa stylu domyślnego.  
  
 W pliku MyControl1. XAML Dodaj następujący kod XAML tuż po elemencie <xref:System.Windows.Controls.Grid> Start.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Dodawanie przycisków OK i Anuluj  
 Końcowe elementy kontrolki złożonej są elementami **OK** i **Cancel**<xref:System.Windows.Controls.Button>, które zajmują pierwsze dwie kolumny ostatniego wiersza <xref:System.Windows.Controls.Grid>. Te elementy używają typowego programu obsługi zdarzeń, `ButtonClicked`i domyślnego stylu <xref:System.Windows.Controls.Button> zdefiniowanego w poprzednim kodzie XAML.  
  
 W MyControl1. XAML Dodaj następujący kod XAML po ostatnim elemencie <xref:System.Windows.Controls.TextBox>. Część [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] formantu złożonego jest teraz ukończona.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Implementowanie pliku związanego z kodem  
 Plik związany z kodem, MyControl1.xaml.cs, implementuje trzy zasadnicze zadania:
  
1. Obsługuje zdarzenie, które występuje, gdy użytkownik kliknie jeden z przycisków.  
  
2. Pobiera dane z elementów <xref:System.Windows.Controls.TextBox> i pakuje je w obiekcie argumentu zdarzenia niestandardowego.  
  
3. Wywołuje niestandardowe zdarzenie `OnButtonClick`, które powiadamia hosta, że użytkownik jest zakończony i przekazuje dane z powrotem do hosta.  
  
 Kontrolka udostępnia również szereg właściwości kolorów i czcionek, które umożliwiają zmianę wyglądu. W przeciwieństwie do klasy <xref:System.Windows.Forms.Integration.WindowsFormsHost>, która jest używana do hostowania kontrolki Windows Forms, Klasa <xref:System.Windows.Forms.Integration.ElementHost> uwidacznia tylko Właściwość <xref:System.Windows.Controls.Panel.Background%2A> formantu. Aby zachować podobieństwo między tym przykładem kodu i przykładem opisanym w [instruktażu: hostowanie złożonego formantu Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md), formant uwidacznia pozostałe właściwości bezpośrednio.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Podstawowa struktura pliku związanego z kodem  
 Plik związany z kodem składa się z pojedynczej przestrzeni nazw, `MyControls`, która będzie zawierać dwie klasy, `MyControl1` i `MyControlEventArgs`.  
  
```csharp  
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
  
 Pierwsza klasa, `MyControl1`, jest klasą częściową zawierającą kod implementujący funkcje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zdefiniowanej w MyControl1. XAML. Gdy MyControl1. XAML jest analizowany, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest konwertowana na tę samą klasę częściową, a dwie klasy częściowe są scalane w celu utworzenia skompilowanej kontrolki. Z tego powodu nazwa klasy w pliku związanym z kodem musi być zgodna z nazwą klasy przypisaną do MyControl1. XAML i musi dziedziczyć po elemencie głównym formantu. Druga klasa, `MyControlEventArgs`, jest klasą argumentów zdarzeń, która jest używana do wysyłania danych z powrotem do hosta.  
  
 Open MyControl1.xaml.cs. Zmień istniejącą deklarację klasy tak, aby miała następującą nazwę i dziedziczy po <xref:System.Windows.Controls.Grid>.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Inicjowanie kontrolki  
 Poniższy kod implementuje kilka podstawowych zadań:  
  
- Deklaruje zdarzenie prywatne, `OnButtonClick`i skojarzonego z nim delegata, `MyControlEventHandler`.  
  
- Tworzy kilka prywatnych zmiennych globalnych, które przechowują dane użytkownika. Te dane są udostępniane za poorednictwem odpowiednich właściwości.  
  
- Implementuje procedurę obsługi, `Init`dla zdarzenia <xref:System.Windows.FrameworkElement.Loaded> formantu. Ta procedura obsługi inicjuje zmienne globalne, przypisując im wartości zdefiniowane w MyControl1. XAML. W tym celu używa <xref:System.Windows.FrameworkElement.Name%2A> przypisane do typowego elementu <xref:System.Windows.Controls.TextBlock>, `nameLabel`, aby uzyskać dostęp do ustawień właściwości tego elementu.  
  
 Usuń istniejący Konstruktor i Dodaj następujący kod do klasy `MyControl1`.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Obsługa zdarzeń kliknięcia przycisku  
 Użytkownik wskazuje, że zadanie wprowadzania danych zostało zakończone, klikając przycisk **OK** lub przycisk **Anuluj** . Oba przyciski używają tego samego <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obsługi zdarzeń, `ButtonClicked`. Oba przyciski mają nazwę, `btnOK` lub `btnCancel`, która umożliwia programowi obsługi określenie, który przycisk został kliknięty, sprawdzając wartość argumentu `sender`. Program obsługi wykonuje następujące czynności:  
  
- Tworzy obiekt `MyControlEventArgs`, który zawiera dane z elementów <xref:System.Windows.Controls.TextBox>.  
  
- Jeśli użytkownik kliknął przycisk **Anuluj** , ustawia właściwość `IsOK` obiektu `MyControlEventArgs` na `false`.  
  
- Podnosi zdarzenie `OnButtonClick`, aby wskazać hostowi, że użytkownik jest zakończony, i przekazuje zebrane dane.  
  
 Dodaj następujący kod do klasy `MyControl1` po `Init` metodzie.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Tworzenie właściwości  
 Pozostała część klasy po prostu uwidacznia właściwości, które są zgodne z opisanymi wcześniej zmiennymi globalnymi. Gdy właściwość zostanie zmieniona, metoda dostępu set modyfikuje wygląd kontrolki, zmieniając odpowiednie właściwości elementu i aktualizując bazowe zmienne globalne.  
  
 Dodaj następujący kod do klasy `MyControl1`.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Wysyłanie danych z powrotem do hosta  
 Końcowy składnik w pliku jest klasą `MyControlEventArgs`, która jest używana do wysyłania zebranych danych z powrotem do hosta.  
  
 Dodaj następujący kod do przestrzeni nazw `MyControls`. Implementacja jest prosta i nie została omówiona dokładniej.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Skompiluj rozwiązanie. Kompilacja spowoduje utworzenie biblioteki DLL o nazwie WebControls. dll.  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Implementowanie aplikacji hosta Windows Forms  
 Aplikacja hosta Windows Forms używa obiektu <xref:System.Windows.Forms.Integration.ElementHost> do obsługi kontrolki złożonej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Aplikacja obsługuje zdarzenie `OnButtonClick`, aby otrzymywać dane z formantu złożonego. Aplikacja ma również zestaw przycisków opcji, których można użyć do zmodyfikowania wyglądu kontrolki. Na poniższej ilustracji przedstawiono aplikację.  

Na poniższej ilustracji przedstawiono formant złożony WPF hostowany w aplikacji Windows Forms "  

 ![Scteenshot, w którym jest wyświetlany formant Avalon obsługujący formularz systemu Windows.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>Tworzenie projektu  
 Aby rozpocząć projekt:  
  
1. Uruchom program Visual Studio i Otwórz okno dialogowe **Nowy projekt** .  
  
2. W wizualizacji C# i w kategorii Windows wybierz szablon **aplikacji Windows Forms** .  
  
3. Nadaj nazwę nowemu projektowi `WFHost`.  
  
4. Dla lokalizacji Określ ten sam folder najwyższego poziomu, który zawiera projekt kontrolek.  
  
5. Kliknij przycisk **OK** , aby utworzyć projekt.  
  
 Należy również dodać odwołania do biblioteki DLL, która zawiera `MyControl1` i inne zestawy.  
  
1. Kliknij prawym przyciskiem myszy nazwę projektu w Eksplorator rozwiązań i wybierz polecenie **Dodaj odwołanie**.  
  
2. Kliknij kartę **Przeglądaj** i przejdź do folderu, który zawiera plik. dll. W tym instruktażu ten folder jest MyControls\bin\Debug.  
  
3. Wybierz pozycję Moja Controls. dll, a następnie kliknij przycisk **OK**.  
  
4. Dodaj odwołania do następujących zestawów.  
  
    - 'Presentationcore  
  
    - Platformie docelowej  
  
    - System.Xaml  
  
    - WindowsBase  
  
    - WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>Implementowanie interfejsu użytkownika dla aplikacji  
 Interfejs użytkownika aplikacji formularza systemu Windows zawiera kilka kontrolek do współpracy z formantem złożonym WPF.  
  
1. Otwórz formularz Form1 w projektancie formularzy systemu Windows.  
  
2. Powiększ formularz, aby dopasować formanty.  
  
3. W prawym górnym rogu formularza Dodaj formant <xref:System.Windows.Forms.Panel?displayProperty=nameWithType>, aby trzymać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formant złożony.  
  
4. Dodaj do formularza następujące kontrolki <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>.  
  
    |Nazwa|Tekst|  
    |----------|----------|  
    |groupBox1|Kolor tła|  
    |groupBox2|Kolor pierwszego planu|  
    |groupBox3|Rozmiar czcionki|  
    |groupBox4|Rodzina czcionek|  
    |groupBox5|Styl czcionki|  
    |groupBox6|Grubość czcionki|  
    |groupBox7|Dane z kontroli|  
  
5. Dodaj do kontrolek <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> następujące kontrolki <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType>.  
  
    |GroupBox|Nazwa|Tekst|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|Oryginał|  
    |groupBox1|radioBackgroundLightGreen|LightGreen|  
    |groupBox1|radioBackgroundLightSalmon|LightSalmon|  
    |groupBox2|radioForegroundOriginal|Oryginał|  
    |groupBox2|radioForegroundRed|Czerwony|  
    |groupBox2|radioForegroundYellow|Kryje|  
    |groupBox3|radioSizeOriginal|Oryginał|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|Oryginał|  
    |groupBox4|radioFamilyTimes|Times New Roman|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|Normalny|  
    |groupBox5|radioStyleItalic|Wyowietla|  
    |groupBox6|radioWeightOriginal|Oryginał|  
    |groupBox6|radioWeightBold|Zapis|  
  
6. Dodaj następujące kontrolki <xref:System.Windows.Forms.Label?displayProperty=nameWithType> do ostatniego <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>. Te kontrolki wyświetlają dane zwrócone przez formant złożony [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    |GroupBox|Nazwa|Tekst|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Nazwa:|  
    |groupBox7|lblAddress|Ulica:|  
    |groupBox7|lblCity|—|  
    |groupBox7|lblState|Stan:|  
    |groupBox7|lblZip|Kodu|  
  
### <a name="initializing-the-form"></a>Inicjowanie formularza  
 Na ogół implementujemy kod hostingu w <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń w formularzu. Poniższy kod przedstawia procedurę obsługi zdarzeń <xref:System.Windows.Forms.Form.Load>, procedurę obsługi dla zdarzenia <xref:System.Windows.FrameworkElement.Loaded> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]j kontrolki złożonej oraz deklaracje dla kilku zmiennych globalnych, które są używane później.  
  
 W Projektant formularzy systemu Windows kliknij dwukrotnie formularz, aby utworzyć procedurę obsługi zdarzeń <xref:System.Windows.Forms.Form.Load>. W górnej części Form1.cs Dodaj następujące instrukcje `using`.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Zastąp zawartość istniejącej klasy `Form1` poniższym kodem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 Metoda `Form1_Load` w poprzednim kodzie przedstawia ogólną procedurę hostingu kontrolki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
1. Utwórz nowy obiekt <xref:System.Windows.Forms.Integration.ElementHost>.  
  
2. Ustaw właściwość <xref:System.Windows.Forms.Control.Dock%2A> formantu na <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>.  
  
3. Dodaj kontrolkę <xref:System.Windows.Forms.Integration.ElementHost> do kolekcji <xref:System.Windows.Forms.Control.Controls%2A> kontrolki <xref:System.Windows.Forms.Panel>.  
  
4. Utwórz wystąpienie kontrolki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
5. Hostować formant złożony w formularzu, przypisując formant do właściwości <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> kontrolki <xref:System.Windows.Forms.Integration.ElementHost>.  
  
 Pozostałe dwa wiersze w metodzie `Form1_Load` dołączają programy obsługi do dwóch zdarzeń kontroli:  
  
- `OnButtonClick` jest zdarzeniem niestandardowym, które jest wywoływane przez formant złożony, gdy użytkownik kliknie przycisk **OK** lub **Anuluj** . Możesz obsłużyć zdarzenie, aby uzyskać odpowiedź użytkownika i zebrać dane określone przez użytkownika.  
  
- <xref:System.Windows.FrameworkElement.Loaded> jest zdarzeniem standardowym, które jest zgłaszane przez kontrolkę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], gdy jest ona w pełni załadowana. To zdarzenie jest używane w tym miejscu, ponieważ przykład wymaga zainicjowania kilku zmiennych globalnych przy użyciu właściwości z formantu. W czasie zdarzenia <xref:System.Windows.Forms.Form.Load> formularza formant nie jest w pełni załadowany i te wartości nadal są ustawione na `null`. Zanim będzie można uzyskać dostęp do tych właściwości, musisz poczekać, aż wystąpi <xref:System.Windows.FrameworkElement.Loaded> zdarzenie.  
  
 Procedura obsługi zdarzeń <xref:System.Windows.FrameworkElement.Loaded> jest pokazywana w powyższym kodzie. Procedura obsługi `OnButtonClick` została omówiona w następnej sekcji.  
  
### <a name="handling-onbuttonclick"></a>Obsługa OnButtonClick  
 Zdarzenie `OnButtonClick` występuje, gdy użytkownik kliknie przycisk **OK** lub **Anuluj** .  
  
 Program obsługi zdarzeń sprawdza pole `IsOK` argumentu zdarzenia, aby określić, który przycisk został kliknięty. Zmienne *danych* `lbl`odpowiadają formantom <xref:System.Windows.Forms.Label>, które zostały omówione wcześniej. Jeśli użytkownik kliknie przycisk **OK** , dane z kontrolek <xref:System.Windows.Controls.TextBox> kontrolki są przypisywane do odpowiedniej kontrolki <xref:System.Windows.Forms.Label>. Jeśli użytkownik kliknie **przycisk Anuluj**, wartości <xref:System.Windows.Forms.Label.Text%2A> są ustawiane na domyślne ciągi.  
  
 Dodaj poniższy przycisk i kliknij kod programu obsługi zdarzeń do klasy `Form1`.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Skompiluj i uruchom aplikację. Dodaj tekst do kontrolki złożonej WPF, a następnie kliknij przycisk **OK**. Tekst zostanie wyświetlony w etykietach. W tym momencie kod nie został dodany do obsługi przycisków radiowych.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Modyfikowanie wyglądu kontrolki  
 Kontrolki <xref:System.Windows.Forms.RadioButton> w formularzu umożliwią użytkownikowi zmianę koloru pierwszego planu i tła [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki złożonej oraz kilku właściwości czcionki. Kolor tła jest uwidaczniany przez obiekt <xref:System.Windows.Forms.Integration.ElementHost>. Pozostałe właściwości są ujawniane jako właściwości niestandardowe kontrolki.  
  
 Kliknij dwukrotnie każdy formant <xref:System.Windows.Forms.RadioButton> w formularzu, aby utworzyć <xref:System.Windows.Forms.RadioButton.CheckedChanged> programy obsługi zdarzeń. Zastąp obsługę zdarzeń <xref:System.Windows.Forms.RadioButton.CheckedChanged> poniższym kodem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Skompiluj i uruchom aplikację. Kliknij różne przyciski radiowe, aby zobaczyć efekt na formancie złożonym WPF.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: hosting złożonej kontrolki 3D WPF w Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
