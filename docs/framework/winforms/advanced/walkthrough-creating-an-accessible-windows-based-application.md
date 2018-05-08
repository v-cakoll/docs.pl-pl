---
title: 'Wskazówki: tworzenie dostępnej aplikacji bazującej na systemie Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: 6c798d0f6a454c7ee819d5556970bca12f1812e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a>Wskazówki: tworzenie dostępnej aplikacji bazującej na systemie Windows
Tworzenie aplikacji dostępny implikacje ważnymi. Wiele rządy ma przepisy dotyczące ułatwień dostępu dla zakupów oprogramowania. Logo Certified for Windows zawiera wymagania dotyczące ułatwień dostępu. Szacowany mieszkańców 30 milionów intruzowi US, ile z nich potencjalnych klientów, mają wpływu na dostępność oprogramowania.  
  
 W tym przewodniku zajmie się pięć wymagania związane z dostępem do logo Certified for Windows. Zgodnie z tych wymagań będzie dostępny aplikacji:  
  
-   Obsługuje rozmiar panelu sterowania, kolorów, czcionki i wprowadź ustawienia. Paska menu, paska tytułu, obramowania i paska stanu spowoduje wszystkie zmiany rozmiaru się gdy użytkownik zmieni ustawienia Panelu sterowania. W tej aplikacji nie są konieczne nie dodatkowe zmiany do formantów lub kodu.  
  
-   Obsługuje tryb dużego kontrastu.  
  
-   Podaj klawiaturę udokumentowaną dostęp do wszystkich funkcji.  
  
-   Udostępnianie lokalizacji fokus klawiatury ModelID.  
  
-   Unikaj przekazywania ważnych informacji przez samego dźwięku.  
  
 Aby uzyskać więcej informacji, zobacz [zasoby do projektowania dostępnych aplikacji](/visualstudio/ide/reference/resources-for-designing-accessible-applications).  
  
 Aby uzyskać informacje dotyczące obsługi różnych układów klawiatury, zobacz [najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych](../../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 W tym przewodniku tworzy interfejsu użytkownika dla aplikacji, która przyjmuje pizza zleceń. Składa się z <xref:System.Windows.Forms.TextBox> dla nazwy klienta <xref:System.Windows.Forms.RadioButton> grupy, aby wybrać rozmiar pizza <xref:System.Windows.Forms.CheckedListBox> doboru toppings dwóch formantów przycisk etykietą kolejności i Anuluj i Menu za pomocą wiersza polecenia zakończenia.  
  
 Użytkownik wprowadza nazwę klienta, rozmiar pizza i toppings potrzeby. Gdy użytkownik kliknie przycisk kolejność, podsumowanie kolejność i jego koszty są wyświetlane w oknie komunikatu i formanty są wyczyszczone i jest gotowa do następnej kolejności. Gdy użytkownik kliknie przycisk Anuluj, formanty są wyczyszczone i jest gotowa do następnej kolejności. Po kliknięciu elementu menu zakończenia zamyka program.  
  
 Nacisk ten przewodnik nie jest kod systemu kolejności detaliczne, ale ułatwień dostępu interfejsu użytkownika. Funkcje ułatwień dostępu w kilku często używanych formantów, w tym przyciski, przyciski radiowe pola tekstowe i etykiety przedstawiono wskazówki.  
  
#### <a name="to-begin-making-the-application"></a>Aby rozpocząć tworzenie aplikacji  
  
-   Utwórz nową aplikację systemu Windows w języku Visual Basic lub Visual C#. Nazwij projekt **PizzaOrder**. (Aby uzyskać więcej informacji, zobacz [tworzenie nowych rozwiązań i projektów](/visualstudio/ide/creating-solutions-and-projects).)  
  
## <a name="adding-the-controls-to-the-form"></a>Dodawanie formantów do formularza  
 Gdy dodawanie formantów do formularza, należy pamiętać, aby aplikacja dostępne poniższe wskazówki:  
  
-   Ustaw <xref:System.Windows.Forms.Control.AccessibleDescription%2A> i <xref:System.Windows.Forms.Control.AccessibleName%2A> właściwości. W tym przykładzie ustawienie domyślne <xref:System.Windows.Forms.Control.AccessibleRole%2A> jest wystarczająca. Aby uzyskać więcej informacji na temat właściwości ułatwień dostępu, zobacz [dostarczanie informacji dotyczących ułatwień dostępu dla formantów w formularzu systemu Windows](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md).  
  
-   Ustaw rozmiar czcionki, do 10 punktów lub większy.  
  
    > [!NOTE]
    >  Jeśli ustawisz rozmiar czcionki w postaci 10 podczas uruchamiania, wszystkie formanty dodane do formularza będzie mieć rozmiar czcionki 10.  
  
-   Upewnij się, że wszelkie formant etykiety, który opisuje kontrolki pola tekstowego bezpośrednio poprzedza formantu TextBox w kolejności tabulacji.  
  
-   Dodaj klucz dostępu za pomocą znaku "&", do <xref:System.Windows.Forms.Control.Text%2A> żadnego formantu, użytkownik może chcieć przejdź do właściwości.  
  
-   Dodaj klucz dostępu za pomocą znaku "&", do <xref:System.Windows.Forms.Control.Text%2A> właściwości poprzedzający formant, który użytkownik może chcieć przejdź do etykiety. Ustaw etykiet <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwości `true`, dzięki czemu fokus jest ustawiony do następnego formantu w kolejności tabulacji, gdy użytkownik naciśnie klawisz dostępu.  
  
-   Dodaj klucze dostępu do wszystkich elementów menu.  
  
#### <a name="to-make-your-windows-application-accessible"></a>Aby udostępnić aplikację systemu Windows  
  
-   Dodawanie formantów do formularza i ustaw właściwości, zgodnie z poniższym opisem. Zobacz obraz na koniec tabeli dla modeli sposób rozmieszczenia kontrolek w formularzu.  
  
    |Obiekt|Właściwość|Wartość|  
    |------------|--------------|-----------|  
    |Form1|AccessibleDescription|Formularz zamówienia|  
    ||AccessibleName|Formularz zamówienia|  
    ||Rozmiar czcionki|10|  
    ||Tekst|Formularz zamawiania pizzy|  
    |PictureBox|Nazwa|logo|  
    ||AccessibleDescription|Wycinek pizza|  
    ||AccessibleName|Logo firmy|  
    ||Obraz|Wszystkie ikony lub mapy bitowej|  
    |Etykieta|Nazwa|companyLabel|  
    ||Tekst|Dobrym Pizza|  
    ||TabIndex|1|  
    ||AccessibleDescription|Nazwa firmy|  
    ||AccessibleName|Nazwa firmy|  
    ||Kolor tła|niebieski|  
    ||ForeColor|żółty|  
    ||Rozmiar czcionki|18|  
    |Etykieta|Nazwa|customerLabel|  
    ||Tekst|& Nazwa|  
    ||TabIndex|2|  
    ||AccessibleDescription|Etykieta nazwy klienta|  
    ||AccessibleName|Etykieta nazwy klienta|  
    ||UseMnemonic|True|  
    |TextBox|Nazwa|CustomerName|  
    ||Tekst|(Brak)|  
    ||TabIndex|3|  
    ||AccessibleDescription|Nazwa klienta|  
    ||AccessibleName|Nazwa klienta|  
    |GroupBox|Nazwa|sizeOptions|  
    ||AccessibleDescription|Opcje rozmiaru pizza|  
    ||AccessibleName|Opcje rozmiaru pizza|  
    ||Tekst|Rozmiar pizza|  
    ||TabIndex|4|  
    |RadioButton|Nazwa|smallPizza|  
    ||Tekst|& małe $6,00|  
    ||Zaznaczone|True|  
    ||TabIndex|0|  
    ||AccessibleDescription|Mała pizza|  
    ||AccessibleName|Mała pizza|  
    |RadioButton|Nazwa|largePizza|  
    ||Tekst|& dużych $10,00|  
    ||TabIndex|1|  
    ||AccessibleDescription|Wielka pizza|  
    ||AccessibleName|Wielka pizza|  
    |Etykieta|Nazwa|toppingsLabel|  
    ||Tekst|& toppings ($0,75 każdego)|  
    ||TabIndex|5|  
    ||AccessibleDescription|Etykieta toppings|  
    ||AccessibleName|Etykieta toppings|  
    ||UseMnemonic|True|  
    |CheckedListBox —|Nazwa|toppings|  
    ||TabIndex|6|  
    ||AccessibleDescription|Dostępne toppings|  
    ||AccessibleName|Dostępne toppings|  
    ||Elementy|Pepperoni, produkcji kiełbas, grzyby|  
    |Przycisk|Nazwa|kolejność|  
    ||Tekst|& kolejności|  
    ||TabIndex|7|  
    ||AccessibleDescription|Łączna liczba kolejności|  
    ||AccessibleName|Kolejność|  
    |Przycisk|Nazwa|Anuluj|  
    ||Tekst|& Anuluj|  
    ||TabIndex|8|  
    ||AccessibleDescription|Anulowanie zamówienia|  
    ||AccessibleName|Anulowanie zlecenia|  
    |MainMenu —|Nazwa|theMainMenu|  
    |Element MenuItem|Nazwa|fileCommands|  
    ||Tekst|& pliku|  
    |Element MenuItem|Nazwa|exitApp|  
    ||Tekst|& Zakończ|  
  
     ![Formularz zamawiania pizzy](../../../../docs/framework/winforms/advanced/media/vbpizzaorderform.gif "vbPizzaOrderForm")  
Formularz będzie wyglądać jak poniżej:  
  
## <a name="supporting-high-contrast-mode"></a>Obsługa w trybie dużego kontrastu  
 Wysoki kontrast tryb jest ustawienie systemu Windows, które poprawia czytelność przy użyciu wyraźnych kolorów i rozmiary czcionek, które są przydatne dla użytkowników niedowidzących. <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Właściwość jest udostępniana do określenia, czy ustawiono tryb dużego kontrastu.  
  
 Jeśli jest SystemInformation.HighContrast `true`, powinien aplikacji:  
  
-   Wyświetl wszystkie elementy interfejsu użytkownika przy użyciu schemat kolorów systemu  
  
-   Przekazuje za pomocą wizualnych lub dźwięk wszystkie informacje, które jest przekazywany za pomocą kolorów. Na przykład jeśli wyróżniania elementów określonej listy przy użyciu czcionki czerwony, można również dodaniu pogrubioną czcionką, tak, aby użytkownik miał wskazówki-color wyróżniono elementy.  
  
-   Pomiń wszystkie obrazy lub wzorce pod tekstem  
  
 Aplikacja ma sprawdzać ustawienie <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> po aplikacji uruchamia i odpowiadać na zdarzenie systemowe <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>. <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Zdarzenie jest wywoływane zawsze, gdy wartość <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> zmiany.  
  
 W naszej aplikacji jest jedynym elementem, który nie używa systemowe ustawienia koloru `lblCompanyName`. <xref:System.Drawing.SystemColors> Klasa jest używana do zmiany ustawień kolor etykiety kolory wybrane przez użytkownika systemu.  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a>Aby włączyć tryb dużego kontrastu w sposób  
  
1.  Tworzenie metody, aby ustawić kolory etykiety do kolorów systemu.  
  
    ```  
    ' Visual Basic  
    Private Sub SetColorScheme()  
       If SystemInformation.HighContrast Then  
          companyLabel.BackColor = SystemColors.Window  
          companyLabel.ForeColor = SystemColors.WindowText  
       Else  
          companyLabel.BackColor = Color.Blue  
          companyLabel.ForeColor = Color.Yellow  
       End If  
    End Sub  
  
    // C#  
    private void SetColorScheme()  
    {  
       if (SystemInformation.HighContrast)  
       {  
          companyLabel.BackColor = SystemColors.Window;  
          companyLabel.ForeColor = SystemColors.WindowText;  
       }  
       else  
       {  
          companyLabel.BackColor = Color.Blue;  
          companyLabel.ForeColor = Color.Yellow;  
       }  
    }  
    ```  
  
2.  Wywołanie `SetColorScheme` procedury w Konstruktorze formularza (`Public Sub New()` w języku Visual Basic i `public class Form1` języka Visual C#). Aby uzyskać dostęp do konstruktora w języku Visual Basic, konieczne będzie Rozwiń pole oznaczone **kod wygenerowany przez projektanta formularzy systemu Windows**.  
  
    ```  
    ' Visual Basic   
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
    }  
    ```  
  
3.  Utwórz procedurę zdarzenia z odpowiednim podpisem, aby odpowiedzieć na <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> zdarzeń.  
  
    ```  
    ' Visual Basic  
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _  
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public void UserPreferenceChanged(object sender,   
    Microsoft.Win32.UserPreferenceChangedEventArgs e)  
    {  
       SetColorScheme();  
    }  
    ```  
  
4.  Dodaj kod konstruktora formularza po wywołaniu `InitializeComponents`, aby Podłączanie procedury zdarzenia zdarzeń systemowych. Ta metoda wywołuje `SetColorScheme` procedury.  
  
    ```  
    ' Visual Basic  
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          += new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
    }  
    ```  
  
5.  Dodaj kod, aby formularz <xref:System.Windows.Forms.Control.Dispose%2A> przed wywołaniem metody <xref:System.Windows.Forms.Control.Dispose%2A> metody klasy podstawowej, aby zwolnić zdarzeń po zamknięciu aplikacji. Aby uzyskać dostęp do <xref:System.Windows.Forms.Control.Dispose%2A> metody w języku Visual Basic, konieczne będzie Rozwiń pole oznaczone kod generowany przez projektanta formularzy systemu Windows.  
  
    > [!NOTE]
    >  Kod zdarzeń systemu działa niezależnie od aplikacji głównej wątku. Jeśli zdarzenie nie zwalnia, kod, który Podłączanie do zdarzeń zostanie uruchomiony, nawet po zamknięciu programu.  
  
    ```  
    ' Visual Basic  
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)  
       If disposing Then  
          If Not (components Is Nothing) Then  
             components.Dispose()  
          End If  
       End If  
       RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
       MyBase.Dispose(disposing)  
    End Sub  
  
    // C#  
    protected override void Dispose( bool disposing )  
    {  
       if( disposing )  
       {  
          if (components != null)   
          {  
             components.Dispose();  
          }  
       }  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          -= new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
       base.Dispose( disposing );  
    }  
    ```  
  
6.  Naciśnij klawisz F5, aby uruchomić aplikację.  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a>Ważne informacje w sposób niż dźwięk przekazywania  
 W tej aplikacji żadnych informacji przekazywanych dźwięk samodzielnie. Jeśli używasz dźwięk w aplikacji, należy określić informacje przy użyciu innych metod również.  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a>Aby podać informacje w inny sposób niż dźwięku  
  
1.  Pasek tytułu flash za pomocą funkcji Windows API FlashWindow. Przykład wywołania funkcji API systemu Windows, temacie [wskazówki: wywoływanie Windows API](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
    > [!NOTE]
    >  Użytkownik może korzystać z usługi WartownikDźwięków Windows włączone, co spowoduje również okna flash podczas odtwarzania dźwięki systemu za pośrednictwem wbudowanego prelegenta komputera.  
  
2.  Wyświetlanie ważne informacje w oknie niemodalne, dzięki czemu użytkownik może odpowiadać na go.  
  
3.  Wyświetlany komunikat, który uzyskuje fokus klawiatury. Unikaj tej metody, gdy użytkownik może wpisać.  
  
4.  Wyświetlanie wskaźnika stanu w obszarze powiadomień stanu na pasku zadań. Aby uzyskać więcej informacji, zobacz [dodawanie ikon aplikacji do elementu TaskBar za pomocą składnika NotifyIcon formularzy systemu Windows](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Przed wdrożeniem aplikacji, należy przetestować funkcje ułatwień dostępu, które zostały zaimplementowane.  
  
#### <a name="to-test-accessibility-features"></a>Aby przetestować funkcje ułatwień dostępu  
  
1.  Aby przetestować dostęp za pomocą klawiatury, odłącz myszy, a następnie przejdź interfejsu użytkownika dla każdej funkcji za pomocą klawiatury. Upewnij się, że wszystkie zadania może być wykonana przy użyciu tylko klawiatury.  
  
2.  Aby przetestować Obsługa dużego kontrastu, wybierz ikonę Opcje ułatwień dostępu w Panelu sterowania. Kliknij kartę Wyświetlanie i zaznacz pole wyboru Użyj dużego kontrastu. Przejdź przez wszystkie elementy interfejsu użytkownika, aby upewnić się, że zmiany kolorów i czcionek są uwzględniane. Upewnij się również, obrazy lub wzorce rysowane pod tekstem zostaną pominięte.  
  
    > [!NOTE]
    >  Windows NT 4 nie ma ikony Opcje ułatwień dostępu w Panelu sterowania. W związku z tym tej procedury do zmiany ustawień SystemInformation.HighContrast nie działa w systemie Windows NT 4.  
  
3.  Inne narzędzia są dostępne do testowania dostępności aplikacji.  
  
4.  Aby przetestować udostępnianie fokus klawiatury, uruchom program Lupa. (Aby go otworzyć, kliknij przycisk **Start** menu wskaż **programy**, wskaż **Akcesoria**, wskaż **ułatwień dostępu**, a następnie kliknij przycisk  **Program Lupa**). Przejdź interfejsu użytkownika za pomocą klawisza TAB klawiatury i myszy. Upewnij się, że wszystkie nawigacji jest śledzony poprawnie w **Lupa**.  
  
5.  Aby przetestować uwidaczniającą elementów ekranu, uruchom inspekcję i używane zarówno mysz, jak i klawisza TAB do osiągnięcia każdego elementu. Upewnij się, że informacje przedstawione w polach Nazwa, stan roli, lokalizacji i wartość okna inspekcja jest zrozumiały dla użytkownika, dla każdego obiektu w interfejsie użytkownika.
