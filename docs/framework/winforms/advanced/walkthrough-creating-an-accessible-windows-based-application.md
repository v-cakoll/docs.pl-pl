---
title: 'Przewodnik: Tworzenie dostępnej aplikacji bazującej na systemie Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: 6d246c56af191189fa775be3248d3099d2aa2544
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203694"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a>Przewodnik: Tworzenie dostępnej aplikacji bazującej na systemie Windows
Tworzenie dostępnej aplikacji ma skutki dla firmy ważne. Wiele rządy mieć ułatwień dostępu przepisami lub ustaleniami dotyczącymi oprogramowania zakupionego. Logo Certified for Windows zawiera wymagania dotyczące ułatwień dostępu. Szacowany mieszkańcy 30 mln Stanów Zjednoczonych samodzielnie, wiele potencjalnych klientów, są zagrożone dostępność oprogramowania.  
  
 Ten przewodnik pozwala sprostać pięć wymagania dotyczące ułatwień dostępu, logo Certified for Windows. Zgodnie z tymi wymaganiami dostępnej aplikacji wykonują następujące czynności:  
  
-   Obsługuje rozmiar panelu sterowania, kolory, czcionki i wprowadź ustawienia. Pasek menu, pasek tytułu, obramowania i pasek stanu będzie wszystkie rozmiar się po użytkownik zmienia ustawienia Panelu sterowania. Nie dodatkowe zmiany do kontrolki lub kodu są wymagane w tej aplikacji.  
  
-   Obsługa trybu wysokiego kontrastu.  
  
-   Podaj udokumentowanego klawiatury dostęp do wszystkich funkcji.  
  
-   Udostępnianie lokalizacji fokus klawiatury ModelID.  
  
-   Należy unikać przekazywania ważnych informacji za pomocą dźwięku samodzielnie.  
  
 Aby uzyskać więcej informacji, zobacz [zasoby do projektowania dostępnych aplikacji](/visualstudio/ide/reference/resources-for-designing-accessible-applications).  
  
 Aby uzyskać informacje dotyczące obsługi różnych układów klawiatury, zobacz [najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Ten poradnik tworzy interfejsu użytkownika dla aplikacji, która przyjmuje pizza zamówienia. Składa się z <xref:System.Windows.Forms.TextBox> dla nazwy klienta <xref:System.Windows.Forms.RadioButton> grupy, aby wybrać rozmiar pizza <xref:System.Windows.Forms.CheckedListBox> służąca do wybierania toppings, dwie kontrolki przycisku etykietą, kolejność i Anuluj i Menu przy użyciu polecenia Exit.  
  
 Użytkownik wprowadza nazwę klienta, rozmiar pizza i toppings żądanego. Gdy użytkownik kliknie przycisk Zamówienie, podsumowanie kolejności i jego kosztów są wyświetlane w oknie komunikatu i formanty są wyczyszczone i jest gotowa do następnej kolejności. Gdy użytkownik kliknie przycisk Anuluj, formanty są wyczyszczone i jest gotowa do następnej kolejności. Gdy użytkownik kliknie element menu zakończenia, zamyka program.  
  
 Szczególnym w tym przewodniku nie jest w kodzie system zamówień sprzedaży detalicznej, ale dostępność interfejsu użytkownika. Instruktaż demonstruje funkcje ułatwień dostępu kilka często używanych formantów, w tym przycisków, przyciski radiowe, pola tekstowe i etykiety.  
  
#### <a name="to-begin-making-the-application"></a>Aby rozpocząć tworzenie aplikacji  
  
-   Utwórz nową aplikację Windows w języku Visual Basic lub Visual C#. Nadaj projektowi nazwę **PizzaOrder**. (Aby uzyskać szczegółowe informacje, zobacz [tworzenie nowych rozwiązań i projektów](/visualstudio/ide/creating-solutions-and-projects).)  
  
## <a name="adding-the-controls-to-the-form"></a>Dodawanie formantów do formularza  
 Podczas dodawania formantów do formularza, należy pamiętać, poniższe wskazówki umożliwiają dostępnej aplikacji:  
  
-   Ustaw <xref:System.Windows.Forms.Control.AccessibleDescription%2A> i <xref:System.Windows.Forms.Control.AccessibleName%2A> właściwości. W tym przykładzie domyślne ustawienie dla <xref:System.Windows.Forms.Control.AccessibleRole%2A> jest wystarczająca. Aby uzyskać więcej informacji na temat właściwości ułatwień dostępu, zobacz [dostarczanie informacji o ułatwieniach dostępu dla formantów w formularzu Windows](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).  
  
-   Ustaw rozmiar czcionki do 10 punktów i większych.  
  
    > [!NOTE]
    >  Jeśli ustawisz rozmiar czcionki w formularzu do 10 podczas uruchamiania, wszystkie kontrolki, następnie dodawane do formularza będzie miał rozmiar czcionki, 10.  
  
-   Upewnij się, że wszystkie kontrolki etykiety, która opisuje kontrolki TextBox bezpośrednio poprzedza formant pola tekstowego w kolejności tabulacji.  
  
-   Dodaj klucz dostępu, korzystając ze znaku "&", do <xref:System.Windows.Forms.Control.Text%2A> dowolną kontrolkę, użytkownik może chcieć przejść do właściwości.  
  
-   Dodaj klucz dostępu, korzystając ze znaku "&", do <xref:System.Windows.Forms.Control.Text%2A> właściwość etykiety, który poprzedza formant, który użytkownik może chcieć przejść do. Ustawić etykiety <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwości `true`, dzięki czemu fokus jest ustawiony do następnej kontrolki w kolejności tabulacji, gdy użytkownik naciśnie klawisz dostępu.  
  
-   Dodaj klucze dostępu do wszystkich elementów menu.  
  
#### <a name="to-make-your-windows-application-accessible"></a>Aby udostępnić aplikację Windows  
  
-   Dodaj formanty do formularza, a następnie ustaw właściwości, zgodnie z poniższym opisem. Zobacz obraz na koniec tabeli dla modeli rozmieszczanie formantów w formularzu.  
  
    |Obiekt|Właściwość|Wartość|  
    |------------|--------------|-----------|  
    |Formularz Form1|AccessibleDescription|Formularz zamówienia|  
    ||AccessibleName|Formularz zamówienia|  
    ||Rozmiar czcionki|10|  
    ||Tekst|Formularz zamówienia pizza|  
    |PictureBox|Nazwa|logo|  
    ||AccessibleDescription|Wycinek pizza|  
    ||AccessibleName|Logo firmy|  
    ||Obraz|Wszystkie ikony lub mapy bitowej|  
    |Etykieta|Nazwa|companyLabel|  
    ||Tekst|Dobre Pizza|  
    ||TabIndex|1|  
    ||AccessibleDescription|Nazwa firmy|  
    ||AccessibleName|Nazwa firmy|  
    ||Backcolor|Niebieski|  
    ||ForeColor|Żółty|  
    ||Rozmiar czcionki|18|  
    |Etykieta|Nazwa|customerLabel|  
    ||Tekst|& Nazwa|  
    ||TabIndex|2|  
    ||AccessibleDescription|Etykieta nazwy klienta|  
    ||AccessibleName|Etykieta nazwy klienta|  
    ||UseMnemonic|Prawda|  
    |TextBox|Nazwa|customerName|  
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
    ||Tekst|& małe $6.00|  
    ||Zaznaczone|Prawda|  
    ||TabIndex|0|  
    ||AccessibleDescription|Małe pizza|  
    ||AccessibleName|Małe pizza|  
    |RadioButton|Nazwa|largePizza|  
    ||Tekst|& dużych 10,00 zł|  
    ||TabIndex|1|  
    ||AccessibleDescription|Duże pizza|  
    ||AccessibleName|Duże pizza|  
    |Etykieta|Nazwa|toppingsLabel|  
    ||Tekst|& toppings ($0,75 każdy)|  
    ||TabIndex|5|  
    ||AccessibleDescription|Etykieta toppings|  
    ||AccessibleName|Etykieta toppings|  
    ||UseMnemonic|Prawda|  
    |CheckedListBox|Nazwa|toppings|  
    ||TabIndex|6|  
    ||AccessibleDescription|Dostępne toppings|  
    ||AccessibleName|Dostępne toppings|  
    ||Elementy|Pepperoni, produkcji kiełbas, grzyby|  
    |Przycisk|Nazwa|kolejność|  
    ||Tekst|& kolejność|  
    ||TabIndex|7|  
    ||AccessibleDescription|Łączna liczba kolejności|  
    ||AccessibleName|Zamówienia|  
    |Przycisk|Nazwa|Anuluj|  
    ||Tekst|& Anuluj|  
    ||TabIndex|8|  
    ||AccessibleDescription|Anulowanie zamówienia|  
    ||AccessibleName|Anulowanie zamówienia|  
    |MainMenu|Nazwa|theMainMenu|  
    |Element MenuItem|Nazwa|fileCommands|  
    ||Tekst|&File|  
    |Element MenuItem|Nazwa|exitApp|  
    ||Tekst|Za & kończ|
    
      Formularz będzie wyglądać podobnie do następującego:
    
      ![Formularz kolejności pizza z pola tekstowego, a rozmiar i toppings wybór nazwy.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)  

## <a name="supporting-high-contrast-mode"></a>Obsługa trybu wysokiego kontrastu  
 Trybu wysokiego kontrastu jest ustawienie systemu Windows, który poprawia czytelność przy użyciu kontrastujących i rozmiary czcionek, które są przydatne dla użytkowników niedowidzących. <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Właściwość została podana w celu ustalenia, czy ustawiono trybu wysokiego kontrastu.  
  
 Jeśli jest SystemInformation.HighContrast `true`, aplikacja powinna:  
  
-   Wyświetlanie wszystkich elementów interfejsu użytkownika przy użyciu schematu kolorów systemu  
  
-   Przekazuje za pomocą wizualnych lub dźwięk wszystkie informacje, które jest przekazywane przez kolor. Na przykład jeśli elementy konkretnej listy są wyróżnione za pomocą czerwonego czcionki, można również dodasz pogrubioną czcionką, tak, aby użytkownik miał cue-color, że elementy są wyróżnione.  
  
-   Pomiń wszelkie obrazy i wzorce pod tekstem  
  
 Aplikacja powinna sprawdzać, czy ustawienie <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> podczas uruchamiania aplikacji i odpowiedzieć na zdarzenie systemowe <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>. <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Zdarzenie jest wywoływane zawsze wtedy, gdy wartość <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> zmiany.  
  
 W naszej aplikacji jest jedynym elementem, który nie używa ustawień systemowych dla koloru `lblCompanyName`. <xref:System.Drawing.SystemColors> Klasa jest używana, aby zmienić ustawienia koloru etykiety na kolory systemowe wybrane przez użytkownika.  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a>Aby włączyć tryb dużego kontrastu w skutecznym sposobem  
  
1.  Utwórz metodę, aby ustawić kolory, etykiety kolory systemowe.  
  
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
  
2.  Wywołaj `SetColorScheme` procedury w Konstruktorze formularza (`Public Sub New()` w języku Visual Basic i `public class Form1` w elemencie wizualnym C#). Aby uzyskać dostęp do konstruktora w języku Visual Basic, konieczne będzie rozwiń region etykietą **kod wygenerowany przez projektanta formularzy Windows**.  
  
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
  
4.  Dodaj kod konstruktora formularza po wywołaniu `InitializeComponents`, żeby podpiąć procedury zdarzenia zdarzeń systemu. Ta metoda wywołuje `SetColorScheme` procedury.  
  
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
  
5.  Dodaj kod do formularza <xref:System.Windows.Forms.Control.Dispose%2A> metoda przed wywołaniem do <xref:System.Windows.Forms.Control.Dispose%2A> metody klasy bazowej, aby zwolnić zdarzenia po zamknięciu aplikacji. Aby uzyskać dostęp do <xref:System.Windows.Forms.Control.Dispose%2A> metoda w języku Visual Basic, konieczne będzie rozwiń region, kod generowany przez projektanta formularzy Windows etykietą.  
  
    > [!NOTE]
    >  Kod zdarzenia system działa wątku oddzielnie od głównej aplikacji. Jeśli zdarzenie nie jest zwolniony, kod, który można dołączyć do zdarzenia będzie działać po zamknięciu programu.  
  
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
  
## <a name="conveying-important-information-by-means-other-than-sound"></a>Przekazywania ważnych informacji przy użyciu metod innych niż dźwięku  
 W tej aplikacji żadne informacje jest przekazywany za pomocą samodzielnie dźwięku. Jeśli używasz dźwięk w aplikacji należy dostarczać informacji za pomocą innych środków także.  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a>Aby podać informacje w inny sposób niż dźwięku  
  
1.  Należy na pasku tytułu flash przy użyciu funkcji Windows API FlashWindow. Na przykład sposób wywołania funkcji Windows API zobacz [instruktażu: Wywoływanie Windows API](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
    > [!NOTE]
    >  Użytkownik może korzystać z usługi Windows WartownikDźwięków włączone, co spowoduje również okna flash odtwarzania dźwięki systemu za pomocą wbudowanych głośników komputera.  
  
2.  Wyświetlania ważnych informacji w kompaktowym niemodalnym oknie, dzięki czemu użytkownik może odpowiedzieć na.  
  
3.  Wyświetla okno komunikatu, który uzyskuje fokus klawiatury. Należy unikać tej metody, gdy użytkownik może wpisać.  
  
4.  Wyświetl wskaźnik stanu w obszarze stanu powiadomień paska zadań. Aby uzyskać więcej informacji, zobacz [dodawanie ikon aplikacji do paska zadań za pomocą składnika NotifyIcon formularzy Windows](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Przed wdrożeniem aplikacji, należy przetestować funkcje ułatwień dostępu, które zostały zaimplementowane.  
  
#### <a name="to-test-accessibility-features"></a>Aby przetestować funkcje ułatwień dostępu  
  
1.  Aby przetestować dostęp za pomocą klawiatury, odłącz myszy, a następnie przejdź do interfejsu użytkownika dla każdej funkcji, za pomocą klawiatury. Upewnij się, że wszystkie zadania można wykonać za pomocą klawiatury, tylko.  
  
2.  Aby przetestować obsługę dużego kontrastu, wybierz ikonę aplet Opcje ułatwień dostępu w Panelu sterowania. Kliknij kartę ekran, a następnie zaznacz pole wyboru Użyj o wysokim kontraście. Przejdź do wszystkich elementów interfejsu użytkownika, aby upewnić się, że odzwierciedlenie zmiany kolorów i czcionek. Ponadto upewnij się, obrazów lub wzorców rysowane pod tekstem zostaną pominięte.  
  
    > [!NOTE]
    >  Windows NT 4 nie ma ikony opcji ułatwień dostępu w Panelu sterowania. W związku z tym tę procedurę dla zmiany ustawienia SystemInformation.HighContrast nie działa w Windows NT 4.  
  
3.  Inne narzędzia są łatwo dostępne dla testów dostępności aplikacji.  
  
4.  Aby przetestować udostępnianie fokus klawiatury, uruchom program Lupa. (Aby go otworzyć, kliknij przycisk **Start** menu wskaż **programy**, wskaż polecenie **Akcesoria**, wskaż **ułatwień dostępu**, a następnie kliknij przycisk  **Program Lupa**). Przejdź interfejsu użytkownika przy użyciu przełączania klawiatury i myszy. Upewnij się poprawnie w systemie śledzenia wszystkich nawigacji **Lupa**.  
  
5.  Aby przetestować uwidaczniającą elementów na ekranie, uruchom Sprawdź, a następnie użyj myszy i klawisz TAB, aby dotrzeć do każdego elementu. Upewnij się, że informacje znajdujące się w polach Nazwa, stan, rola, lokalizacji i wartość okna Sprawdź zrozumiały dla użytkownika dla każdego obiektu w interfejsie użytkownika.
