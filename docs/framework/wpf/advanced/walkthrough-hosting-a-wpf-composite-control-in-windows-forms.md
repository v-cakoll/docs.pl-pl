---
title: 'Przewodnik: hostowanie kontrolki złożonej WPF w Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: bff89f1d81b16c8c66d73901ef951626f6d2cb9e
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400621"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>Przewodnik: hostowanie kontrolki złożonej WPF w Windows Forms
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]oferuje bogate środowisko do tworzenia aplikacji. Jeśli jednak masz znaczną inwestycję w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kod, może być bardziej skutecznym rozszerzeniem istniejącej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , a nie od początku. Typowym scenariuszem jest osadzenie co najmniej jednej kontrolki zaimplementowanej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w ramach aplikacji Windows Forms. Aby uzyskać więcej informacji na temat dostosowywania formantów WPF, zobacz [Dostosowywanie kontroli](../controls/control-customization.md).  
  
 Ten Instruktaż przeprowadzi Cię przez aplikację, która hostuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożone kontrolki do wykonywania wpisów danych w aplikacji Windows Forms. Formant złożony jest spakowany w bibliotece DLL. Ta ogólna procedura może zostać rozszerzona na bardziej złożone aplikacje i kontrolki. Ten przewodnik został zaprojektowany tak, aby był niemal identyczny w wyglądzie i funkcji w celu [instruktażu: Hostowanie złożonego formantu Windows Forms w](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)WPF. Podstawowa różnica polega na tym, że scenariusz hostingu jest odwrócony.  
  
 Przewodnik jest podzielony na dwie sekcje. W pierwszej sekcji krótko opisano implementację [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożonego formantu. W drugiej sekcji omówiono szczegółowo, jak hostować formant złożony w aplikacji Windows Forms, odbierać zdarzenia z kontrolki i uzyskiwać dostęp do niektórych właściwości kontrolki.  
  
 Zadania przedstawione w tym instruktażu obejmują:  
  
- Implementowanie kontrolki złożonej WPF.  
  
- Implementowanie aplikacji hosta Windows Forms.  
  
 Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [hosting złożonego formantu WPF w Windows Forms przykładzie](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WindowsFormsHostingWpfControl).  
  
## <a name="prerequisites"></a>Wymagania wstępne  

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.  
  
## <a name="implementing-the-wpf-composite-control"></a>Implementowanie kontrolki złożonej WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Złożona kontrolka używana w tym przykładzie jest prostym formularzem wprowadzania danych, który pobiera nazwę i adres użytkownika. Gdy użytkownik kliknie jeden z dwóch przycisków, aby wskazać, że zadanie zostało zakończone, formant wywołuje zdarzenie niestandardowe, aby zwrócić te informacje do hosta. Poniższa ilustracja przedstawia renderowany formant. 

 Na poniższej ilustracji przedstawiono formant złożony WPF: 

 ![Zrzut ekranu, który pokazuje prostą kontrolkę WPF.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>Tworzenie projektu  
 Aby rozpocząć projekt:  
  
1. Uruchom [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]i Otwórz okno dialogowe **Nowy projekt** .  
  
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
 Dla formantu złożonego jest implementowany przy [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]użyciu. [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Kontrolka [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] złożona składa się <xref:System.Windows.Controls.TextBox> z pięciu elementów. Każdy <xref:System.Windows.Controls.TextBox> element ma skojarzony <xref:System.Windows.Controls.TextBlock> element, który służy jako etykieta. Na dole znajdują się dwa <xref:System.Windows.Controls.Button> elementy, **OK** i **Anuluj**. Gdy użytkownik kliknie jeden z przycisków, formant wywołuje zdarzenie niestandardowe, aby zwrócić informacje do hosta.  
  
#### <a name="basic-layout"></a>Układ podstawowy  
 Różne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy są zawarte <xref:System.Windows.Controls.Grid> w elemencie. Można użyć <xref:System.Windows.Controls.Grid> , aby rozmieścić zawartość kontrolki złożonej w podobny sposób, jak `Table` używać elementu w kodzie HTML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ma <xref:System.Windows.Documents.Table> także element, ale <xref:System.Windows.Controls.Grid> jest bardziej lekki i lepszy dla prostych zadań układu.  
  
 Poniższy kod XAML pokazuje podstawowy układ. Ten kod XAML definiuje ogólną strukturę kontrolki, określając liczbę kolumn i wierszy w <xref:System.Windows.Controls.Grid> elemencie.  
  
 W MyControl1. XAML Zastąp istniejący kod XAML następującym XAML.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Dodawanie elementów TextBlock i TextBox do siatki  
 Aby umieścić [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] element w siatce, należy ustawić dla <xref:System.Windows.Controls.Grid.RowProperty> elementu i <xref:System.Windows.Controls.Grid.ColumnProperty> atrybutów odpowiedni numer wiersza i kolumny. Należy pamiętać, że numery wierszy i kolumn są numerowane od zera. Element może zawierać wiele kolumn, ustawiając jego <xref:System.Windows.Controls.Grid.ColumnSpanProperty> atrybut. Aby uzyskać więcej informacji <xref:System.Windows.Controls.Grid> o elementach, zobacz [Tworzenie elementu siatki](../controls/how-to-create-a-grid-element.md).  
  
 Poniższy kod XAML <xref:System.Windows.Controls.TextBox> pokazuje złożone kontrolki i <xref:System.Windows.Controls.TextBlock> elementy z ich <xref:System.Windows.Controls.Grid.RowProperty> atrybutami <xref:System.Windows.Controls.Grid.ColumnProperty> i, które są ustawione tak, aby elementy były prawidłowo umieszczane w siatce.  
  
 W pliku MyControl1. XAML Dodaj następujący kod XAML w obrębie <xref:System.Windows.Controls.Grid> elementu.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Określanie stylu elementów interfejsu użytkownika  
 Wiele elementów w formularzu wprowadzania danych ma podobny wygląd, co oznacza, że mają identyczne ustawienia dla kilku właściwości. Zamiast oddzielnie ustawić atrybuty każdego elementu, poprzedni kod XAML używa <xref:System.Windows.Style> elementów do definiowania standardowych ustawień właściwości dla klas elementów. Takie podejście zmniejsza złożoność kontrolki i umożliwia zmianę wyglądu wielu elementów za pomocą jednego atrybutu stylu.  
  
 Elementy są zawarte <xref:System.Windows.Controls.Grid> we <xref:System.Windows.FrameworkElement.Resources%2A> właściwości elementu, więc mogą być używane przez wszystkie elementy w formancie. <xref:System.Windows.Style> Jeśli styl ma nazwę, należy zastosować go do elementu przez dodanie <xref:System.Windows.Style> elementu zestawu do nazwy stylu. Style, które nie są nazwane, stają się stylem domyślnym elementu. Aby uzyskać więcej informacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na temat stylów, zobacz [Style i tworzenia szablonów](../controls/styling-and-templating.md).  
  
 Poniższy kod XAML pokazuje <xref:System.Windows.Style> elementy dla formantu złożonego. Aby zobaczyć, jak style są stosowane do elementów, zobacz poprzedni kod XAML. Na przykład ostatni <xref:System.Windows.Controls.TextBlock> element `inlineText` ma styl, a ostatni <xref:System.Windows.Controls.TextBox> element używa stylu domyślnego.  
  
 W MyControl1. XAML Dodaj następujący kod XAML zaraz po <xref:System.Windows.Controls.Grid> elemencie początkowym.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Dodawanie przycisków OK i Anuluj  
 Końcowymi elementami formantu złożonego są elementy **OK** i **Cancel** <xref:System.Windows.Controls.Button> , które zajmują pierwsze dwie kolumny ostatniego wiersza. <xref:System.Windows.Controls.Grid> Te elementy używają typowego programu obsługi `ButtonClicked`zdarzeń oraz stylu domyślnego <xref:System.Windows.Controls.Button> zdefiniowanego w poprzednim kodzie XAML.  
  
 W MyControl1. XAML Dodaj następujący kod XAML po ostatnim <xref:System.Windows.Controls.TextBox> elemencie. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Część kontrolki złożonej została ukończona.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Implementowanie pliku związanego z kodem  
 Plik związany z kodem, MyControl1.xaml.cs, implementuje trzy zasadnicze zadania:
  
1. Obsługuje zdarzenie, które występuje, gdy użytkownik kliknie jeden z przycisków.  
  
2. Pobiera dane z <xref:System.Windows.Controls.TextBox> elementów i umieszcza je w niestandardowym obiekcie argumentu zdarzenia.  
  
3. Podnosi zdarzenie niestandardowe `OnButtonClick` , które powiadamia hosta, że użytkownik zakończy pracę i przekazuje dane z powrotem do hosta.  
  
 Kontrolka udostępnia również szereg właściwości kolorów i czcionek, które umożliwiają zmianę wyglądu. W <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Controls.Panel.Background%2A> przeciwieństwie do klasy, która jest używana do hostowania formantu Windows Forms, Klasa uwidacznia tylko właściwość formantu. <xref:System.Windows.Forms.Integration.ElementHost> Aby zachować podobieństwo między tym przykładem kodu i przykładem opisanym [w przewodniku: Hosting Windows Formsego formantu złożonego w](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)WPF, formant uwidacznia pozostałe właściwości bezpośrednio.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Podstawowa struktura pliku związanego z kodem  
 Plik związany z kodem składa się z pojedynczej przestrzeni `MyControls`nazw, która będzie zawierać dwie klasy `MyControl1` , `MyControlEventArgs`i.  
  
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
  
 Pierwsza Klasa `MyControl1`,, jest klasą częściową zawierającą kod implementujący funkcje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zdefiniowane w MyControl1. XAML. Gdy MyControl1. XAML jest analizowany, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest konwertowany na tę samą klasę częściową, a dwie klasy częściowe są scalane w celu utworzenia skompilowanej kontrolki. Z tego powodu nazwa klasy w pliku związanym z kodem musi być zgodna z nazwą klasy przypisaną do MyControl1. XAML i musi dziedziczyć po elemencie głównym formantu. Druga klasa, `MyControlEventArgs`, jest klasą argumentów zdarzeń, która jest używana do wysyłania danych z powrotem do hosta.  
  
 Open MyControl1.xaml.cs. Zmień istniejącą deklarację klasy tak, aby miała następującą nazwę i dziedziczy z <xref:System.Windows.Controls.Grid>.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Inicjowanie kontrolki  
 Poniższy kod implementuje kilka podstawowych zadań:  
  
- Deklaruje zdarzenie prywatne, `OnButtonClick`i skojarzonego z nim delegata `MyControlEventHandler`,.  
  
- Tworzy kilka prywatnych zmiennych globalnych, które przechowują dane użytkownika. Te dane są udostępniane za poorednictwem odpowiednich właściwości.  
  
- Implementuje procedurę obsługi `Init`dla <xref:System.Windows.FrameworkElement.Loaded> zdarzenia kontrolki. Ta procedura obsługi inicjuje zmienne globalne, przypisując im wartości zdefiniowane w MyControl1. XAML. W tym celu używa <xref:System.Windows.FrameworkElement.Name%2A> przypisanego do typowego <xref:System.Windows.Controls.TextBlock> elementu `nameLabel`, aby uzyskać dostęp do ustawień właściwości tego elementu.  
  
 Usuń istniejący Konstruktor i Dodaj do swojej `MyControl1` klasy następujący kod.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Obsługa zdarzeń kliknięcia przycisku  
 Użytkownik wskazuje, że zadanie wprowadzania danych zostało zakończone, klikając przycisk **OK** lub przycisk **Anuluj** . Oba przyciski używają tego samego <xref:System.Windows.Controls.Primitives.ButtonBase.Click> programu obsługi zdarzeń `ButtonClicked`,. Oba przyciski mają nazwę lub `btnOK` `btnCancel`, która umożliwia programowi obsługi określenie, który przycisk został kliknięty, sprawdzając wartość `sender` argumentu. Program obsługi wykonuje następujące czynności:  
  
- Tworzy obiekt, który zawiera dane <xref:System.Windows.Controls.TextBox> z elementów. `MyControlEventArgs`  
  
- Jeśli użytkownik kliknął przycisk **Anuluj** , ustawia `MyControlEventArgs` `IsOK` właściwość obiektu na `false`.  
  
- `OnButtonClick` Podnosi zdarzenie, aby wskazać hostowi, że użytkownik zakończy pracę i przeszedł ponownie zebrane dane.  
  
 Dodaj następujący kod do `MyControl1` klasy `Init` po metodzie.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Tworzenie właściwości  
 Pozostała część klasy po prostu uwidacznia właściwości, które są zgodne z opisanymi wcześniej zmiennymi globalnymi. Gdy właściwość zostanie zmieniona, metoda dostępu set modyfikuje wygląd kontrolki, zmieniając odpowiednie właściwości elementu i aktualizując bazowe zmienne globalne.  
  
 Dodaj następujący kod do `MyControl1` klasy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Wysyłanie danych z powrotem do hosta  
 Końcowy składnik w pliku jest `MyControlEventArgs` klasą, która jest używana do wysyłania zebranych danych z powrotem do hosta.  
  
 Dodaj następujący kod do `MyControls` przestrzeni nazw. Implementacja jest prosta i nie została omówiona dokładniej.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Skompiluj rozwiązanie. Kompilacja spowoduje utworzenie biblioteki DLL o nazwie WebControls. dll.  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Implementowanie aplikacji hosta Windows Forms  
 Aplikacja hosta Windows Forms używa <xref:System.Windows.Forms.Integration.ElementHost> obiektu do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostowania złożonego formantu. Aplikacja obsługuje zdarzenie, `OnButtonClick` aby otrzymywać dane z formantu złożonego. Aplikacja ma również zestaw przycisków opcji, których można użyć do zmodyfikowania wyglądu kontrolki. Na poniższej ilustracji przedstawiono aplikację.  

Na poniższej ilustracji przedstawiono formant złożony WPF hostowany w aplikacji Windows Forms "  

 ![Scteenshot, w którym jest wyświetlany formant Avalon obsługujący formularz systemu Windows.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>Tworzenie projektu  
 Aby rozpocząć projekt:  
  
1. Uruchom [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]i Otwórz okno dialogowe **Nowy projekt** .  
  
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
  
3. W prawym górnym rogu formularza Dodaj <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> kontrolkę do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przechowywania złożonego formantu.  
  
4. Dodaj następujące <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> kontrolki do formularza.  
  
    |Nazwa|Tekst|  
    |----------|----------|  
    |groupBox1|Kolor tła|  
    |groupBox2|Kolor pierwszego planu|  
    |groupBox3|Rozmiar czcionki|  
    |groupBox4|Rodzina czcionek|  
    |groupBox5|Styl czcionki|  
    |groupBox6|Grubość czcionki|  
    |groupBox7|Dane z kontroli|  
  
5. Dodaj następujące <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> kontrolki <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> do kontrolek.  
  
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
    |groupBox5|radioStyleOriginal|Normalne|  
    |groupBox5|radioStyleItalic|Wyowietla|  
    |groupBox6|radioWeightOriginal|Oryginał|  
    |groupBox6|radioWeightBold|Zapis|  
  
6. Dodaj następujące <xref:System.Windows.Forms.Label?displayProperty=nameWithType> kontrolki do ostatniego <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>. Te kontrolki wyświetlają dane zwrócone przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formant złożony.  
  
    |GroupBox|Nazwa|Tekst|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Nazwij|  
    |groupBox7|lblAddress|Ulica:|  
    |groupBox7|lblCity|—|  
    |groupBox7|lblState|Państwu|  
    |groupBox7|lblZip|Kodu|  
  
### <a name="initializing-the-form"></a>Inicjowanie formularza  
 Na ogół implementujemy kod hostingu w programie obsługi <xref:System.Windows.Forms.Form.Load> zdarzeń formularza. Poniższy kod przedstawia <xref:System.Windows.Forms.Form.Load> procedurę obsługi zdarzeń, procedurę obsługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dla <xref:System.Windows.FrameworkElement.Loaded> zdarzenia kontrolki złożonej oraz deklaracje dla kilku zmiennych globalnych, które są używane później.  
  
 W Projektant formularzy systemu Windows kliknij dwukrotnie formularz, aby utworzyć <xref:System.Windows.Forms.Form.Load> procedurę obsługi zdarzeń. W górnej części Form1.cs Dodaj następujące `using` instrukcje.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Zastąp zawartość istniejącej `Form1` klasy następującym kodem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 Metoda w poprzednim kodzie przedstawia ogólną procedurę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostingu kontrolki: `Form1_Load`  
  
1. Utwórz nowy <xref:System.Windows.Forms.Integration.ElementHost> obiekt.  
  
2. Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość kontrolki na <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>wartość.  
  
3. Dodaj formant do kolekcji<xref:System.Windows.Forms.Control.Controls%2A>kontrolki. <xref:System.Windows.Forms.Panel> <xref:System.Windows.Forms.Integration.ElementHost>  
  
4. Utwórz wystąpienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.  
  
5. Hostować formant złożony w formularzu, przypisując formant do <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> właściwości kontrolki.  
  
 Pozostałe dwa wiersze w `Form1_Load` metodzie dołączają programy obsługi do dwóch zdarzeń kontroli:  
  
- `OnButtonClick`jest zdarzeniem niestandardowym, które jest wywoływane przez formant złożony, gdy użytkownik kliknie przycisk **OK** lub **Anuluj** . Możesz obsłużyć zdarzenie, aby uzyskać odpowiedź użytkownika i zebrać dane określone przez użytkownika.  
  
- <xref:System.Windows.FrameworkElement.Loaded>to zdarzenie standardowe wywoływane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolkę, gdy jest ona w pełni załadowana. To zdarzenie jest używane w tym miejscu, ponieważ przykład wymaga zainicjowania kilku zmiennych globalnych przy użyciu właściwości z formantu. W czasie trwania <xref:System.Windows.Forms.Form.Load> zdarzenia formularza formant nie jest w pełni załadowany i te wartości nadal są ustawione na `null`. Zanim będzie można uzyskać dostęp do tych właściwości <xref:System.Windows.FrameworkElement.Loaded> , musisz poczekać, aż wystąpi zdarzenie kontrolki.  
  
 Procedura <xref:System.Windows.FrameworkElement.Loaded> obsługi zdarzeń jest pokazana w poprzednim kodzie. `OnButtonClick` Program obsługi został omówiony w następnej sekcji.  
  
### <a name="handling-onbuttonclick"></a>Obsługa OnButtonClick  
 Zdarzenie występuje, gdy użytkownik kliknie przycisk **OK** lub **Anuluj.** `OnButtonClick`  
  
 Program obsługi zdarzeń sprawdza `IsOK` pole argumentu zdarzenia w celu określenia, który przycisk został kliknięty. Zmienne danych odpowiadają  formantom,którezostałyomówione<xref:System.Windows.Forms.Label>wcześniej. `lbl` Jeśli użytkownik kliknie przycisk **OK** , dane z <xref:System.Windows.Controls.TextBox> kontrolek kontrolki są przypisywane do odpowiedniej <xref:System.Windows.Forms.Label> kontrolki. Jeśli użytkownik kliknie **przycisk Anuluj**, <xref:System.Windows.Forms.Label.Text%2A> wartości są ustawiane na ciągi domyślne.  
  
 Dodaj poniższy przycisk, a `Form1` następnie kliknij polecenie kod obsługi zdarzeń w klasie.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Skompiluj i uruchom aplikację. Dodaj tekst do kontrolki złożonej WPF, a następnie kliknij przycisk **OK**. Tekst zostanie wyświetlony w etykietach. W tym momencie kod nie został dodany do obsługi przycisków radiowych.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Modyfikowanie wyglądu kontrolki  
 Kontrolki w formularzu umożliwią użytkownikowi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zmianę pierwszego planu i tła formantu złożonego oraz kilku właściwości czcionki. <xref:System.Windows.Forms.RadioButton> Kolor tła jest uwidaczniany przez <xref:System.Windows.Forms.Integration.ElementHost> obiekt. Pozostałe właściwości są ujawniane jako właściwości niestandardowe kontrolki.  
  
 Kliknij dwukrotnie każdy <xref:System.Windows.Forms.RadioButton> formant w formularzu, aby utworzyć <xref:System.Windows.Forms.RadioButton.CheckedChanged> programy obsługi zdarzeń. Zastąp programy obsługi zdarzeń poniższym kodem. <xref:System.Windows.Forms.RadioButton.CheckedChanged>  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Skompiluj i uruchom aplikację. Kliknij różne przyciski radiowe, aby zobaczyć efekt na formancie złożonym WPF.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Przewodnik: Hostowanie złożonego formantu Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: Hostowanie złożonej kontrolki WPF z 3-D w Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
