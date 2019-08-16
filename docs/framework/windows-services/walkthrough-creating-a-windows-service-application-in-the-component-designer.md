---
title: 'Samouczek: Tworzenie aplikacji usługi systemu Windows'
ms.date: 03/27/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
ms.openlocfilehash: df2a99b6fe288cfa8b8a5d60bb127849323ed3a9
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545323"
---
# <a name="tutorial-create-a-windows-service-app"></a>Samouczek: Tworzenie aplikacji usługi systemu Windows

W tym artykule pokazano, jak utworzyć aplikację usługi systemu Windows w programie Visual Studio, która zapisuje komunikaty w dzienniku zdarzeń.

## <a name="create-a-service"></a>Tworzenie usługi

Aby rozpocząć, Utwórz projekt i ustaw wartości, które są wymagane do poprawnego działania usługi.

1. Z menu **plik** programu Visual Studio wybierz pozycję **Nowy** > **projekt** (lub naciśnij **klawisze CTRL**+**SHIFT**+**N**), aby otworzyć okno **Nowy projekt** .

2. Przejdź do i wybierz szablon projektu **usługi systemu Windows (.NET Framework)** . Aby go znaleźć, rozwiń węzeł **zainstalowane** i **Wizualizacja C#**  lub **Visual Basic**, a następnie wybierz pozycję **Windows Desktop**. Lub wprowadź *usługę systemu Windows* w polu wyszukiwania w prawym górnym rogu, a następnie naciśnij klawisz **Enter**.

   ![Szablon usługi systemu Windows w oknie dialogowym Nowy projekt w programie Visual Studio](media/new-project-dialog.png)

   > [!NOTE]
   > Jeśli szablon **usługi systemu Windows** nie jest widoczny, może być konieczne zainstalowanie obciążeń **programistycznych programu .NET Desktop** :
   >
   > W oknie dialogowym **Nowy projekt** wybierz pozycję **Otwórz Instalator programu Visual Studio** w lewym dolnym rogu. Wybierz obciążenie **Programowanie aplikacji klasycznych platformy .NET** , a następnie wybierz pozycję **Modyfikuj**.

3. W obszarze **Nazwa**wpisz *MyNewService*, a następnie wybierz przycisk **OK**.

   Zostanie wyświetlona karta **projektowanie** (**Service1.cs [projekt]** lub **Service1. vb [projekt]** ).

   Szablon projektu zawiera klasę składnika o nazwie `Service1` , która dziedziczy z. <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> Zawiera on wiele podstawowych kodów usług, takich jak kod do uruchomienia usługi.

## <a name="rename-the-service"></a>Zmień nazwę usługi

Zmień nazwę usługi z **Service1** na **MyNewService**.

1. W **Eksplorator rozwiązań**wybierz pozycję **Service1.cs**lub **Service1. vb**i wybierz polecenie **Zmień nazwę** z menu skrótów. Zmień nazwę pliku na **MyNewService.cs**lub **MyNewService. vb**, a następnie naciśnij klawisz **Enter** .

    Zostanie wyświetlone okno podręczne z pytaniem, czy chcesz zmienić nazwy wszystkich odwołań do elementu kodu *Service1*.

2. W oknie podręcznym wybierz pozycję **tak**.

    ![Zmień nazwę monitu](media/windows-service-rename.png "Monit o zmianę nazwy usługi systemu Windows")

3. Na karcie **projektowanie** wybierz pozycję **Właściwości** z menu skrótów. W oknie **Właściwości** Zmień wartość właściwości **ServiceName** na *MyNewService*.

    ![Właściwości usługi](media/windows-service-properties.png "Właściwości usługi systemu Windows")

4. Wybierz pozycję **Zapisz wszystko** w menu **plik** .

## <a name="add-features-to-the-service"></a>Dodawanie funkcji do usługi

W tej sekcji dodasz niestandardowy dziennik zdarzeń do usługi systemu Windows. <xref:System.Diagnostics.EventLog> Składnik jest przykładem typu składnika, który można dodać do usługi systemu Windows.

### <a name="add-custom-event-log-functionality"></a>Dodaj niestandardową funkcję dziennika zdarzeń

1. W **Eksplorator rozwiązań**z menu skrótów dla **MyNewService.cs**lub **MyNewService. vb**wybierz polecenie **Projektant widoków**.

2. W **przyborniku**rozwiń węzeł **składniki**, a następnie przeciągnij składnik **EventLog** do karty **Service1.cs [Design]** lub **Service1. vb [Design]** .

3. W **Eksplorator rozwiązań**z menu skrótów dla **MyNewService.cs**lub **MyNewService. vb**wybierz polecenie **Wyświetl kod**.

4. Zdefiniuj niestandardowy dziennik zdarzeń. W C#przypadku, Edytuj istniejący `MyNewService()` Konstruktor; dla `New()` Visual Basic Dodaj Konstruktor:

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. `Imports` <xref:System.Diagnostics?displayProperty=nameWithType>Dodaj instrukcję do MyNewService.cs (jeśli jeszcze nie istnieje) lub instrukcji MyNewService. vb dla przestrzeni nazw: `using`

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. Wybierz pozycję **Zapisz wszystko** w menu **plik** .

### <a name="define-what-occurs-when-the-service-starts"></a>Zdefiniuj, co ma miejsce w przypadku uruchomienia usługi

W edytorze kodu dla **MyNewService.cs** lub **MyNewService. vb**Znajdź <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodę; Program Visual Studio automatycznie utworzył pustą definicję metody podczas tworzenia projektu. Dodaj kod, który zapisuje wpis w dzienniku zdarzeń po uruchomieniu usługi:

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a>Sondowania

Ponieważ aplikacja usługi jest zaprojektowana tak, aby była długotrwała, zwykle sonduje lub monitoruje system, który został skonfigurowany w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodzie. `OnStart` Metoda musi powrócić do systemu operacyjnego po rozpoczęciu operacji usługi, aby system nie został zablokowany.

Aby skonfigurować prosty mechanizm sondowania, użyj <xref:System.Timers.Timer?displayProperty=nameWithType> składnika. Czasomierz zgłasza <xref:System.Timers.Timer.Elapsed> zdarzenie w regularnych odstępach czasu, w którym usługa może przeprowadzić monitorowanie. <xref:System.Timers.Timer> Składnik jest używany w następujący sposób:

- Ustaw właściwości <xref:System.Timers.Timer> składnika `MyNewService.OnStart` w metodzie.
- Uruchom czasomierz, wywołując <xref:System.Timers.Timer.Start%2A> metodę.

##### <a name="set-up-the-polling-mechanism"></a>Skonfiguruj mechanizm sondowania.

1. Dodaj następujący kod w `MyNewService.OnStart` zdarzeniu, aby skonfigurować mechanizm sondowania:

   ```csharp
   // Set up a timer that triggers every minute.
   Timer timer = new Timer();
   timer.Interval = 60000; // 60 seconds
   timer.Elapsed += new ElapsedEventHandler(this.OnTimer);
   timer.Start();
   ```

   ```vb
   ' Set up a timer that triggers every minute.
   Dim timer As Timer = New Timer()
   timer.Interval = 60000 ' 60 seconds
   AddHandler timer.Elapsed, AddressOf Me.OnTimer
   timer.Start()
   ```

2. `Imports` Dodajinstrukcjędo<xref:System.Timers?displayProperty=nameWithType> MyNewService.cs lub instrukcję do **MyNewService. vb**dla przestrzeni nazw: `using`

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. W klasie Dodaj metodę, aby obsłużyć <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> zdarzenie: `OnTimer` `MyNewService`

   ```csharp
   public void OnTimer(object sender, ElapsedEventArgs args)
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

4. `MyNewService` W klasie Dodaj zmienną członkowską. Zawiera identyfikator następnego zdarzenia do zapisu w dzienniku zdarzeń:

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

Zamiast uruchamiać wszystkie prace w głównym wątku, można uruchamiać zadania przy użyciu wątków roboczych w tle. Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.

### <a name="define-what-occurs-when-the-service-is-stopped"></a>Określ, co ma miejsce w przypadku zatrzymania usługi

Wstaw wiersz kodu w <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metodzie, która dodaje wpis do dziennika zdarzeń po zatrzymaniu usługi:

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a>Zdefiniuj inne akcje dla usługi

Można zastąpić <xref:System.ServiceProcess.ServiceBase.OnPause%2A>metody, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>i <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> , aby zdefiniować dodatkowe przetwarzanie dla składnika.

Poniższy kod pokazuje, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> jak zastąpić metodę `MyNewService` w klasie:

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a>Ustawianie stanu usługi

Usługi raportują swój stan do [Menedżera kontroli usług](/windows/desktop/Services/service-control-manager) , aby użytkownik mógł stwierdzić, czy usługa działa poprawnie. Domyślnie usługa, która dziedziczy z <xref:System.ServiceProcess.ServiceBase> raportów, zawiera ograniczony zestaw ustawień stanu, takich jak SERVICE_STOPPED, SERVICE_PAUSED i SERVICE_RUNNING. Jeśli uruchomienie usługi trwa dłużej, warto zgłosić status SERVICE_START_PENDING.

Ustawienia stanu SERVICE_START_PENDING i SERVICE_STOP_PENDING można zaimplementować, dodając kod, który wywołuje funkcję [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) systemu Windows.

### <a name="implement-service-pending-status"></a>Zaimplementuj stan oczekiwania usługi

1. `Imports` Dodajinstrukcjędo<xref:System.Runtime.InteropServices?displayProperty=nameWithType> MyNewService.cs lub instrukcję do **MyNewService. vb**dla przestrzeni nazw: `using`

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. Dodaj następujący kod do **MyNewService.cs**lub **MyNewService. vb**, `ServiceState` aby zadeklarować wartości i dodać strukturę dla stanu, który będzie używany w wywołaniu wywołania platformy:

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

    > [!NOTE]
    > Menedżer sterowania usługami używa `dwWaitHint` i `dwCheckpoint` składowych [struktury SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) , aby określić czas oczekiwania na uruchomienie lub wyłączenie usługi systemu Windows. Jeśli metody `OnStop` `dwCheckPoint` i są wykonywane długo, usługa może zażądać więcej czasu, wywołując `SetServiceStatus` ponownie z wartością przyrostową. `OnStart`

3. W klasie deklaruj funkcję [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) przy użyciu [wywołania platformy:](../interop/consuming-unmanaged-dll-functions.md) `MyNewService`

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. Aby zaimplementować stan SERVICE_START_PENDING, Dodaj następujący kod na początku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody:

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

5. Dodaj kod na końcu `OnStart` metody, aby ustawić stan na SERVICE_RUNNING:

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

6. Obowiązkowe Jeśli <xref:System.ServiceProcess.ServiceBase.OnStop%2A> jest metodą długotrwałą, powtórz tę procedurę `OnStop` w metodzie. Zaimplementuj stan SERVICE_STOP_PENDING i zwróć stan SERVICE_STOPPED przed wyjściem `OnStop` z metody.

   Przykład:

    ```csharp
    // Update the service state to Stop Pending.
    ServiceStatus serviceStatus = new ServiceStatus();
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING;
    serviceStatus.dwWaitHint = 100000;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);

    // Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Stop Pending.
    Dim serviceStatus As ServiceStatus = New ServiceStatus()
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING
    serviceStatus.dwWaitHint = 100000
    SetServiceStatus(Me.ServiceHandle, serviceStatus)

    ' Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

## <a name="add-installers-to-the-service"></a>Dodawanie instalatorów do usługi

Przed uruchomieniem usługi systemu Windows należy ją zainstalować, co spowoduje zarejestrowanie jej w Menedżerze kontroli usług. Dodaj Instalatory do projektu, aby obsłużyć szczegóły rejestracji.

1. W **Eksplorator rozwiązań**z menu skrótów dla **MyNewService.cs**lub **MyNewService. vb**wybierz polecenie **Projektant widoków**.

2. W widoku **projekt** wybierz obszar tła, a następnie wybierz polecenie **Dodaj Instalatora** z menu skrótów.

     Domyślnie program Visual Studio dodaje klasę składnika o nazwie `ProjectInstaller`, która zawiera dwóch instalatorów do projektu. Te Instalatory są przeznaczone dla usługi i dla procesu związanego z usługą.

3. W widoku **projekt** dla **ProjectInstaller**wybierz pozycję **serviceInstaller1** dla projektu wizualnego C# lub **serviceInstaller1** dla projektu Visual Basic, a następnie wybierz **Właściwości** z menu skrótów.

4. W oknie **Właściwości** Sprawdź, czy <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość jest ustawiona na **MyNewService**.

5. Dodaj tekst do <xref:System.ServiceProcess.ServiceInstaller.Description%2A> właściwości, takiej jak *Przykładowa usługa*.

     Ten tekst jest wyświetlany w kolumnie **Opis** okna **usługi** i zawiera opis usługi dla użytkownika.

    ![Opis usługi w oknie usługi.](media/windows-service-description.png "Opis usługi")

6. Dodaj tekst do <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> właściwości. Na przykład *MyNewService nazwa wyświetlana*.

     Ten tekst jest wyświetlany w kolumnie **Nazwa wyświetlana** okna **usługi** . Ta nazwa może się różnić od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwości, która jest nazwą używaną przez system (na przykład nazwę używaną `net start` przez polecenie w celu uruchomienia usługi).

7. Ustaw właściwość na <xref:System.ServiceProcess.ServiceStartMode.Automatic> wartość z listy rozwijanej. <xref:System.ServiceProcess.ServiceInstaller.StartType%2A>

8. Po zakończeniu okna **Właściwości** powinny wyglądać tak, jak na poniższej ilustracji:

     ![Właściwości Instalatora dla usługi systemu Windows](media/windows-service-installer-properties.png "Właściwości Instalatora usługi systemu Windows")

9. W widoku **projekt** dla **ProjectInstaller**wybierz pozycję **ServiceProcessInstaller1** dla projektu wizualnego C# lub **ServiceProcessInstaller1** dla projektu Visual Basic, a następnie wybierz **Właściwości** z menu skrótów. . Ustaw właściwość na <xref:System.ServiceProcess.ServiceAccount.LocalSystem> wartość z listy rozwijanej. <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A>

     To ustawienie powoduje zainstalowanie usługi i uruchomienie jej przy użyciu lokalnego konta systemowego.

    > [!IMPORTANT]
    > <xref:System.ServiceProcess.ServiceAccount.LocalSystem> Konto ma szerokie uprawnienia, w tym możliwość zapisu w dzienniku zdarzeń. Należy go używać ostrożnie, ponieważ może zwiększyć ryzyko ataku przez złośliwe oprogramowanie. W przypadku innych zadań należy rozważyć użycie <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, które działa jako użytkownik nieuprzywilejowany na komputerze lokalnym i prezentuje anonimowe poświadczenia na dowolnym serwerze zdalnym. Ten przykład kończy się niepowodzeniem, jeśli spróbujesz użyć <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, ponieważ wymaga ono uprawnienia do zapisu w dzienniku zdarzeń.

Aby uzyskać więcej informacji na temat instalatorów [, zobacz How to: Dodaj Instalatory do aplikacji](how-to-add-installers-to-your-service-application.md)usługi.

## <a name="optional-set-startup-parameters"></a>Obowiązkowe Ustaw parametry uruchamiania

> [!NOTE]
> Przed podjęciem decyzji o dodaniu parametrów uruchamiania należy rozważyć, czy jest to najlepszy sposób przekazywania informacji do usługi. Mimo że jest to łatwe w użyciu i przeanalizowanie, a użytkownik może je łatwo przesłonić, może być trudniejsze dla użytkownika do odnalezienia i użycia bez dokumentacji. Ogólnie rzecz biorąc, jeśli usługa wymaga więcej niż kilku parametrów uruchamiania, zamiast tego należy użyć rejestru lub pliku konfiguracji.

Usługa systemu Windows może akceptować argumenty wiersza polecenia lub parametry uruchamiania. Po dodaniu kodu do przetwarzania parametrów uruchamiania, użytkownik może uruchomić usługę z własnymi własnymi parametrami uruchamiania w oknie właściwości usługi. Jednak te Parametry uruchomieniowe nie są zachowywane podczas następnego uruchomienia usługi. Aby trwale ustawić parametry uruchamiania, ustaw je w rejestrze.

Każda usługa systemu Windows ma wpis rejestru w podkluczu **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** . W obszarze podklucza każdego usługi Użyj podklucza **Parameters** do przechowywania informacji, do których usługa może uzyskać dostęp. Można używać plików konfiguracji aplikacji dla usługi systemu Windows w taki sam sposób jak w przypadku innych typów programów. Aby zapoznać się z przykładowym kodem, zobacz <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.

### <a name="to-add-startup-parameters"></a>Aby dodać parametry uruchamiania

1. Wybierz pozycję **program.cs**lub **MyNewService. Designer. vb**, a następnie wybierz pozycję **Wyświetl kod** z menu skrótów. `Main` W metodzie Zmień kod, aby dodać parametr wejściowy i przekazać go do konstruktora usługi:

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. W **MyNewService.cs**lub **MyNewService. vb**Zmień `MyNewService` konstruktora, aby przetworzyć parametr wejściowy w następujący sposób:

   ```csharp
   using System.Diagnostics;

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

       eventLog1 = new EventLog();

       if (!EventLog.SourceExists(eventSourceName))
       {
           EventLog.CreateEventSource(eventSourceName, logName);
       }

       eventLog1.Source = eventSourceName;
       eventLog1.Log = logName;
   }
   ```

   ```vb
   Imports System.Diagnostics

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
       eventLog1 = New EventLog()
       If (Not EventLog.SourceExists(eventSourceName)) Then
           EventLog.CreateEventSource(eventSourceName, logName)
       End If
       eventLog1.Source = eventSourceName
       eventLog1.Log = logName
   End Sub
   ```

   Ten kod ustawia Źródło zdarzenia i nazwę dziennika zgodnie z parametrami uruchamiania dostarczanymi przez użytkownika. Jeśli nie podano argumentów, używa wartości domyślnych.

3. Aby określić argumenty wiersza polecenia, Dodaj następujący kod do `ProjectInstaller` klasy w **ProjectInstaller.cs**lub **ProjectInstaller. vb**:

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

   Zazwyczaj ta wartość zawiera pełną ścieżkę do pliku wykonywalnego dla usługi systemu Windows. Aby usługa została prawidłowo uruchomiona, użytkownik musi podać znaki cudzysłowu dla ścieżki i każdego parametru. Aby zmienić parametry uruchamiania usługi systemu Windows, użytkownik może zmienić parametry w wpisie w rejestrze **ImagePath** . Lepszym sposobem jest jednak zmiana wartości programowo i udostępnienie funkcji w sposób przyjazny dla użytkownika, na przykład za pomocą narzędzia do zarządzania lub konfiguracji.

## <a name="build-the-service"></a>Tworzenie usługi

1. W **Eksplorator rozwiązań**, wybierz **Właściwości** z menu skrótów dla projektu **MyNewService** .

   Pojawią się strony właściwości projektu.

2. Na karcie **aplikacja** na liście **obiekt początkowy** wybierz **MyNewService. program**lub **Sub Main** dla projektów Visual Basic.

3. Aby skompilować projekt, w **Eksplorator rozwiązań**wybierz opcję **Kompiluj** z menu skrótów dla projektu (lub naciśnij **klawisze CTRL**+**SHIFT**+**B**).

## <a name="install-the-service"></a>Instalowanie usługi

Teraz, gdy została skompilowana usługa systemu Windows, możesz ją zainstalować. Aby zainstalować usługę systemu Windows, musisz mieć poświadczenia administratora na komputerze, na którym jest zainstalowany.

1. Otwórz [wiersz polecenia dla deweloperów dla programu Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) z poświadczeniami administracyjnymi. Z menu **Start** systemu Windows wybierz opcję **wiersz polecenia dla deweloperów dla programu vs 2017** w folderze Visual Studio, a następnie wybierz pozycję **więcej** > **Uruchom jako administrator** z menu skrótów.

2. W oknie **wiersz polecenia dla deweloperów dla programu Visual Studio** przejdź do folderu, który zawiera dane wyjściowe projektu (domyślnie podkatalog *\bin\debug* projektu).

3. Wprowadź następujące polecenie:

    ```shell
    installutil MyNewService.exe
    ```

    Jeśli usługa zostanie pomyślnie zainstalowana, polecenie zgłosi powodzenie.

    Jeśli system nie może odnaleźć pliku *Installutil. exe*, upewnij się, że istnieje on na komputerze. To narzędzie jest instalowane z .NET Framework do folderu *%windir%\Microsoft.NET\Framework [64]\\&lt;&gt;Framework wersja*. Na przykład domyślną ścieżką dla wersji 64-bitowej jest *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

    Jeśli proces **Installutil. exe** nie powiedzie się, sprawdź dziennik instalacji, aby dowiedzieć się, dlaczego. Domyślnie dziennik znajduje się w tym samym folderze co plik wykonywalny usługi. Instalacja może zakończyć się niepowodzeniem, jeśli:
    - Klasa nie jest obecna `ProjectInstaller` w klasie. <xref:System.ComponentModel.RunInstallerAttribute>
    - Atrybut nie jest ustawiony na `true`.
    - Klasa nie jest zdefiniowana jako `public`. `ProjectInstaller`

Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie](how-to-install-and-uninstall-services.md)usług.

## <a name="start-and-run-the-service"></a>Uruchom i uruchom usługę

1. W systemie Windows otwórz aplikację Desktop **Services** . Naciśnij pozycję **Windows**+**R** , aby otworzyć okno **uruchamiania** , wpisz *Services. msc*, a następnie naciśnij klawisz **Enter** lub wybierz **przycisk OK**.

     Twoja usługa powinna zostać wyświetlona na liście **usługi**, w kolejności alfabetycznej według nazwy wyświetlanej, która została ustawiona dla tego ustawienia.

     ![MyNewService w oknie usługi.](media/windowsservices-serviceswindow.PNG)

2. Aby uruchomić usługę, wybierz pozycję **Rozpocznij** od menu skrótów usługi.

3. Aby zatrzymać usługę, wybierz pozycję **Zatrzymaj** w menu skrótów usługi.

4. Obowiązkowe W wierszu polecenia Użyj poleceń **net start &lt;Service Name&gt;**  i **net stop &lt;Service Name&gt;**  , aby uruchomić i zatrzymać usługę.

### <a name="verify-the-event-log-output-of-your-service"></a>Weryfikowanie danych wyjściowych dziennika zdarzeń usługi

1. W systemie Windows otwórz aplikację klasyczną **Podgląd zdarzeń** . Wprowadź *Podgląd zdarzeń* na pasku wyszukiwania systemu Windows, a następnie wybierz **Podgląd zdarzeń** z wyników wyszukiwania.

   > [!TIP]
   > W programie Visual Studio można uzyskać dostęp do dzienników zdarzeń, **otwierając Eksplorator serwera** z **menu Widok** (lub naciskając klawisze **Ctrl**+**Alt**+**S**) i rozszerzając węzeł **dzienniki zdarzeń** dla komputera lokalnego.

2. W **Podgląd zdarzeń**rozwiń węzeł **Dzienniki aplikacji i usług**.

3. Znajdź listę dla **myNewLog** (lub **MyLogFile1** , jeśli wykonano procedurę dodawania argumentów wiersza polecenia) i rozwiń ją. Powinny zostać wyświetlone wpisy dotyczące dwóch akcji (uruchamiania i zatrzymywania) wykonywanych przez usługę.

     ![Użyj Podgląd zdarzeń, aby wyświetlić wpisy dziennika zdarzeń](media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

Jeśli aplikacja usługi systemu Windows nie jest już potrzebna, można ją usunąć.

1. Otwórz **wiersz polecenia dla deweloperów dla programu Visual Studio** z poświadczeniami administracyjnymi.

2. W oknie **wiersz polecenia dla deweloperów dla programu Visual Studio** przejdź do folderu, który zawiera dane wyjściowe projektu.

3. Wprowadź następujące polecenie:

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   Jeśli usługa została pomyślnie odinstalowana, polecenie zgłosi, że usługa została pomyślnie usunięta. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie](how-to-install-and-uninstall-services.md)usług.

## <a name="next-steps"></a>Następne kroki

Teraz, gdy została utworzona usługa, możesz:

- Utwórz autonomiczny program instalacyjny, który będzie używany przez inne osoby do instalacji usługi systemu Windows. Użyj zestawu [narzędzi WIX](https://wixtoolset.org/) , aby utworzyć Instalatora dla usługi systemu Windows. Aby poznać inne pomysły, zobacz [Tworzenie pakietu Instalatora](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).

- <xref:System.ServiceProcess.ServiceController> Eksploruj składnik, który umożliwia wysyłanie poleceń do zainstalowanej usługi.

- Zamiast tworzyć dziennik zdarzeń, gdy aplikacja jest uruchomiona, użyj Instalatora, aby utworzyć dziennik zdarzeń podczas instalowania aplikacji. Dziennik zdarzeń jest usuwany przez Instalatora podczas odinstalowywania aplikacji. Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.EventLogInstaller>.

## <a name="see-also"></a>Zobacz także

- [Aplikacje usług systemu Windows](index.md)
- [Wprowadzenie do aplikacji usług systemu Windows](introduction-to-windows-service-applications.md)
- [Instrukcje: Debuguj aplikacje usług systemu Windows](how-to-debug-windows-service-applications.md)
- [Usługi (Windows)](/windows/desktop/Services/services)
