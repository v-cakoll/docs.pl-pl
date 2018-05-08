---
title: 'Wskazówki: tworzenie formantu złożonego za pomocą Visual Basic'
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
ms.openlocfilehash: d919112cf1a1462b4a60ef6dbdf60798d72c3e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a>Wskazówki: tworzenie formantu złożonego za pomocą Visual Basic
Formanty złożone umożliwiają za pomocą którego niestandardowych interfejsów graficznego można tworzyć i użyć ponownie. Formantu złożonego jest zasadniczo składnik o wizualnej reprezentacji. W efekcie może składać się z co najmniej jeden program Windows Forms kontrolki, składniki lub bloki kodu, które mogą rozszerzyć funkcjonalność, sprawdzanie poprawności danych wejściowych użytkownika, modyfikując właściwości ekranu lub wykonywania innych zadań wymaganych przez autora. Formanty złożone można umieścić w formularzach systemu Windows w taki sam sposób jak inne formanty. W pierwszej części tego przewodnika, tworzenie prostego formantu złożonego o nazwie `ctlClock`. W drugiej części tego przewodnika, można rozszerzyć funkcjonalność `ctlClock` przez dziedziczenie.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Podczas tworzenia nowego projektu można określić jego nazwę, aby ustawić głównej przestrzeni nazw, nazwa zestawu i nazwa projektu i upewnij się, że składnik domyślna będzie poprawną przestrzeń nazw.  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Aby utworzyć biblioteki formantu ctlClockLib i kontroli ctlClock  
  
1.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu** otworzyć **nowy projekt** okno dialogowe.  
  
2.  Wybierz z listy projektów programu Visual Basic, **Biblioteka formantów systemu Windows** szablon projektu, typ `ctlClockLib` w **nazwa** , a następnie kliknij przycisk **OK**.  
  
     Nazwa projektu `ctlClockLib`, jest również przypisany do głównej przestrzeni nazw domyślnie. Główna przestrzeń nazw są używane do kwalifikowania nazwy elementów w zestawie. Na przykład, jeśli dwa zestawy zawiera składniki o nazwie `ctlClock`, można określić użytkownika `ctlClock` za pomocą składnika `ctlClockLib.ctlClock.`  
  
3.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **UserControl1.vb**, a następnie kliknij przycisk **zmienić**. Zmień nazwę pliku, aby `ctlClock.vb`. Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu "UserControl1".  
  
    > [!NOTE]
    >  Domyślnie formantu złożonego dziedziczy <xref:System.Windows.Forms.UserControl> klasy obsługiwanych przez system. <xref:System.Windows.Forms.UserControl> Klasa udostępnia funkcje wymagane przez formanty wszystkie złożone i implementuje standardowe metody i właściwości.  
  
4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Dodawanie Windows formanty i składniki do złożonych kontrolek  
 Wizualny interfejs jest integralną część złożonego formantu. Ten interfejs visual jest implementowany przez dodanie jednego lub kilku formantów systemu Windows na powierzchnię projektanta. W następujących wykazanie możesz dołączyć formantów systemu Windows do formantu złożonego i napisać kod do implementacji funkcji.  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Aby dodać etykietę i czasomierz do formantu złożonego  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.vb**, a następnie kliknij przycisk **Widok projektanta**.  
  
2.  W przyborniku rozwiń **formanty standardowe** węzeł, a następnie kliknij dwukrotnie plik **etykiety**.  
  
     A <xref:System.Windows.Forms.Label> formantu o nazwie `Label1` zostanie dodany do formantu na powierzchnię projektanta.  
  
3.  W projektancie, kliknij **Label1**. W oknie właściwości ustaw następujące właściwości.  
  
    |Właściwość|Zmień na|  
    |--------------|---------------|  
    |**Nazwa**|`lblDisplay`|  
    |**Tekst**|`(blank space)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  W **przybornika**, rozwiń węzeł **składniki** węzeł, a następnie kliknij dwukrotnie plik **czasomierza**.  
  
     Ponieważ <xref:System.Windows.Forms.Timer> to składnik go nie ma reprezentacji wizualnej w czasie wykonywania. W związku z tym nie ma z formantami na powierzchni projektanta, ale w Projektancie składników (na pasku zadań u dołu powierzchni projektanta).  
  
5.  W Projektancie składników, kliknij przycisk **czasomierz 1**, a następnie ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwości `1000` i <xref:System.Windows.Forms.Timer.Enabled%2A> właściwości `True`.  
  
     <xref:System.Windows.Forms.Timer.Interval%2A> Właściwość kontroluje częstotliwość, z którym składnika timer znaczników. Zawsze `Timer1` znaczniki, go uruchamia kod w `Timer1_Tick` zdarzeń. Interwał reprezentuje liczbę milisekund między taktami.  
  
6.  W Projektancie składników, kliknij dwukrotnie **czasomierz 1** można przejść do `Timer1_Tick` zdarzenia dla `ctlClock`.  
  
7.  Zmodyfikuj kod, aby go podobny Poniższy przykładowy kod. Należy zmienić modyfikator dostępu z `Private` do `Protected`.  
  
    ```vb  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     Ten kod spowoduje, że bieżący czas, który będzie wyświetlany w `lblDisplay`. Ponieważ interwał `Timer1` ustawiono `1000`, to zdarzenie wystąpi co tysięcy milisekund, w związku z tym aktualizowanie bieżący czas ciągu sekundy.  
  
8.  Zmodyfikuj metodę, aby możliwym do zastąpienia. Aby uzyskać więcej informacji zobacz sekcję "Dziedziczy z kontrolki użytkownika" poniżej.  
  
    ```vb  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.  
  
## <a name="adding-properties-to-the-composite-control"></a>Dodawanie właściwości do złożonych kontrolek  
 Teraz hermetyzuje formantu zegara <xref:System.Windows.Forms.Label> kontroli i <xref:System.Windows.Forms.Timer> z zestawem właściwości związanego z używaniem składnika. Podczas poszczególnych właściwości tych kontrolek nie będzie dostępna dla kolejnych użytkowników formantu, można tworzyć i ujawnia właściwości niestandardowe pisząc odpowiednie bloki kodu. W poniższej procedurze właściwości doda do formantu, który umożliwia użytkownikowi zmianę koloru tła i tekstu.  
  
#### <a name="to-add-a-property-to-your-composite-control"></a>Aby dodać właściwość do formantu złożonego  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.vb**, a następnie kliknij przycisk **kod widoku**.  
  
     Otwiera edytora kodu dla formantu.  
  
2.  Zlokalizuj `Public Class ctlClock` instrukcji. Poniżej wpisz następujący kod.  
  
    ```vb  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     Te instrukcje tworzenia zmiennych prywatnych, które będzie używany do przechowywania wartości właściwości, które zostały utworzone.  
  
3.  Wstaw następujący kod pod deklaracje zmiennej w kroku 2.  
  
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
  
     Poprzedni kod sprawia, że dwie właściwości niestandardowej, `ClockForeColor` i `ClockBackColor`, dostępne dla użytkowników kolejnych tego formantu, wywołując `Property` instrukcji. `Get` i `Set` zapewniają instrukcje dla magazynu i pobierania wartości właściwości, a także kod do implementowania odpowiednie właściwości.  
  
4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.  
  
## <a name="testing-the-control"></a>Testowanie formantu  
 Formanty nie są autonomicznych projektów; muszą one być obsługiwane w kontenerze. Testowanie zachowania w czasie wykonywania formantu i wykonywania jej właściwości z **kontener testu UserControl**. Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### <a name="to-test-your-control"></a>Aby przetestować formantu  
  
1.  Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontrolę w **kontener testu UserControl**.  
  
2.  Kontener testu siatki właściwości, wybierz `ClockBackColor` właściwości, a następnie kliknij strzałkę listy rozwijanej do wyświetlania paletę kolorów.  
  
3.  Wybierz kolor, klikając go.  
  
     Kolor wybranego zmienia kolor tła formantu.  
  
4.  Sprawdź, czy za pomocą sekwencji podobnych zdarzeń `ClockForeColor` właściwości działa zgodnie z oczekiwaniami.  
  
5.  Kliknij przycisk **zamknąć** zamknąć **kontener testu UserControl**.  
  
     W tej sekcji i poprzednich sekcjach, już wspomniano, jak można łączyć składników i formantów systemu Windows z kodem i pakowania umożliwiają korzystanie z funkcji niestandardowych w formie formantu złożonego. Wiesz już ujawnić właściwości formantu złożonego i testowanie formantu po zakończeniu. W następnej sekcji dowiesz sposób tworzenia dziedziczonych formantu złożonego za pomocą `ctlClock` jako podstawy.  
  
## <a name="inheriting-from-a-composite-control"></a>Dziedziczenie z formantu złożonego  
 W poprzednich sekcjach przedstawiono sposób łączenia formantów systemu Windows, składników i kodu w wielokrotnego użytku formanty złożone. Można teraz używać formantu złożonego jako podstawa, na których mogą być tworzone na inne formanty. Wyprowadzanie klasy z klasy podstawowej proces jest nazywany *dziedziczenia*. W tej sekcji utworzysz formantu złożonego o nazwie `ctlAlarmClock`. Ten formant będzie pochodzić z kontrolki nadrzędnej, `ctlClock`. Dowiesz się rozszerzyć funkcjonalność `ctlClock` przez zastąpienie metody nadrzędnego i dodawanie nowych metod i właściwości.  
  
 Pierwszym krokiem tworzenia dziedziczonych kontrolek jest pochodną nadrzędnego. Ta akcja tworzy nowy formant, który zawiera wszystkie właściwości, metody i właściwości graficzne kontrolki nadrzędnej, ale mogą również działać jako podstawa dla nowych lub zmodyfikowanych funkcja.  
  
#### <a name="to-create-the-inherited-control"></a>Można utworzyć formantu dziedziczonych  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **kontrolki użytkownika**.  
  
     **Dodaj nowy element** zostanie otwarte okno dialogowe.  
  
2.  Wybierz **dziedziczone kontrolki użytkownika** szablonu.  
  
3.  W **nazwa** wpisz `ctlAlarmClock.vb`, a następnie kliknij przycisk **Dodaj**.  
  
     **Selektora dziedziczenia** zostanie wyświetlone okno dialogowe.  
  
4.  W obszarze **nazwa składnika**, kliknij dwukrotnie **ctlClock**.  
  
5.  W Eksploratorze rozwiązań przeglądać bieżących projektów.  
  
    > [!NOTE]
    >  Plik o nazwie **ctlAlarmClock.vb** został dodany do bieżącego projektu.  
  
### <a name="adding-the-alarm-properties"></a>Dodawanie właściwości alarmu  
 Właściwości są dodawane do formantu dziedziczone w taki sam sposób, są one dodawane do formantu złożonego. Teraz użyje składni deklaracji właściwości można dodać dwóch właściwości do formantu: `AlarmTime`, który będzie przechowywać wartość daty i godziny alarm jest wyłączona, i `AlarmSet`, który będzie wskazywać, czy ustawiono alarm.  
  
##### <a name="to-add-properties-to-your-composite-control"></a>Aby dodać właściwości do formantu złożonego  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij przycisk **kod widoku**.  
  
2.  Zlokalizuj deklaracja klasy formantu ctlAlarmClock, który jest wyświetlany jako `Public Class ctlAlarmClock`.  W deklaracji klasy wstaw poniższy kod.  
  
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
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a>Dodawanie do formantu interfejsu graficznego  
 Dziedziczony formantu ma wizualny interfejs, który jest taki sam jak formant, który dziedziczy z. Posiada tego samego formanty składników jako kontrolki nadrzędnej, ale właściwości formantów składowych nie będą dostępne, chyba że zostały one specjalnie widoczne. Można dodać do interfejsu graficznego dziedziczone formantu złożonego w taki sam sposób, jak z żadnym formantem złożonego. Aby kontynuować, dodawanie do wizualny interfejs zegar alarmu, należy dodać formant etykiety, który będzie flash, gdy jest podawania alarm.  
  
##### <a name="to-add-the-label-control"></a>Aby dodać formantu etykiety  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**i kliknij przycisk **Widok projektanta**.  
  
     Projektant `ctlAlarmClock` w głównym oknie zostanie otwarta.  
  
2.  Kliknij przycisk `lblDisplay` (wyświetlania część kontrolka) i wyświetlić okno właściwości.  
  
    > [!NOTE]
    >  Gdy wyświetlane są wszystkie właściwości, są niedostępne. Oznacza to, że te właściwości są macierzysty `lblDisplay` i nie można zmodyfikować lub dostępne w oknie właściwości. Domyślnie formantach zawartych w kontrolce złożone są `Private`, i ich właściwości nie są dostępne w jakikolwiek sposób.  
  
    > [!NOTE]
    >  Kolejni użytkownicy złożonego formantu do dostępu do jego kontrole wewnętrzne należy zadeklarować je jako `Public` lub `Protected`. Umożliwi to ustawienie i modyfikowanie właściwości kontrolki zawartych w formantu złożonego za pomocą odpowiedni kod.  
  
3.  Dodaj <xref:System.Windows.Forms.Label> formantu złożonego formantu.  
  
4.  Za pomocą myszy, przeciągnij <xref:System.Windows.Forms.Label> formantu natychmiast poniżej wyświetlanego pola. W oknie właściwości ustaw następujące właściwości.  
  
    |Właściwość|Ustawienie|  
    |--------------|-------------|  
    |**Nazwa**|`lblAlarm`|  
    |**Tekst**|**Alarm!**|  
    |**TextAlign**|`MiddleCenter`|  
    |**Widoczne**|`False`|  
  
### <a name="adding-the-alarm-functionality"></a>Dodawanie funkcji alarmu  
 W ramach poprzednich procedur dodać właściwości i kontrolkę, która spowoduje włączenie funkcji alarm złożonego formantu. W tej procedurze zostanie Dodaj kod, aby porównany bieżący czas na czas alarmu i, jeśli są one takie same, dźwiękowe i alarmu flash. Przez zastąpienie `Timer1_Tick` metody `ctlClock` i dodanie dodatkowego kodu do niego, zostaną rozszerzyć możliwości `ctlAlarmClock` przy zachowaniu wszystkie funkcje związane z `ctlClock`.  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a>Aby zastąpić metodę Timer1_Tick ctlClock  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock.vb**, a następnie kliknij przycisk **kod widoku**.  
  
2.  Zlokalizuj `Private blnAlarmSet As Boolean` instrukcji. Natychmiast poniżej, dodaj następującą instrukcję.  
  
    ```vb  
    Dim blnColorTicker as Boolean  
    ```  
  
3.  Zlokalizuj `End Class` instrukcji w dolnej części strony. Tuż przed `End Class` instrukcji, Dodaj następujący kod.  
  
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
  
     Dodanie tego kodu wykonuje kilka zadań. `Overrides` Instrukcji kieruje formant do użycia tej metody zamiast metody, która została odziedziczona z klasy bazowej. Gdy ta metoda jest wywoływana, wywołuje metodę zastępuje on wywołując `MyBase.Timer1_Tick` instrukcji zapewnienie, że włączone wszystkie funkcje kontroli oryginalnego jest przedstawiony w tym formancie. Następnie uruchomieniu dodatkowy kod w celu włączać funkcje alarm. Po wystąpieniu alarmu, a sygnały dźwiękowe będzie Twój głos zostanie wysłuchany pojawi miga formantu etykiety.  
  
    > [!NOTE]
    >  Ponieważ program obsługi zdarzeń dziedziczone są zastępowanie, nie masz określa zdarzenie z `Handles` — słowo kluczowe. Zdarzenie jest już podłączony. Wszystko, co jest zastępowanie to implementację programu obsługi.  
  
     Formant alarm zegara jest niemal ukończone. Jedyną operacją, której jest wdrożenie sposób, aby je wyłączyć. Aby to zrobić, można dodać kod `lblAlarm_Click` metody.  
  
##### <a name="to-implement-the-shutoff-method"></a>Aby zaimplementować metodę bliskie  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock.vb**, a następnie kliknij przycisk **Widok projektanta**.  
  
2.  W projektancie, kliknij dwukrotnie **lblAlarm**. **Edytora kodu** otwiera `Private Sub lblAlarm_Click` wiersza.  
  
3.  Zmodyfikuj tę metodę, tak, aby podobny do następującego kodu.  
  
    ```vb  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.  
  
### <a name="using-the-inherited-control-on-a-form"></a>Przy użyciu dziedziczone kontrolkę w formularzu  
 Można przetestować dziedziczone formantu przetestowane formantu klasy podstawowej, tak samo `ctlClock`: naciśnij klawisz F5, aby skompilować projekt i uruchomić kontrolę w **kontenera testu UserControl**. Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Aby umieścić formantu do użycia, należy udostępnić go w formularzu. Podobnie jak w przypadku złożonego formantu standardowego, dziedziczone formantu złożonego nie może występować samodzielnie i musi być hostowany w formularzu lub innych kontenera. Ponieważ `ctlAlarmClock` głębokość większej funkcjonalności, dodatkowy kod jest wymagany do testowania go. W tej procedurze, jak napisać prosty program, aby przetestować funkcje `ctlAlarmClock`. Jak napisać kod, aby ustawić i wyświetlić `AlarmTime` właściwość `ctlAlarmClock`i Testuj jego związanego z używaniem funkcji.  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a>Tworzenie i dodawanie formantu do formularza testu  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, a następnie kliknij przycisk **kompilacji**.  
  
2.  Na **pliku** menu wskaż **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
3.  Dodaj nową **aplikacji systemu Windows** projektu do rozwiązania i nadaj mu nazwę `Test`.  
  
     **Testu** projekt zostanie dodany do Eksploratora rozwiązań.  
  
4.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy `Test` węzła projektu, a następnie kliknij przycisk **Dodaj odwołanie** do wyświetlenia **Dodaj odwołanie** okno dialogowe.  
  
5.  Kliknij kartę **projekty**. Projekt **ctlClockLib** zostaną wyświetlone w obszarze **Nazwa projektu**. Kliknij dwukrotnie **ctlClockLib** można dodać odwołania do projektu testowego.  
  
6.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **testu**, a następnie kliknij przycisk **kompilacji**.  
  
7.  W **przybornika**, rozwiń węzeł **ctlClockLib składniki** węzła.  
  
8.  Kliknij dwukrotnie **ctlAlarmClock** można dodać wystąpienia `ctlAlarmClock` do formularza.  
  
9. W **przybornika**, Znajdź i kliknij dwukrotnie **DateTimePicker** można dodać <xref:System.Windows.Forms.DateTimePicker> sterowania do formularza, a następnie dodaj <xref:System.Windows.Forms.Label> kontroli przez dwukrotne kliknięcie **etykiety**.  
  
10. Umieść formanty w dogodnym miejscu w formularzu za pomocą myszy.  
  
11. Ustaw właściwości tych kontrolek w następujący sposób.  
  
    |Formant|Właściwość|Wartość|  
    |-------------|--------------|-----------|  
    |`label1`|**Tekst**|`(blank space)`|  
    ||**Nazwa**|`lblTest`|  
    |`dateTimePicker1`|**Nazwa**|`dtpTest`|  
    ||**Format**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
12. W projektancie, kliknij dwukrotnie **dtpTest**.  
  
     **Edytora kodu** otwiera się `Private Sub dtpTest_ValueChanged`.  
  
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
  
     Uruchamia test program. Należy pamiętać, że bieżący czas jest aktualizowany w `ctlAlarmClock` kontroli i czy czas rozpoczęcia jest wyświetlany w <xref:System.Windows.Forms.DateTimePicker> formantu.  
  
16. Kliknij przycisk <xref:System.Windows.Forms.DateTimePicker> gdzie minuty, godziny są wyświetlane.  
  
17. Przy użyciu klawiatury, ustaw wartość minut, która jest większa niż bieżący czas systemowy przez jedną minutę `ctlAlarmClock`.  
  
     Czas w ustawieniach alarm, gdy jest wyświetlany w obszarze `lblTest`. Poczekaj na wyświetlonej czasu do czasu ustawienie alarmu. Po wyświetlonym czasie osiągnie czas, do którego ustawiono alarmu, dźwiękowe dźwięku i `lblAlarm` będzie flash.  
  
18. Wyłączyć alarm, klikając `lblAlarm`. Alarm mogą teraz zresetować.  
  
     Ten przewodnik zawiera obejmujący wiele kluczowych założeń. Wiesz już, można utworzyć formantu złożonego przez połączenie formanty i składniki w kontenerze formantu złożonego. Kiedy znasz już pozwala dodać właściwości do formantu i napisać kod do implementacji funkcji niestandardowych. W ostatniej sekcji przedstawiono mogą rozszerzyć funkcjonalność danego formantu złożonego za pomocą dziedziczenia i zmieniać funkcje metod hosta przez zastąpienie tych metod.  
  
## <a name="see-also"></a>Zobacz też  
 [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Instrukcje: tworzenie kontrolek złożonych](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [Wskazówki dotyczące tworzenia składników](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
