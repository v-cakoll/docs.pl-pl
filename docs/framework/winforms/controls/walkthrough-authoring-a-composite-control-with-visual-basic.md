---
title: 'Przewodnik: tworzenie kontrolki złożonej za pomocą Visual Basic'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
ms.openlocfilehash: cb54ef372e6da551b95f1edf61e3844b9dcba4c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950040"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a>Przewodnik: tworzenie kontrolki złożonej za pomocą Visual Basic
Kontrolki złożone zapewniają metodę, za pomocą której można tworzyć i ponownie używać niestandardowych interfejsów graficznych. Formant złożony jest zasadniczo składnikiem z reprezentacją wizualną. W związku z tym może składać się z co najmniej jednego Windows Forms kontrolek, składników lub bloków kodu, który może zwiększyć funkcjonalność, sprawdzając dane wejściowe użytkownika, modyfikując właściwości wyświetlania lub wykonując inne zadania wymagane przez autora. Kontrolki złożone mogą być umieszczane na Windows Forms w taki sam sposób jak w przypadku innych kontrolek. W pierwszej części tego przewodnika utworzysz prostą kontrolkę złożoną o nazwie `ctlClock`. W drugiej części przewodnika rozszerzono funkcjonalność programu `ctlClock` przez dziedziczenie.

## <a name="creating-the-project"></a>Tworzenie projektu
 Podczas tworzenia nowego projektu należy określić jego nazwę, aby ustawić główną przestrzeń nazw, nazwę zestawu i nazwę projektu, i upewnić się, że składnik domyślny będzie w poprawnej przestrzeni nazw.

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Aby utworzyć bibliotekę kontrolek ctlClockLib i formant ctlClock

1. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt** , aby otworzyć okno dialogowe **Nowy projekt** .

2. Z listy projektów Visual Basic wybierz szablon projektu **Biblioteka formantów systemu Windows** , wpisz `ctlClockLib` w polu **Nazwa** , a następnie kliknij przycisk **OK**.

     Nazwa projektu, `ctlClockLib`, również jest domyślnie przypisana do głównej przestrzeni nazw. Główna przestrzeń nazw służy do kwalifikowania nazw składników w zestawie. Na przykład jeśli dwa zestawy dostarczają składniki o nazwie `ctlClock`, można `ctlClock` określić składnik przy użyciu`ctlClockLib.ctlClock.`

3. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy **UserControl1. vb**, a następnie kliknij polecenie **Zmień nazwę**. Zmień nazwę pliku na `ctlClock.vb`. Kliknij przycisk **tak** po wyświetleniu monitu, jeśli chcesz zmienić nazwy wszystkich odwołań do elementu kodu "UserControl1".

    > [!NOTE]
    > Domyślnie formant złożony dziedziczy z <xref:System.Windows.Forms.UserControl> klasy dostarczonej przez system. <xref:System.Windows.Forms.UserControl> Klasa zawiera funkcje wymagane przez wszystkie kontrolki złożone i implementuje standardowe metody i właściwości.

4. W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.

## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Dodawanie formantów i składników systemu Windows do kontrolki złożonej
 Interfejs wizualny jest istotną częścią formantu złożonego. Ten interfejs wizualny jest implementowany przez dodanie jednego lub większej liczby kontrolek systemu Windows do powierzchni projektanta. Poniższa prezentacja zawiera kontrolki systemu Windows w kontrolce złożonej i pisanie kodu w celu zaimplementowania funkcji.

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Aby dodać etykietę i czasomierz do kontrolki złożonej

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **ctlClock. vb**, a następnie kliknij pozycję **Projektant widoków**.

2. W przyborniku rozwiń węzeł **formanty wspólne** , a następnie kliknij dwukrotnie pozycję **etykieta**.

     Kontrolka o `Label1` nazwie jest dodawana do kontrolki na powierzchni projektanta. <xref:System.Windows.Forms.Label>

3. W projektancie kliknij pozycję **Label1**. W okno Właściwości ustaw następujące właściwości.

    |Właściwość|Zmień na|
    |--------------|---------------|
    |**Nazwa**|`lblDisplay`|
    |**Text**|`(blank space)`|
    |**TextAlign**|`MiddleCenter`|
    |**Font.Size**|`14`|

4. W **przyborniku**rozwiń węzeł **składniki** , a następnie kliknij dwukrotnie przycisk **czasomierz**.

     Ponieważ element <xref:System.Windows.Forms.Timer> jest składnikiem, nie ma żadnej wizualizacji w czasie wykonywania. W związku z tym nie jest wyświetlany z kontrolkami na powierzchni projektanta, ale raczej w projektancie składników (zasobnik u dołu powierzchni projektanta).

5. W projektancie składników kliknij pozycję **Timer1**, a następnie ustaw <xref:System.Windows.Forms.Timer.Interval%2A> <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość na `1000` wartość i właściwość na `True`.

     <xref:System.Windows.Forms.Timer.Interval%2A> Właściwość kontroluje częstotliwość taktowania składnika czasomierza. Każdy cykl `Timer1` czasu uruchamia kod `Timer1_Tick` w zdarzeniu. Interwał reprezentuje liczbę milisekund między taktami.

6. W projektancie składników kliknij dwukrotnie pozycję **Timer1** , aby przejść do `Timer1_Tick` zdarzenia. `ctlClock`

7. Zmodyfikuj kod w taki sposób, aby wyglądał jak Poniższy przykład kodu. Upewnij się, że modyfikator dostępu został zmieniony `Private` z `Protected`na.

    ```vb
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles Timer1.Tick
        ' Causes the label to display the current time.
        lblDisplay.Text = Format(Now, "hh:mm:ss")
    End Sub
    ```

     Ten kod spowoduje, że bieżący czas będzie pokazywany w `lblDisplay`. Ze względu na `Timer1` to, że `1000`interwał został ustawiony na, to zdarzenie będzie wykonywane co tysiąc milisekund, co oznacza, że bieżący czas jest aktualizowany co sekundę.

8. Zmodyfikuj metodę, aby była możliwy do zastąpienia. Aby uzyskać więcej informacji, zobacz sekcję "dziedziczenie z kontrolki użytkownika" poniżej.

    ```vb
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _
        e As System.EventArgs) Handles Timer1.Tick
    ```

9. W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.

## <a name="adding-properties-to-the-composite-control"></a>Dodawanie właściwości do kontrolki złożonej
 Kontrolka zegara hermetyzuje <xref:System.Windows.Forms.Label> obecnie formant <xref:System.Windows.Forms.Timer> i składnik, z których każdy ma własny zestaw właściwości. Chociaż poszczególne właściwości tych kontrolek nie będą dostępne dla kolejnych użytkowników kontrolki, można utworzyć i uwidocznić właściwości niestandardowe przez napisanie odpowiednich bloków kodu. Poniższa procedura obejmuje dodanie do kontrolki właściwości, które umożliwiają użytkownikowi zmianę koloru tła i tekstu.

### <a name="to-add-a-property-to-your-composite-control"></a>Aby dodać właściwość do kontrolki złożonej

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy **ctlClock. vb**, a następnie kliknij polecenie **Wyświetl kod**.

     Zostanie otwarty Edytor kodu dla kontrolki.

2. `Public Class ctlClock` Znajdź instrukcję. Poniżej wpisz poniższy kod.

    ```vb
    Private colFColor as Color
    Private colBColor as Color
    ```

     Te instrukcje tworzą zmienne prywatne, które będą używane do przechowywania wartości właściwości, które mają zostać utworzone.

3. Wstaw następujący kod poniżej deklaracji zmiennych z kroku 2.

    ```vb
    ' Declares the name and type of the property.
    Property ClockBackColor() as Color
        ' Retrieves the value of the private variable colBColor.
        Get
            Return colBColor
        End Get
        ' Stores the selected value in the private variable colBColor, and
        ' updates the background color of the label control lblDisplay.
        Set(ByVal value as Color)
            colBColor = value
            lblDisplay.BackColor = colBColor
        End Set

    End Property
    ' Provides a similar set of instructions for the foreground color.
    Property ClockForeColor() as Color
        Get
            Return colFColor
        End Get
        Set(ByVal value as Color)
            colFColor = value
            lblDisplay.ForeColor = colFColor
        End Set
    End Property
    ```

     Poprzedni kod tworzy dwie właściwości `ClockForeColor` niestandardowe i `ClockBackColor`, dostępne dla kolejnych użytkowników tej `Property` kontrolki przez wywoływanie instrukcji. Instrukcje `Get` and`Set` zapewniają przechowywanie i pobieranie wartości właściwości, a także kod służący do implementowania funkcji odpowiednich dla właściwości.

4. W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.

## <a name="testing-the-control"></a>Testowanie kontrolki
 Formanty nie są projektami autonomicznymi; muszą być hostowane w kontenerze. Przetestuj zachowanie w czasie wykonywania formantu i wykonuj jego właściwości za pomocą **kontenera testów UserControl**. Aby uzyskać więcej informacji, zobacz [jak: Przetestuj zachowanie elementu UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)w czasie wykonywania.

### <a name="to-test-your-control"></a>Aby przetestować kontrolkę

1. Naciśnij klawisz F5, aby skompilować projekt i uruchomić formant w **kontenerze Test UserControl**.

2. W siatce właściwości kontenera testów zaznacz `ClockBackColor` właściwość, a następnie kliknij strzałkę listy rozwijanej, aby wyświetlić paletę kolorów.

3. Wybierz kolor, klikając go.

     Kolor tła kontrolki zmieni się na wybrany kolor.

4. Użyj podobnej sekwencji zdarzeń, aby sprawdzić, czy `ClockForeColor` Właściwość działa zgodnie z oczekiwaniami.

5. Kliknij przycisk **Zamknij** , aby zamknąć **kontener testów UserControl**.

     W tej sekcji i w powyższych sekcjach pokazano, jak można łączyć składniki i formanty systemu Windows z kodem i opakowaniem, aby zapewnić niestandardowe funkcje w formie złożonego formantu. Wiesz już, jak uwidocznić właściwości w kontrolce złożonej oraz jak przetestować swój formant po jego zakończeniu. W następnej sekcji dowiesz się, jak utworzyć Dziedziczony formant złożony, używając `ctlClock` jako podstawy.

## <a name="inheriting-from-a-composite-control"></a>Dziedziczenie z kontrolki złożonej
 W poprzednich sekcjach przedstawiono sposób łączenia formantów, składników i kodu systemu Windows z kontrolkami złożonymi do wielokrotnego użytku. Formant złożony może być teraz używany jako podstawa, na której można skompilować inne kontrolki. Proces wyprowadzania klasy z klasy bazowej nosi nazwę *dziedziczenia*. W tej sekcji utworzysz formant złożony o nazwie `ctlAlarmClock`. Ten formant będzie pochodzący z jego formantu `ctlClock`nadrzędnego. Dowiesz się, jak zwiększyć funkcjonalność `ctlClock` przez zastępowanie metod nadrzędnych i dodawanie nowych metod i właściwości.

 Pierwszym krokiem tworzenia dziedziczonej kontrolki jest uzyskanie jej z elementu nadrzędnego. Ta akcja tworzy nową kontrolkę, która ma wszystkie właściwości, metody i charakterystyki graficzne kontrolki nadrzędnej, ale może również stanowić podstawę do dodania nowych lub zmodyfikowanych funkcji.

### <a name="to-create-the-inherited-control"></a>Aby utworzyć Dziedziczony formant

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **ctlClockLib**, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Kontrola użytkownika**.

     **Dodaj nowy element** zostanie otwarte okno dialogowe.

2. Wybierz szablon **dziedziczonej kontrolki użytkownika** .

3. W polu **Nazwa** wpisz `ctlAlarmClock.vb`, a następnie kliknij przycisk **Dodaj**.

     Zostanie wyświetlone okno dialogowe **Selektor dziedziczenia** .

4. W obszarze **Nazwa składnika**kliknij dwukrotnie pozycję **ctlClock**.

5. W Eksplorator rozwiązań Przeglądaj bieżące projekty.

    > [!NOTE]
    > Plik o nazwie **ctlAlarmClock. vb** został dodany do bieżącego projektu.

### <a name="adding-the-alarm-properties"></a>Dodawanie właściwości alarmu
 Właściwości są dodawane do dziedziczonej kontrolki w taki sam sposób, w jaki są dodawane do kontrolki złożonej. Teraz użyj składni deklaracji właściwości, aby dodać dwie właściwości do kontrolki: `AlarmTime`, w której będzie przechowywana wartość daty i godziny, w której ma się pojawić alarm, i `AlarmSet`wskazująca, czy alarm jest ustawiony.

#### <a name="to-add-properties-to-your-composite-control"></a>Aby dodać właściwości do kontrolki złożonej

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **ctlAlarmClock**, a następnie kliknij pozycję **Wyświetl kod**.

2. Znajdź deklarację klasy dla kontrolki ctlAlarmClock, która jest wyświetlana `Public Class ctlAlarmClock`jako.  W deklaracji klasy Wstaw następujący kod.

    ```vb
    Private dteAlarmTime As Date
    Private blnAlarmSet As Boolean
    ' These properties will be declared as Public to allow future
    ' developers to access them.
    Public Property AlarmTime() As Date
        Get
            Return dteAlarmTime
        End Get
        Set(ByVal value as Date)
            dteAlarmTime = value
        End Set
    End Property
    Public Property AlarmSet() As Boolean
        Get
            Return blnAlarmSet
        End Get
        Set(ByVal value as Boolean)
            blnAlarmSet = value
        End Set
    End Property
    ```

### <a name="adding-to-the-graphical-interface-of-the-control"></a>Dodawanie do interfejsu graficznego formantu
 Formant dziedziczony ma interfejs wizualny, który jest identyczny z kontrolką, z której dziedziczy. Posiada te same kontrolki elementów, jak jej kontrolki nadrzędne, ale właściwości kontrolek elementów nie będą dostępne, chyba że zostały one jawnie ujawnione. Można dodać do interfejsu graficznego dziedziczonego formantu złożonego w taki sam sposób, jak w przypadku dowolnej kontrolki złożonej. Aby kontynuować dodawanie do interfejsu wizualizacji zegara alarmu, należy dodać kontrolkę etykieta, która będzie Flash, gdy alarm jest dźwiękowy.

#### <a name="to-add-the-label-control"></a>Aby dodać kontrolkę etykieta

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **ctlAlarmClock**, a następnie kliknij pozycję **Projektant widoków**.

     Projektant do `ctlAlarmClock` otwarcia w oknie głównym.

2. Kliknij `lblDisplay` (część wyświetlania kontrolki) i Wyświetl okno właściwości.

    > [!NOTE]
    > Wszystkie właściwości są wyświetlane, są wygaszone. Oznacza to, że te właściwości są natywne `lblDisplay` i nie można ich modyfikować ani uzyskać do nich dostępu w okno właściwości. Domyślnie formanty zawarte w kontrolce złożonej są `Private`, a ich właściwości nie są dostępne w żaden sposób.

    > [!NOTE]
    > Jeśli chcesz, aby inni użytkownicy formantu złożonego mieli dostęp do jego wewnętrznych formantów, zadeklaruj je jako `Public` lub `Protected`. Umożliwi to Ustawianie i modyfikowanie właściwości kontrolek zawartych w kontrolce złożonej przy użyciu odpowiedniego kodu.

3. <xref:System.Windows.Forms.Label> Dodaj kontrolkę do kontrolki złożonej.

4. Za pomocą myszy przeciągnij <xref:System.Windows.Forms.Label> formant bezpośrednio poniżej pola wyświetlania. W okno Właściwości ustaw następujące właściwości.

    |Właściwość|Ustawienie|
    |--------------|-------------|
    |**Nazwa**|`lblAlarm`|
    |**Text**|**Uruchomienia!**|
    |**TextAlign**|`MiddleCenter`|
    |**Widać**|`False`|

### <a name="adding-the-alarm-functionality"></a>Dodawanie funkcji alarmu
 W poprzednich procedurach dodano właściwości i kontrolkę, która spowoduje włączenie funkcji alarmu w formancie złożonym. W ramach tej procedury dodasz kod w celu porównania bieżącego czasu z czasem alarmu i, jeśli są one takie same, do dźwięku i błysku alarmu. Poprzez zastąpienie `Timer1_Tick` `ctlAlarmClock` metody i dodanie do niej dodatkowego kodu, można zwiększyć możliwości programu, zachowując wszystkie nieodłączne funkcje programu `ctlClock`. `ctlClock`

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a>Aby zastąpić metodę Timer1_Tick ctlClock

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock. vb**, a następnie kliknij polecenie **Wyświetl kod**.

2. `Private blnAlarmSet As Boolean` Znajdź instrukcję. Bezpośrednio poniżej, Dodaj następującą instrukcję.

    ```vb
    Dim blnColorTicker as Boolean
    ```

3. `End Class` Znajdź instrukcję w dolnej części strony. Tuż przed `End Class` instrukcją Dodaj następujący kod.

    ```vb
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _
        As System.EventArgs)
        ' Calls the Timer1_Tick method of ctlClock.
        MyBase.Timer1_Tick(sender, e)
        ' Checks to see if the Alarm is set.
        If AlarmSet = False Then
            Exit Sub
        End If
        ' If the date, hour, and minute of the alarm time are the same as
        ' now, flash and beep an alarm.
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _
            AlarmTime.Minute = Now.Minute Then
            ' Sounds an audible beep.
            Beep()
            ' Sets lblAlarmVisible to True, and changes the background color based on the
            ' value of blnColorTicker. The background color of the label will
            ' flash once per tick of the clock.
            lblAlarm.Visible = True
            If blnColorTicker = False Then
                lblAlarm.BackColor = Color.PeachPuff
                blnColorTicker = True
            Else
                lblAlarm.BackColor = Color.Plum
                blnColorTicker = False
            End If
        Else
            ' Once the alarm has sounded for a minute, the label is made
            ' invisible again.
            lblAlarm.Visible = False
        End If
    End Sub
    ```

     Dodanie tego kodu wykonuje kilka zadań. `Overrides` Instrukcja kieruje formant do użycia tej metody zamiast metody, która była dziedziczona z kontrolki podstawowej. Gdy ta metoda jest wywoływana, wywołuje metodę, która zastąpi przez wywoływanie `MyBase.Timer1_Tick` instrukcji, co zapewnia, że wszystkie funkcje wbudowane w pierwotnej kontrolce są odtwarzane w tym formancie. Następnie uruchamia dodatkowy kod w celu uwzględnienia funkcji alarmu. Migająca kontrolka etykieta zostanie wyświetlona, gdy wystąpi alarm, i słychać dźwięk dźwiękowy.

    > [!NOTE]
    > Ponieważ przesłaniasz dziedziczonego programu obsługi zdarzeń, nie trzeba określać zdarzenia za pomocą `Handles` słowa kluczowego. Zdarzenie zostało już podłączane. Wszystkie zastępowanie są implementacją programu obsługi.

     Kontrola zegara alarmu jest niemal ukończona. Jedyną czynnością, która pozostanie, jest zaimplementowanie sposobu jej wyłączenia. W tym celu należy dodać kod do `lblAlarm_Click` metody.

#### <a name="to-implement-the-shutoff-method"></a>Aby zaimplementować metodę ShutOff

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **ctlAlarmClock. vb**, a następnie kliknij pozycję **Projektant widoków**.

2. W projektancie kliknij dwukrotnie pozycję **lblAlarm**. **Edytor kodu** zostanie otwarty `Private Sub lblAlarm_Click` w wierszu.

3. Zmodyfikuj tę metodę, tak aby była podobna do poniższego kodu.

    ```vb
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _
     System.EventArgs) Handles lblAlarm.Click
        ' Turns off the alarm.
        AlarmSet = False
        ' Hides the flashing label.
        lblAlarm.Visible = False
    End Sub
    ```

4. W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.

### <a name="using-the-inherited-control-on-a-form"></a>Używanie dziedziczonej kontrolki w formularzu
 Można testować Dziedziczony formant w taki sam sposób, `ctlClock`w jaki przetestowano formant klasy bazowej: Naciśnij klawisz F5, aby skompilować projekt i uruchomić formant w **kontenerze Test UserControl**. Aby uzyskać więcej informacji, zobacz [jak: Przetestuj zachowanie elementu UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)w czasie wykonywania.

 Aby można było użyć formantu, musisz go hostować w formularzu. Podobnie jak w przypadku standardowej kontroli złożonej, Dziedziczony formant złożony nie może być autonomiczny i musi być hostowany w formie lub w innym kontenerze. Ponieważ `ctlAlarmClock` ma większą głębię funkcjonalności, wymagany jest dodatkowy kod do przetestowania. Ta procedura polega na napisaniu prostego programu w celu przetestowania funkcji programu `ctlAlarmClock`. Napisz kod `AlarmTime` `ctlAlarmClock`, aby ustawić i wyświetlić właściwość, i przetestować jej funkcje.

#### <a name="to-build-and-add-your-control-to-a-test-form"></a>Aby skompilować i dodać formant do formularza testowego

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **ctlClockLib**, a następnie kliknij pozycję **Kompiluj**.

2. W menu **plik** wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**.

3. Dodaj nowy projekt **aplikacji systemu Windows** do rozwiązania i nadaj mu `Test`nazwę.

     Projekt **testowy** zostanie dodany do Eksplorator rozwiązań.

4. W Eksplorator rozwiązań kliknij prawym przyciskiem `Test` myszy węzeł projektu, a następnie kliknij pozycję **Dodaj odwołanie** , aby wyświetlić okno dialogowe **Dodawanie odwołania** .

5. Kliknij kartę z etykietą **projekty**. Projekt **ctlClockLib** zostanie wyświetlony na liście **Nazwa projektu**. Kliknij dwukrotnie pozycję **ctlClockLib** , aby dodać odwołanie do projektu testowego.

6. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **test**, a następnie kliknij polecenie **Kompiluj**.

7. W **przyborniku**rozwiń węzeł **składniki ctlClockLib** .

8. Kliknij dwukrotnie pozycję **ctlAlarmClock** , aby dodać wystąpienie `ctlAlarmClock` do formularza.

9. W **przyborniku**Znajdź i kliknij dwukrotnie pozycję **DateTimePicker** , <xref:System.Windows.Forms.DateTimePicker> aby dodać kontrolkę do <xref:System.Windows.Forms.Label> formularza, a następnie Dodaj kontrolkę, klikając dwukrotnie pozycję **etykieta**.

10. Użyj myszy, aby ustawić kontrolki w wygodnym miejscu w formularzu.

11. Ustaw właściwości tych kontrolek w następujący sposób.

    |formant|Właściwość|Wartość|
    |-------------|--------------|-----------|
    |`label1`|**Text**|`(blank space)`|
    ||**Nazwa**|`lblTest`|
    |`dateTimePicker1`|**Nazwa**|`dtpTest`|
    ||**Formatowanie**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

12. W projektancie kliknij dwukrotnie pozycję **dtpTest**.

     Zostanie otwarty `Private Sub dtpTest_ValueChanged` **Edytor kodu** .

13. Zmodyfikuj kod w taki sposób, aby wyglądał następująco.

    ```vb
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles dtpTest.ValueChanged
        ctlAlarmClock1.AlarmTime = dtpTest.Value
        ctlAlarmClock1.AlarmSet = True
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _
            "hh:mm")
    End Sub
    ```

14. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **test**, a następnie kliknij pozycję **Ustaw jako projekt startowy**.

15. Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.

     Zostanie uruchomiony program testowy. Należy pamiętać, że bieżący czas jest aktualizowany w `ctlAlarmClock` kontrolce, a czas rozpoczęcia jest pokazywany <xref:System.Windows.Forms.DateTimePicker> w formancie.

16. <xref:System.Windows.Forms.DateTimePicker> Kliknij miejsce, gdzie są wyświetlane minuty godziny.

17. Korzystając z klawiatury, ustaw wartość minut na minutę, która jest większa niż bieżąca godzina pokazana przez `ctlAlarmClock`.

     Godzina ustawienia alarmu jest pokazywana w `lblTest`. Poczekaj, aż wyświetlany czas osiągnie czas ustawienia alarmu. Gdy wyświetlany czas osiągnie czas, w którym ustawiono alarm, dźwięk zostanie dźwiękowy i `lblAlarm` rozpocznie się błysk.

18. Wyłącz alarm, klikając pozycję `lblAlarm`. Teraz możesz zresetować alarm.

     W tym instruktażu przedstawiono szereg kluczowych pojęć. Wiesz już, jak utworzyć formant złożony przez połączenie formantów i składników do kontenera kontroli złożonej. Wiesz już, jak dodać właściwości do kontrolki i napisać kod w celu zaimplementowania funkcji niestandardowych. W ostatniej sekcji pokazano, jak zwiększyć funkcjonalność danego formantu złożonego przez dziedziczenie i zmienić funkcjonalność metod hosta, zastępując te metody.

## <a name="see-also"></a>Zobacz także

- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
- [Instrukcje: Tworzenie złożonych kontrolek](how-to-author-composite-controls.md)
- [Instrukcje: Wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
