---
title: Hostowanie kontrolki złożonej WPF w formularzach systemu Windows
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: e3326f654e05ef7d487a76f076f8ad0da3637096
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187245"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>Wskazówki: Hosting złożonego formantu WPF w Windows Forms
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zapewnia bogate środowisko do tworzenia aplikacji. Jednak jeśli masz znaczne inwestycje w kod formularzy systemu Windows, może być [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bardziej skuteczne rozszerzenie istniejącej aplikacji Windows Forms, a nie przepisać go od podstaw. Typowym scenariuszem jest, gdy chcesz osadzić jeden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lub więcej formantów zaimplementowanych w aplikacji Windows Forms. Aby uzyskać więcej informacji na temat dostosowywania formantów WPF, zobacz [Dostosowywanie sterowania](../controls/control-customization.md).  
  
 W tym instruktażu zostanie przedstawiona aplikacja, która obsługuje formant [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożony w celu wykonania wprowadzania danych w aplikacji Windows Forms. Formant złożony jest pakowany w bibliotekę DLL. Tę ogólną procedurę można rozszerzyć na bardziej złożone aplikacje i formanty. Ten przewodnik ma być prawie identyczny pod względem wyglądu i funkcjonalności do [przewodnika: Hosting form systemu Windows Composite Control w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md). Podstawową różnicą jest to, że scenariusz hostingu jest odwrócony.  
  
 Instruktaż jest podzielony na dwie sekcje. W pierwszej sekcji pokrótce opisano implementację formantu złożonego. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] W drugiej sekcji szczegółowo omówiono sposób hostowanie formantu złożonego w aplikacji Windows Forms, odbieranie zdarzeń z formantu i dostęp do niektórych właściwości formantu.  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
- Implementowanie kontroli złożonej WPF.  
  
- Implementowanie aplikacji hosta formularzy systemu Windows.  
  
 Aby uzyskać pełną listę kodów zadań zilustrowanych w tym instruktażu, zobacz [Hosting formantu złożonego WPF w przykładzie formularzy systemu Windows](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WindowsFormsHostingWpfControl).  
  
## <a name="prerequisites"></a>Wymagania wstępne  

Program Visual Studio musi ukończyć ten instruktaż.  
  
## <a name="implementing-the-wpf-composite-control"></a>Implementowanie kontroli złożonej WPF  
 Formant [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożony używany w tym przykładzie jest prosty formularz wprowadzania danych, który przyjmuje nazwę użytkownika i adres. Gdy użytkownik kliknie jeden z dwóch przycisków, aby wskazać, że zadanie zostało zakończone, formant wywołuje zdarzenie niestandardowe, aby zwrócić te informacje do hosta. Na poniższej ilustracji przedstawiono renderowany formant.

 Na poniższej ilustracji przedstawiono formant kompozytowy WPF:

 ![Zrzut ekranu, który pokazuje prosty formant WPF.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>Tworzenie projektu  
 Aby rozpocząć projekt:  
  
1. Uruchom program Visual Studio i otwórz okno dialogowe **Nowy projekt.**  
  
2. W języku Visual C# i kategorii systemu Windows wybierz szablon **biblioteki kontroli użytkownika WPF.**  
  
3. Nazwij `MyControls`nowy projekt .  
  
4. W przypadku lokalizacji określ dogodnie nazwany `WindowsFormsHostingWpfControl`folder najwyższego poziomu, taki jak . Później umieścisz aplikację hosta w tym folderze.  
  
5. Kliknij przycisk **OK**, aby utworzyć projekt. Domyślny projekt zawiera jeden `UserControl1`formant o nazwie .  
  
6. W Eksploratorze `UserControl1` `MyControl1`rozwiązań zmień nazwę na .  
  
 Projekt powinien mieć odwołania do następujących bibliotek DLL systemu. Jeśli którakolwiek z tych bibliotek DLL nie jest domyślnie uwzględniona, dodaj je do projektu.  
  
- PrezentacjaCore  
  
- PresentationFramework (Ramwork prezentacji)  
  
- System  
  
- Windowsbase  
  
### <a name="creating-the-user-interface"></a>Tworzenie interfejsu użytkownika  
 Dla [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] sterowania kompozytowego [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]jest realizowany z . Sterowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kompozytowe składa się z pięciu <xref:System.Windows.Controls.TextBox> elementów. Każdy <xref:System.Windows.Controls.TextBox> element ma <xref:System.Windows.Controls.TextBlock> skojarzony element, który służy jako etykieta. Na dole <xref:System.Windows.Controls.Button> znajdują się dwa elementy: **OK** i **Anuluj**. Gdy użytkownik kliknie dowolny przycisk, formant wywołuje zdarzenie niestandardowe, aby zwrócić informacje do hosta.  
  
#### <a name="basic-layout"></a>Układ podstawowy  
 Różne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy są zawarte <xref:System.Windows.Controls.Grid> w elemencie. Zawartość formantu złożonego służy <xref:System.Windows.Controls.Grid> do rozmieszczenia zawartości formantu złożonego `Table` w taki sam sposób, w jaki można użyć elementu w formacie HTML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]również ma <xref:System.Windows.Documents.Table> element, <xref:System.Windows.Controls.Grid> ale jest bardziej lekki i lepiej nadaje się do prostych zadań układu.  
  
 Poniższy kod XAML przedstawia podstawowy układ. Ten kod XAML definiuje ogólną strukturę formantu, określając liczbę <xref:System.Windows.Controls.Grid> kolumn i wierszy w elemencie.  
  
 W pliku MyControl1.xaml zastąp istniejący kod XAML następującym kodem XAML.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Dodawanie elementów TextBlock i TextBox do siatki  
 Element należy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] umieścić w siatce, <xref:System.Windows.Controls.Grid.RowProperty> <xref:System.Windows.Controls.Grid.ColumnProperty> ustawiając element i atrybuty na odpowiedni numer wiersza i kolumny. Należy pamiętać, że numerowanie wierszy i kolumn jest oparte na wartości zero. Można mieć element obejmuje wiele kolumn, <xref:System.Windows.Controls.Grid.ColumnSpanProperty> ustawiając jego atrybut. Aby uzyskać <xref:System.Windows.Controls.Grid> więcej informacji o elementach, zobacz [Tworzenie elementu siatki](../controls/how-to-create-a-grid-element.md).  
  
 Poniższy kod XAML przedstawia <xref:System.Windows.Controls.TextBox> formant złożony i <xref:System.Windows.Controls.TextBlock> elementy z ich <xref:System.Windows.Controls.Grid.RowProperty> i <xref:System.Windows.Controls.Grid.ColumnProperty> atrybutów, które są ustawione, aby umieścić elementy poprawnie w siatce.  
  
 W pliku MyControl1.xaml dodaj następujący kod <xref:System.Windows.Controls.Grid> XAML w elemencie.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Stylizacja elementów interfejsu użytkownika  
 Wiele elementów w formularzu wprowadzania danych mają podobny wygląd, co oznacza, że mają identyczne ustawienia dla kilku ich właściwości. Zamiast ustawiać atrybuty każdego elementu oddzielnie, poprzedni <xref:System.Windows.Style> XAML używa elementów do definiowania standardowych ustawień właściwości dla klas elementów. Takie podejście zmniejsza złożoność formantu i umożliwia zmianę wyglądu wielu elementów za pomocą atrybutu pojedynczego stylu.  
  
 Elementy <xref:System.Windows.Style> są zawarte we <xref:System.Windows.Controls.Grid> <xref:System.Windows.FrameworkElement.Resources%2A> właściwości elementu, dzięki czemu mogą być używane przez wszystkie elementy w formancie. Jeśli styl jest nazwany, należy zastosować go <xref:System.Windows.Style> do elementu, dodając element ustawiony do nazwy stylu. Style, które nie są nazwane, stają się domyślnym stylem elementu. Aby uzyskać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] więcej informacji o stylach, zobacz [Stylowanie i tworzenie szablonów](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
 Poniższy kod XAML przedstawia <xref:System.Windows.Style> elementy formantu złożonego. Aby zobaczyć, jak style są stosowane do elementów, zobacz poprzedni kod XAML. Na przykład ostatni <xref:System.Windows.Controls.TextBlock> element `inlineText` ma styl, <xref:System.Windows.Controls.TextBox> a ostatni element używa stylu domyślnego.  
  
 W myControl1.xaml dodaj następujący kod XAML zaraz po elemencie początkowym. <xref:System.Windows.Controls.Grid>  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Dodawanie przycisków OK i Anuluj  
 Końcowe elementy na kontrolce złożonej są **OK** i **Anuluj** <xref:System.Windows.Controls.Button> elementów, <xref:System.Windows.Controls.Grid>które zajmują pierwsze dwie kolumny ostatniego wiersza . Te elementy używają wspólnego `ButtonClicked`programu obsługi <xref:System.Windows.Controls.Button> zdarzeń i domyślnego stylu zdefiniowanego w poprzednim XAML.  
  
 W myControl1.xaml dodaj następujący kod XAML po ostatnim <xref:System.Windows.Controls.TextBox> elemencie. Część [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] formantu złożonego została ukończona.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Implementowanie pliku zakodowego  
 Plik związany z kodem, MyControl1.xaml.cs, implementuje trzy podstawowe zadania:
  
1. Obsługuje zdarzenie, które występuje, gdy użytkownik kliknie jeden z przycisków.  
  
2. Pobiera dane z <xref:System.Windows.Controls.TextBox> elementów i pakuje je w obiekcie argumentu zdarzenia niestandardowego.  
  
3. Wywołuje zdarzenie `OnButtonClick` niestandardowe, które powiadamia hosta, że użytkownik jest gotowy i przekazuje dane z powrotem do hosta.  
  
 Formant udostępnia również szereg właściwości koloru i czcionki, które umożliwiają zmianę wyglądu. W <xref:System.Windows.Forms.Integration.WindowsFormsHost> przeciwieństwie do klasy, która jest używana <xref:System.Windows.Forms.Integration.ElementHost> do hosta formantu Windows Forms, klasa udostępnia tylko <xref:System.Windows.Controls.Panel.Background%2A> właściwości formantu. Aby zachować podobieństwo między tym przykładem kodu i przykład omówione w [przewodniku: Hosting Windows Forms Composite Control w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md), formant udostępnia pozostałe właściwości bezpośrednio.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Podstawowa struktura pliku zakodowego  
 Plik związany z kodem składa się `MyControls`z jednego obszaru `MyControl1` nazw, który będzie zawierał dwie klasy i `MyControlEventArgs`.  
  
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
  
 Pierwsza klasa `MyControl1`, jest klasą częściową zawierającą kod, który [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] implementuje funkcjonalność zdefiniowanego w MyControl1.xaml. Gdy MyControl1.xaml jest analizowany, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest konwertowany do tej samej klasy częściowej, a dwie klasy częściowe są scalane w celu utworzenia skompilowanego formantu. Z tego powodu nazwa klasy w pliku związanym z kodem musi być zgodna z nazwą klasy przypisaną do myControl1.xaml i musi dziedziczyć z głównego elementu formantu. Druga klasa `MyControlEventArgs`, jest klasą argumentów zdarzeń, która jest używana do wysyłania danych z powrotem do hosta.  
  
 Otwórz MyControl1.xaml.cs. Zmień istniejącą deklarację klasy tak, aby ma <xref:System.Windows.Controls.Grid>następującą nazwę i dziedziczyła z .  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Inicjowanie formantu  
 Poniższy kod implementuje kilka podstawowych zadań:  
  
- Deklaruje zdarzenie `OnButtonClick`prywatne i jego skojarzonego `MyControlEventHandler`pełnomocnika .  
  
- Tworzy kilka prywatnych zmiennych globalnych, które przechowują dane użytkownika. Te dane są udostępniane za pośrednictwem odpowiednich właściwości.  
  
- Implementuje program `Init`obsługi, dla <xref:System.Windows.FrameworkElement.Loaded> zdarzenia formantu. Ten program obsługi inicjuje zmienne globalne, przypisując im wartości zdefiniowane w pliku MyControl1.xaml. Aby to zrobić, używa <xref:System.Windows.FrameworkElement.Name%2A> przypisany do <xref:System.Windows.Controls.TextBlock> typowego elementu, `nameLabel`aby uzyskać dostęp do ustawień właściwości tego elementu.  
  
 Usuń istniejący konstruktor i dodaj `MyControl1` następujący kod do klasy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Obsługa zdarzeń kliknięcia przycisków  
 Użytkownik wskazuje, że zadanie wprowadzania danych zostało zakończone przez kliknięcie przycisku **OK** lub przycisku **Anuluj.** Oba przyciski <xref:System.Windows.Controls.Primitives.ButtonBase.Click> używają tego `ButtonClicked`samego programu obsługi zdarzeń, . Oba przyciski mają `btnOK` `btnCancel`nazwę lub , który umożliwia programowi obsługi, aby określić, który przycisk został kliknięty przez badanie wartości argumentu. `sender` Program obsługi wykonuje następujące czynności:  
  
- Tworzy `MyControlEventArgs` obiekt, który zawiera <xref:System.Windows.Controls.TextBox> dane z elementów.  
  
- Jeśli użytkownik kliknął przycisk **Anuluj,** ustawia `MyControlEventArgs` `IsOK` właściwość obiektu na `false`.  
  
- Wywołuje zdarzenie, `OnButtonClick` aby wskazać do hosta, że użytkownik jest gotowy i przekazuje z powrotem zebrane dane.  
  
 Dodaj następujący kod `MyControl1` do klasy, `Init` po metodzie.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Tworzenie właściwości  
 Pozostała część klasy po prostu udostępnia właściwości, które odpowiadają zmiennym globalnym omówione wcześniej. Gdy właściwość się zmienia, set akcesor modyfikuje wygląd formantu, zmieniając odpowiednie właściwości elementu i aktualizując podstawowe zmienne globalne.  
  
 Dodaj następujący kod `MyControl1` do swojej klasy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Wysyłanie danych z powrotem do hosta  
 Ostatnim składnikiem w pliku `MyControlEventArgs` jest klasa, która jest używana do wysyłania zebranych danych z powrotem do hosta.  
  
 Dodaj następujący kod `MyControls` do obszaru nazw. Wdrożenie jest proste i nie jest dalej omawiane.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Skompiluj rozwiązanie. Kompilacja będzie produkować bibliotekę DLL o nazwie MyControls.dll.  
  
<a name="winforms_host_section"></a>
## <a name="implementing-the-windows-forms-host-application"></a>Implementowanie aplikacji hosta formularzy systemu Windows  
 Aplikacja hosta formularzy <xref:System.Windows.Forms.Integration.ElementHost> systemu Windows [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa obiektu do obsługi formantu złożonego. Aplikacja obsługuje zdarzenie, `OnButtonClick` aby odebrać dane z kontroli złożonej. Aplikacja posiada również zestaw przycisków opcji, których można użyć do modyfikowania wyglądu formantu. Na poniższej ilustracji przedstawiono aplikację.  

Na poniższej ilustracji przedstawiono formant złożony WPF hostowany w aplikacji Windows Forms"  

 ![Scteenshot, który pokazuje formę Hostingu formularzy systemu Windows Avalon.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>Tworzenie projektu  
 Aby rozpocząć projekt:  
  
1. Uruchom program Visual Studio i otwórz okno dialogowe **Nowy projekt.**  
  
2. W języku Visual C# i kategorii systemu Windows wybierz szablon **aplikacji formularzy systemu Windows.**  
  
3. Nazwij `WFHost`nowy projekt .  
  
4. Dla lokalizacji należy określić ten sam folder najwyższego poziomu, który zawiera projekt MyControls.  
  
5. Kliknij przycisk **OK**, aby utworzyć projekt.  
  
 Należy również dodać odwołania do biblioteki `MyControl1` DLL, która zawiera i innych zestawów.  
  
1. Kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań, a następnie wybierz polecenie **Dodaj odwołanie**.  
  
2. Kliknij kartę **Przeglądaj** i przejdź do folderu zawierającego plik MyControls.dll. W tym instruktażu ten folder to MyControls\bin\Debug.  
  
3. Wybierz pozycję MyControls.dll, a następnie kliknij przycisk **OK**.  
  
4. Dodaj odwołania do następujących zestawów.  
  
    - PrezentacjaCore  
  
    - PresentationFramework (Ramwork prezentacji)  
  
    - System.xaml  
  
    - Windowsbase  
  
    - Integracja z formami systemu Windows  
  
### <a name="implementing-the-user-interface-for-the-application"></a>Implementowanie interfejsu użytkownika dla aplikacji  
 Interfejs użytkownika aplikacji formularza systemu Windows zawiera kilka formantów do interakcji z formantem złożonym WPF.  
  
1. Otwórz formę1 w Projektancie formularzy systemu Windows.  
  
2. Powiększ formularz, aby pomieścić formanty.  
  
3. W prawym górnym rogu formularza dodaj <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> formant, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aby utrzymać formant złożony.  
  
4. Dodaj następujące <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> formanty do formularza.  
  
    |Nazwa|Tekst|  
    |----------|----------|  
    |skrzynka grupy1|Kolor tła|  
    |skrzynka grupy2|Kolor pierwszego planu|  
    |skrzynka grupy3|Rozmiar czcionki|  
    |skrzynka grupy4|Rodzina czcionek|  
    |skrzynka grupowa5|Styl czcionki|  
    |skrzynka grupowa6|Waga czcionki|  
    |skrzynka grupy7|Dane z kontroli|  
  
5. Dodaj następujące <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> kontrolki do formantów. <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>  
  
    |GroupBox|Nazwa|Tekst|  
    |--------------|----------|----------|  
    |skrzynka grupy1|radioBackgroundOryginalny|Oryginał|  
    |skrzynka grupy1|radioBackgroundLightGreen|LightGreen (Zielony)|  
    |skrzynka grupy1|radioBackgroundLightSalmon|LightSalmon (Leksalmon)|  
    |skrzynka grupy2|radioForegroundOryginalny|Oryginał|  
    |skrzynka grupy2|radioForegroundRed|Red|  
    |skrzynka grupy2|radioForegroundJellow|Yellow|  
    |skrzynka grupy3|radioSizeOryginalny|Oryginał|  
    |skrzynka grupy3|radioSizeTen|10|  
    |skrzynka grupy3|radioSizeTwelve|12|  
    |skrzynka grupy4|radioRodzina oryginalna|Oryginał|  
    |skrzynka grupy4|radioFamilyTimes|Czasy Nowy Roman|  
    |skrzynka grupy4|radioFamilyWingDings|Wingdings|  
    |skrzynka grupowa5|radioStyleoryginalne|Normalne|  
    |skrzynka grupowa5|radioStyleItalic|Kursywa|  
    |skrzynka grupowa6|radioWeightOryginalny|Oryginał|  
    |skrzynka grupowa6|radioWeightBold|Pogrubienie|  
  
6. Dodaj następujące <xref:System.Windows.Forms.Label?displayProperty=nameWithType> kontrolki <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>do ostatniego . Te formanty wyświetlają [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dane zwrócone przez formant złożony.  
  
    |GroupBox|Nazwa|Tekst|  
    |--------------|----------|----------|  
    |skrzynka grupy7|lblName|Nazwa:|  
    |skrzynka grupy7|lblAddress|Adres ulicy:|  
    |skrzynka grupy7|lblCity (niem.|Miasta:|  
    |skrzynka grupy7|lblPaństwo|Państwa:|  
    |skrzynka grupy7|lblZip|Zip:|  
  
### <a name="initializing-the-form"></a>Inicjowanie formularza  
 Zazwyczaj implementujesz kod hostingu w <xref:System.Windows.Forms.Form.Load> programie obsługi zdarzeń formularza. Poniższy kod <xref:System.Windows.Forms.Form.Load> przedstawia program obsługi zdarzeń, program obsługi dla zdarzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantu złożonego <xref:System.Windows.FrameworkElement.Loaded> i deklaracje dla kilku zmiennych globalnych, które są używane później.  
  
 W projektancie formularzy systemu Windows kliknij <xref:System.Windows.Forms.Form.Load> dwukrotnie formularz, aby utworzyć program obsługi zdarzeń. W górnej części Form1.cs dodaj następujące `using` instrukcje.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Zastąp zawartość `Form1` istniejącej klasy następującym kodem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 Metoda `Form1_Load` w poprzednim kodzie pokazuje ogólną [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procedurę hostowania formantu:  
  
1. Utwórz <xref:System.Windows.Forms.Integration.ElementHost> nowy obiekt.  
  
2. Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość formantu na <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>.  
  
3. Dodaj <xref:System.Windows.Forms.Integration.ElementHost> formant <xref:System.Windows.Forms.Panel> do kolekcji <xref:System.Windows.Forms.Control.Controls%2A> formantu.  
  
4. Utwórz wystąpienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantu.  
  
5. Hosta kontrolki złożonej w formularzu, przypisując formant do <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> właściwości formantu.  
  
 Pozostałe dwa wiersze `Form1_Load` w metodzie dołączyć programy obsługi do dwóch zdarzeń kontroli:  
  
- `OnButtonClick`jest zdarzeniem niestandardowym, które jest uruchamiane przez formant złożony, gdy użytkownik kliknie przycisk **OK** lub **Anuluj.** Obsługiwane zdarzenia, aby uzyskać odpowiedź użytkownika i zbierać wszelkie dane, które użytkownik określony.  
  
- <xref:System.Windows.FrameworkElement.Loaded>jest zdarzeniem standardowym, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] które jest wywoływane przez formant, gdy jest w pełni załadowany. Zdarzenie jest używane w tym miejscu, ponieważ przykład musi zainicjować kilka zmiennych globalnych przy użyciu właściwości z formantu. W momencie <xref:System.Windows.Forms.Form.Load> zdarzenia formularza formant nie jest w pełni załadowany, `null`a te wartości są nadal ustawione na . Należy poczekać, aż <xref:System.Windows.FrameworkElement.Loaded> wystąpi zdarzenie formantu, zanim będzie można uzyskać dostęp do tych właściwości.  
  
 Program <xref:System.Windows.FrameworkElement.Loaded> obsługi zdarzeń jest wyświetlany w poprzednim kodzie. Program `OnButtonClick` obsługi jest omówiony w następnej sekcji.  
  
### <a name="handling-onbuttonclick"></a>Obsługa OnButtonClick  
 Zdarzenie `OnButtonClick` występuje, gdy użytkownik kliknie przycisk **OK** lub **Anuluj.**  
  
 Program obsługi zdarzeń sprawdza `IsOK` pole argumentu zdarzenia, aby określić, który przycisk został kliknięty. Zmienne danych odpowiadają <xref:System.Windows.Forms.Label> formantom, które zostały omówione wcześniej. *data* `lbl` Jeśli użytkownik kliknie przycisk **OK,** dane z <xref:System.Windows.Controls.TextBox> formantów formantu są przypisywane do odpowiedniego <xref:System.Windows.Forms.Label> formantu. Jeśli użytkownik kliknie <xref:System.Windows.Forms.Label.Text%2A> **przycisk Anuluj,** wartości są ustawione na domyślne ciągi.  
  
 Dodaj następujący przycisk kliknij kod `Form1` obsługi zdarzeń do klasy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Skompiluj i uruchom aplikację. Dodaj tekst w formancie złożonym WPF, a następnie kliknij przycisk **OK**. Tekst pojawi się na etykietach. W tym momencie kod nie został dodany do obsługi przycisków radiowych.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Modyfikowanie wyglądu formantu  
 Formanty <xref:System.Windows.Forms.RadioButton> w formularzu umożliwią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użytkownikowi zmianę kolorów pierwszego planu i tła formantu złożonego, a także kilku właściwości czcionki. Kolor tła jest <xref:System.Windows.Forms.Integration.ElementHost> narażony przez obiekt. Pozostałe właściwości są udostępniane jako właściwości niestandardowe formantu.  
  
 Kliknij dwukrotnie <xref:System.Windows.Forms.RadioButton> każdy formant w <xref:System.Windows.Forms.RadioButton.CheckedChanged> formularzu, aby utworzyć programy obsługi zdarzeń. Zastąp <xref:System.Windows.Forms.RadioButton.CheckedChanged> programy obsługi zdarzeń następującym kodem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Skompiluj i uruchom aplikację. Kliknij różne przyciski radiowe, aby zobaczyć wpływ na formant złożony WPF.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Wskazówki: Hosting złożonego formantu 3D WPF w Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
