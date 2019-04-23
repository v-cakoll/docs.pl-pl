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
ms.openlocfilehash: 6404e5933f886578b4ad8afd0d3da324541fc3f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299985"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a>Przewodnik: tworzenie kontrolki złożonej za pomocą Visual Basic
Formanty złożone umożliwiają za pomocą którego niestandardowe interfejsy graficzne można tworzyć i ponownie używane. Formant złożony jest zasadniczo składnika za pomocą wizualnej reprezentacji. W efekcie może składać się z co najmniej Windows Forms formantów, składników lub bloki kodu, które mogą rozszerzyć funkcjonalność, sprawdzanie poprawności danych wejściowych użytkownika, modyfikując właściwości wyświetlania lub wykonywania innych zadań wymaganych przez autora. Formanty złożone można umieścić na formularzach Windows Forms w taki sam sposób jak inne kontrolki. W pierwszej części tego przewodnika, tworzenie prostego formantu złożonego o nazwie `ctlClock`. W drugiej części tego przewodnika, możesz rozszerzyć funkcjonalność `ctlClock` poprzez dziedziczenie.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Podczas tworzenia nowego projektu można określić jego nazwę, aby ustawić głównej przestrzeni nazw, nazwa zestawu i nazwa projektu i upewnij się, że składnik domyślną będzie poprawną przestrzeń nazw.  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Aby utworzyć ctlClockLib Biblioteka kontrolek i kontrola ctlClock  
  
1. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu** otworzyć **nowy projekt** okno dialogowe.  
  
2. Wybierz z listy projektów języka Visual Basic, **Biblioteka formantów Windows** szablon projektu, należy wpisać `ctlClockLib` w **nazwa** , a następnie kliknij przycisk **OK**.  
  
     Nazwa projektu `ctlClockLib`, również jest domyślnie przypisane do głównej przestrzeni nazw. Główna przestrzeń nazw są używane do kwalifikowania nazwy elementów w zestawie. Na przykład, jeśli dwa zestawy zawiera składniki o nazwie `ctlClock`, możesz określić swoje `ctlClock` za pomocą składnika `ctlClockLib.ctlClock.`  
  
3. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **UserControl1.vb**, a następnie kliknij przycisk **Zmień nazwę**. Zmień nazwę pliku, aby `ctlClock.vb`. Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu "UserControl1".  
  
    > [!NOTE]
    >  Domyślnie przez kontrolki złożonej dziedziczy <xref:System.Windows.Forms.UserControl> klasy udostępnianej przez system. <xref:System.Windows.Forms.UserControl> Zapewnia funkcje wymagane przez formanty złożone wszystkie klasy i implementuje standardowe metody i właściwości.  
  
4. Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Dodawanie Windows kontrolek i składników do kontrolek złożonych  
 Interfejs graficzny jest integralną część złożonego formantu. Ten interfejs graficzny jest implementowany przez dodanie jednego lub kilku formantów Windows do powierzchni projektanta. W poniższy pokaz możesz zintegrować formanty Windows złożonego formantu i napisać kod, aby zaimplementować funkcje.  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Aby dodać etykietę i czasomierz do złożonego formantu  
  
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.vb**, a następnie kliknij przycisk **Projektant widoków**.  
  
2. W przyborniku, rozwiń węzeł **wspólnych formantów** węzłem, a następnie kliknij dwukrotnie plik **etykiety**.  
  
     A <xref:System.Windows.Forms.Label> formantu o nazwie `Label1` zostanie dodany do formantu na powierzchni projektowej.  
  
3. W projektancie, kliknij **Label1**. W oknie właściwości ustaw następujące właściwości.  
  
    |Właściwość|Zmień na|  
    |--------------|---------------|  
    |**Nazwa**|`lblDisplay`|  
    |**Text**|`(blank space)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4. W **przybornika**, rozwiń węzeł **składniki** węzłem, a następnie kliknij dwukrotnie plik **czasomierza**.  
  
     Ponieważ <xref:System.Windows.Forms.Timer> jest składnikiem, ma ona nie wizualnej reprezentacji w czasie wykonywania. W związku z tym nie wydaje się za pomocą kontrolek na powierzchni projektowej, ale raczej w Projektancie składników (zasobnik w dolnej części powierzchni projektanta).  
  
5. W Projektancie składników kliknij **Timer1**, a następnie ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwości `1000` i <xref:System.Windows.Forms.Timer.Enabled%2A> właściwości `True`.  
  
     <xref:System.Windows.Forms.Timer.Interval%2A> Właściwość określa częstotliwość, z którym znaczniki składnika timer. Każdorazowo `Timer1` znaczniki, uruchamia kod `Timer1_Tick` zdarzeń. Interwał reprezentuje liczbę milisekund między taktami.  
  
6. W Projektancie składników, kliknij dwukrotnie **Timer1** można przejść do `Timer1_Tick` zdarzenie `ctlClock`.  
  
7. Należy zmodyfikować kod, tak aby wyglądała jak poniższy przykładowy kod. Pamiętaj zmieniać modyfikatora dostępu z `Private` do `Protected`.  
  
    ```vb  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     Ten kod powoduje, że bieżący czas, który ma być wyświetlany w `lblDisplay`. Ponieważ interwał `Timer1` została ustawiona na `1000`, to zdarzenie wystąpi co tysięcy milisekund, w związku z tym aktualizacji bieżący czas co sekundę.  
  
8. Zmodyfikuj metodę możliwym do zastąpienia. Aby uzyskać więcej informacji zobacz sekcję "Dziedziczenie z kontrolki użytkownika" poniżej.  
  
    ```vb  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.  
  
## <a name="adding-properties-to-the-composite-control"></a>Dodawanie właściwości do kontrolek złożonych  
 Formant zegara teraz hermetyzuje <xref:System.Windows.Forms.Label> kontroli i <xref:System.Windows.Forms.Timer> składnika, z których każdy swój własny zestaw właściwości związanych. Gdy poszczególne właściwości tych kontrolek nie będą dostępne dla użytkowników kolejne kontrolki, można tworzyć i udostępnianie właściwości niestandardowych, pisząc odpowiednich bloków kodu. W poniższej procedurze będzie dodać właściwości do formantu, który umożliwia użytkownikowi zmianę koloru tła i tekstu.  
  
#### <a name="to-add-a-property-to-your-composite-control"></a>Aby dodać właściwości do kontrolki złożonej  
  
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.vb**, a następnie kliknij przycisk **Wyświetl kod**.  
  
     Zostanie otwarty Edytor kodu dla formantu.  
  
2. Znajdź `Public Class ctlClock` instrukcji. Znajdujące się poniżej wpisz następujący kod.  
  
    ```vb  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     Te instrukcje tworzenia zmienne prywatne, które będą używane do przechowywania wartości właściwości, które masz zamiar utworzyć.  
  
3. Wstaw następujący kod pod deklaracje zmiennych w kroku 2.  
  
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
  
     Poprzedzający kod wprowadza dwie właściwości niestandardowe, `ClockForeColor` i `ClockBackColor`, która jest dostępna dla kolejnych użytkowników tej kontrolki, wywołując `Property` instrukcji. `Get` i `Set` instrukcji zapewniać przechowywania i pobierania wartości właściwości, a także kod do implementacji funkcji odpowiednich właściwości.  
  
4. Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.  
  
## <a name="testing-the-control"></a>Testowanie kontrolki  
 Formanty nie są autonomiczne projektów; muszą one być obsługiwane w kontenerze. Testowanie zachowania w czasie wykonywania kontroli nad i sprawdzić jego właściwości, za pomocą **UserControl — kontener testowy**. Aby uzyskać więcej informacji, zobacz [jak: Testowanie zachowania UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### <a name="to-test-your-control"></a>Aby przetestować formant  
  
1. Naciśnij klawisz F5, aby skompilować projekt i uruchomić Twoją kontrolą w **UserControl — kontener testowy**.  
  
2. W siatce właściwości kontener testu, wybierz `ClockBackColor` właściwości, a następnie kliknij strzałkę listy rozwijanej do wyświetlania palety kolorów.  
  
3. Wybierz kolor, klikając go.  
  
     Kolor tła kontrolki zmienia kolor, który wybrano.  
  
4. Upewnij się, że za pomocą sekwencji podobnych zdarzeń `ClockForeColor` właściwości działa zgodnie z oczekiwaniami.  
  
5. Kliknij przycisk **Zamknij** zamknąć **UserControl — kontener testowy**.  
  
     W poprzedniej sekcji i w tej sekcji, wiesz, jak można łączyć składników i formantów Windows z kodem i pakowania do dostarczają niestandardowych funkcjonalności w formie kontrolek złożonych. Wiesz, że udostępnianie właściwości złożonej kontrolki i testowanie formantu po jego zakończeniu. W następnej sekcji zostanie dowiesz się, jak skonstruować dziedziczone kontrolki złożonej za pomocą `ctlClock` jako podstawy.  
  
## <a name="inheriting-from-a-composite-control"></a>Dziedziczenie z kontrolki złożonej  
 W poprzednich sekcjach wiesz, jak połączyć kontrolki Windows, składników i kod do kontrolek złożonych wielokrotnego użytku. Złożonego formantu może być teraz używane jako podstawa, na którym mogą być wbudowane w innych kontrolek. Wyprowadzanie klasy z klasy bazowej proces jest nazywany *dziedziczenia*. W tej sekcji spowoduje utworzenie kontrolki złożonej o nazwie `ctlAlarmClock`. Ta kontrolka będzie pochodzić z kontrolki nadrzędnej, `ctlClock`. Jak rozszerzyć funkcjonalność `ctlClock` nadpisywania metod nadrzędnego i dodawania nowych metod i właściwości.  
  
 Pierwszym krokiem w tworzeniu odziedziczoną kontrolkę jest pochodną jego obiektu nadrzędnego. Ta akcja tworzy nowy formant, który zawiera wszystkie właściwości, metod i właściwości graficzne kontroli nadrzędnej, ale mogą również działać jako podstawa dla nowych lub zmodyfikowanych funkcja.  
  
#### <a name="to-create-the-inherited-control"></a>Aby utworzyć odziedziczoną kontrolkę  
  
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **kontrolki użytkownika**.  
  
     **Dodaj nowy element** zostanie otwarte okno dialogowe.  
  
2. Wybierz **dziedziczone kontrolki użytkownika** szablonu.  
  
3. W **nazwa** wpisz `ctlAlarmClock.vb`, a następnie kliknij przycisk **Dodaj**.  
  
     **Selektor dziedziczenia** pojawi się okno dialogowe.  
  
4. W obszarze **nazwa składnika**, kliknij dwukrotnie **ctlClock**.  
  
5. W Eksploratorze rozwiązań należy przejrzeć bieżących projektów.  
  
    > [!NOTE]
    >  Plik o nazwie **ctlAlarmClock.vb** został dodany do bieżącego projektu.  
  
### <a name="adding-the-alarm-properties"></a>Dodawanie właściwości alarmów  
 Właściwości są dodawane do odziedziczoną kontrolkę w taki sam sposób, w których są one dodawane do kontrolek złożonych. Teraz użyjesz Składnia deklaracji właściwości można dodać dwie właściwości do kontrolki: `AlarmTime`, której będzie przechowywana wartość daty i godziny alarmu jest wyłączona, a `AlarmSet`, który będzie wskazywać, czy ustawiono alarmu.  
  
##### <a name="to-add-properties-to-your-composite-control"></a>Aby dodać właściwości do kontrolki złożonej  
  
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij przycisk **Wyświetl kod**.  
  
2. Znajdź deklarację klasy dla formantu ctlAlarmClock, który jest wyświetlany jako `Public Class ctlAlarmClock`.  W deklaracji klasy Wstaw następujący kod.  
  
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
 Odziedziczone kontrolki ma interfejs graficzny, która jest taka sama jak formant, który dziedziczy. Posiada on te same kontrolki składowych co kontrolki nadrzędnej, ale właściwości formantów składowych nie będzie dostępna, chyba że zostały one specjalnie ujawnione. Można dodać do graficznego interfejsu dziedziczone złożonego formantu w taki sam sposób jak należy dodać do dowolnego złożonego formantu. Aby kontynuować, dodając do zegar alarm wizualny interfejs, dodasz formant etykiety, który będzie flash, gdy jest podawania alarmu.  
  
##### <a name="to-add-the-label-control"></a>Aby dodać formant etykiety  
  
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**i kliknij przycisk **Projektant widoków**.  
  
     Projektant `ctlAlarmClock` otwiera się w głównym oknie.  
  
2. Kliknij przycisk `lblDisplay` (wyświetlanie części kontrolki) i wyświetlić okno właściwości.  
  
    > [!NOTE]
    >  Chociaż wyświetlane są wszystkie właściwości, są niedostępne. Oznacza to, że te właściwości są natywne `lblDisplay` i nie może zostać zmodyfikowany lub dostępne w oknie dialogowym właściwości. Domyślnie są zawarte w kontrolki złożonej kontrolki `Private`, i ich właściwości nie są dostępne w jakikolwiek sposób.  
  
    > [!NOTE]
    >  Kolejni użytkownicy złożonej kontrolki mają mieć dostęp do jego wewnętrznych kontroli, zadeklarować je jako `Public` lub `Protected`. To pozwala ustawić i zmodyfikować właściwości formantów zawartych w złożonej kontrolki przy użyciu odpowiedniego kodu.  
  
3. Dodaj <xref:System.Windows.Forms.Label> kontrolki złożonej kontrolki.  
  
4. Za pomocą myszy, przeciągnij <xref:System.Windows.Forms.Label> formantu bezpośrednio poniżej wyświetlanego pola. W oknie właściwości ustaw następujące właściwości.  
  
    |Właściwość|Ustawienie|  
    |--------------|-------------|  
    |**Nazwa**|`lblAlarm`|  
    |**Text**|**Alarm!**|  
    |**TextAlign**|`MiddleCenter`|  
    |**Widoczne**|`False`|  
  
### <a name="adding-the-alarm-functionality"></a>Dodawanie funkcji alarmów  
 W ramach poprzednich procedur dodać właściwości i formant, który spowoduje włączenie funkcji alarmu w złożonej kontrolki. W tej procedurze należy dodać kod do porównania bieżącego czasu do czasu alarmów i, jeśli są takie same, dźwięk i flash alarmu. Przez zastąpienie `Timer1_Tick` metody `ctlClock` i dodanie dodatkowego kodu do niego, zostaną rozszerzone możliwości `ctlAlarmClock` przy zachowaniu wszystkich funkcji związanych z `ctlClock`.  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a>Aby zastąpić metodę Timer1_Tick ctlClock  
  
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock.vb**, a następnie kliknij przycisk **Wyświetl kod**.  
  
2. Znajdź `Private blnAlarmSet As Boolean` instrukcji. Bezpośrednio pod nim, należy dodać następującą instrukcję.  
  
    ```vb  
    Dim blnColorTicker as Boolean  
    ```  
  
3. Znajdź `End Class` instrukcji w dolnej części strony. Tuż przed `End Class` instrukcji, Dodaj następujący kod.  
  
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
  
     Dodanie tego kodu w ramach kilku zadań. `Overrides` Instrukcja określa, że formant Aby użyć tej metody, zamiast metody, która została odziedziczona z bazowej. Gdy ta metoda jest wywoływana, wywołuje metodę, zastępuje ona wywołując `MyBase.Timer1_Tick` instrukcji, zapewniając wszystkich funkcji włączonych oryginalnego formantu jest przedstawiony w tym elemencie sterującym. Następnie działa dodatkowego kodu, aby włączać funkcje alarmu. Formant etykiety migające pojawi się alarm występuje, gdy sygnały dźwiękowe będzie Twój głos zostanie wysłuchany.  
  
    > [!NOTE]
    >  Ponieważ są zastępują program obsługi zdarzeń dziedziczone, nie należy określić to zdarzenie o `Handles` — słowo kluczowe. Zdarzenie jest już podłączony. Wszystko, co jest zastąpienie stanowi implementację programu obsługi.  
  
     Formant alarm zegara jest niemal ukończone. Jest jedynym elementem, który pozostaje do zaimplementowania sposób, aby je wyłączyć. Aby to zrobić, można dodać kod `lblAlarm_Click` metody.  
  
##### <a name="to-implement-the-shutoff-method"></a>Aby wdrożyć metodę bliskie  
  
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock.vb**, a następnie kliknij przycisk **Projektant widoków**.  
  
2. W projektancie, kliknij dwukrotnie **lblAlarm**. **Edytor kodu** otwiera `Private Sub lblAlarm_Click` wiersza.  
  
3. Zmodyfikuj tę metodę, tak, aby wyglądała jak poniższy kod.  
  
    ```vb  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4. Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.  
  
### <a name="using-the-inherited-control-on-a-form"></a>Za pomocą odziedziczoną kontrolkę w formularzu  
 Można przetestować kontroli nad dziedziczone przetestowane kontrolki klasy bazowej, tak samo `ctlClock`: Naciśnij klawisz F5, aby skompilować projekt i uruchomić Twoją kontrolą w **UserControl — kontener testowy**. Aby uzyskać więcej informacji, zobacz [jak: Testowanie zachowania UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Aby przełączyć kontrolki do użycia, należy ją hostować na formularzu. Podobnie jak w przypadku złożonego formantu standardowego dziedziczone złożonego formantu nie może występować samodzielnie i musi być hostowany w formie lub innego kontenera. Ponieważ `ctlAlarmClock` ma większą głębokość funkcjonalności, dodatkowy kod jest wymagany do testowania. W tej procedurze, jak napisać prosty program, aby przetestować działanie `ctlAlarmClock`. Możesz napisać kod, aby ustawić i wyświetlić `AlarmTime` właściwość `ctlAlarmClock`i przetestujesz jej nieodłączne funkcji.  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a>Tworzenie i dodawanie formantu do formularza testu  
  
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, a następnie kliknij przycisk **kompilacji**.  
  
2. Na **pliku** menu wskaż **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
3. Dodaj nową **aplikacji Windows** projektu do rozwiązania i nadaj mu nazwę `Test`.  
  
     **Testu** projekt jest dodawany do Eksploratora rozwiązań.  
  
4. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy `Test` węzła projektu, a następnie kliknij przycisk **Dodaj odwołanie** do wyświetlenia **Dodaj odwołanie** okno dialogowe.  
  
5. Kliknij kartę **projektów**. Projekt **ctlClockLib** zostaną wyświetlone w obszarze **Nazwa projektu**. Kliknij dwukrotnie **ctlClockLib** można dodać odwołania do projektu testowego.  
  
6. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **testu**, a następnie kliknij przycisk **kompilacji**.  
  
7. W **przybornika**, rozwiń węzeł **ctlClockLib składniki** węzła.  
  
8. Kliknij dwukrotnie **ctlAlarmClock** można dodać wystąpienia `ctlAlarmClock` do formularza.  
  
9. W **przybornika**, zlokalizuj i kliknij dwukrotnie **DateTimePicker** dodać <xref:System.Windows.Forms.DateTimePicker> sterowania do formularza, a następnie dodaj <xref:System.Windows.Forms.Label> kontroli przez dwukrotne kliknięcie **etykiety**.  
  
10. Umieść formanty w wygodne miejsce w formularzu za pomocą myszy.  
  
11. Ustaw właściwości tych kontrolek, w następujący sposób.  
  
    |formant|Właściwość|Wartość|  
    |-------------|--------------|-----------|  
    |`label1`|**Text**|`(blank space)`|  
    ||**Nazwa**|`lblTest`|  
    |`dateTimePicker1`|**Nazwa**|`dtpTest`|  
    ||**Format**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
12. W projektancie, kliknij dwukrotnie **dtpTest**.  
  
     **Edytor kodu** otwiera `Private Sub dtpTest_ValueChanged`.  
  
13. Zmodyfikuj kod, dzięki czemu jest podobny do następującego.  
  
    ```vb  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **testu**, a następnie kliknij przycisk **Ustaw jako projekt startowy**.  
  
15. Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.  
  
     Zostanie uruchomiony test program. Należy pamiętać, że bieżący czas jest aktualizowana w `ctlAlarmClock` kontroli i że godzina rozpoczęcia jest wyświetlany w <xref:System.Windows.Forms.DateTimePicker> kontroli.  
  
16. Kliknij przycisk <xref:System.Windows.Forms.DateTimePicker> gdzie minuty godziny są wyświetlane.  
  
17. Za pomocą klawiatury, ustaw wartość minut, która jest większa niż bieżąca godzina wyświetlane według jedną minutę `ctlAlarmClock`.  
  
     Czas ustawienie alarmu jest wyświetlany w `lblTest`. Poczekaj, aż wyświetlonym czasie osiągnąć czas ustawienie alarmu. Po wyświetlonym czasie osiągnie czas, w którym ustawiono alarmu, dźwięku dźwiękowe i `lblAlarm` będzie flash.  
  
18. Wyłączyć alarm, klikając `lblAlarm`. Może teraz zresetować alarmu.  
  
     W tym przewodniku ma obejmujący wiele kluczowych założeń. Wiesz, że tworzenie formantu złożonego, łącząc w kontenerze kontrolek złożonych kontrolek i składników. Wiesz, można dodać właściwości do kontrolki, a następnie napisać kod do implementacji funkcji niestandardowych. W ostatniej sekcji pokazano, aby rozszerzyć funkcjonalność danej kontrolki złożonej za pomocą dziedziczenia i zmieniać funkcje metod hosta przez zastąpienie tych metod.  
  
## <a name="see-also"></a>Zobacz także

- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
- [Instrukcje: Formanty złożone autora](how-to-author-composite-controls.md)
- [Instrukcje: Wyświetlanie kontroli w wybierz elementy przybornika — okno dialogowe](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
