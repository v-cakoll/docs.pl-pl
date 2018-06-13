---
title: 'Wskazówki: tworzenie aplikacji usługowej systemu Windows w Projektancie składników'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Service applications, walkthroughs
- Windows Service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
manager: douge
ms.openlocfilehash: c33b8badcacd4e228d70f8e770d4bf27144c29eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520516"
---
# <a name="walkthrough-creating-a-windows-service-application-in-the-component-designer"></a>Wskazówki: tworzenie aplikacji usługowej systemu Windows w Projektancie składników
W tym artykule pokazano, jak utworzyć prostą aplikację usługi systemu Windows w programie Visual Studio, który zapisuje komunikaty do dziennika zdarzeń. Poniżej przedstawiono podstawowe kroki, które należy wykonać w celu tworzenia i używania usługi:  
  
1.  [Tworzenie usługi](#BK_CreateProject) za pomocą **usługi systemu Windows** projektu szablonu i skonfiguruj go. Ten szablon umożliwia tworzenie dla Ciebie, która dziedziczy po klasie <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> i zapisuje większość kodu podstawowej usługi, na przykład kod, aby uruchomić usługę.  
  
2.  [Dodawanie funkcji do usługi](#BK_WriteCode) dla <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedur i zastąpienie innych metod, które chcesz zdefiniować ponownie.  
  
3.  [Ustawienie stanu usługi](#BK_SetStatus). Domyślnie usługi utworzone za pomocą <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> implementuje tylko podzestaw flagi stanu dostępne. Jeżeli usługi zajmuje dużo czasu, aby rozpocząć, wstrzymać lub zatrzymać, można zaimplementować wartości stanu, takie jak uruchomić Oczekiwanie lub zatrzymać oczekiwanie, aby wskazać, że działa w przypadku operacji.  
  
4.  [Dodawanie instalatorów do usługi](#BK_AddInstallers) dla aplikacji usługi.  
  
5.  (Opcjonalnie) [Ustawić parametry uruchamiania](#BK_StartupParameters)określ argumenty uruchomienia domyślne, a użytkownicy mogli zastępują ustawienia domyślne przy ich ręcznie uruchomić usługę.  
  
6.  [Tworzenie usługi](#BK_Build).  
  
7.  [Instalowanie usługi](#BK_Install) na komputerze lokalnym.  
  
8.  Dostęp do Menedżera sterowania usługami systemu Windows i [uruchomienie usługi](#BK_StartService).  
  
9. [Odinstalowywanie usług systemu Windows](#BK_Uninstall).  
  
> [!WARNING]
>  Szablon projektu usług systemu Windows Services wymagany w tym instruktażu jest niedostępny w wydaniu Express programu Visual Studio.  
  
 [!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]  
  
<a name="BK_CreateProject"></a>   
## <a name="creating-a-service"></a>Tworzenie usługi  
 Na początku utworzysz projekt i skonfigurujesz wartości niezbędne do poprawnego działania usługi.  
  
#### <a name="to-create-and-configure-your-service"></a>Aby utworzyć i skonfigurować usługę  
  
1.  W programie Visual Studio na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
2.  Na liście szablony projektu Visual Basic lub Visual C#, wybierz **usługi systemu Windows**i nazwij projekt **MyNewService**. Wybierz **OK**.  
  
     Szablon projektu automatycznie dodaje klasę składnika o nazwie `Service1` dziedziczący po <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.  
  
3.  Na **Edytuj** menu, wybierz **Znajdź i Zamień**, **Znajdź w plikach** (klawiatury: Ctrl + Shift + F). Zmień wszystkie wystąpienia `Service1` do `MyNewService`. Można znaleźć wystąpień w Service1.cs, pliku Program.cs i Service1.Designer.cs (lub odpowiedniki .vb).  
  
4.  W **właściwości** w oknie **Service1.cs [projekt]** lub **Service1.vb [projekt]** ustaw <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> i **(nazwa)** Właściwość `Service1` do **MyNewService**, jeśli jeszcze nie jest ustawiona.  
  
5.  W Eksploratorze rozwiązań, Zmień nazwę **Service1.cs** do **MyNewService.cs**, lub **Service1.vb** do **MyNewService.vb**.  
  
<a name="BK_WriteCode"></a>   
## <a name="adding-features-to-the-service"></a>Dodawanie funkcji do usługi  
 W tej sekcji możesz dodać niestandardowe dziennik zdarzeń usługi systemu Windows. Dzienniki zdarzeń nie w żaden sposób powiązane z usługami systemu Windows. W tym miejscu <xref:System.Diagnostics.EventLog> składnik jest używany na przykład typ składnika można dodać do usługi systemu Windows.  
  
#### <a name="to-add-custom-event-log-functionality-to-your-service"></a>Aby dodać funkcjonalność niestandardowego dziennika zdarzeń do usługi  
  
1.  W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **MyNewService.cs** lub **MyNewService.vb**, a następnie wybierz pozycję **Widok projektanta**.  
  
2.  Z **składniki** sekcji **przybornika**, przeciągnij <xref:System.Diagnostics.EventLog> składnika do projektanta.  
  
3.  W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **MyNewService.cs** lub **MyNewService.vb**, a następnie wybierz pozycję **kod widoku**.  
  
4.  Dodaj deklarację dla **eventLog** obiektu w `MyNewService` klasy bezpośrednio po wiersza, który deklaruje `components` zmienną:  
  
     [!code-csharp[VbRadconService#16](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#16)]
     [!code-vb[VbRadconService#16](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#16)]  
  
5.  Dodawanie lub edytowanie konstruktora, aby zdefiniować niestandardowe dziennika zdarzeń:  
  
     [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
     [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]  
  
#### <a name="to-define-what-occurs-when-the-service-starts"></a>Aby określić zachowanie występujące podczas uruchamiania usługi  
  
-   Znajdź w edytorze kodu <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodę, która została automatycznie zastąpione podczas tworzenia projektu i Zastąp kod następującym kodem. Spowoduje to dodanie wpisu w dzienniku zdarzeń podczas uruchamiania usługi:  
  
     [!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
     [!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]  
  
     Aplikacja usługi ma być długotrwałe, dlatego zazwyczaj sonduje lub monitoruje coś w systemie. Monitorowanie skonfigurowano <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody. Jednak <xref:System.ServiceProcess.ServiceBase.OnStart%2A> faktycznie nie monitorowania. <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Metoda musi zwracać do systemu operacyjnego, po rozpoczęciu operacji usługi. Nie może być wykonywana bezterminowo w pętli ani nakładać żadnych blokad. Aby skonfigurować mechanizmu sondowania proste, można użyć <xref:System.Timers.Timer?displayProperty=nameWithType> składnika w następujący sposób: W <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody, Ustaw parametry dla składnika, a następnie ustaw <xref:System.Timers.Timer.Enabled%2A> właściwości `true`. Czasomierz informuje o zdarzeniach w kodzie okresowo, w tym czasie usługa może wykonać jego monitorowanie. Poniższy kod służy w tym celu:  
  
    ```csharp  
    // Set up a timer to trigger every minute.  
    System.Timers.Timer timer = new System.Timers.Timer();  
    timer.Interval = 60000; // 60 seconds  
    timer.Elapsed += new System.Timers.ElapsedEventHandler(this.OnTimer);  
    timer.Start();  
    ```  
  
    ```vb  
    ' Set up a timer to trigger every minute.  
    Dim timer As System.Timers.Timer = New System.Timers.Timer()  
    timer.Interval = 60000 ' 60 seconds  
    AddHandler timer.Elapsed, AddressOf Me.OnTimer  
    timer.Start()  
    ```  
     Dodaj zmienną członkowską do klasy. Będzie zawierać identyfikator następnego zdarzenia do zapisania w dzienniku zdarzeń.

    ```csharp
    private int eventId = 1;
    ```

    ```vb
    Private eventId As Integer = 1
    ```

     Dodaj kod obsługi zdarzeń czasomierza:  
  
    ```csharp  
    public void OnTimer(object sender, System.Timers.ElapsedEventArgs args)  
    {  
        // TODO: Insert monitoring activities here.  
        eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId++);  
    }  
    ```  
  
    ```vb  
    Private Sub OnTimer(sender As Object, e As Timers.ElapsedEventArgs)  
        ' TODO: Insert monitoring activities here.  
        eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId)  
        eventId = eventId + 1  
    End Sub  
    ```  
  
     Można wykonywać zadania za pomocą wątków roboczych tła zamiast uruchamiania całą pracę w głównym wątku. Aby na przykład, zobacz <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> strony odwołania.  
  
#### <a name="to-define-what-occurs-when-the-service-is-stopped"></a>Aby określić zachowanie występujące podczas zatrzymywania usługi  
  
-   Zastąp kod <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody następującym kodem. Spowoduje to dodanie wpisu w dzienniku zdarzeń po zatrzymaniu usługi:  
  
     [!code-csharp[VbRadconService#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
     [!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]  
  
 W następnej sekcji, można zastąpić <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, i <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> metod do definiowania dodatkowego przetwarzania dla składnika.  
  
#### <a name="to-define-other-actions-for-the-service"></a>Aby zdefiniować inne czynności do wykonania w usłudze  
  
-   Zlokalizuj metody, które mają być obsługiwane, a następnie zastąpić, aby zdefiniować, co ma nastąpić.  
  
     Poniższy kod przedstawia, jak można zastąpić <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> metody:  
  
     [!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
     [!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]  
  
 Niektóre akcje niestandardowe musi wystąpić, gdy usługa systemu Windows jest zainstalowana przez <xref:System.Configuration.Install.Installer> klasy. Program Visual Studio może utworzyć te instalatory specjalnie dla usługi systemu Windows i dodać je do projektu.  
  
<a name="BK_SetStatus"></a>   
## <a name="setting-service-status"></a>Ustawienie stanu usługi  
 Usługi zgłaszają swój stan do Menedżera sterowania usługami, dzięki czemu użytkownik może stwierdzić, czy usługa działa poprawnie. Domyślnie usługi, które dziedziczą z <xref:System.ServiceProcess.ServiceBase> ograniczony zestaw ustawień stanu, takich jak zatrzymana, wstrzymana i uruchamianie raportu. Jeśli usługa ma nieco podczas uruchamiania, jego może być przydatne do raportowania stanu Start oczekiwania. Można też wdrożyć ustawienia stanu oczekujące uruchomić i zatrzymać oczekujące przez dodanie kodu, który odwołuje się do systemu Windows [funkcji SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx).  
  
#### <a name="to-implement-service-pending-status"></a>Aby wdrożyć usługę w stanie oczekiwania  
  
1.  Dodaj `using` instrukcji lub `Imports` deklaracji <xref:System.Runtime.InteropServices?displayProperty=nameWithType> przestrzeni nazw w pliku MyNewService.cs lub MyNewService.vb:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    ```  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    ```  
  
2.  Dodaj następujący kod do MyNewService.cs Aby zadeklarować `ServiceState` wartości i dodać strukturę stanu, który zostanie użyty na platformie invoke wywołania:  
  
    ```csharp  
    public enum ServiceState  
      {  
          SERVICE_STOPPED = 0x00000001,  
          SERVICE_START_PENDING = 0x00000002,  
          SERVICE_STOP_PENDING = 0x00000003,  
          SERVICE_RUNNING = 0x00000004,  
          SERVICE_CONTINUE_PENDING = 0x00000005,  
          SERVICE_PAUSE_PENDING = 0x00000006,  
          SERVICE_PAUSED = 0x00000007,  
      }  
  
      [StructLayout(LayoutKind.Sequential)]  
      public struct ServiceStatus  
      {  
          public int dwServiceType;  
          public ServiceState dwCurrentState;  
          public int dwControlsAccepted;  
          public int dwWin32ExitCode;  
          public int dwServiceSpecificExitCode;  
          public int dwCheckPoint;  
          public int dwWaitHint;  
      };  
    ```  
  
    ```vb  
    Public Enum ServiceState  
        SERVICE_STOPPED = 1  
        SERVICE_START_PENDING = 2  
        SERVICE_STOP_PENDING = 3  
        SERVICE_RUNNING = 4  
        SERVICE_CONTINUE_PENDING = 5  
        SERVICE_PAUSE_PENDING = 6  
        SERVICE_PAUSED = 7  
    End Enum  
  
    <StructLayout(LayoutKind.Sequential)>  
    Public Structure ServiceStatus  
        Public dwServiceType As Long  
        Public dwCurrentState As ServiceState  
        Public dwControlsAccepted As Long  
        Public dwWin32ExitCode As Long  
        Public dwServiceSpecificExitCode As Long  
        Public dwCheckPoint As Long  
        Public dwWaitHint As Long  
    End Structure  
    ```  
  
3.  Teraz, w `MyNewService` klasy, Zadeklaruj [funkcji SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) przy użyciu platformy wywołania:  
  
    ```csharp  
    [DllImport("advapi32.dll", SetLastError=true)]  
            private static extern bool SetServiceStatus(IntPtr handle, ref ServiceStatus serviceStatus);  
    ```  
  
    ```vb  
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean  
    ```  
  
4.  Aby zaimplementować stanu oczekiwania Start, Dodaj następujący kod na początku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody:  
  
    ```csharp  
    // Update the service state to Start Pending.  
    ServiceStatus serviceStatus = new ServiceStatus();  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING;  
    serviceStatus.dwWaitHint = 100000;  
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);  
    ```  
  
    ```vb  
    ' Update the service state to Start Pending.  
    Dim serviceStatus As ServiceStatus = New ServiceStatus()  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING  
    serviceStatus.dwWaitHint = 100000  
    SetServiceStatus(Me.ServiceHandle, serviceStatus)  
    ```  
  
5.  Dodaj kod, aby ustawić stan do uruchomienia na końcu <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody.  
  
    ```csharp
    // Update the service state to Running.  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING;  
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);  
    ```  
  
    ```vb  
    ' Update the service state to Running.  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING  
    SetServiceStatus(Me.ServiceHandle, serviceStatus)  
    ```  
  
6.  (Opcjonalnie) Powtórz tę procedurę dla <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody.  
  
> [!CAUTION]
>  [Menedżera sterowania usługami](http://msdn.microsoft.com/library/windows/desktop/ms685150.aspx) używa `dwWaitHint` i `dwCheckpoint` członkami [struktury SERVICE_STATUS](http://msdn.microsoft.com/library/windows/desktop/ms685996.aspx) określić ilość czasu oczekiwania dla usługi systemu Windows uruchomić lub zamknąć. Jeśli Twoje <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metod Uruchom długie, usługi mogą żądać więcej czasu, przez wywołanie metody [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) ponownie, podając zwiększany `dwCheckPoint` wartość.  
  
<a name="BK_AddInstallers"></a>   
## <a name="adding-installers-to-the-service"></a>Dodawanie instalatorów do usługi  
 Przed uruchomieniem usługi systemu Windows, musisz zainstalować go, który rejestruje go z Menedżerem sterowania usługami. Instalatorzy można dodać do projektu, który obsłuży szczegóły rejestracji.  
  
#### <a name="to-create-the-installers-for-your-service"></a>Aby utworzyć instalatory dla usługi  
  
1.  W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **MyNewService.cs** lub **MyNewService.vb**, a następnie wybierz pozycję **Widok projektanta**.  
  
2.  Kliknij tło projektanta, aby zaznaczyć samą usługę, a nie jakąkolwiek jej zawartość.  
  
3.  Otwórz menu kontekstowe okna Projektanta (Jeśli używasz urządzenia wskazującego, kliknij prawym przyciskiem myszy w oknie), a następnie wybierz pozycję **dodać Instalatora**.  
  
     Domyślnie do projektu zostanie dodana klasa składnika zawierająca dwa instalatory. Nosi nazwę składnika **ProjectInstaller**i zawiera pliki instalacyjne Instalatora usługi, a Instalator usługi przez skojarzony proces.  
  
4.  W **projekt** wyświetlić **ProjectInstaller**, wybierz **serviceInstaller1** dla projektu Visual C# lub **ServiceInstaller1** wizualnego Podstawowe projektu.  
  
5.  W **właściwości** okna, upewnij się, że <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość jest ustawiona na **MyNewService**.  
  
6.  Ustaw **opis** część tekstu, na przykład "Usługi próbki" dla właściwości. Ten tekst jest wyświetlany w oknie usług i ułatwia użytkownikom w identyfikacji usługi i zrozumieć, co jest używane.  
  
7.  Ustaw <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> właściwości tekst, który ma być wyświetlany w oknie usługi **nazwa** kolumny. Na przykład można wprowadzić "MyNewService Display Name". Ta nazwa może być inna niż <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość, która jest to nazwa używana przez system (na przykład, jeśli używasz `net start` polecenie, aby uruchomić usługę).  
  
8.  Ustaw <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwości <xref:System.ServiceProcess.ServiceStartMode.Automatic>.  
  
     ![Właściwości Instalatora dla systemu Windows z](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")  
  
9. W projektancie, wybierz **serviceProcessInstaller1** dla projektu Visual C# lub **ServiceProcessInstaller1** dla projektu Visual Basic. Ustaw <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> właściwości <xref:System.ServiceProcess.ServiceAccount.LocalSystem>. Spowoduje to zainstalowanie i uruchamianie usługi w kontekście konta usługi lokalnej.  
  
    > [!IMPORTANT]
    >  <xref:System.ServiceProcess.ServiceAccount.LocalSystem> Konto ma uprawnienia szerokie, łącznie z możliwością zapisu w dzienniku zdarzeń. Należy go używać ostrożnie, ponieważ może zwiększyć ryzyko ataku przez złośliwe oprogramowanie. W przypadku innych zadań, należy rozważyć użycie <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, które działa jako użytkownik bez uprawnień na komputerze lokalnym i przedstawia poświadczeń anonimowego z żadnym serwerem zdalnym. W tym przykładzie zakończy się niepowodzeniem, Jeśli spróbujesz użyć <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, ponieważ wymaga uprawnień do zapisu w dzienniku zdarzeń.  
  
     Aby uzyskać więcej informacji na temat instalatorów, zobacz [porady: Dodawanie instalatorów do Twojej aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
<a name="BK_StartupParameters"></a>   
## <a name="set-startup-parameters"></a>Ustaw parametry uruchamiania  
 Usługa systemu Windows, takich jak każdego innego pliku wykonywalnego, mogą akceptować argumenty wiersza polecenia lub parametry uruchamiania. Po dodaniu kod do parametrów uruchamiania procesu użytkowników można uruchomić usługi z własne parametry uruchamiania niestandardowych przy użyciu okna usługi w Panelu sterowania systemu Windows. Jednak te parametry uruchamiania nie są zachowywane podczas następnego uruchomienia usługi. Aby ustawić parametry uruchamiania trwale, można ustawić je w rejestrze, jak pokazano w tej procedurze.  
  
> [!NOTE]
>  Przed podjęciem decyzji o Dodaj parametry uruchamiania, należy rozważyć, czy to najlepszy sposób przekazywania informacji do usługi. Mimo że parametry uruchamiania są łatwe w użyciu i do analizy, a użytkownicy mogą łatwo one zastąpione, może być trudne dla użytkowników do odnajdywania i używania bez dokumentacji. Ogólnie rzecz biorąc Jeśli usługa wymaga więcej niż kilka parametrów uruchamiania, należy rozważyć zamiast rejestru lub pliku konfiguracji. Każda usługa systemu Windows ma wpis w rejestrze, w obszarze klucza HKLM\System\CurrentControlSet\services. W kluczu usługi można użyć **parametry** podklucz do przechowywania informacji, które mogą uzyskiwać dostęp do usługi. Pliki konfiguracji aplikacji można użyć usługi systemu Windows tak samo jak w przypadku innych programów. Na przykład kodu, zobacz <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.  
  
#### <a name="adding-startup-parameters"></a>Dodawanie parametrów uruchamiania  
  
1.  W `Main` metody w pliku Program.cs lub MyNewService.Designer.vb, Dodaj argument w wierszu polecenia:  
  
```csharp  
static void Main(string[] args)
{
    ServiceBase[] ServicesToRun = new ServiceBase[] { new MyNewService(args) };
    ServiceBase.Run(ServicesToRun);
}
```  
  
```vb
Shared Sub Main(ByVal cmdArgs() As String)
    Dim ServicesToRun() As System.ServiceProcess.ServiceBase = New System.ServiceProcess.ServiceBase() {New MyNewServiceVB(cmdArgs)}
    System.ServiceProcess.ServiceBase.Run(ServicesToRun)
End Sub
```  
  
2.  Zmień `MyNewService` konstruktora w następujący sposób:  
  
```csharp  
public MyNewService(string[] args)
{
    InitializeComponent();
    string eventSourceName = "MySource";
    string logName = "MyNewLog";
    if (args.Count() > 0) 
    {
        eventSourceName = args[0];
    }
    if (args.Count() > 1)
    {
        logName = args[1];
    }
    eventLog1 = new System.Diagnostics.EventLog();
    if (!System.Diagnostics.EventLog.SourceExists(eventSourceName))
    {
        System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName);
    }
    eventLog1.Source = eventSourceName;
    eventLog1.Log = logName;        
}
```  
  
```vb  
Public Sub New(ByVal cmdArgs() As String)
    InitializeComponent()
    Dim eventSourceName As String = "MySource"
    Dim logName As String = "MyNewLog"
    If (cmdArgs.Count() > 0) Then
        eventSourceName = cmdArgs(0)
    End If
    If (cmdArgs.Count() > 1) Then
        logName = cmdArgs(1)
    End If
    eventLog1 = New System.Diagnostics.EventLog()
    If (Not System.Diagnostics.EventLog.SourceExists(eventSourceName)) Then
        System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName)
    End If
    eventLog1.Source = eventSourceName
    eventLog1.Log = logName
End Sub  
```  
  
Ten kod ustawia nazwę źródła i dziennik zdarzeń zgodnie z parametrami dostarczonego uruchomienia lub jeśli podano argumenty nie są używane wartości domyślne.  
  
3. Aby określić argumenty wiersza polecenia, Dodaj następujący kod, aby `ProjectInstaller` klasy ProjectInstaller.cs lub ProjectInstaller.vb:  
  
```csharp  
protected override void OnBeforeInstall(IDictionary savedState)
{
    string parameter = "MySource1\" \"MyLogFile1";
    Context.Parameters["assemblypath"] = "\"" + Context.Parameters["assemblypath"] + "\" \"" + parameter + "\"";
    base.OnBeforeInstall(savedState);
}
```

```vb  
Protected Overrides Sub OnBeforeInstall(ByVal savedState As IDictionary)
    Dim parameter As String = "MySource1"" ""MyLogFile1"
    Context.Parameters("assemblypath") = """" + Context.Parameters("assemblypath") + """ """ + parameter + """"
    MyBase.OnBeforeInstall(savedState)
End Sub  
```  
  
Ten kod modyfikuje **ImagePath** klucz rejestru zwykle zawiera pełną ścieżkę do pliku wykonywalnego usługi systemu Windows, dodając domyślne wartości parametrów. Znaki cudzysłowu wokół ścieżki (i wokół każdego parametru poszczególnych) są wymagane dla usługi prawidłowo uruchomiona. Aby zmienić parametry uruchamiania usługi systemu Windows, użytkownicy mogą zmieniać parametrów podanych w **ImagePath** klucza rejestru, tym lepiej sposób jest Zmień ją programowo i udostępniają funkcje dla użytkowników w przyjazne sposób (na przykład w narzędzia zarządzania lub konfiguracją).  
  
<a name="BK_Build"></a>   
## <a name="building-the-service"></a>Tworzenie usługi  
  
#### <a name="to-build-your-service-project"></a>Aby skompilować projekt usługi  
  
1.  W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla projektu, a następnie wybierz **właściwości**. Są wyświetlane na stronach właściwości projektu.  
  
2.  Na karcie aplikacji w **obiekt uruchomieniowy** wybierz **MyNewService.Program**.  
  
3.  W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla projektu, a następnie wybierz **kompilacji** do kompilacji projektu (klawiatury: Ctrl + Shift + B).  
  
<a name="BK_Install"></a>   
## <a name="installing-the-service"></a>Instalowanie usługi  
 Teraz gdy masz utworzoną usługę systemu Windows, należy ją zainstalować. Aby zainstalować usługi systemu Windows, należy mieć poświadczenia administracyjne na komputerze, na którym instalujesz go.  
  
#### <a name="to-install-a-windows-service"></a>Aby zainstalować usługę systemu Windows  
  
1.  W systemie Windows 7 i Windows Server otwórz **wiersza polecenia dewelopera** w obszarze **programu Visual Studio Tools** w **Start** menu. W systemie Windows 8 lub Windows 8.1, wybierz **programu Visual Studio Tools** Kafelek na **Start** ekranu, a następnie uruchom wiersz polecenia dla deweloperów z poświadczeniami administracyjnymi. (Jeśli używasz myszy, kliknij prawym przyciskiem myszy **wiersza polecenia dewelopera**, a następnie wybierz pozycję **Uruchom jako Administrator**.)  
  
2.  W oknie wiersza polecenia przejdź do folderu, który zawiera dane wyjściowe projektu. Na przykład w folderze Moje dokumenty przejdź do folderu Visual Studio 2013\Projects\MyNewService\bin\Debug.  
  
3.  Wprowadź następujące polecenie:  
  
    ```  
    installutil.exe MyNewService.exe  
    ```  
  
     Jeśli usługa zostanie zainstalowana pomyślnie, narzędzie installutil.exe zakomunikuje sukces. Jeśli system nie może odnaleźć InstallUtil.exe, upewnij się, że plik istnieje na tym komputerze. To narzędzie jest zainstalowany w środowisku .NET Framework do folderu `%WINDIR%\Microsoft.NET\Framework[64]\` *framework_version*. Na przykład domyślna ścieżka dla 32-bitowej wersji programu .NET Framework 4, 4.5.1, 4.5 i 4.5.2 to `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.  
  
     Jeśli proces installutil.exe zgłasza błąd, sprawdź dziennik instalacji, aby dowiedzieć się, dlaczego. Domyślnie dziennik jest w tym samym folderze co plik wykonywalny usługi. Instalacja może zakończyć się niepowodzeniem, jeśli <xref:System.ComponentModel.RunInstallerAttribute> klasy nie jest dostępny w `ProjectInstaller` klasy, w przeciwnym razie ten atrybut nie jest ustawiony na `true`, w przeciwnym razie `ProjectInstaller` klasa nie jest `public`.  
  
     Aby uzyskać więcej informacji, zobacz [porady: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
<a name="BK_StartService"></a>   
## <a name="starting-and-running-the-service"></a>Uruchomienie usługi  
  
#### <a name="to-start-and-stop-your-service"></a>Aby uruchomić i zatrzymać usługę  
  
1.  W systemie Windows, należy otworzyć **Start** ekranu lub **Start** menu, a typ `services.msc`.  
  
     Powinien zostać wyświetlony **MyNewService** na liście **usług** okna.  
  
     ![MyNewService w oknie usług. ] (../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG "WindowsServices_ServicesWindow")  
  
2.  W **usług** okna, otwórz menu skrótów dla usługi, a następnie wybierz **Start**.  
  
3.  Otwórz menu skrótów dla usługi, a następnie wybierz pozycję **zatrzymać**.  
  
4.  (Opcjonalnie) Z poziomu wiersza polecenia, można użyć poleceń `net start``ServiceName` i `net stop``ServiceName` do uruchamiania i zatrzymywania usługi.  
  
#### <a name="to-verify-the-event-log-output-of-your-service"></a>Aby zweryfikować informacje o efektach działania usługi znajdujące się w dzienniku zdarzeń  
  
1.  W programie Visual Studio Otwórz **Eksploratora serwera** (klawiatury: Ctrl + Alt + S) i uzyskać dostęp do **dzienniki zdarzeń** węzła na komputerze lokalnym.  
  
2.  Znajdź na liście **MyNewLog** (lub **MyLogFile1**, jeśli użyto procedury opcjonalnej można dodać argumenty wiersza polecenia) i rozwiń go. Powinny pojawić się wpisy dla dwie akcje (rozpoczęcie i zakończenie) wykonanych z usługą.  
  
     ![Użyj podglądu zdarzeń, aby wyświetlić wpisy w dzienniku zdarzeń. ] (../../../docs/framework/windows-services/media/windowsservices-eventviewer.PNG "WindowsServices_EventViewer")  
  
<a name="BK_Uninstall"></a>   
## <a name="uninstalling-a-windows-service"></a>Odinstalowywanie usług systemu Windows  
  
#### <a name="to-uninstall-your-service"></a>Aby odinstalować usługę  
  
1.  Otwórz wiersz polecenia dewelopera z poświadczeniami administracyjnymi.  
  
2.  W oknie wiersza polecenia przejdź do folderu, który zawiera dane wyjściowe projektu. Na przykład w folderze Moje dokumenty przejdź do folderu Visual Studio 2013\Projects\MyNewService\bin\Debug.  
  
3.  Wprowadź następujące polecenie:  
  
    ```  
    installutil.exe /u MyNewService.exe  
    ```  
  
     Jeśli usługa zostanie pomyślnie odinstalowana, narzędzie installutil.exe zakomunikuje jej usunięcie. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="next-steps"></a>Następne kroki  
 Można utworzyć autonomiczny program instalacyjny, który inne można użyć do zainstalowania usługi systemu Windows, ale wymaga dodatkowych kroków. Funkcja ClickOnce nie obsługuje usług systemu Windows, dlatego nie można używać Kreatora publikacji. Można używać pełnego wydania narzędzia InstallShield, którego nie dostarcza firma Microsoft. Aby uzyskać więcej informacji na temat InstallShield, zobacz [InstallShield Limited Edition](/visualstudio/deployment/installshield-limited-edition). Można również użyć [zestaw narzędzi XML Instalatora Windows](http://go.microsoft.com/fwlink/?LinkId=249067) Aby utworzyć Instalatora usługi systemu Windows.  
  
 Może zbadać użycie <xref:System.ServiceProcess.ServiceController> składników, co pozwala na wysyłanie poleceń z usługą został zainstalowany.  
  
 Odpowiednio konfigurując instalatora, można spowodować generowanie dziennika zdarzeń podczas instalowania aplikacji, a nie jej działania. Ponadto z chwilą odinstalowania aplikacji dziennik zostanie usunięty. Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.EventLogInstaller> strony odwołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje usług systemu Windows](../../../docs/framework/windows-services/index.md)  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Instrukcje: debugowanie aplikacji usług systemu Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Usługi (system Windows)](http://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)
