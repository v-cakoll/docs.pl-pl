---
title: 'Wskazówki: tworzenie formantu złożonego za pomocą Visual C#'
ms.date: 03/30/2017
dev_langs:
- CSharp
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ad9aad026a1a6a1266845736d7651db77fd5d5c
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546727"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a>Instruktaż: Autor kontrolki złożonej z C\#

Formanty kompozytowe zapewniają sposób, za pomocą którego można tworzyć i ponownie konfigurować niestandardowe interfejsy graficzne. Formant złożony jest zasadniczo komponentem z wizualną reprezentacją. W związku z tym może składać się z jednego lub więcej formantów, składników lub bloków kodu Windows Forms, które mogą rozszerzać funkcjonalność, sprawdzając poprawność danych wejściowych użytkownika, modyfikując właściwości wyświetlania lub wykonując inne zadania wymagane przez autora. Formantów złożonych mogą być umieszczane w formularzach systemu Windows w taki sam sposób jak inne formanty. W pierwszej części tego przewodnika można utworzyć prosty formant złożony o nazwie `ctlClock`. W drugiej części przewodnika można rozszerzyć funkcjonalność poprzez `ctlClock` dziedziczenie.

## <a name="create-the-project"></a>Tworzenie projektu

Podczas tworzenia nowego projektu należy określić jego nazwę, aby ustawić główny obszar nazw, nazwę zestawu i nazwę projektu oraz upewnić się, że domyślny składnik będzie w poprawnym obszarze nazw.

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Aby utworzyć bibliotekę kontrolną ctlClockLib i kontrolka ctlClock

1. W programie Visual Studio utwórz nowy projekt **biblioteki kontroli formularzy systemu Windows** i nadaj jej nazwę **ctlClockLib**.

     Nazwa `ctlClockLib`projektu jest również domyślnie przypisana do głównego obszaru nazw. Główny obszar nazw jest używany do kwalifikowaniu nazw komponentów w zestawie. Na przykład, jeśli dwa złoża zawierają komponenty o nazwie `ctlClock`, można określić `ctlClock` komponent za pomocą`ctlClockLib.ctlClock.`

2. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **UserControl1.cs**, a następnie kliknij polecenie **Zmień nazwę**. Zmień nazwę pliku `ctlClock.cs`na . Kliknij przycisk **Tak,** gdy pojawi się pytanie, czy chcesz zmienić nazwę wszystkich odwołań do elementu kodu "UserControl1".

    > [!NOTE]
    > Domyślnie formant złożony dziedziczy <xref:System.Windows.Forms.UserControl> z klasy dostarczonej przez system. Klasa <xref:System.Windows.Forms.UserControl> zapewnia funkcje wymagane przez wszystkie formanty złożone i implementuje standardowe metody i właściwości.

3. W menu **Plik** kliknij polecenie **Zapisz wszystko,** aby zapisać projekt.

## <a name="add-windows-controls-and-components-to-the-composite-control"></a>Dodawanie formantów i składników systemu Windows do kontrolki złożonej

Interfejs wizualny jest istotną częścią kontroli złożonej. Ten interfejs wizualny jest implementowany przez dodanie jednego lub więcej formantów systemu Windows do powierzchni projektanta. W poniższej demonstracji zostaną uwzględnione formanty systemu Windows do kontroli złożonej i napisać kod do zaimplementowania funkcji.

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Aby dodać etykietę i timer do formantu złożonego

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **ctlClock.cs**, a następnie kliknij polecenie **Projektant widoku**.

2. W **przyborniku**rozwiń węzeł **Typowe formanty,** a następnie kliknij dwukrotnie pozycję **Etykieta**.

     Formant <xref:System.Windows.Forms.Label> `label1` o nazwie jest dodawany do formantu na powierzchni projektanta.

3. W projektancie kliknij pozycję **label1**. W oknie Właściwości ustaw następujące właściwości.

    |Właściwość|Zmień na|
    |--------------|---------------|
    |**Nazwa**|`lblDisplay`|
    |**Tekst**|`(blank space)`|
    |**Textalign**|`MiddleCenter`|
    |**Czcionka.Rozmiar**|`14`|

4. W **przyborniku**rozwiń węzeł **Składniki,** a następnie kliknij dwukrotnie pozycję **Timer**.

     Ponieważ <xref:System.Windows.Forms.Timer> a jest składnikiem, nie ma wizualnej reprezentacji w czasie wykonywania. W związku z tym nie pojawia się z formantami na powierzchni **projektanta,** ale raczej w Projektancie składników (zasobnik u dołu powierzchni projektanta).

5. W **Projektancie składników**kliknij przycisk **Timer1**, `1000` a <xref:System.Windows.Forms.Timer.Enabled%2A> następnie `true`ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwość na i właściwość na .

     Właściwość <xref:System.Windows.Forms.Timer.Interval%2A> kontroluje częstotliwość, <xref:System.Windows.Forms.Timer> z jaką składnik tyka. Za `timer1` każdym razem zaznacza, uruchamia `timer1_Tick` kod w przypadku. Interwał reprezentuje liczbę milisekund między znacznikami.

6. W **Projektancie składników**kliknij dwukrotnie **timer1,** aby przejść do `timer1_Tick` zdarzenia dla `ctlClock`.

7. Zmodyfikuj kod tak, aby przypominał poniższy przykładowy kod. Pamiętaj, aby zmienić modyfikator dostępu z `private` na `protected`.

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     Ten kod spowoduje, że bieżący `lblDisplay`czas będzie wyświetlany w . Ponieważ interwał `timer1` został `1000`ustawiony na , to zdarzenie będzie występować co tysiąc milisekund, aktualizując w ten sposób bieżący czas co sekundę.

8. Zmodyfikuj metodę, `virtual` która ma być zastąpiona słowem kluczowym. Aby uzyskać więcej informacji, zobacz sekcję "Dziedziczenie z kontroli użytkownika" poniżej.

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. W menu **Plik** kliknij polecenie **Zapisz wszystko,** aby zapisać projekt.

## <a name="add-properties-to-the-composite-control"></a>Dodawanie właściwości do kontrolki złożonej

Kontrola zegara teraz hermetyzuje <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.Timer> formant i składnik, każdy z własnym zestawem właściwości nieodłączne. Podczas gdy poszczególne właściwości tych formantów nie będą dostępne dla kolejnych użytkowników formantu, można utworzyć i udostępnić właściwości niestandardowe, zapisując odpowiednie bloki kodu. W poniższej procedurze dodasz do formantu właściwości, które umożliwiają użytkownikowi zmianę koloru tła i tekstu.

### <a name="to-add-a-property-to-your-composite-control"></a>Aby dodać właściwość do formantu złożonego

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **ctlClock.cs**, a następnie kliknij polecenie **Wyświetl kod**.

     Zostanie otwarty **Edytor kodu** formantu.

2. Znajdź `public partial class ctlClock` instrukcję. Pod nawiasem klamrowym`{)`otwierającym ( wpisz następujący kod.

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     Te instrukcje tworzą zmienne prywatne, które będą używane do przechowywania wartości właściwości, które mają być utworzone.

3. Wprowadź lub wklej następujący kod pod deklaracjami zmiennych z kroku 2.

    ```csharp
    // Declares the name and type of the property.
    public Color ClockBackColor
    {
        // Retrieves the value of the private variable colBColor.
        get
        {
            return colBColor;
        }
        // Stores the selected value in the private variable colBColor, and
        // updates the background color of the label control lblDisplay.
        set
        {
            colBColor = value;
            lblDisplay.BackColor = colBColor;
        }
    }
    // Provides a similar set of instructions for the foreground color.
    public Color ClockForeColor
    {
        get
        {
            return colFColor;
        }
        set
        {
            colFColor = value;
            lblDisplay.ForeColor = colFColor;
        }
    }
    ```

     Powyższy kod sprawia, `ClockForeColor` że dwie `ClockBackColor`właściwości niestandardowe i , dostępne dla kolejnych użytkowników tego formantu. `get` Instrukcje `set` i zapewniają przechowywanie i pobieranie wartości właściwości, a także kod do zaimplementowania funkcji odpowiednich dla właściwości.

4. W menu **Plik** kliknij polecenie **Zapisz wszystko,** aby zapisać projekt.

## <a name="test-the-control"></a>Przetestuj formant

Formanty nie są aplikacjami autonomicznymi; muszą być hostowane w kontenerze. Przetestuj zachowanie w czasie wykonywania formantu i wykonuj jego właściwości za pomocą **kontenera testowego UserControl.** Aby uzyskać więcej informacji, zobacz [Jak: Testowanie zachowania w czasie wykonywania usercontrol](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

### <a name="to-test-your-control"></a>Aby przetestować kontrolę

1. Naciśnij **klawisz F5,** aby utworzyć projekt i uruchomić formant w **kontenerze testowym UserControl**.

2. W siatce właściwości kontenera `ClockBackColor` testowego zlokalizuj właściwość, a następnie wybierz właściwość, aby wyświetlić paletę kolorów.

3. Wybierz kolor, klikając go.

   Kolor tła formantu zmieni się na wybrany kolor.

4. Użyj podobnej sekwencji zdarzeń, `ClockForeColor` aby sprawdzić, czy właściwość działa zgodnie z oczekiwaniami.

   W tej sekcji i poprzednich sekcjach można zobaczyć, jak składniki i formanty systemu Windows mogą być łączone z kodem i opakowaniem, aby zapewnić niestandardowe funkcje w postaci formantu złożonego. Nauczysz się uwidaczniać właściwości w formancie złożonym i jak przetestować formant po jego zakończeniu. W następnej sekcji dowiesz się, jak skonstruować formant złożony dziedziczone przy użyciu `ctlClock` jako podstawy.

## <a name="inherit-from-a-composite-control"></a>Dziedzicz po formancie złożonym

W poprzednich sekcjach opisano, jak łączyć formanty systemu Windows, składniki i kod w formantów złożonych wielokrotnegoużytnia. Formant złożony może być teraz używany jako podstawa, na której można zbudować inne formanty. Proces wyprowadzania klasy z klasy podstawowej jest nazywany *dziedziczeniem*. W tej sekcji utworzysz formant złożony o nazwie `ctlAlarmClock`. Ta kontrolka będzie pochodzić `ctlClock`z jego kontroli nadrzędnej, . Nauczysz się rozszerzać `ctlClock` funkcjonalność, zastępując metody nadrzędne i dodając nowe metody i właściwości.

Pierwszym krokiem w tworzeniu formantu dziedziczonego jest wyprowadzenie go z jego nadrzędnego. Ta akcja tworzy nowy formant, który ma wszystkie właściwości, metody i graficzne właściwości formantu nadrzędnego, ale może również działać jako podstawa do dodawania nowych lub zmodyfikowanych funkcji.

### <a name="to-create-the-inherited-control"></a>Aby utworzyć formant dziedziczony

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **polecenie ctlClockLib**, wskaż polecenie **Dodaj**, a następnie kliknij polecenie **Kontrola użytkownika**.

     Zostanie otwarte okno dialogowe **Dodawanie nowego elementu.**

2. Wybierz szablon **Formant dziedziczonego użytkownika.**

3. W polu **Nazwa** `ctlAlarmClock.cs`wpisz , a następnie kliknij przycisk **Dodaj**.

     Zostanie wyświetlone okno dialogowe **Selektor dziedziczenia.**

4. W obszarze **Nazwa składnika**kliknij dwukrotnie **ctlClock**.

5. W **Eksploratorze rozwiązań**przeglądaj bieżące projekty.

    > [!NOTE]
    > Plik o nazwie **ctlAlarmClock.cs** został dodany do bieżącego projektu.

### <a name="add-the-alarm-properties"></a>Dodawanie właściwości alarmu

Właściwości są dodawane do formantu dziedziczonego w taki sam sposób, w jaki są dodawane do formantu złożonego. Teraz użyjesz składni deklaracji właściwości, aby dodać dwie `AlarmTime`właściwości do formantu: , która będzie przechowywać `AlarmSet`wartość daty i godziny alarmu, która ma zniknąć, oraz , która wskaże, czy alarm jest ustawiony.

#### <a name="to-add-properties-to-your-composite-control"></a>Aby dodać właściwości do formantu złożonego

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij polecenie **Wyświetl kod**.

2. Znajdź `public class` instrukcję. Należy pamiętać, że `ctlClockLib.ctlClock`formant dziedziczy z . Pod nawiasem klamrowym`{)` otwarcia ( instrukcja wpisz następujący kod.

    ```csharp
    private DateTime dteAlarmTime;
    private bool blnAlarmSet;
    // These properties will be declared as public to allow future
    // developers to access them.
    public DateTime AlarmTime
    {
        get
        {
            return dteAlarmTime;
        }
        set
        {
            dteAlarmTime = value;
        }
    }
    public bool AlarmSet
    {
        get
        {
            return blnAlarmSet;
        }
        set
        {
            blnAlarmSet = value;
        }
    }
    ```

### <a name="add-to-the-graphical-interface-of-the-control"></a>Dodaj do interfejsu graficznego formantu

Formant dziedziczony ma interfejs wizualny, który jest identyczny z formantu dziedziczy z. Posiada te same kontrole składników, co jego formant nadrzędny, ale właściwości formantów składowych nie będą dostępne, chyba że zostały one wyraźnie ujawnione. Można dodać do interfejsu graficznego dziedziczonego formantu złożonego w taki sam sposób, jak można dodać do dowolnego formantu złożonego. Aby kontynuować dodawanie do interfejsu wizualnego budzika, dodasz kontrolkę etykiety, która będzie migać, gdy alarm będzie brzmiał.

#### <a name="to-add-the-label-control"></a>Aby dodać kontrolka etykiety

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij polecenie **Wyświetl projektanta**.

     Projektant otwiera `ctlAlarmClock` się w oknie głównym.

2. Kliknij część wyświetlania formantu i wyświetl okno Właściwości.

    > [!NOTE]
    > Podczas gdy wszystkie właściwości są wyświetlane, są one wyszarzone. Oznacza to, że te właściwości `lblDisplay` są natywne i nie mogą być modyfikowane lub dostępne w oknie Właściwości. Domyślnie formanty zawarte w `private`formancie złożonym są , a ich właściwości nie są dostępne w żaden sposób.

    > [!NOTE]
    > Jeśli chcesz, aby kolejni użytkownicy formantu złożonego `public` mieli `protected`dostęp do kontroli wewnętrznej, zadeklaruj ich jako . Umożliwi to ustawienie i zmodyfikowanie właściwości formantów zawartych w formancie złożonym przy użyciu odpowiedniego kodu.

3. Dodaj <xref:System.Windows.Forms.Label> formant do formantu złożonego.

4. Za pomocą myszy <xref:System.Windows.Forms.Label> przeciągnij kontrolkę bezpośrednio pod polem wyświetlania. W oknie Właściwości ustaw następujące właściwości.

    |Właściwość|Ustawienie|
    |--------------|-------------|
    |**Nazwa**|`lblAlarm`|
    |**Tekst**|**Alarm!**|
    |**Textalign**|`MiddleCenter`|
    |**Widoczne**|`false`|

### <a name="add-the-alarm-functionality"></a>Dodawanie funkcji alarmu

W poprzednich procedurach dodano właściwości i formant, który włączy funkcje alarmu w formancie złożonym. W tej procedurze dodasz kod, aby porównać bieżący czas z czasem alarmu i, jeśli są one takie same, aby migać alarm. Poprzez `timer1_Tick` zastąpienie metody `ctlClock` i dodanie dodatkowego kodu do niego, można `ctlAlarmClock` rozszerzyć możliwości przy zachowaniu `ctlClock`wszystkich nieodłącznych funkcji .

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a>Aby zastąpić timer1_Tick metodę ctlClock

1. W **Edytorze kodu** `private bool blnAlarmSet;` znajdź instrukcję. Natychmiast pod nim dodaj następującą instrukcję.

    ```csharp
    private bool blnColorTicker;
    ```

2. W **Edytorze kodu**znajdź nawias`})` zamykający ( na końcu klasy. Tuż przed nawiasem klamrowym dodaj następujący kod.

    ```csharp
    protected override void timer1_Tick(object sender, System.EventArgs e)
    {
        // Calls the Timer1_Tick method of ctlClock.
        base.timer1_Tick(sender, e);
        // Checks to see if the alarm is set.
        if (AlarmSet == false)
            return;
        else
            // If the date, hour, and minute of the alarm time are the same as
            // the current time, flash an alarm.
        {
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)
            {
                // Sets lblAlarmVisible to true, and changes the background color based on
                // the value of blnColorTicker. The background color of the label
                // will flash once per tick of the clock.
                lblAlarm.Visible = true;
                if (blnColorTicker == false)
                {
                    lblAlarm.BackColor = Color.Red;
                    blnColorTicker = true;
                }
                else
                {
                    lblAlarm.BackColor = Color.Blue;
                    blnColorTicker = false;
                }
            }
            else
            {
                // Once the alarm has sounded for a minute, the label is made
                // invisible again.
                lblAlarm.Visible = false;
            }
        }
    }
    ```

     Dodanie tego kodu wykonuje kilka zadań. Instrukcja `override` kieruje formantu do korzystania z tej metody zamiast metody, która została odziedziczona z formantu podstawowego. Gdy ta metoda jest wywoływana, wywołuje metodę, którą `base.timer1_Tick` zastępuje, wywołując instrukcję, zapewniając, że wszystkie funkcje włączone w oryginalnym formancie jest powielana w tym formancie. Następnie uruchamia dodatkowy kod, aby włączyć funkcję alarmu. Po wystąpieniu alarmu pojawi się migająca kontrolka etykiety.

     Sterowanie budzikiem jest prawie kompletne. Pozostaje tylko wdrożyć sposób, aby go wyłączyć. Aby to zrobić, należy dodać `lblAlarm_Click` kod do metody.

#### <a name="to-implement-the-shutoff-method"></a>Aby zaimplementować metodę wyłączania

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **ctlAlarmClock.cs**, a następnie kliknij polecenie **Widok Projektanta**.

     Projektant otwiera.

2. Dodaj przycisk do formantu. Ustaw właściwości przycisku w następujący sposób.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|`btnAlarmOff`|
    |**Tekst**|**Wyłącz alarm**|

3. W projektancie kliknij dwukrotnie **btnAlarmOff**.

     **Edytor kodu** zostanie `private void btnAlarmOff_Click` otwarty do wiersza.

4. Zmodyfikuj tę metodę, tak aby przypominała następujący kod.

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. W menu **Plik** kliknij polecenie **Zapisz wszystko,** aby zapisać projekt.

### <a name="use-the-inherited-control-on-a-form"></a>Używanie formantu dziedziczonego w formularzu

Odziedziczonego formantu można przetestować w taki sam `ctlClock`sposób, w jaki testowano kontrolę klasy podstawowej: Naciśnij **klawisz F5,** aby utworzyć projekt i uruchomić formant w **kontenerze testowym UserControl**. Aby uzyskać więcej informacji, zobacz [Jak: Testowanie zachowania w czasie wykonywania usercontrol](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

Aby użyć formantu, musisz go hostować w formularzu. Podobnie jak w przypadku standardowego formantu złożonego, dziedziczona formant złożony nie może być autonomiczna i musi być hostowana w formularzu lub innym kontenerze. Ponieważ `ctlAlarmClock` ma większą głębię funkcjonalności, dodatkowy kod jest wymagany do przetestowania go. W tej procedurze napiszesz prosty program do `ctlAlarmClock`testowania funkcjonalności . Napiszesz kod, aby `AlarmTime` ustawić `ctlAlarmClock`i wyświetlić właściwość , i przetestuje jego nieodłączne funkcje.

#### <a name="to-build-and-add-your-control-to-a-test-form"></a>Aby utworzyć i dodać formant do formularza testowego

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **ctlClockLib**, a następnie kliknij polecenie **Kompilacja**.

2. Dodaj do rozwiązania nowy projekt **aplikacji Formularze systemu Windows** i nazwij go **Test**.

3. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **Odwołania** dla projektu testowego. Kliknij **pozycję Dodaj odwołanie,** aby wyświetlić okno dialogowe **Dodawanie odwołania.** Kliknij kartę z etykietą **Projekty**. Projekt `ctlClockLib` zostanie wyświetlony w obszarze **Nazwa projektu**. Kliknij dwukrotnie projekt, aby dodać odwołanie do projektu testowego.

4. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy pozycję **Testuj,** a następnie kliknij polecenie **Kompilacja**.

5. W **przyborniku**rozwiń węzeł **składniki ctlClockLib.**

6. Kliknij dwukrotnie **ctlAlarmClock,** aby `ctlAlarmClock` dodać kopię do formularza.

7. W **przyborniku**znajdź i kliknij dwukrotnie **datetimepicker,** aby dodać <xref:System.Windows.Forms.DateTimePicker> formant do formularza, a następnie dodaj <xref:System.Windows.Forms.Label> formant, klikając dwukrotnie pozycję **Etykieta**.

8. Użyj myszki, aby ustawić kontrolki w dogodnym miejscu w formularzu.

9. Ustaw właściwości tych formantów w następujący sposób.

    |Kontrola|Właściwość|Wartość|
    |-------------|--------------|-----------|
    |`label1`|**Tekst**|`(blank space)`|
    ||**Nazwa**|`lblTest`|
    |`dateTimePicker1`|**Nazwa**|`dtpTest`|
    ||**Formacie**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. W projektancie kliknij dwukrotnie **dtpTest**.

     **Otworzy** się `private void dtpTest_ValueChanged`Edytor kodu .

11. Zmodyfikuj kod tak, aby przypominał następującą.

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy pozycję **Testuj**, a następnie kliknij polecenie **Ustaw jako projekt startowy**.

13. W menu **Debugowanie** kliknij polecenie **Rozpocznij debugowanie**.

     Rozpocznie się program testowy. Należy zauważyć, że bieżący `ctlAlarmClock` czas jest aktualizowany w formancie i że godzina rozpoczęcia jest wyświetlana w formancie. <xref:System.Windows.Forms.DateTimePicker>

14. Kliknij <xref:System.Windows.Forms.DateTimePicker> miejsce wyświetlania minut godziny.

15. Za pomocą klawiatury ustaw wartość minut o minutę większą niż `ctlAlarmClock`bieżący czas wyświetlany przez program .

     Czas ustawienia alarmu jest `lblTest`wyświetlany w pliku . Poczekaj, aż wyświetlany czas osiągnie czas ustawienia alarmu. Gdy wyświetlany czas osiągnie czas, na który ustawiony `lblAlarm` jest alarm, będzie migać.

16. Wyłącz alarm, klikając `btnAlarmOff`przycisk . Możesz teraz zresetować alarm.

Ten artykuł obejmuje szereg kluczowych pojęć. Nauczysz się tworzyć formant złożony, łącząc formanty i składniki w kontenerze sterowania kompozytowego. Nauczysz się dodawać właściwości do formantu i pisać kod w celu zaimplementowania funkcji niestandardowych. W ostatniej sekcji, można nauczyć się rozszerzyć funkcjonalność danego sterowania złożonego poprzez dziedziczenie i zmienić funkcjonalność metod hosta przez zastąpienie tych metod.

## <a name="see-also"></a>Zobacz też

- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
- [Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual C#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
