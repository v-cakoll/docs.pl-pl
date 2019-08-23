---
title: 'Przewodnik: Tworzenie dostępnej aplikacji bazującej na systemie Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: 5768177401504f4776a34e499d07b7600597175a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957193"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a>Przewodnik: Tworzenie dostępnej aplikacji bazującej na systemie Windows

Tworzenie dostępnej aplikacji ma istotne znaczenie biznesowe. Wiele rządów ma regulacje dotyczące ułatwień dostępu do zakupu oprogramowania. Logo certyfikowane dla systemu Windows zawiera wymagania dotyczące ułatwień dostępu. W przypadku, gdy wszyscy potencjalni klienci mają wpływ na 30 000 000y, mogą oni uzyskać dostęp do oprogramowania.

Ten przewodnik dotyczy pięciu wymagań dotyczących ułatwień dostępu dla logo certyfikowane dla systemu Windows. Zgodnie z tymi wymaganiami dostępna aplikacja będzie:

- Obsługa rozmiaru panelu sterowania, koloru, czcionki i ustawień wejściowych. Pasek menu, pasek tytułu, obramowania i pasek stanu będą wszystkie zmiany rozmiaru, gdy użytkownik zmieni ustawienia panelu sterowania. W tej aplikacji nie są wymagane żadne dodatkowe zmiany w kontrolkach lub kodzie.

- Duży kontrast tryb obsługi.

- Zapewnianie udokumentowanego dostępu klawiaturowego do wszystkich funkcji.

- Uwidocznij lokalizację fokusu klawiatury wizualnie i programowo.

- Unikaj samodzielnego przekazywania ważnych informacji.

Aby uzyskać więcej informacji, zobacz [zasoby dotyczące projektowania dostępnych aplikacji](/visualstudio/ide/reference/resources-for-designing-accessible-applications).

Aby uzyskać informacje na temat obsługi różnych układów klawiatury, zobacz [najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych do użytku](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).

## <a name="creating-the-project"></a>Tworzenie projektu

W tym instruktażu tworzony jest interfejs użytkownika dla aplikacji, która przyjmuje zamówienia Pizza. Składa się z <xref:System.Windows.Forms.TextBox> nazwy klienta <xref:System.Windows.Forms.RadioButton> , grupy w celu wybrania rozmiaru Pizza, a <xref:System.Windows.Forms.CheckedListBox> do wybrania toppings, dwóch kontrolek z etykietą kolejność i Anuluj oraz menu z poleceniem Exit.

Użytkownik wprowadza nazwę klienta, rozmiar Pizza i żądany toppings. Gdy użytkownik kliknie przycisk zamówienie, w oknie komunikatu zostanie wyświetlone podsumowanie zamówienia i jego koszt, a kontrolki są wyczyszczone i gotowe do kolejnej kolejności. Gdy użytkownik kliknie przycisk Anuluj, formanty są wyczyszczone i gotowe do kolejnej kolejności. Gdy użytkownik kliknie element menu Zakończ, program zostanie zamknięty.

Nacisk tego instruktażu nie jest kodem dla systemu zamówień sprzedaży detalicznej, ale umożliwia dostęp do interfejsu użytkownika. W przewodniku przedstawiono funkcje ułatwień dostępu kilku często używanych kontrolek, w tym przyciski, przyciski radiowe, pola tekstowe i etykiety.

#### <a name="to-begin-making-the-application"></a>Aby rozpocząć tworzenie aplikacji

- Utwórz nową aplikację systemu Windows w Visual Basic lub wizualizacji C#. Nazwij projekt **PizzaOrder**. (Aby uzyskać szczegółowe informacje [, zobacz Tworzenie nowych rozwiązań i projektów](/visualstudio/ide/creating-solutions-and-projects)).

## <a name="adding-the-controls-to-the-form"></a>Dodawanie kontrolek do formularza

Podczas dodawania kontrolek do formularza należy wziąć pod uwagę następujące wytyczne, aby udostępnić dostępną aplikację:

- Ustaw właściwości <xref:System.Windows.Forms.Control.AccessibleName%2A>i. <xref:System.Windows.Forms.Control.AccessibleDescription%2A> W tym przykładzie domyślnym ustawieniem <xref:System.Windows.Forms.Control.AccessibleRole%2A> jest wystarczające. Aby uzyskać więcej informacji na temat właściwości ułatwień dostępu, zobacz temat [zapewnianie informacji o ułatwieniach dostępu dla kontrolek w formularzu systemu Windows](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).

- Ustaw rozmiar czcionki na 10 punktów lub większy.

  > [!NOTE]
  > Jeśli ustawisz rozmiar czcionki formularza na 10 po rozpoczęciu, wówczas wszystkie kontrolki dodane do formularza będą mieć rozmiar czcionki 10.

- Upewnij się, że każda kontrolka etykieta opisująca kontrolkę TextBox bezpośrednio poprzedza formant TextBox w kolejności tabulacji.

- Dodaj klucz dostępu, używając znaku "&", do <xref:System.Windows.Forms.Control.Text%2A> właściwości każdej kontrolki, do której użytkownik może chcieć przejść.

- Dodaj klucz dostępu przy użyciu znaku "&" do <xref:System.Windows.Forms.Control.Text%2A> właściwości etykiety, która poprzedza kontrolkę, do której użytkownik może chcieć przejść. Ustaw <xref:System.Windows.Forms.Label.UseMnemonic%2A> Właściwość Labels na `true`, tak aby fokus został ustawiony na następną kontrolkę w kolejności tabulacji, gdy użytkownik naciśnie klawisz dostępu.

- Dodaj klucze dostępu do wszystkich elementów menu.

#### <a name="to-make-your-windows-application-accessible"></a>Aby udostępnić aplikację systemu Windows

- Dodaj kontrolki do formularza i ustaw właściwości zgodnie z poniższym opisem. Zapoznaj się z obrazem na końcu tabeli, aby zapoznać się z modelem jak rozmieścić kontrolki w formularzu.

   |Obiekt|Właściwość|Wartość|
   |------------|--------------|-----------|
   |Formularz|AccessibleDescription|Formularz zamówienia|
   ||AccessibleName|Formularz zamówienia|
   ||Rozmiar czcionki|10|
   ||Tekst|Formularz zamówienia Pizza|
   |Elemencie|Nazwa|logo|
   ||AccessibleDescription|Wycinek elementu Pizza|
   ||AccessibleName|Logo firmy|
   ||Obraz|Dowolna ikona lub mapa bitowa|
   |Etykieta|Nazwa|companyLabel|
   ||Tekst|Dobre Pizza|
   ||TabIndex|1|
   ||AccessibleDescription|Nazwa firmy|
   ||AccessibleName|Nazwa firmy|
   ||BackColor|Niebieski|
   ||ForeColor|Kryje|
   ||Rozmiar czcionki|18|
   |Etykieta|Nazwa|customerLabel|
   ||Tekst|Nazwa &|
   ||TabIndex|2|
   ||AccessibleDescription|Etykieta nazwy klienta|
   ||AccessibleName|Etykieta nazwy klienta|
   ||UseMnemonic|Prawda|
   |TextBox|Nazwa|customerName|
   ||Tekst|dawaj|
   ||TabIndex|3|
   ||AccessibleDescription|Nazwa klienta|
   ||AccessibleName|Nazwa klienta|
   |GroupBox|Nazwa|sizeOptions|
   ||AccessibleDescription|Opcje rozmiaru Pizza|
   ||AccessibleName|Opcje rozmiaru Pizza|
   ||Tekst|Rozmiar Pizza|
   ||TabIndex|4|
   |RadioButton|Nazwa|smallPizza|
   ||Tekst|& mała $6,00|
   ||Zaznaczone|Prawda|
   ||TabIndex|0|
   ||AccessibleDescription|Mały Pizza|
   ||AccessibleName|Mały Pizza|
   |RadioButton|Nazwa|largePizza|
   ||Tekst|& duże $10,00|
   ||TabIndex|1|
   ||AccessibleDescription|Duże Pizza|
   ||AccessibleName|Duże Pizza|
   |Etykieta|Nazwa|toppingsLabel|
   ||Tekst|& toppings ($0,75)|
   ||TabIndex|5|
   ||AccessibleDescription|Etykieta toppings|
   ||AccessibleName|Etykieta toppings|
   ||UseMnemonic|Prawda|
   |CheckedListBox|Nazwa|toppings|
   ||TabIndex|6|
   ||AccessibleDescription|Dostępne toppings|
   ||AccessibleName|Dostępne toppings|
   ||Elementy|Pepperoni, kiełbasy, grzyby|
   |Przycisk|Nazwa|kolejność|
   ||Tekst|Kolejność &|
   ||TabIndex|7|
   ||AccessibleDescription|Suma zamówienia|
   ||AccessibleName|Suma zamówień|
   |Przycisk|Nazwa|Anuluj|
   ||Tekst|& Anuluj|
   ||TabIndex|8|
   ||AccessibleDescription|Anulowanie zamówienia|
   ||AccessibleName|Anuluj zamówienie|
   |MainMenu|Nazwa|theMainMenu|
   |MenuItem|Nazwa|fileCommands|
   ||Tekst|Plik &|
   |MenuItem|Nazwa|exitApp|
   ||Tekst|E & kończ|

   Formularz będzie wyglądać podobnie jak na poniższym obrazie:

   ![Formularz zamówienia Pizza z nazwą pola tekstowego oraz rozmiarem i toppings zaznaczeniem.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)

## <a name="supporting-high-contrast-mode"></a>Tryb obsługi duży kontrast

Tryb duży kontrast to ustawienie systemu Windows, które zwiększa czytelność przy użyciu kolorów kontrastu i rozmiarów czcionek, które są korzystne dla użytkowników niedowidzących. <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Właściwość jest dostarczana, aby określić, czy tryb duży kontrast jest ustawiony.

Jeśli SystemInformation. HighContrast ma `true`wartość, aplikacja powinna:

- Wyświetlanie wszystkich elementów interfejsu użytkownika przy użyciu schematu kolorów systemu

- Przekazuj podpowiedzi wizualne lub dźwiękowe informacje, które są przekazywane przez kolor. Na przykład, jeśli konkretne elementy listy są wyróżnione przy użyciu czerwonej czcionki, można również dodać pogrubienie do czcionki, aby użytkownik miał niekolorową sygnalizację, że elementy są wyróżnione.

- Pomiń wszystkie obrazy lub wzorce w tle tekstu

Aplikacja powinna sprawdzić ustawienie <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> podczas uruchamiania aplikacji i reagować na zdarzenie <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>systemowe. Zdarzenie jest zgłaszane przy każdej <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> wartości zmiany. <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>

W naszej aplikacji jedynym elementem, który nie korzysta z ustawień systemowych dla koloru jest `lblCompanyName`. <xref:System.Drawing.SystemColors> Klasa służy do zmiany ustawień koloru etykiety na kolory systemu wybrane przez użytkownika.

#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a>Aby włączyć tryb duży kontrast w skuteczny sposób

1. Utwórz metodę, aby ustawić kolory etykiety na kolory systemowe.

    ```vb
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
    ```

    ```csharp
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

2. Wywołaj`Public Sub New()` `public class Form1` C#procedurę w konstruktorze formularzy (w Visual Basic i w wizualizacji). `SetColorScheme` Aby uzyskać dostęp do konstruktora w Visual Basic, należy rozwinąć region o nazwie **kod wygenerowany przez projektanta formularzy systemu Windows**.

    ```vb
    ' Visual Basic
    Public Sub New()
       MyBase.New()
       InitializeComponent()
       SetColorScheme()
    End Sub
    ```

    ```csharp
    // C#
    public Form1()
    {
       InitializeComponent();
       SetColorScheme();
    }
    ```

3. Utwórz procedurę zdarzenia z odpowiednim podpisem, aby odpowiedzieć na <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> zdarzenie.

    ```vb
    ' Visual Basic
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)
       SetColorScheme()
    End Sub
    ```

    ```csharp
    // C#
    public void UserPreferenceChanged(object sender,
    Microsoft.Win32.UserPreferenceChangedEventArgs e)
    {
       SetColorScheme();
    }
    ```

4. Dodaj kod do konstruktora formularzy po wywołaniu do `InitializeComponents`, aby podłączyć procedurę zdarzenia do zdarzenia systemowego. Ta metoda wywołuje `SetColorScheme` procedurę.

    ```vb
    ' Visual Basic
    Public Sub New()
       MyBase.New()
       InitializeComponent()
       SetColorScheme()
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
          AddressOf Me.UserPreferenceChanged
    End Sub
    ```

    ```csharp
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

5. Dodaj kod do metody formularza <xref:System.Windows.Forms.Control.Dispose%2A> przed wywołaniem <xref:System.Windows.Forms.Control.Dispose%2A> metody klasy bazowej, aby zwolnić zdarzenie po zamknięciu aplikacji. Aby uzyskać dostęp <xref:System.Windows.Forms.Control.Dispose%2A> do metody w Visual Basic, należy rozwinąć region o nazwie kod wygenerowany przez projektanta formularzy systemu Windows.

    > [!NOTE]
    > Kod zdarzenia systemowego uruchamia wątek oddzielony od głównej aplikacji. Jeśli nie zwolnisz zdarzenia, kod, który zostanie poddany do zdarzenia, zostanie uruchomiony nawet po zamknięciu programu.

    ```vb
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
    ```

    ```csharp
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

6. Naciśnij klawisz F5, aby uruchomić aplikację.

## <a name="conveying-important-information-by-means-other-than-sound"></a>Przekazywanie ważnych informacji przy użyciu metody innej niż dźwięk

W tej aplikacji żadne informacje nie są przekazywane przez sam dźwięk. Jeśli używasz dźwięku w aplikacji, należy również podać informacje o innych sposobach.

#### <a name="to-supply-information-by-some-other-means-than-sound"></a>Aby podać informacje w inny sposób niż dźwięk

1. Zmień pasek tytułu na Flash przy użyciu funkcji interfejsu API systemu Windows FlashWindow. Aby zapoznać się z przykładem sposobu wywoływania funkcji interfejsu API systemu [Windows, zobacz Przewodnik: Wywoływanie interfejsów](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)API systemu Windows.

    > [!NOTE]
    > Użytkownik może mieć włączoną usługę Windows WartownikDźwięków, co spowoduje również, że okno zostanie wybłyskowe, gdy dźwięki systemu są odtwarzane za pomocą wbudowanego głośnika komputera.

2. Wyświetl ważne informacje w oknie niemodalnym, aby użytkownik mógł je odpowiedzieć.

3. Wyświetla okno komunikatu, które uzyskuje fokus klawiatury. Należy unikać tej metody, gdy użytkownik może pisać.

4. Wyświetl wskaźnik stanu w obszarze powiadomień o stanie na pasku zadań. Aby uzyskać szczegółowe informacje, zobacz [Dodawanie ikon aplikacji do paska zadań ze składnikiem Windows Forms NotifyIcon](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).

## <a name="testing-the-application"></a>Testowanie aplikacji

Przed wdrożeniem aplikacji należy przetestować funkcje ułatwień dostępu, które zostały zaimplementowane.

#### <a name="to-test-accessibility-features"></a>Aby przetestować funkcje ułatwień dostępu

1. Aby przetestować dostęp do klawiatury, odłącz mysz i przejdź do interfejsu użytkownika dla każdej funkcji przy użyciu tylko klawiatury. Upewnij się, że wszystkie zadania mogą być wykonywane tylko przy użyciu klawiatury.

2. Aby przetestować obsługę duży kontrast, wybierz ikonę Opcje ułatwień dostępu w panelu sterowania. Kliknij kartę Wyświetlanie, a następnie zaznacz pole wyboru Użyj duży kontrast. Przejdź przez wszystkie elementy interfejsu użytkownika, aby upewnić się, że zmiany koloru i czcionki są odzwierciedlone. Upewnij się również, że obrazy lub wzorce rysowane w tle tekstu są pomijane.

    > [!NOTE]
    > W systemie Windows NT 4 nie ma ikony Opcje ułatwień dostępu w panelu sterowania. W rezultacie ta procedura zmiany ustawienia SystemInformation. HighContrast nie działa w systemie Windows NT 4.

3. Inne narzędzia są łatwo dostępne do testowania dostępności aplikacji.

4. Aby przetestować Uwidacznianie fokusu klawiatury, uruchom program Lupa. (Aby otworzyć, kliknij menu **Start** , wskaż pozycję **programy**, wskaż pozycję **akcesoria**, wskaż pozycję **ułatwienia dostępu**, a następnie kliknij pozycję **Lupa**). Przejdź do interfejsu użytkownika, używając klawisza Tab i myszy. Upewnij się, że cała nawigacja jest prawidłowo śledzona w programie **Lupa**.

5. Aby przetestować Uwidacznianie elementów ekranu, uruchom inspekcję i użyj zarówno myszy, jak i klawisza TAB, aby dotrzeć do każdego elementu. Upewnij się, że informacje prezentowane w polach Nazwa, stan, rola, lokalizacja i wartość okna inspekcji są zrozumiałe dla użytkownika dla każdego obiektu w interfejsie użytkownika.
