---
title: "Wskazówki: tworzenie formantu złożonego za pomocą Visual C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 725dc47ce1bda753717c1aac813b8a692ce58001
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a>Wskazówki: tworzenie formantu złożonego za pomocą Visual C# #
Formanty złożone umożliwiają za pomocą którego niestandardowych interfejsów graficznego można tworzyć i użyć ponownie. Formantu złożonego jest zasadniczo składnik o wizualnej reprezentacji. W efekcie może składać się z co najmniej jeden program Windows Forms kontrolki, składniki lub bloki kodu, które mogą rozszerzyć funkcjonalność, sprawdzanie poprawności danych wejściowych użytkownika, modyfikując właściwości ekranu lub wykonywania innych zadań wymaganych przez autora. Formanty złożone można umieścić w formularzach systemu Windows w taki sam sposób jak inne formanty. W pierwszej części tego przewodnika, tworzenie prostego formantu złożonego o nazwie `ctlClock`. W drugiej części tego przewodnika, można rozszerzyć funkcjonalność `ctlClock` przez dziedziczenie.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Podczas tworzenia nowego projektu można określić jego nazwę, aby ustawić głównej przestrzeni nazw, nazwa zestawu i nazwa projektu i upewnij się, że składnik domyślna będzie poprawną przestrzeń nazw.  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Aby utworzyć biblioteki formantu ctlClockLib i kontroli ctlClock  
  
1.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu** otworzyć **nowy projekt** okno dialogowe.  
  
2.  Z listy [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] projektów, wybierz opcję **Biblioteka formantów formularzy systemu Windows** szablon projektu, typ `ctlClockLib` w **nazwa** , a następnie kliknij przycisk **OK** .  
  
     Nazwa projektu `ctlClockLib`, jest również przypisany do głównej przestrzeni nazw domyślnie. Główna przestrzeń nazw są używane do kwalifikowania nazwy elementów w zestawie. Na przykład, jeśli dwa zestawy zawiera składniki o nazwie `ctlClock`, można określić użytkownika `ctlClock` za pomocą składnika`ctlClockLib.ctlClock.`  
  
3.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **UserControl1.cs**, a następnie kliknij przycisk **zmienić**. Zmień nazwę pliku, aby `ctlClock.cs`. Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu "UserControl1".  
  
    > [!NOTE]
    >  Domyślnie formantu złożonego dziedziczy <xref:System.Windows.Forms.UserControl> klasy obsługiwanych przez system. <xref:System.Windows.Forms.UserControl> Klasa udostępnia funkcje wymagane przez formanty wszystkie złożone i implementuje standardowe metody i właściwości.  
  
4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Dodawanie Windows formanty i składniki do złożonych kontrolek  
 Wizualny interfejs jest integralną część złożonego formantu. Ten interfejs visual jest implementowany przez dodanie jednego lub kilku formantów systemu Windows na powierzchnię projektanta. W następujących wykazanie możesz dołączyć formantów systemu Windows do formantu złożonego i napisać kod do implementacji funkcji.  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Aby dodać etykietę i czasomierz do formantu złożonego  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.cs**, a następnie kliknij przycisk **Widok projektanta**.  
  
2.  W **przybornika**, rozwiń węzeł **formanty standardowe** węzeł, a następnie kliknij dwukrotnie plik **etykiety**.  
  
     A <xref:System.Windows.Forms.Label> formantu o nazwie `label1` zostanie dodany do formantu na powierzchnię projektanta.  
  
3.  W projektancie, kliknij **label1**. W oknie właściwości ustaw następujące właściwości.  
  
    |Właściwość|Zmień na|  
    |--------------|---------------|  
    |**Nazwa**|`lblDisplay`|  
    |**Tekst**|`(blank space)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  W **przybornika**, rozwiń węzeł **składniki** węzeł, a następnie kliknij dwukrotnie plik **czasomierza**.  
  
     Ponieważ <xref:System.Windows.Forms.Timer> to składnik go nie ma reprezentacji wizualnej w czasie wykonywania. W związku z tym nie ma z formantami na powierzchni projektanta, ale raczej w **projektanta składników** (pasku w dolnej części powierzchni projektanta).  
  
5.  W **projektanta składników**, kliknij przycisk **czasomierz 1**, a następnie ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwości `1000` i <xref:System.Windows.Forms.Timer.Enabled%2A> właściwości `true`.  
  
     <xref:System.Windows.Forms.Timer.Interval%2A> Właściwość kontroluje częstotliwość <xref:System.Windows.Forms.Timer> Takty składnika. Zawsze `timer1` znaczniki, go uruchamia kod w `timer1_Tick` zdarzeń. Interwał reprezentuje liczbę milisekund między taktami.  
  
6.  W **projektanta składników**, kliknij dwukrotnie **czasomierz 1** można przejść do `timer1_Tick` zdarzenia dla `ctlClock`.  
  
7.  Zmodyfikuj kod, aby go podobny Poniższy przykładowy kod. Należy zmienić modyfikator dostępu z `private` do `protected`.  
  
    ```csharp  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     Ten kod spowoduje, że bieżący czas, który będzie wyświetlany w `lblDisplay`. Ponieważ interwał `timer1` ustawiono `1000`, to zdarzenie wystąpi co tysięcy milisekund, w związku z tym aktualizowanie bieżący czas ciągu sekundy.  
  
8.  Zmodyfikuj metodę, aby żaden z `virtual` — słowo kluczowe. Aby uzyskać więcej informacji zobacz sekcję "Dziedziczy z kontrolki użytkownika" poniżej.  
  
    ```csharp  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.  
  
## <a name="adding-properties-to-the-composite-control"></a>Dodawanie właściwości do złożonych kontrolek  
 Teraz hermetyzuje formantu zegara <xref:System.Windows.Forms.Label> kontroli i <xref:System.Windows.Forms.Timer> z zestawem właściwości związanego z używaniem składnika. Podczas poszczególnych właściwości tych kontrolek nie będzie dostępna dla kolejnych użytkowników formantu, można tworzyć i ujawnia właściwości niestandardowe pisząc odpowiednie bloki kodu. W poniższej procedurze właściwości doda do formantu, który umożliwia użytkownikowi zmianę koloru tła i tekstu.  
  
#### <a name="to-add-a-property-to-your-composite-control"></a>Aby dodać właściwość do formantu złożonego  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.cs**, a następnie kliknij przycisk **kod widoku**.  
  
     **Edytora kodu** dla formantu zostanie otwarty.  
  
2.  Zlokalizuj `public partial class ctlClock` instrukcji. Poniżej nawiasu otwierającego (`{)`, wpisz następujący kod.  
  
    ```csharp  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     Te instrukcje tworzenia zmiennych prywatnych, które będzie używany do przechowywania wartości właściwości, które zostały utworzone.  
  
3.  Wpisz następujący kod pod deklaracje zmiennej w kroku 2.  
  
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
  
     Poprzedni kod sprawia, że dwie właściwości niestandardowej, `ClockForeColor` i `ClockBackColor`, dostępne dla użytkowników kolejnych tego formantu. `get` i `set` zapewniają instrukcje dla magazynu i pobierania wartości właściwości, a także kod do implementowania odpowiednie właściwości.  
  
4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.  
  
## <a name="testing-the-control"></a>Testowanie formantu  
 Formanty nie są aplikacje autonomiczne; muszą one być obsługiwane w kontenerze. Testowanie zachowania w czasie wykonywania formantu i wykonywania jej właściwości z **kontener testu UserControl**. Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### <a name="to-test-your-control"></a>Aby przetestować formantu  
  
1.  Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontrolę w **kontener testu UserControl**.  
  
2.  Kontener testu siatki właściwości, odszukaj `ClockBackColor` właściwości, a następnie wybierz właściwość do wyświetlenia paletę kolorów.  
  
3.  Wybierz kolor, klikając go.  
  
     Kolor wybranego zmienia kolor tła formantu.  
  
4.  Sprawdź, czy za pomocą sekwencji podobnych zdarzeń `ClockForeColor` właściwości działa zgodnie z oczekiwaniami.  
  
     W tej sekcji i poprzednich sekcjach, już wspomniano, jak można łączyć składników i formantów systemu Windows z kodem i pakowania umożliwiają korzystanie z funkcji niestandardowych w formie formantu złożonego. Wiesz już ujawnić właściwości formantu złożonego i testowanie formantu po zakończeniu. W następnej sekcji dowiesz sposób tworzenia dziedziczonych formantu złożonego za pomocą `ctlClock` jako podstawy.  
  
## <a name="inheriting-from-a-composite-control"></a>Dziedziczenie z formantu złożonego  
 W poprzednich sekcjach przedstawiono sposób łączenia formantów systemu Windows, składników i kodu w wielokrotnego użytku formanty złożone. Można teraz używać formantu złożonego jako podstawa, na których mogą być tworzone na inne formanty. Wyprowadzanie klasy z klasy podstawowej proces jest nazywany *dziedziczenia*. W tej sekcji utworzysz formantu złożonego o nazwie `ctlAlarmClock`. Ten formant będzie pochodzić z kontrolki nadrzędnej, `ctlClock`. Dowiesz się rozszerzyć funkcjonalność `ctlClock` przez zastąpienie metody nadrzędnego i dodawanie nowych metod i właściwości.  
  
 Pierwszym krokiem tworzenia dziedziczonych kontrolek jest pochodną nadrzędnego. Ta akcja tworzy nowy formant, który zawiera wszystkie właściwości, metody i właściwości graficzne kontrolki nadrzędnej, ale mogą również działać jako podstawa dla nowych lub zmodyfikowanych funkcja.  
  
#### <a name="to-create-the-inherited-control"></a>Można utworzyć formantu dziedziczonych  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **kontrolki użytkownika**.  
  
     **Dodaj nowy element** zostanie otwarte okno dialogowe.  
  
2.  Wybierz **dziedziczone kontrolki użytkownika** szablonu.  
  
3.  W **nazwa** wpisz `ctlAlarmClock.cs`, a następnie kliknij przycisk **Dodaj**.  
  
     **Selektora dziedziczenia** zostanie wyświetlone okno dialogowe.  
  
4.  W obszarze **nazwa składnika**, kliknij dwukrotnie **ctlClock**.  
  
5.  W Eksploratorze rozwiązań przeglądać bieżących projektów.  
  
    > [!NOTE]
    >  Plik o nazwie **ctlAlarmClock.cs** został dodany do bieżącego projektu.  
  
### <a name="adding-the-alarm-properties"></a>Dodawanie właściwości alarmu  
 Właściwości są dodawane do formantu dziedziczone w taki sam sposób, są one dodawane do formantu złożonego. Teraz użyje składni deklaracji właściwości można dodać dwóch właściwości do formantu: `AlarmTime`, który będzie przechowywać wartość daty i godziny alarm jest wyłączona, i `AlarmSet`, który będzie wskazywać, czy ustawiono alarm.  
  
##### <a name="to-add-properties-to-your-composite-control"></a>Aby dodać właściwości do formantu złożonego  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij przycisk **kod widoku**.  
  
2.  Zlokalizuj `public class` instrukcji. Należy pamiętać, że formant dziedziczy `ctlClockLib.ctlClock`. Poniżej nawiasu otwierającego (`{)` instrukcji, wpisz następujący kod.  
  
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
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a>Dodawanie do formantu interfejsu graficznego  
 Dziedziczony formantu ma wizualny interfejs, który jest taki sam jak formant, który dziedziczy z. Posiada tego samego formanty składników jako kontrolki nadrzędnej, ale właściwości formantów składowych nie będą dostępne, chyba że zostały one specjalnie widoczne. Można dodać do interfejsu graficznego dziedziczone formantu złożonego w taki sam sposób, jak z żadnym formantem złożonego. Aby kontynuować, dodawanie do wizualny interfejs zegar alarmu, należy dodać formant etykiety, który będzie flash, gdy jest podawania alarm.  
  
##### <a name="to-add-the-label-control"></a>Aby dodać formantu etykiety  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij przycisk **Widok projektanta**.  
  
     Projektant `ctlAlarmClock` w głównym oknie zostanie otwarta.  
  
2.  Kliknij przycisk Wyświetl części kontrolki i wyświetlić okno właściwości.  
  
    > [!NOTE]
    >  Gdy wyświetlane są wszystkie właściwości, są niedostępne. Oznacza to, że te właściwości są macierzysty `lblDisplay` i nie można zmodyfikować lub dostępne w oknie właściwości. Domyślnie formantach zawartych w kontrolce złożone są `private`, i ich właściwości nie są dostępne w jakikolwiek sposób.  
  
    > [!NOTE]
    >  Kolejni użytkownicy złożonego formantu do dostępu do jego kontrole wewnętrzne należy zadeklarować je jako `public` lub `protected`. Umożliwi to ustawienie i modyfikowanie właściwości kontrolki zawartych w formantu złożonego za pomocą odpowiedni kod.  
  
3.  Dodaj <xref:System.Windows.Forms.Label> formantu złożonego formantu.  
  
4.  Za pomocą myszy, przeciągnij <xref:System.Windows.Forms.Label> formantu natychmiast poniżej wyświetlanego pola. W oknie właściwości ustaw następujące właściwości.  
  
    |Właściwość|Ustawienie|  
    |--------------|-------------|  
    |**Nazwa**|`lblAlarm`|  
    |**Tekst**|**Alarm!**|  
    |**TextAlign**|`MiddleCenter`|  
    |**Widoczne**|`false`|  
  
### <a name="adding-the-alarm-functionality"></a>Dodawanie funkcji alarmu  
 W ramach poprzednich procedur dodać właściwości i kontrolkę, która spowoduje włączenie funkcji alarm złożonego formantu. W tej procedurze zostanie Dodaj kod, aby porównany bieżący czas na czas alarmu i, jeśli są one takie same na flash alarmu. Przez zastąpienie `timer1_Tick` metody `ctlClock` i dodanie dodatkowego kodu do niego, zostaną rozszerzyć możliwości `ctlAlarmClock` przy zachowaniu wszystkie funkcje związane z `ctlClock`.  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a>Aby zastąpić metodę timer1_Tick ctlClock  
  
1.  W **edytora kodu**, zlokalizuj `private bool blnAlarmSet;` instrukcji. Natychmiast poniżej, dodaj następującą instrukcję.  
  
    ```csharp  
    private bool blnColorTicker;  
    ```  
  
2.  W **edytora kodu**, zlokalizuj zamykający nawias klamrowy (`})` na końcu tej klasy. Tuż przed nawiasem Dodaj następujący kod.  
  
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
  
     Dodanie tego kodu wykonuje kilka zadań. `override` Instrukcji kieruje formant do użycia tej metody zamiast metody, która została odziedziczona z klasy bazowej. Gdy ta metoda jest wywoływana, wywołuje metodę zastępuje on wywołując `base.timer1_Tick` instrukcji zapewnienie, że włączone wszystkie funkcje kontroli oryginalnego jest przedstawiony w tym formancie. Następnie uruchomieniu dodatkowy kod w celu włączać funkcje alarm. Po wystąpieniu alarmu, zostanie wyświetlony miga formantu etykiety.  
  
     Formant alarm zegara jest niemal ukończone. Jedyną operacją, której jest wdrożenie sposób, aby je wyłączyć. Aby to zrobić, można dodać kod `lblAlarm_Click` metody.  
  
##### <a name="to-implement-the-shutoff-method"></a>Aby zaimplementować metodę bliskie  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock.cs**, a następnie kliknij przycisk **Widok projektanta**.  
  
     Zostanie otwarte okno projektowania.  
  
2.  Dodawanie przycisku do formantu. Ustaw właściwości przycisku w następujący sposób.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|`btnAlarmOff`|  
    |**Tekst**|**Wyłączyć Alarm**|  
  
3.  W projektancie, kliknij dwukrotnie **btnAlarmOff**.  
  
     **Edytora kodu** otwiera `private void btnAlarmOff_Click` wiersza.  
  
4.  Zmodyfikuj tę metodę, tak, aby podobny do następującego kodu.  
  
    ```csharp  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.  
  
### <a name="using-the-inherited-control-on-a-form"></a>Przy użyciu dziedziczone kontrolkę w formularzu  
 Można przetestować dziedziczone formantu przetestowane formantu klasy podstawowej, tak samo `ctlClock`: naciśnij klawisz F5, aby skompilować projekt i uruchomić kontrolę w **kontenera testu UserControl**. Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Aby umieścić formantu do użycia, należy udostępnić go w formularzu. Podobnie jak w przypadku złożonego formantu standardowego, dziedziczone formantu złożonego nie może występować samodzielnie i musi być hostowany w formularzu lub innych kontenera. Ponieważ `ctlAlarmClock` głębokość większej funkcjonalności, dodatkowy kod jest wymagany do testowania go. W tej procedurze, jak napisać prosty program, aby przetestować funkcje `ctlAlarmClock`. Jak napisać kod, aby ustawić i wyświetlić `AlarmTime` właściwość `ctlAlarmClock`i Testuj jego związanego z używaniem funkcji.  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a>Tworzenie i dodawanie formantu do formularza testu  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, a następnie kliknij przycisk **kompilacji**.  
  
2.  Dodaj nową **aplikacji systemu Windows** projektu do rozwiązania i nadaj mu nazwę `Test`.  
  
3.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **odwołania** węzła dla projektu testowego. Kliknij przycisk **Dodaj odwołanie** do wyświetlenia **Dodaj odwołanie** okno dialogowe. Kliknij kartę **projekty**. Twoje `ctlClockLib` projektu zostaną wyświetlone w obszarze **Nazwa projektu**. Kliknij dwukrotnie plik projektu można dodać odwołania do projektu testowego.  
  
4.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **testu**, a następnie kliknij przycisk **kompilacji**.  
  
5.  W **przybornika**, rozwiń węzeł **ctlClockLib składniki** węzła.  
  
6.  Kliknij dwukrotnie **ctlAlarmClock** można dodać kopię `ctlAlarmClock` do formularza.  
  
7.  W **przybornika**, Znajdź i kliknij dwukrotnie **DateTimePicker** można dodać <xref:System.Windows.Forms.DateTimePicker> sterowania do formularza, a następnie dodaj <xref:System.Windows.Forms.Label> kontroli przez dwukrotne kliknięcie **etykiety**.  
  
8.  Umieść formanty w dogodnym miejscu w formularzu za pomocą myszy.  
  
9. Ustaw właściwości tych kontrolek w następujący sposób.  
  
    |Formant|Właściwość|Wartość|  
    |-------------|--------------|-----------|  
    |`label1`|**Tekst**|`(blank space)`|  
    ||**Nazwa**|`lblTest`|  
    |`dateTimePicker1`|**Nazwa**|`dtpTest`|  
    ||**Format**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
10. W projektancie, kliknij dwukrotnie **dtpTest**.  
  
     **Edytora kodu** otwiera się `private void dtpTest_ValueChanged`.  
  
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
  
     Uruchamia test program. Należy pamiętać, że bieżący czas jest aktualizowany w `ctlAlarmClock` kontroli i czy czas rozpoczęcia jest wyświetlany w <xref:System.Windows.Forms.DateTimePicker> formantu.  
  
14. Kliknij przycisk <xref:System.Windows.Forms.DateTimePicker> gdzie minuty, godziny są wyświetlane.  
  
15. Przy użyciu klawiatury, ustaw wartość minut, która jest większa niż bieżący czas systemowy przez jedną minutę `ctlAlarmClock`.  
  
     Czas w ustawieniach alarm, gdy jest wyświetlany w obszarze `lblTest`. Poczekaj na wyświetlonej czasu do czasu ustawienie alarmu. Gdy czas, do którego alarm jest ustawiona, osiągnie wyświetlonym czasie `lblAlarm` będzie flash.  
  
16. Wyłączyć alarm, klikając `btnAlarmOff`. Alarm mogą teraz zresetować.  
  
     Ten przewodnik zawiera obejmujący wiele kluczowych założeń. Wiesz już, można utworzyć formantu złożonego przez połączenie formanty i składniki w kontenerze formantu złożonego. Kiedy znasz już pozwala dodać właściwości do formantu i napisać kod do implementacji funkcji niestandardowych. W ostatniej sekcji przedstawiono mogą rozszerzyć funkcjonalność danego formantu złożonego za pomocą dziedziczenia i zmieniać funkcje metod hosta przez zastąpienie tych metod.  
  
## <a name="see-also"></a>Zobacz też  
 [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Programowanie przy użyciu składników](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [Wskazówki dotyczące tworzenia składników](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
