---
title: 'Wskazówki: tworzenie formantu złożonego za pomocą Visual C#'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
ms.openlocfilehash: 5f8384140b813400e106ad959684264304541c93
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580826"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a>Wskazówki: tworzenie formantu złożonego za pomocą Visual C# #
Formanty złożone umożliwiają za pomocą którego niestandardowe interfejsy graficzne można tworzyć i ponownie używane. Formant złożony jest zasadniczo składnika za pomocą wizualnej reprezentacji. W efekcie może składać się z co najmniej Windows Forms formantów, składników lub bloki kodu, które mogą rozszerzyć funkcjonalność, sprawdzanie poprawności danych wejściowych użytkownika, modyfikując właściwości wyświetlania lub wykonywania innych zadań wymaganych przez autora. Formanty złożone można umieścić na formularzach Windows Forms w taki sam sposób jak inne kontrolki. W pierwszej części tego przewodnika, tworzenie prostego formantu złożonego o nazwie `ctlClock`. W drugiej części tego przewodnika, możesz rozszerzyć funkcjonalność `ctlClock` poprzez dziedziczenie.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Podczas tworzenia nowego projektu można określić jego nazwę, aby ustawić głównej przestrzeni nazw, nazwa zestawu i nazwa projektu i upewnij się, że składnik domyślną będzie poprawną przestrzeń nazw.  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Aby utworzyć ctlClockLib Biblioteka kontrolek i kontrola ctlClock  
  
1.  Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu** otworzyć **nowy projekt** okno dialogowe.  
  
2.  Wybierz z listy projektów języka Visual C#, **Biblioteka kontrolek formularzy Windows** szablon projektu, należy wpisać `ctlClockLib` w **nazwa** , a następnie kliknij przycisk **OK**.  
  
     Nazwa projektu `ctlClockLib`, również jest domyślnie przypisane do głównej przestrzeni nazw. Główna przestrzeń nazw są używane do kwalifikowania nazwy elementów w zestawie. Na przykład, jeśli dwa zestawy zawiera składniki o nazwie `ctlClock`, możesz określić swoje `ctlClock` za pomocą składnika `ctlClockLib.ctlClock.`  
  
3.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **UserControl1.cs**, a następnie kliknij przycisk **Zmień nazwę**. Zmień nazwę pliku, aby `ctlClock.cs`. Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu "UserControl1".  
  
    > [!NOTE]
    >  Domyślnie przez kontrolki złożonej dziedziczy <xref:System.Windows.Forms.UserControl> klasy udostępnianej przez system. <xref:System.Windows.Forms.UserControl> Zapewnia funkcje wymagane przez formanty złożone wszystkie klasy i implementuje standardowe metody i właściwości.  
  
4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Dodawanie Windows kontrolek i składników do kontrolek złożonych  
 Interfejs graficzny jest integralną część złożonego formantu. Ten interfejs graficzny jest implementowany przez dodanie jednego lub kilku formantów Windows do powierzchni projektanta. W poniższy pokaz możesz zintegrować formanty Windows złożonego formantu i napisać kod, aby zaimplementować funkcje.  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Aby dodać etykietę i czasomierz do złożonego formantu  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.cs**, a następnie kliknij przycisk **Projektant widoków**.  
  
2.  W **przybornika**, rozwiń węzeł **wspólnych formantów** węzłem, a następnie kliknij dwukrotnie plik **etykiety**.  
  
     A <xref:System.Windows.Forms.Label> formantu o nazwie `label1` zostanie dodany do formantu na powierzchni projektowej.  
  
3.  W projektancie, kliknij **label1**. W oknie właściwości ustaw następujące właściwości.  
  
    |Właściwość|Zmień na|  
    |--------------|---------------|  
    |**Nazwa**|`lblDisplay`|  
    |**Tekst**|`(blank space)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  W **przybornika**, rozwiń węzeł **składniki** węzłem, a następnie kliknij dwukrotnie plik **czasomierza**.  
  
     Ponieważ <xref:System.Windows.Forms.Timer> jest składnikiem, ma ona nie wizualnej reprezentacji w czasie wykonywania. W związku z tym, nie ma za pomocą kontrolek na powierzchni projektowej, ale raczej w **projektanta składników** (zasobnik w dolnej części powierzchni projektanta).  
  
5.  W **projektanta składników**, kliknij przycisk **timer1**, a następnie ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwości `1000` i <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość `true`.  
  
     <xref:System.Windows.Forms.Timer.Interval%2A> Właściwość kontroluje częstotliwość <xref:System.Windows.Forms.Timer> impulsów składnika. Każdorazowo `timer1` znaczniki, uruchamia kod `timer1_Tick` zdarzeń. Interwał reprezentuje liczbę milisekund między taktami.  
  
6.  W **projektanta składników**, kliknij dwukrotnie **timer1** można przejść do `timer1_Tick` zdarzenie `ctlClock`.  
  
7.  Należy zmodyfikować kod, tak aby wyglądała jak poniższy przykładowy kod. Pamiętaj zmieniać modyfikatora dostępu z `private` do `protected`.  
  
    ```csharp  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     Ten kod powoduje, że bieżący czas, który ma być wyświetlany w `lblDisplay`. Ponieważ interwał `timer1` została ustawiona na `1000`, to zdarzenie wystąpi co tysięcy milisekund, w związku z tym aktualizacji bieżący czas co sekundę.  
  
8.  Zmodyfikuj metodę możliwym do zastąpienia przy użyciu `virtual` — słowo kluczowe. Aby uzyskać więcej informacji zobacz sekcję "Dziedziczenie z kontrolki użytkownika" poniżej.  
  
    ```csharp  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.  
  
## <a name="adding-properties-to-the-composite-control"></a>Dodawanie właściwości do kontrolek złożonych  
 Formant zegara teraz hermetyzuje <xref:System.Windows.Forms.Label> kontroli i <xref:System.Windows.Forms.Timer> składnika, z których każdy swój własny zestaw właściwości związanych. Gdy poszczególne właściwości tych kontrolek nie będą dostępne dla użytkowników kolejne kontrolki, można tworzyć i udostępnianie właściwości niestandardowych, pisząc odpowiednich bloków kodu. W poniższej procedurze będzie dodać właściwości do formantu, który umożliwia użytkownikowi zmianę koloru tła i tekstu.  
  
#### <a name="to-add-a-property-to-your-composite-control"></a>Aby dodać właściwości do kontrolki złożonej  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.cs**, a następnie kliknij przycisk **Wyświetl kod**.  
  
     **Edytor kodu** dla kontrolki zostanie otwarty.  
  
2.  Znajdź `public partial class ctlClock` instrukcji. Poniżej otwierający nawias klamrowy (`{)`, wpisz następujący kod.  
  
    ```csharp  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     Te instrukcje tworzenia zmienne prywatne, które będą używane do przechowywania wartości właściwości, które masz zamiar utworzyć.  
  
3.  Wpisz następujący kod pod deklaracje zmiennych w kroku 2.  
  
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
  
     Poprzedzający kod wprowadza dwie właściwości niestandardowe, `ClockForeColor` i `ClockBackColor`, która jest dostępna dla kolejnych użytkowników tej kontrolki. `get` i `set` instrukcji zapewniać przechowywania i pobierania wartości właściwości, a także kod do implementacji funkcji odpowiednich właściwości.  
  
4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.  
  
## <a name="testing-the-control"></a>Testowanie kontrolki  
 Formanty nie są aplikacje autonomiczne; muszą one być obsługiwane w kontenerze. Testowanie zachowania w czasie wykonywania kontroli nad i sprawdzić jego właściwości, za pomocą **UserControl — kontener testowy**. Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### <a name="to-test-your-control"></a>Aby przetestować formant  
  
1.  Naciśnij klawisz F5, aby skompilować projekt i uruchomić Twoją kontrolą w **UserControl — kontener testowy**.  
  
2.  W siatce właściwości kontener testu, zlokalizuj `ClockBackColor` właściwości, a następnie wybierz właściwość do wyświetlenia palety kolorów.  
  
3.  Wybierz kolor, klikając go.  
  
     Kolor tła kontrolki zmienia kolor, który wybrano.  
  
4.  Upewnij się, że za pomocą sekwencji podobnych zdarzeń `ClockForeColor` właściwości działa zgodnie z oczekiwaniami.  
  
     W poprzedniej sekcji i w tej sekcji, wiesz, jak można łączyć składników i formantów Windows z kodem i pakowania do dostarczają niestandardowych funkcjonalności w formie kontrolek złożonych. Wiesz, że udostępnianie właściwości złożonej kontrolki i testowanie formantu po jego zakończeniu. W następnej sekcji zostanie dowiesz się, jak skonstruować dziedziczone kontrolki złożonej za pomocą `ctlClock` jako podstawy.  
  
## <a name="inheriting-from-a-composite-control"></a>Dziedziczenie z kontrolki złożonej  
 W poprzednich sekcjach wiesz, jak połączyć kontrolki Windows, składników i kod do kontrolek złożonych wielokrotnego użytku. Złożonego formantu może być teraz używane jako podstawa, na którym mogą być wbudowane w innych kontrolek. Wyprowadzanie klasy z klasy bazowej proces jest nazywany *dziedziczenia*. W tej sekcji spowoduje utworzenie kontrolki złożonej o nazwie `ctlAlarmClock`. Ta kontrolka będzie pochodzić z kontrolki nadrzędnej, `ctlClock`. Jak rozszerzyć funkcjonalność `ctlClock` nadpisywania metod nadrzędnego i dodawania nowych metod i właściwości.  
  
 Pierwszym krokiem w tworzeniu odziedziczoną kontrolkę jest pochodną jego obiektu nadrzędnego. Ta akcja tworzy nowy formant, który zawiera wszystkie właściwości, metod i właściwości graficzne kontroli nadrzędnej, ale mogą również działać jako podstawa dla nowych lub zmodyfikowanych funkcja.  
  
#### <a name="to-create-the-inherited-control"></a>Aby utworzyć odziedziczoną kontrolkę  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **kontrolki użytkownika**.  
  
     **Dodaj nowy element** zostanie otwarte okno dialogowe.  
  
2.  Wybierz **dziedziczone kontrolki użytkownika** szablonu.  
  
3.  W **nazwa** wpisz `ctlAlarmClock.cs`, a następnie kliknij przycisk **Dodaj**.  
  
     **Selektor dziedziczenia** pojawi się okno dialogowe.  
  
4.  W obszarze **nazwa składnika**, kliknij dwukrotnie **ctlClock**.  
  
5.  W Eksploratorze rozwiązań należy przejrzeć bieżących projektów.  
  
    > [!NOTE]
    >  Plik o nazwie **ctlAlarmClock.cs** został dodany do bieżącego projektu.  
  
### <a name="adding-the-alarm-properties"></a>Dodawanie właściwości alarmów  
 Właściwości są dodawane do odziedziczoną kontrolkę w taki sam sposób, w których są one dodawane do kontrolek złożonych. Teraz użyjesz Składnia deklaracji właściwości można dodać dwie właściwości do kontrolki: `AlarmTime`, której będzie przechowywana wartość daty i godziny alarmu jest wyłączona, a `AlarmSet`, który będzie wskazywać, czy ustawiono alarmu.  
  
##### <a name="to-add-properties-to-your-composite-control"></a>Aby dodać właściwości do kontrolki złożonej  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij przycisk **Wyświetl kod**.  
  
2.  Znajdź `public class` instrukcji. Należy zauważyć, że formant dziedziczy `ctlClockLib.ctlClock`. Poniżej otwierający nawias klamrowy (`{)` instrukcji, wpisz następujący kod.  
  
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
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a>Dodawanie do interfejsu graficznego formantu  
 Odziedziczone kontrolki ma interfejs graficzny, która jest taka sama jak formant, który dziedziczy. Posiada on te same kontrolki składowych co kontrolki nadrzędnej, ale właściwości formantów składowych nie będzie dostępna, chyba że zostały one specjalnie ujawnione. Można dodać do graficznego interfejsu dziedziczone złożonego formantu w taki sam sposób jak należy dodać do dowolnego złożonego formantu. Aby kontynuować, dodając do zegar alarm wizualny interfejs, dodasz formant etykiety, który będzie flash, gdy jest podawania alarmu.  
  
##### <a name="to-add-the-label-control"></a>Aby dodać formant etykiety  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij przycisk **Projektant widoków**.  
  
     Projektant `ctlAlarmClock` otwiera się w głównym oknie.  
  
2.  Kliknij przycisk Wyświetl części kontrolki i wyświetlać w oknie właściwości.  
  
    > [!NOTE]
    >  Chociaż wyświetlane są wszystkie właściwości, są niedostępne. Oznacza to, że te właściwości są natywne `lblDisplay` i nie może zostać zmodyfikowany lub dostępne w oknie dialogowym właściwości. Domyślnie są zawarte w kontrolki złożonej kontrolki `private`, i ich właściwości nie są dostępne w jakikolwiek sposób.  
  
    > [!NOTE]
    >  Kolejni użytkownicy złożonej kontrolki mają mieć dostęp do jego wewnętrznych kontroli, zadeklarować je jako `public` lub `protected`. To pozwala ustawić i zmodyfikować właściwości formantów zawartych w złożonej kontrolki przy użyciu odpowiedniego kodu.  
  
3.  Dodaj <xref:System.Windows.Forms.Label> kontrolki złożonej kontrolki.  
  
4.  Za pomocą myszy, przeciągnij <xref:System.Windows.Forms.Label> formantu bezpośrednio poniżej wyświetlanego pola. W oknie właściwości ustaw następujące właściwości.  
  
    |Właściwość|Ustawienie|  
    |--------------|-------------|  
    |**Nazwa**|`lblAlarm`|  
    |**Tekst**|**Alarm!**|  
    |**TextAlign**|`MiddleCenter`|  
    |**Widoczne**|`false`|  
  
### <a name="adding-the-alarm-functionality"></a>Dodawanie funkcji alarmów  
 W ramach poprzednich procedur dodać właściwości i formant, który spowoduje włączenie funkcji alarmu w złożonej kontrolki. W tej procedurze należy dodać kod do porównania bieżącego czasu do czasu alarmów i, jeśli są takie same, zaktualizować alarmu. Przez zastąpienie `timer1_Tick` metody `ctlClock` i dodanie dodatkowego kodu do niego, zostaną rozszerzone możliwości `ctlAlarmClock` przy zachowaniu wszystkich funkcji związanych z `ctlClock`.  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a>Aby zastąpić metodę timer1_Tick ctlClock  
  
1.  W **Edytor kodu**, zlokalizuj `private bool blnAlarmSet;` instrukcji. Bezpośrednio pod nim, należy dodać następującą instrukcję.  
  
    ```csharp  
    private bool blnColorTicker;  
    ```  
  
2.  W **Edytor kodu**, zlokalizuj zamykającego nawiasu klamrowego (`})` na końcu tej klasy. Tuż przed nawiasu klamrowego Dodaj następujący kod.  
  
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
  
     Dodanie tego kodu w ramach kilku zadań. `override` Instrukcja określa, że formant Aby użyć tej metody, zamiast metody, która została odziedziczona z bazowej. Gdy ta metoda jest wywoływana, wywołuje metodę, zastępuje ona wywołując `base.timer1_Tick` instrukcji, zapewniając wszystkich funkcji włączonych oryginalnego formantu jest przedstawiony w tym elemencie sterującym. Następnie działa dodatkowego kodu, aby włączać funkcje alarmu. Migające formant etykiety będą wyświetlane po wystąpieniu alarmu.  
  
     Formant alarm zegara jest niemal ukończone. Jest jedynym elementem, który pozostaje do zaimplementowania sposób, aby je wyłączyć. Aby to zrobić, można dodać kod `lblAlarm_Click` metody.  
  
##### <a name="to-implement-the-shutoff-method"></a>Aby wdrożyć metodę bliskie  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock.cs**, a następnie kliknij przycisk **Projektant widoków**.  
  
     Zostanie otwarty projektant.  
  
2.  Dodaj przycisk do formantu. Ustaw następujące właściwości przycisku.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|`btnAlarmOff`|  
    |**Tekst**|**Wyłącz alarmów**|  
  
3.  W projektancie, kliknij dwukrotnie **btnAlarmOff**.  
  
     **Edytor kodu** otwiera `private void btnAlarmOff_Click` wiersza.  
  
4.  Zmodyfikuj tę metodę, tak, aby wyglądała jak poniższy kod.  
  
    ```csharp  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.  
  
### <a name="using-the-inherited-control-on-a-form"></a>Za pomocą odziedziczoną kontrolkę w formularzu  
 Można przetestować kontroli nad dziedziczone przetestowane kontrolki klasy bazowej, tak samo `ctlClock`: naciśnij klawisz F5, aby skompilować projekt i uruchomić Twoją kontrolą w **UserControl — kontener testu**. Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Aby przełączyć kontrolki do użycia, należy ją hostować na formularzu. Podobnie jak w przypadku złożonego formantu standardowego dziedziczone złożonego formantu nie może występować samodzielnie i musi być hostowany w formie lub innego kontenera. Ponieważ `ctlAlarmClock` ma większą głębokość funkcjonalności, dodatkowy kod jest wymagany do testowania. W tej procedurze, jak napisać prosty program, aby przetestować działanie `ctlAlarmClock`. Możesz napisać kod, aby ustawić i wyświetlić `AlarmTime` właściwość `ctlAlarmClock`i przetestujesz jej nieodłączne funkcji.  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a>Tworzenie i dodawanie formantu do formularza testu  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, a następnie kliknij przycisk **kompilacji**.  
  
2.  Dodaj nową **aplikacji Windows** projektu do rozwiązania i nadaj mu nazwę `Test`.  
  
3.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **odwołania** węzeł dla projektu testowego. Kliknij przycisk **Dodaj odwołanie** do wyświetlenia **Dodaj odwołanie** okno dialogowe. Kliknij kartę **projektów**. Twoje `ctlClockLib` projektu zostaną wyświetlone w obszarze **Nazwa projektu**. Kliknij dwukrotnie projektu można dodać odwołania do projektu testowego.  
  
4.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **testu**, a następnie kliknij przycisk **kompilacji**.  
  
5.  W **przybornika**, rozwiń węzeł **ctlClockLib składniki** węzła.  
  
6.  Kliknij dwukrotnie **ctlAlarmClock** można dodać kopię `ctlAlarmClock` do formularza.  
  
7.  W **przybornika**, zlokalizuj i kliknij dwukrotnie **DateTimePicker** dodać <xref:System.Windows.Forms.DateTimePicker> sterowania do formularza, a następnie dodaj <xref:System.Windows.Forms.Label> kontroli przez dwukrotne kliknięcie **etykiety**.  
  
8.  Umieść formanty w wygodne miejsce w formularzu za pomocą myszy.  
  
9. Ustaw właściwości tych kontrolek, w następujący sposób.  
  
    |Formant|Właściwość|Wartość|  
    |-------------|--------------|-----------|  
    |`label1`|**Tekst**|`(blank space)`|  
    ||**Nazwa**|`lblTest`|  
    |`dateTimePicker1`|**Nazwa**|`dtpTest`|  
    ||**Format**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
10. W projektancie, kliknij dwukrotnie **dtpTest**.  
  
     **Edytor kodu** otwiera `private void dtpTest_ValueChanged`.  
  
11. Zmodyfikuj kod, dzięki czemu jest podobny do następującego.  
  
    ```csharp  
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)  
    {  
        ctlAlarmClock1.AlarmTime = dtpTest.Value;  
        ctlAlarmClock1.AlarmSet = true;  
        lblTest.Text = "Alarm Time is " +  
            ctlAlarmClock1.AlarmTime.ToShortTimeString();  
    }  
    ```  
  
12. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **testu**, a następnie kliknij przycisk **Ustaw jako projekt startowy**.  
  
13. Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.  
  
     Zostanie uruchomiony test program. Należy pamiętać, że bieżący czas jest aktualizowana w `ctlAlarmClock` kontroli i że godzina rozpoczęcia jest wyświetlany w <xref:System.Windows.Forms.DateTimePicker> kontroli.  
  
14. Kliknij przycisk <xref:System.Windows.Forms.DateTimePicker> gdzie minuty godziny są wyświetlane.  
  
15. Za pomocą klawiatury, ustaw wartość minut, która jest większa niż bieżąca godzina wyświetlane według jedną minutę `ctlAlarmClock`.  
  
     Czas ustawienie alarmu jest wyświetlany w `lblTest`. Poczekaj, aż wyświetlonym czasie osiągnąć czas ustawienie alarmu. Po wyświetlonym czasie osiągnie czas, w którym ustawiono alarmu, `lblAlarm` będzie flash.  
  
16. Wyłączyć alarm, klikając `btnAlarmOff`. Może teraz zresetować alarmu.  
  
     W tym przewodniku ma obejmujący wiele kluczowych założeń. Wiesz, że tworzenie formantu złożonego, łącząc w kontenerze kontrolek złożonych kontrolek i składników. Wiesz, można dodać właściwości do kontrolki, a następnie napisać kod do implementacji funkcji niestandardowych. W ostatniej sekcji pokazano, aby rozszerzyć funkcjonalność danej kontrolki złożonej za pomocą dziedziczenia i zmieniać funkcje metod hosta przez zastąpienie tych metod.  
  
## <a name="see-also"></a>Zobacz też  
 [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Programowanie przy użyciu składników](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [Tworzenie składników — wskazówki](https://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
