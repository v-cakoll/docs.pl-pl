---
title: Tworzenie aplikacji usługi Windows w programie Visual Studio
ms.date: 09/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
manager: douge
ms.openlocfilehash: 27acdac5d34b96dd04fec1bb763edec9077ff928
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677373"
---
# <a name="walkthrough-create-a-windows-service-app"></a>Przewodnik: Tworzenie aplikacji usługi Windows

W tym artykule przedstawiono sposób tworzenia prostej aplikacji usługi Windows w programie Visual Studio, która wypisuje komunikaty w dzienniku zdarzeń.

## <a name="create-a-service"></a>Tworzenie usługi

Aby rozpocząć, Utwórz projekt i ustaw wartości, które są niezbędne do poprawnego działania usługi.

1. W programie Visual Studio, na pasku menu wybierz **pliku** > **New** > **projektu** (lub naciśnij **Ctrl** + **Shift**+**N**) aby otworzyć **nowy projekt** okna dialogowego.

2. Przejdź do, a następnie wybierz pozycję **usługi Windows** szablonu projektu. Rozwiń **zainstalowane** > [**Visual C#** lub **języka Visual Basic**] > **pulpitu Windows**, lub typu **usługi Windows** w polu wyszukiwania w prawym górnym rogu.

   ![Szablon usługi Windows w oknie dialogowym Nowy projekt, w programie Visual Studio](media/new-project-dialog.png)

   > [!NOTE]
   > Jeśli nie widzisz **usługi Windows** szablonu, użytkownik może być konieczne zainstalowanie **programowanie aplikacji klasycznych dla platformy .NET** obciążenia. W **nowy projekt** okno dialogowe, kliknij link, który jest wyświetlany komunikat **Otwórz Instalator programu Visual Studio** w lewym dolnym rogu. W **Instalatora programu Visual Studio**, wybierz opcję **programowanie aplikacji klasycznych dla platformy .NET** obciążenia, a następnie wybierz **Modyfikuj**.

3. Nadaj projektowi nazwę **MyNewService**, a następnie wybierz **OK**.

   Szablon projektu zawiera klasę składnika o nazwie `Service1` tej, która dziedziczy <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>. Zawiera ona większość podstawowego kodu usługi, takie jak kod, aby uruchomić usługę.

## <a name="rename-the-service"></a>Zmień nazwę usługi

Zmień nazwę usługi z **Service1** do **MyNewService**.

1. W **projektowania** widok Service1.cs (lub Service1.vb), kliknij link, aby **przejdź do widoku kodu**. Kliknij prawym przyciskiem myszy **Service1** i wybierz **Zmień nazwę** z menu kontekstowego. Wprowadź **MyNewService** , a następnie naciśnij klawisz **Enter** lub kliknij przycisk **Zastosuj**.

2. W **właściwości** okno **Service1.cs [projekt]** lub **Service1.vb [projekt]**, zmień **ServiceName** wartość **MyNewService**.

3. W **Eksploratora rozwiązań**, Zmień nazwę **Service1.cs** do **MyNewService.cs**, lub zmień nazwę **Service1.vb** do  **MyNewService.vb**.

## <a name="add-features-to-the-service"></a>Dodawanie funkcji do usługi

W tej sekcji dodasz niestandardowy dziennik zdarzeń do usługi Windows. Dzienniki zdarzeń nie w żaden sposób powiązane z usługami systemu Windows. <xref:System.Diagnostics.EventLog> Składnik jest używany tutaj jako przykładu składnika, możesz dodać do usługi Windows.

### <a name="add-custom-event-log-functionality"></a>Dodać funkcjonalność niestandardowego dziennika zdarzeń

1. W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **MyNewService.cs** lub **MyNewService.vb**, a następnie wybierz **Projektant widoków**.

2. Z **składniki** części **przybornika**, przeciągnij <xref:System.Diagnostics.EventLog> składnik do projektanta.

3. W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **MyNewService.cs** lub **MyNewService.vb**, a następnie wybierz **Wyświetl kod**.

4. Zmodyfikuj konstruktora, aby zdefiniować niestandardowy dziennik zdarzeń:

   ```csharp
   public MyNewService()
   {
        InitializeComponent();

        eventLog1 = new System.Diagnostics.EventLog();
        if (!System.Diagnostics.EventLog.SourceExists("MySource"))
        {
            System.Diagnostics.EventLog.CreateEventSource(
                "MySource", "MyNewLog");
        }
        eventLog1.Source = "MySource";
        eventLog1.Log = "MyNewLog";
    }
   ```

   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

### <a name="define-what-occurs-when-the-service-starts"></a>Określić zachowanie występujące podczas uruchamiania usługi

W edytorze kodu zlokalizuj <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodę, która została zastąpiona automatycznie podczas tworzenia projektu. Dodaj wiersz kodu, który zapisuje wpis dziennika zdarzeń podczas uruchamiania usługi:

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

Aplikacja usługi jest przeznaczony jako długotrwałych, dzięki czemu zwykle sonduje lub monitoruje coś w systemie. Monitorowanie jest skonfigurowana w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody. Jednak <xref:System.ServiceProcess.ServiceBase.OnStart%2A> faktycznie nie wykonuje monitorowania. <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Metoda musi powrócić do systemu operacyjnego, po rozpoczęciu operacji usługi. Nie może być wykonywana bezterminowo w pętli ani nakładać żadnych blokad. Aby skonfigurować prosty mechanizm sondowania, można użyć <xref:System.Timers.Timer?displayProperty=nameWithType> składnika w następujący sposób: W <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody, ustawianie parametrów na części, a następnie ustaw <xref:System.Timers.Timer.Enabled%2A> właściwość `true`. Czasomierz wywołuje zdarzenia w kodzie okresowo, co usługa może zrobić, jego monitorowanie. Aby to zrobić, można użyć następującego kodu:

```csharp
// Set up a timer that triggers every minute.
System.Timers.Timer timer = new System.Timers.Timer();
timer.Interval = 60000; // 60 seconds
timer.Elapsed += new System.Timers.ElapsedEventHandler(this.OnTimer);
timer.Start();
```

```vb
' Set up a timer that triggers every minute.
Dim timer As System.Timers.Timer = New System.Timers.Timer()
timer.Interval = 60000 ' 60 seconds
AddHandler timer.Elapsed, AddressOf Me.OnTimer
timer.Start()
```

Dodaj zmienną składową do klasy. Zawiera ona identyfikator następne zdarzenie do zapisu do dziennika zdarzeń.

```csharp
private int eventId = 1;
```

```vb
Private eventId As Integer = 1
```

Dodaj nową metodę, aby obsłużyć zdarzenie czasomierza:

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

Można wykonywać zadania za pomocą wątków procesów roboczych w tle zamiast uruchamiać swoją pracę w wątku głównym. Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.

### <a name="define-what-occurs-when-the-service-is-stopped"></a>Określić zachowanie występujące podczas zatrzymywania usługi

Dodaj wiersz kodu do <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metodę, która dodaje wpis w dzienniku zdarzeń, gdy usługa zostanie zatrzymana:

```csharp
eventLog1.WriteEntry("In OnStop.");
```

[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a>Zdefiniuj inne akcje usługi

Można zastąpić <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, i <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> metody, aby zdefiniować dodatkowe przetwarzanie składnika. W poniższym kodzie pokazano, jak można zastąpić <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> metody:

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

Pewne niestandardowe czynności muszą występować po zainstalowaniu usługi Windows przez <xref:System.Configuration.Install.Installer> klasy. Program Visual Studio może utworzyć te instalatory specjalnie dla usługi systemu Windows i dodać je do projektu.

## <a name="set-service-status"></a>Ustaw stan usługi

Usługi zgłaszają swój stan do menedżera kontroli usług, dzięki czemu użytkownicy można stwierdzić, czy usługa działa poprawnie. Domyślnie, usług, które dziedziczą z <xref:System.ServiceProcess.ServiceBase> ograniczony zestaw ustawień stanu, w tym zatrzymana, wstrzymana i uruchamianie raportu. Jeśli usługa ma nieco podczas uruchamiania go może być przydatne do raportowania stanu Start oczekiwania. Możesz również wdrożyć ustawienia stanu Start oczekujące i Zatrzymaj oczekiwanie przez dodanie kodu, która wywołuje Windows [funkcji SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).

Aby zaimplementować usługę w stanie oczekiwania:

1. Dodaj `using` instrukcji lub `Imports` deklaracji pod kątem <xref:System.Runtime.InteropServices?displayProperty=nameWithType> przestrzeni nazw w pliku MyNewService.cs lub MyNewService.vb:

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. Dodaj następujący kod do MyNewService.cs do deklarowania `ServiceState` wartości i można dodać struktury stanu, która będzie używana na platformie wywołania wywołania:

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

3. Teraz w `MyNewService` klasy, Zadeklaruj [funkcji SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) przy użyciu [wywołania platformy](../interop/consuming-unmanaged-dll-functions.md):

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. Aby zaimplementować Rozpocznij oczekiwanie stanu, Dodaj następujący kod na początku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody:

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

5. Dodaj kod, aby ustawić stan uruchomione na końcu <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody.

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

6. (Opcjonalnie) Powtórz tę procedurę dla <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody.

> [!NOTE]
> [Menedżera sterowania usługami](/windows/desktop/Services/service-control-manager) używa `dwWaitHint` i `dwCheckpoint` członkowie [struktury SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status) określić ilość czasu oczekiwania dla usługi Windows uruchomić lub zamknąć. Jeśli Twoje <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody trwają długo, usługi mogą żądać więcej czasu, przez wywołanie metody [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) ponownie, używając zwiększona `dwCheckPoint` wartość.

## <a name="add-installers-to-the-service"></a>Dodawanie instalatorów do usługi

Przed uruchomieniem usługi Windows, musisz zainstalować go, który rejestruje je z Menedżerem sterowania usługami. Możesz dodać instalatory projektu, które obsługi szczegółów rejestracji.

1. W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **MyNewService.cs** lub **MyNewService.vb**, a następnie wybierz **Projektant widoków**.

2. Kliknij tło projektanta, aby zaznaczyć samą usługę, a nie jakąkolwiek jej zawartość.

3. Otwórz menu kontekstowe okna Projektanta (Jeśli używasz urządzenia wskazującego, kliknij prawym przyciskiem myszy wewnątrz okna), a następnie wybierz **Dodaj Instalatora**.

   Domyślnie do projektu zostanie dodana klasa składnika zawierająca dwa instalatory. Składnik nazywa **ProjectInstaller**, zawiera pliki instalacyjne są Instalatora usługi i procesu skojarzonego Instalatora usługi.

4. W **projektowania** wyświetlić **ProjectInstaller**, wybierz **serviceInstaller1** dla projektu Visual C# lub **ServiceInstaller1** dla wizualizacji Podstawowy projekt.

5. W **właściwości** okna, upewnij się, że <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość jest ustawiona na **MyNewService**.

6. Ustaw **opis** właściwość jakiś tekst, na przykład "Przykładowej usługi". Ten tekst pojawia się okno usługi i pomaga użytkownikom identyfikować usługi i zrozumieć, co to jest używany.

7. Ustaw <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> właściwość tekst, który ma być wyświetlany w oknie usługi **nazwa** kolumny. Na przykład można wprowadzić "MyNewService Display Name". Ta nazwa może różnić się od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość, która jest to nazwa używana przez system (na przykład, kiedy używasz `net start` polecenie, aby uruchomić usługę).

8. Ustaw <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwość <xref:System.ServiceProcess.ServiceStartMode.Automatic>.

     ![Właściwości Instalatora usługi Windows](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")

9. W projektancie, wybierz **serviceProcessInstaller1** dla projektu Visual C# lub **ServiceProcessInstaller1** dla projektów języka Visual Basic. Ustaw <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> właściwość <xref:System.ServiceProcess.ServiceAccount.LocalSystem>. Powoduje to usługa, można zainstalować i uruchomić przy użyciu lokalnego konta systemowego.

    > [!IMPORTANT]
    > <xref:System.ServiceProcess.ServiceAccount.LocalSystem> Konto ma szerokie uprawnienia, w tym możliwość zapisu do dziennika zdarzeń. Należy go używać ostrożnie, ponieważ może zwiększyć ryzyko ataku przez złośliwe oprogramowanie. W przypadku innych zadań, należy wziąć pod uwagę przy użyciu <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, które działa jako użytkownik bez uprawnień na komputerze lokalnym i przedstawia poświadczenia anonimowe każdemu zdalnemu serwerowi. W tym przykładzie zakończy się niepowodzeniem, jeśli zostanie podjęta próba użycia <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, ponieważ wymaga uprawnień do zapisu w dzienniku zdarzeń.

Aby uzyskać więcej informacji na temat instalatory zobacz [porady: Dodawanie instalatorów do usługi aplikacji](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).

## <a name="optional-set-startup-parameters"></a>(Opcjonalnie) Ustaw parametry uruchamiania

Do usług Windows, takich jak każdego innego pliku wykonywalnego, może akceptować argumentów wiersza polecenia lub parametry uruchamiania. Po dodaniu kodu z parametrami uruchamiania procesu użytkownicy mogą uruchamiać własne parametry niestandardowe uruchomienia usługi przy użyciu okna usługi w Panelu sterowania Windows. Jednak te parametry uruchamiania nie są zachowywane podczas następnego uruchomienia usługi. Aby ustawić parametry uruchamiania trwale, można ustawić je w rejestrze, jak pokazano w tej procedurze.

> [!NOTE]
> Przed podjęciem decyzji o Dodaj parametry uruchamiania, należy wziąć pod uwagę niezależnie czy dotyczyć to najlepszy sposób przekazywania informacji do usługi. Mimo, że parametry uruchamiania są łatwe w użyciu i do analizy, a użytkownicy mogą łatwo je zastąpić, może być trudne dla użytkowników do użytku bez dokumentacji. Ogólnie rzecz biorąc Jeśli usługa wymaga więcej niż kilku Parametry uruchamiania, należy rozważyć użycie rejestru lub pliku konfiguracji zamiast tego. Każda usługa Windows ma wpis w kluczu rejestru **klucza HKLM\System\CurrentControlSet\services**. W kluczu usługi można użyć **parametry** podklucz do przechowywania informacji, które mogą uzyskiwać dostęp do usługi. Może używać plików konfiguracji aplikacji dla usługi Windows w taki sam sposób jak w przypadku innych programów. Przykładowy kod, zobacz <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.

Aby dodać parametry uruchamiania:

1. W `Main` metody w pliku Program.cs lub MyNewService.Designer.vb, Dodawanie parametru wejściowego do przekazania do konstruktora usługi:

   ```csharp
   static void Main(string[] args)
   {
       ServiceBase[] ServicesToRun;
       ServicesToRun = new ServiceBase[]
       {
           new MyNewService(args)
       };
       ServiceBase.Run(ServicesToRun);
   }
   ```

   ```vb
   Shared Sub Main(ByVal cmdArgs() As String)
       Dim ServicesToRun() As System.ServiceProcess.ServiceBase = New System.ServiceProcess.ServiceBase() {New MyNewServiceVB(cmdArgs)}
       System.ServiceProcess.ServiceBase.Run(ServicesToRun)
   End Sub
   ```

2. Zmiana `MyNewService` konstruktora w następujący sposób:

   ```csharp
   public MyNewService(string[] args)
   {
       InitializeComponent();

        string eventSourceName = "MySource";
        string logName = "MyNewLog";

        if (args.Length > 0)
        {
            eventSourceName = args[0];
        }

        if (args.Length > 1)
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

   Ten kod ustawia nazwę źródła i dziennik zdarzeń, zgodnie z Parametry uruchamiania podane lub używa wartości domyślnych, jeśli zostały dostarczone żadne argumenty.

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

   Ten kod modyfikuje **ImagePath** klucz rejestru zwykle zawiera pełną ścieżkę do pliku wykonywalnego dla usługi Windows przez dodanie wartości domyślne parametrów. Znaki cudzysłowu wokół ścieżki (i wokół każdego parametru poszczególnych) są wymagane dla usługi została prawidłowo uruchomiona. Aby zmienić parametry uruchamiania dla tej usługi Windows, użytkownicy mogą zmieniać parametrów podanych w **ImagePath** klucz rejestru, mimo że lepszy sposób jest programowe zmienianie i udostępniają funkcje dla użytkowników w przyjazne sposób (na przykład narzędzie do zarządzania lub konfiguracji).

## <a name="build-the-service"></a>Tworzenie usługi

1. W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla projektu, a następnie wybierz **właściwości**.

   Są wyświetlane na stronach właściwości projektu.

2. Na **aplikacji** na karcie **obiekt początkowy** wybierz **MyNewService.Program**.

3. W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla projektu, a następnie wybierz **kompilacji** do skompilowania projektu (lub naciśnij **Ctrl**+**Shift**  + **B**).

## <a name="install-the-service"></a>Instalowanie usługi

Teraz, gdy masz utworzoną usługę Windows, należy ją zainstalować. Aby zainstalować usługę Windows, musi mieć poświadczenia administratora na komputerze, na którym instalujesz go.

1. Otwórz **wiersz polecenia programisty dla programu Visual Studio** przy użyciu poświadczeń administracyjnych. Jeśli używasz myszy, kliknij prawym przyciskiem myszy **wiersz polecenia programisty dla programu VS 2017** w Windows z menu Start, a następnie wybierz **więcej** > **Uruchom jako Administrator** .

2. W **wiersz polecenia dla deweloperów** okna, przejdź do folderu, który zawiera dane wyjściowe projektu (domyślnie jest *\bin\Debug* podkatalogu projektu).

3. Wprowadź następujące polecenie:

    ```shell
    installutil.exe MyNewService.exe
    ```

    Jeśli usługa zostanie zainstalowana pomyślnie, **installutil.exe** zgłosi powodzenie operacji. Jeśli system nie może odnaleźć **InstallUtil.exe**, upewnij się, że istnieje na tym komputerze. To narzędzie jest instalowane z .NET Framework do folderu *% windir%\Microsoft.NET\Framework[64]\\[framework w wersji]*. Na przykład jest domyślna ścieżka dla 32-bitowej wersji *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.

    Jeśli **installutil.exe** przetwarzać raporty o awarii, sprawdź dziennik instalacji, aby dowiedzieć się, dlaczego. Domyślnie dziennik jest w tym samym folderze co plik wykonywalny usługi. Instalacja może zakończyć się niepowodzeniem, jeśli <xref:System.ComponentModel.RunInstallerAttribute> klasy nie znajduje się na `ProjectInstaller` klasy, jeśli ten atrybut nie jest równa **true**, lub jeśli `ProjectInstaller` klasy nie jest oznaczony jako **publicznych**.

Aby uzyskać więcej informacji, zobacz [porady: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).

## <a name="start-and-run-the-service"></a>Uruchom program i uruchom usługę

1. Windows, otwórz **usług** aplikacji klasycznej. Naciśnij klawisz **Windows**+**R** otworzyć **Uruchom** , a następnie wprowadź **services.msc** i naciśnij klawisz **Enter**  lub kliknij przycisk **OK**.

     Powinien zostać wyświetlony na liście usługi **usług**, wyświetlane alfabetycznie według nazwy wyświetlanej, ustaw dla niego.

     ![MyNewService w oknie usług.](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG)

2. W **usług**, otwórz menu skrótów dla usługi, a następnie wybierz **Start**.

3. Aby zatrzymać usługę, otwórz menu skrótów dla usługi, a następnie wybierz **zatrzymać**.

4. (Opcjonalnie) W wierszu polecenia można użyć poleceń `net start ServiceName` i `net stop ServiceName` uruchamianie i zatrzymywanie usługi.

### <a name="verify-the-event-log-output-of-your-service"></a>Sprawdź dane wyjściowe dziennika zdarzeń, usługi

1. Otwórz **Podgląd zdarzeń** , zaczynając wpisywanie **Podgląd zdarzeń** w polu wyszukiwania na pasku zadań Windows, a następnie wybierając pozycję **Podgląd zdarzeń** w wynikach wyszukiwania.

   > [!TIP]
   > W programie Visual Studio są dostępne dzienniki zdarzeń, otwierając **Eksploratora serwera** (klawiatura: **Ctrl**+**Alt**+**S**) rozwijanie i **dzienniki zdarzeń** węzła na komputerze lokalnym.

2. W **Podgląd zdarzeń**, rozwiń węzeł **Dzienniki aplikacji i usług**.

3. Odszukaj **MyNewLog** (lub **MyLogFile1**, po wykonaniu procedury opcjonalnej można dodać argumenty wiersza polecenia) i rozwiń go. Powinny być widoczne wpisy dwie akcje (rozpoczęcie i zakończenie), wykonanych przez usługę.

     ![Użyj podglądu zdarzeń, aby wyświetlić wpisy dziennika zdarzeń](../../../docs/framework/windows-services/media/windows-service-event-viewer.png)

## <a name="uninstall-the-service"></a>Odinstaluj usługę

1. Otwórz **wiersz polecenia programisty dla programu Visual Studio** przy użyciu poświadczeń administracyjnych.

2. W oknie wiersza polecenia przejdź do folderu, który zawiera dane wyjściowe projektu.

3. Wprowadź następujące polecenie:

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   Jeśli usługa zostanie pomyślnie, odinstalowana **installutil.exe** raporty usługi został pomyślnie usunięty. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).

## <a name="next-steps"></a>Następne kroki

Teraz, po utworzeniu usługi, można utworzyć program instalacyjny autonomicznego, który inne można użyć do zainstalowania usługi Windows. Funkcja ClickOnce nie obsługuje usług Windows, ale można użyć [zestaw narzędzi WiX](http://wixtoolset.org/) możliwość utworzenia Instalatora usługi Windows. Zapoznać się z pomysłami z innymi zobacz [Utwórz pakiet instalacyjny](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).

Może zbadać użycie <xref:System.ServiceProcess.ServiceController> składnik, który umożliwia wysyłanie poleceń do usługi, po zainstalowaniu.

Odpowiednio konfigurując instalatora, można spowodować generowanie dziennika zdarzeń podczas instalowania aplikacji, a nie jej działania. Ponadto z chwilą odinstalowania aplikacji dziennik zostanie usunięty. Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.EventLogInstaller> odwołania do stron.

## <a name="see-also"></a>Zobacz także

- [Aplikacje usług Windows](../../../docs/framework/windows-services/index.md)
- [Wprowadzenie do aplikacji usług Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Porady: debugowanie aplikacji usług Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [Usługi (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)
