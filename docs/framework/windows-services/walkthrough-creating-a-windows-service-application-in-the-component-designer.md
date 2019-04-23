---
title: 'Samouczek: Tworzenie aplikacji usługi Windows'
ms.date: 03/27/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
ms.openlocfilehash: 35ef113acffbebdcd4cb585970e575f17959f75b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59518035"
---
# <a name="tutorial-create-a-windows-service-app"></a>Samouczek: Tworzenie aplikacji usługi Windows

W tym artykule pokazano, jak utworzyć aplikację usługi Windows w programie Visual Studio, która wypisuje komunikaty w dzienniku zdarzeń.

## <a name="create-a-service"></a>Tworzenie usługi

Aby rozpocząć, Utwórz projekt i ustaw wartości, które są niezbędne do poprawnego działania usługi.

1. W programie Visual Studio **pliku** menu, wybierz opcję **New** > **projektu** (lub naciśnij **Ctrl** + **Shift**+**N**) aby otworzyć **nowy projekt** okna.

2. Przejdź do, a następnie wybierz pozycję **usługi Windows (.NET Framework)** szablonu projektu. Aby ją znaleźć, rozwiń węzeł **zainstalowane** i **Visual C#**  lub **języka Visual Basic**, a następnie wybierz **pulpitu Windows**. Lub wprowadź *usługi Windows* w polu wyszukiwania w prawym górnym rogu, a następnie naciśnij klawisz **Enter**.

   ![Szablon usługi Windows w oknie dialogowym Nowy projekt, w programie Visual Studio](media/new-project-dialog.png)

   > [!NOTE]
   > Jeśli nie widzisz **usługi Windows** szablonu, użytkownik może być konieczne zainstalowanie **programowanie aplikacji klasycznych dla platformy .NET** obciążenia:
   >  
   > W **nowy projekt** okno dialogowe, wybierz opcję **Otwórz Instalator programu Visual Studio** w lewym dolnym rogu. Wybierz **programowanie aplikacji klasycznych dla platformy .NET** obciążenia, a następnie wybierz **Modyfikuj**.

3. Aby uzyskać **nazwa**, wprowadź *MyNewService*, a następnie wybierz pozycję **OK**.

   **Projektowania** zostanie wyświetlona karta (**Service1.cs [projekt]** lub **Service1.vb [projekt]**).
   
   Szablon projektu zawiera klasę składnika o nazwie `Service1` tej, która dziedziczy <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>. Zawiera ona większość podstawowego kodu usługi, takie jak kod, aby uruchomić usługę.

## <a name="rename-the-service"></a>Zmień nazwę usługi

Zmień nazwę usługi z **Service1** do **MyNewService**.

1. W **Eksploratora rozwiązań**, wybierz opcję **Service1.cs**, lub **Service1.vb**i wybierz polecenie **Zmień nazwę** z menu skrótów. Zmień nazwę pliku do **MyNewService.cs**, lub **MyNewService.vb**, a następnie naciśnij klawisz **Enter**

    Okno wyskakujące pojawia się pytaniem, czy chcesz zmienić wszystkie odwołania do elementu kodu *Service1*.

2. W oknie podręcznym wybierz **tak**.

    ![Zmień nazwę wiersza](media/windows-service-rename.png "usługi Windows zmień nazwę wiersza")

2. W **projektowania** zaznacz **właściwości** z menu skrótów. Z **właściwości** oknie zmiany **ServiceName** wartość *MyNewService*.

    ![Właściwości usługi](media/windows-service-properties.png "właściwości usługi Windows")

3. Wybierz **Zapisz wszystko** z **pliku** menu.

## <a name="add-features-to-the-service"></a>Dodawanie funkcji do usługi

W tej sekcji dodasz niestandardowy dziennik zdarzeń do usługi Windows. <xref:System.Diagnostics.EventLog> Składnik jest przykładem typu składnika można dodać do usługi Windows.

### <a name="add-custom-event-log-functionality"></a>Dodać funkcjonalność niestandardowego dziennika zdarzeń

1. W **Eksploratora rozwiązań**, z menu skrótów dla **MyNewService.cs**, lub **MyNewService.vb**, wybierz **Projektant widoków**.

2. W **przybornika**, rozwiń węzeł **składniki**, a następnie przeciągnij **dziennika zdarzeń** do **Service1.cs [projekt]**, lub  **Service1.VB [projekt]** kartę.

3. W **Eksploratora rozwiązań**, z menu skrótów dla **MyNewService.cs**, lub **MyNewService.vb**, wybierz **Wyświetl kod**.

4. Zdefiniować niestandardowy dziennik zdarzeń. Aby uzyskać C#, zmodyfikować istniejący `MyNewService()` Konstruktor; dla języka Visual Basic należy dodać `New()` konstruktora:

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. Dodaj `using` instrukcję, aby **MyNewService.cs** (jeśli jeszcze nie istnieje), lub `Imports` instrukcji **MyNewService.vb**, dla <xref:System.Diagnostics?displayProperty=nameWithType> przestrzeni nazw:

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. Wybierz **Zapisz wszystko** z **pliku** menu.

### <a name="define-what-occurs-when-the-service-starts"></a>Określić zachowanie występujące podczas uruchamiania usługi

W edytorze kodu dla **MyNewService.cs** lub **MyNewService.vb**, zlokalizuj <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody. Podczas tworzenia projektu programu Visual Studio automatycznie tworzony definicję metody pusty. Dodaj kod, który zapisuje wpis dziennika zdarzeń, podczas uruchamiania usługi:

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a>Sondowanie

Ponieważ aplikacja usługi została zaprojektowana jako długotrwałych, zazwyczaj sonduje lub monitoruje system, który został skonfigurowany w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody. `OnStart` Metoda musi powrócić do systemu operacyjnego, po rozpoczęciu operacji usługi, tak aby system nie jest zablokowany. 

Aby skonfigurować prosty mechanizm sondowania, użyj <xref:System.Timers.Timer?displayProperty=nameWithType> składnika. Wywołuje czasomierza <xref:System.Timers.Timer.Elapsed> zdarzeń w regularnych odstępach czasu, co Twoja usługa mogła wykonać jego monitorowanie. Możesz użyć <xref:System.Timers.Timer> składnika w następujący sposób:

- Ustawianie właściwości <xref:System.Timers.Timer> składnika w `MyNewService.OnStart` metody.
- Uruchomienia czasomierza, wywołując <xref:System.Timers.Timer.Start%2A> metody.

##### <a name="set-up-the-polling-mechanism"></a>Konfigurowanie mechanizmu sondowania.

1. Dodaj następujący kod w `MyNewService.OnStart` zdarzenie, aby ustawić mechanizm sondowania:

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

2. Dodaj `using` instrukcję, aby **MyNewService.cs**, lub `Imports` instrukcję, aby **MyNewService.vb**, aby uzyskać <xref:System.Timers?displayProperty=nameWithType> przestrzeni nazw:

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. W `MyNewService` klasy, Dodaj `OnTimer` metody, aby obsłużyć <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> zdarzeń:

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

4. W `MyNewService` klasy, Dodaj zmienną składową. Zawiera identyfikator następne zdarzenie do zapisu do dziennika zdarzeń:

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

Zamiast uruchamiać swoją pracę w wątku głównym, można uruchamiać zadania za pomocą wątków w tle proces roboczy. Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.

### <a name="define-what-occurs-when-the-service-is-stopped"></a>Określić zachowanie występujące podczas zatrzymywania usługi

Wstaw wiersz kodu w <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metodę, która dodaje wpis w dzienniku zdarzeń, gdy usługa zostanie zatrzymana:

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a>Zdefiniuj inne akcje usługi

Można zastąpić <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, i <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> metody, aby zdefiniować dodatkowe przetwarzanie składnika. 

Poniższy kod przedstawia sposób na zastąpienie <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method in Class metoda `MyNewService` klasy:

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a>Ustaw stan usługi

Usługi raportowania ich stanu do [Menedżera sterowania usługami](/windows/desktop/Services/service-control-manager) , dzięki czemu użytkownik może stwierdzić, czy usługa działa poprawnie. Domyślnie usługa tej, która dziedziczy <xref:System.ServiceProcess.ServiceBase> ograniczony zestaw stan ustawienia, które obejmują SERVICE_STOPPED, SERVICE_PAUSED i SERVICE_RUNNING raportów. Jeśli usługa może trochę mogła się uruchomić, jest przydatne do raportowania stanu SERVICE_START_PENDING. 

Ustawienia stanu SERVICE_START_PENDING i SERVICE_STOP_PENDING można zaimplementować, dodając kod, który wywołuje Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) funkcji.

### <a name="implement-service-pending-status"></a>Implementowanie usługi w stanie oczekiwania

1. Dodaj `using` instrukcję, aby **MyNewService.cs**, lub `Imports` instrukcję, aby **MyNewService.vb**, aby uzyskać <xref:System.Runtime.InteropServices?displayProperty=nameWithType> przestrzeni nazw:

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. Dodaj następujący kod do **MyNewService.cs**, lub **MyNewService.vb**, aby zadeklarować `ServiceState` wartości i można dodać struktury stanu, która będzie używana na platformie wywołania wywołania:

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
    > Korzysta z Menedżera sterowania usługami `dwWaitHint` i `dwCheckpoint` członkowie [struktury SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status) określić ilość czasu oczekiwania dla usługi Windows uruchomić lub zamknąć. Jeśli Twoje `OnStart` i `OnStop` metody trwają długo, usługi mogą żądać więcej czasu, przez wywołanie metody `SetServiceStatus` ponownie, używając zwiększona `dwCheckPoint` wartość.

3. W `MyNewService` klasy, Zadeklaruj [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) funkcji przy użyciu [wywołania platformy](../interop/consuming-unmanaged-dll-functions.md):

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

5. Dodaj kod na końcu `OnStart` metodę, aby ustawić stan na SERVICE_RUNNING:

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

6. (Opcjonalnie) Jeśli <xref:System.ServiceProcess.ServiceBase.OnStop%2A> jest metoda długotrwałych, powtórz tę procedurę w `OnStop` metody. Implementowanie stan SERVICE_STOP_PENDING i zwrócony stan SERVICE_STOPPED przed `OnStop` wyjścia metody.

   Na przykład:

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

Przed uruchomieniem usługi Windows, musisz zainstalować go, który rejestruje je z Menedżerem sterowania usługami. Dodawanie instalatorów do projektu w celu obsługi szczegółów rejestracji.

1. W **Eksploratora rozwiązań**, z menu skrótów dla **MyNewService.cs**, lub **MyNewService.vb**, wybierz **Projektant widoków**.

2. W **projektowania** wyświetlić, wybierz obszar tła, a następnie wybierz **Dodaj Instalatora** z menu skrótów.

     Domyślnie program Visual Studio dodana Klasa składnika o nazwie `ProjectInstaller`, który zawiera dwa pliki instalacyjne do projektu. Te instalatory są usługi i procesu skojarzonego z usługi.

4. W **projektowania** wyświetlić **ProjectInstaller**, wybierz opcję **serviceInstaller1** dla wizualizacji C# projektu, lub **ServiceInstaller1**projektu języka Visual Basic, następnie wybierz **właściwości** z menu skrótów.

5. W **właściwości** oknie Sprawdź <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość jest ustawiona na **MyNewService**.

6. Dodawanie tekstu do <xref:System.ServiceProcess.ServiceInstaller.Description%2A> właściwości, takie jak *usługi przykładowe*. 

     Ten tekst jest wyświetlany w **opis** kolumny **usług** okna i zawiera opis usługi dla użytkownika.

    ![Opis usługi, w oknie usług. ](media/windows-service-description.png "Opis usługi")

7. Dodawanie tekstu do <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> właściwości. Na przykład *nazwę wyświetlaną MyNewService*. 

     Ten tekst jest wyświetlany w **nazwę wyświetlaną** kolumny **usług** okna. Ta nazwa może różnić się od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość, która jest nazwą, wówczas system używa (na przykład nazwy można użyć dla `net start` polecenie, aby uruchomić usługę).

8. Ustaw <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwość <xref:System.ServiceProcess.ServiceStartMode.Automatic> z listy rozwijanej.

9. Gdy skończysz, **właściwości** windows powinno wyglądać podobnie do poniższej ilustracji:

     ![Właściwości Instalatora usługi Windows](media/windows-service-installer-properties.png "właściwości Instalatora usługi Windows")

9. W **projektowania** wyświetlić **ProjectInstaller**, wybierz **serviceProcessInstaller1** dla wizualizacji C# projektu, lub **ServiceProcessInstaller1**  projektu języka Visual Basic, następnie wybierz **właściwości** z menu skrótów. Ustaw <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> właściwość <xref:System.ServiceProcess.ServiceAccount.LocalSystem> z listy rozwijanej. 

     To ustawienie instaluje usługę i uruchamia je przy użyciu konta systemu lokalnego.

    > [!IMPORTANT]
    > <xref:System.ServiceProcess.ServiceAccount.LocalSystem> Konto ma szerokie uprawnienia, w tym możliwość zapisu do dziennika zdarzeń. Należy go używać ostrożnie, ponieważ może zwiększyć ryzyko ataku przez złośliwe oprogramowanie. W przypadku innych zadań, należy wziąć pod uwagę przy użyciu <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, które działa jako użytkownik bez uprawnień na komputerze lokalnym i przedstawia poświadczenia anonimowe każdemu zdalnemu serwerowi. W tym przykładzie zakończy się niepowodzeniem, jeśli zostanie podjęta próba użycia <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, ponieważ wymaga uprawnień do zapisu w dzienniku zdarzeń.

Aby uzyskać więcej informacji na temat instalatory zobacz [jak: Dodawanie instalatorów od aplikacji usług](how-to-add-installers-to-your-service-application.md).

## <a name="optional-set-startup-parameters"></a>(Opcjonalnie) Ustaw parametry uruchamiania

> [!NOTE]
> Przed podjęciem decyzji o Dodaj parametry uruchamiania, należy rozważyć, czy jest najlepszym sposobem przekazywania informacji do usługi. Mimo że są one łatwe w użyciu i analizy, a użytkownik może łatwo je zastąpić, może być trudniejsze dla użytkownika do użytku bez dokumentacji. Ogólnie rzecz biorąc Jeśli usługa wymaga więcej niż kilku Parametry uruchamiania, należy użyć rejestru lub pliku konfiguracji zamiast tego. 

Usługa Windows może akceptować argumentów wiersza polecenia lub parametry uruchamiania. Po dodaniu kodu z parametrami uruchomienia procesu, użytkownik może uruchomić usługi za pomocą ich własnych parametrów startowy niestandardowe w oknie dialogowym właściwości usługi. Jednak te parametry uruchamiania nie są zachowywane podczas następnego uruchomienia usługi. Aby ustawić parametry uruchamiania trwale, należy ustawić je w rejestrze.

Każda usługa Windows ma wpis rejestru, w obszarze **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** podklucza. W podkluczu każdej z tych usług użyj **parametry** podklucz do przechowywania informacji, które mogą uzyskiwać dostęp do usługi. Może używać plików konfiguracji aplikacji dla usługi Windows w taki sam sposób jak w przypadku innych programów. Przykładowy kod, zobacz <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.

### <a name="to-add-startup-parameters"></a>Aby dodać parametry uruchamiania

1. Wybierz **Program.cs**, lub **MyNewService.Designer.vb**, następnie wybierz **Wyświetl kod** z menu skrótów. W `Main` metodę, Zmień kod, aby dodać parametr wejściowy i przekaż go do konstruktora usługi:

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. W **MyNewService.cs**, lub **MyNewService.vb**, zmień `MyNewService` konstruktora, aby przetworzyć parametr wejściowy w następujący sposób:

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

   Ten kod ustawia nazwę źródła i dziennik zdarzeń, zgodnie z Parametry uruchamiania, które użytkownik podaje. Jeśli zostały dostarczone żadne argumenty, używa domyślnych wartości.

3. Aby określić argumenty wiersza polecenia, Dodaj następujący kod do `ProjectInstaller` klasy w **ProjectInstaller.cs**, lub **ProjectInstaller.vb**:

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

   Zazwyczaj ta wartość zawiera pełną ścieżkę do pliku wykonywalnego dla usługi Windows. Dla usługi została prawidłowo uruchomiona że użytkownik musi podać znaki cudzysłowu dla ścieżki i wszystkich poszczególnych parametrów. Użytkownik może zmienić parametry w **ImagePath** wpis rejestru, aby zmienić parametry uruchamiania usługi Windows. Jednak lepszy sposób jest programowe Zmienianie wartości i udostępniają funkcje w sposób, przyjazny dla użytkownika, takie jak za pomocą narzędzia zarządzania lub konfiguracji.

## <a name="build-the-service"></a>Tworzenie usługi

1. W **Eksploratora rozwiązań**, wybierz **właściwości** z menu skrótów dla **MyNewService** projektu.

   Są wyświetlane na stronach właściwości projektu.

2. Na **aplikacji** na karcie **obiekt początkowy** wybierz **MyNewService.Program**, lub **Sub Main** dla projektów języka Visual Basic.

3. Aby skompilować projekt, w **Eksploratora rozwiązań**, wybierz **kompilacji** z menu skrótów dla projektu (lub naciśnij **Ctrl**+**Shift** + **B**).

## <a name="install-the-service"></a>Instalowanie usługi

Teraz, gdy masz utworzoną usługę Windows, należy ją zainstalować. Aby zainstalować usługę Windows, musi mieć poświadczenia administratora na komputerze, na którym jest zainstalowany.

1. Otwórz [wiersz polecenia programisty dla programu Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) przy użyciu poświadczeń administracyjnych. Od Windows **Start** menu, wybierz opcję **wiersz polecenia programisty dla programu VS 2017** w folderze programu Visual Studio, a następnie zaznacz **więcej** > **Uruchom jako Administrator** z menu skrótów.

2. W **wiersz polecenia programisty dla programu Visual Studio** okna, przejdź do folderu, który zawiera dane wyjściowe projektu (domyślnie *\bin\Debug* podkatalogu projektu).

3. Wprowadź następujące polecenie:

    ```shell
    installutil MyNewService.exe
    ```

    Jeśli usługa zostanie zainstalowana pomyślnie, polecenie zgłosi powodzenie operacji. 

    Jeśli system nie może znaleźć *installutil.exe*, upewnij się, że istnieje na tym komputerze. To narzędzie jest instalowane z .NET Framework do folderu *% windir%\Microsoft.NET\Framework[64]\\&lt;framework w wersji&gt;*. Na przykład jest domyślna ścieżka dla 64-bitowej wersji *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

    Jeśli **installutil.exe** przetwarzania zakończy się niepowodzeniem, sprawdź dziennik instalacji, aby dowiedzieć się, dlaczego. Domyślnie dziennik jest w tym samym folderze co pliku wykonywalnego usługi. Instalacja może zakończyć się niepowodzeniem, jeśli: 
    - <xref:System.ComponentModel.RunInstallerAttribute> Klasy nie znajduje się w `ProjectInstaller` klasy.
    -  Atrybut nie jest ustawiony na `true`. 
    - `ProjectInstaller` Klasa nie jest zdefiniowana jako `public`.

Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie usług](how-to-install-and-uninstall-services.md).

## <a name="start-and-run-the-service"></a>Uruchom program i uruchom usługę

1. Windows, otwórz **usług** aplikacji klasycznej. Naciśnij klawisz **Windows**+**R** otworzyć **Uruchom** wprowadź *services.msc*, a następnie naciśnij klawisz **Enter** lub wybierz **OK**.

     Powinien zostać wyświetlony na liście usługi **usług**, wyświetlane alfabetycznie według nazwy wyświetlanej, ustaw dla niego.

     ![MyNewService w oknie usług.](media/windowsservices-serviceswindow.PNG)

2. Aby uruchomić usługę, wybierz opcję **Start** z menu skrótów usługi.

3. Aby zatrzymać usługę, wybierz opcję **zatrzymać** z menu skrótów usługi.

4. (Opcjonalnie) W wierszu polecenia należy użyć poleceń **net start &lt;nazwa usługi&gt;**  i **net stop &lt;nazwa usługi&gt;**  uruchamianie i zatrzymywanie usługi.

### <a name="verify-the-event-log-output-of-your-service"></a>Sprawdź dane wyjściowe dziennika zdarzeń, usługi

1. Windows, otwórz **Podgląd zdarzeń** aplikacji klasycznej. Wprowadź *Podgląd zdarzeń* w wyszukiwaniu Windows paska, a następnie wybierz pozycję **Podgląd zdarzeń** w wynikach wyszukiwania.

   > [!TIP]
   > W programie Visual Studio są dostępne dzienniki zdarzeń, otwierając **Eksploratora serwera** z **widoku** menu (lub naciśnij **Ctrl**+**Alt** + **S**) i rozwijając **dzienniki zdarzeń** węzła na komputerze lokalnym.

2. W **Podgląd zdarzeń**, rozwiń węzeł **Dzienniki aplikacji i usług**.

3. Odszukaj **MyNewLog** (lub **MyLogFile1** po wykonaniu procedury, aby dodać argumenty wiersza polecenia) i rozwiń go. Powinny być widoczne wpisy dwie akcje (rozpoczęcie i zakończenie), wykonanych przez usługę.

     ![Użyj podglądu zdarzeń, aby wyświetlić wpisy dziennika zdarzeń](media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

Jeśli nie potrzebujesz już Windows service app, możesz go usunąć. 

1. Otwórz **wiersz polecenia programisty dla programu Visual Studio** przy użyciu poświadczeń administracyjnych.

2. W **wiersz polecenia programisty dla programu Visual Studio** okna, przejdź do folderu, który zawiera dane wyjściowe projektu.

3. Wprowadź następujące polecenie:

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   Jeśli usługa zostanie pomyślnie odinstalowana polecenia Raporty z usługą został pomyślnie usunięty. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie usług](how-to-install-and-uninstall-services.md).

## <a name="next-steps"></a>Następne kroki

Teraz, po utworzeniu usługi, możesz wykonywać następujące czynności:

- Utwórz autonomiczny program instalacyjny dla innych użytkowników, aby zainstalować usługę Windows. Użyj [zestaw narzędzi WiX](http://wixtoolset.org/) możliwość utworzenia Instalatora usługi Windows. Zapoznać się z pomysłami z innymi zobacz [Utwórz pakiet instalacyjny](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).

- Zapoznaj się z <xref:System.ServiceProcess.ServiceController> składnik, który umożliwia wysyłanie poleceń do usługi, po zainstalowaniu.

- Zamiast tworzenia dziennika zdarzeń, gdy aplikacja zostanie uruchomiona, należy użyć Instalatora do tworzenia dziennika zdarzeń podczas instalowania aplikacji. Dziennik zdarzeń jest usunięte przez Instalatora po odinstalowaniu aplikacji. Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.EventLogInstaller>.

## <a name="see-also"></a>Zobacz także

- [Aplikacje usług Windows](index.md)
- [Wprowadzenie do aplikacji usług Windows](introduction-to-windows-service-applications.md)
- [Instrukcje: Debugowanie aplikacji usług Windows](how-to-debug-windows-service-applications.md)
- [Usługi (Windows)](/windows/desktop/Services/services)
