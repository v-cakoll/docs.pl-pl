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
ms.openlocfilehash: 52c2f64bbb71e07dcab1fd7cd42662f9ed2c8445
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56665033"
---
# <a name="walkthrough-create-a-windows-service-app"></a><span data-ttu-id="7c27a-102">Przewodnik: Tworzenie aplikacji usługi Windows</span><span class="sxs-lookup"><span data-stu-id="7c27a-102">Walkthrough: Create a Windows service app</span></span>

<span data-ttu-id="7c27a-103">W tym artykule przedstawiono sposób tworzenia prostej aplikacji usługi Windows w programie Visual Studio, która wypisuje komunikaty w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7c27a-103">This article demonstrates how to create a simple Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="7c27a-104">Tworzenie usługi</span><span class="sxs-lookup"><span data-stu-id="7c27a-104">Create a service</span></span>

<span data-ttu-id="7c27a-105">Aby rozpocząć, Utwórz projekt i ustaw wartości, które są niezbędne do poprawnego działania usługi.</span><span class="sxs-lookup"><span data-stu-id="7c27a-105">To begin, create the project and set values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="7c27a-106">W programie Visual Studio, na pasku menu wybierz **pliku** > **New** > **projektu** (lub naciśnij **Ctrl** + **Shift**+**N**) aby otworzyć **nowy projekt** okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="7c27a-106">In Visual Studio, on the menu bar, choose **File** > **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** dialog.</span></span>

2. <span data-ttu-id="7c27a-107">Przejdź do, a następnie wybierz pozycję **usługi Windows** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="7c27a-107">Navigate to and select the **Windows Service** project template.</span></span> <span data-ttu-id="7c27a-108">Rozwiń **zainstalowane** > [**Visual C#**  lub **języka Visual Basic**] > **pulpitu Windows**, lub typu **Windows Usługa** w polu wyszukiwania w prawym górnym rogu.</span><span class="sxs-lookup"><span data-stu-id="7c27a-108">Expand **Installed** > [**Visual C#** or **Visual Basic**] > **Windows Desktop**, or type **Windows Service** in the search box on the upper right.</span></span>

   ![Szablon usługi Windows w oknie dialogowym Nowy projekt, w programie Visual Studio](media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="7c27a-110">Jeśli nie widzisz **usługi Windows** szablonu, użytkownik może być konieczne zainstalowanie **programowanie aplikacji klasycznych dla platformy .NET** obciążenia.</span><span class="sxs-lookup"><span data-stu-id="7c27a-110">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload.</span></span> <span data-ttu-id="7c27a-111">W **nowy projekt** okno dialogowe, kliknij link, który jest wyświetlany komunikat **Otwórz Instalator programu Visual Studio** w lewym dolnym rogu.</span><span class="sxs-lookup"><span data-stu-id="7c27a-111">In the **New Project** dialog, click the link that says **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="7c27a-112">W **Instalatora programu Visual Studio**, wybierz opcję **programowanie aplikacji klasycznych dla platformy .NET** obciążenia, a następnie wybierz **Modyfikuj**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-112">In **Visual Studio Installer**, select the **.NET desktop development** workload and then choose **Modify**.</span></span>

3. <span data-ttu-id="7c27a-113">Nadaj projektowi nazwę **MyNewService**, a następnie wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-113">Name the project **MyNewService**, and then choose **OK**.</span></span>

   <span data-ttu-id="7c27a-114">Szablon projektu zawiera klasę składnika o nazwie `Service1` tej, która dziedziczy <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7c27a-114">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7c27a-115">Zawiera ona większość podstawowego kodu usługi, takie jak kod, aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="7c27a-115">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="7c27a-116">Zmień nazwę usługi</span><span class="sxs-lookup"><span data-stu-id="7c27a-116">Rename the service</span></span>

<span data-ttu-id="7c27a-117">Zmień nazwę usługi z **Service1** do **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-117">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="7c27a-118">W **projektowania** widok Service1.cs (lub Service1.vb), kliknij link, aby **przejdź do widoku kodu**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-118">In the **Design** view for Service1.cs (or Service1.vb), click the link to **switch to code view**.</span></span> <span data-ttu-id="7c27a-119">Kliknij prawym przyciskiem myszy **Service1** i wybierz **Zmień nazwę** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="7c27a-119">Right-click on **Service1** and select **Rename** from the context menu.</span></span> <span data-ttu-id="7c27a-120">Wprowadź **MyNewService** , a następnie naciśnij klawisz **Enter** lub kliknij przycisk **Zastosuj**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-120">Enter **MyNewService** and then press **Enter** or click **Apply**.</span></span>

2. <span data-ttu-id="7c27a-121">W **właściwości** okno **Service1.cs [projekt]** lub **Service1.vb [projekt]**, zmień **ServiceName** wartość **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-121">In the **Properties** window for **Service1.cs [Design]** or **Service1.vb [Design]**, change the **ServiceName** value to **MyNewService**.</span></span>

3. <span data-ttu-id="7c27a-122">W **Eksploratora rozwiązań**, Zmień nazwę **Service1.cs** do **MyNewService.cs**, lub zmień nazwę **Service1.vb** do  **MyNewService.vb**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-122">In **Solution Explorer**, rename **Service1.cs** to **MyNewService.cs**, or rename **Service1.vb** to **MyNewService.vb**.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="7c27a-123">Dodawanie funkcji do usługi</span><span class="sxs-lookup"><span data-stu-id="7c27a-123">Add features to the service</span></span>

<span data-ttu-id="7c27a-124">W tej sekcji dodasz niestandardowy dziennik zdarzeń do usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="7c27a-124">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="7c27a-125">Dzienniki zdarzeń nie w żaden sposób powiązane z usługami systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7c27a-125">Event logs are not associated in any way with Windows services.</span></span> <span data-ttu-id="7c27a-126"><xref:System.Diagnostics.EventLog> Składnik jest używany tutaj jako przykładu składnika, możesz dodać do usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="7c27a-126">The <xref:System.Diagnostics.EventLog> component is used here as an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="7c27a-127">Dodać funkcjonalność niestandardowego dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="7c27a-127">Add custom event log functionality</span></span>

1. <span data-ttu-id="7c27a-128">W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **MyNewService.cs** lub **MyNewService.vb**, a następnie wybierz **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-128">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>

2. <span data-ttu-id="7c27a-129">Z **składniki** części **przybornika**, przeciągnij <xref:System.Diagnostics.EventLog> składnik do projektanta.</span><span class="sxs-lookup"><span data-stu-id="7c27a-129">From the **Components** section of the **Toolbox**, drag an <xref:System.Diagnostics.EventLog> component to the designer.</span></span>

3. <span data-ttu-id="7c27a-130">W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **MyNewService.cs** lub **MyNewService.vb**, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-130">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Code**.</span></span>

4. <span data-ttu-id="7c27a-131">Zmodyfikuj konstruktora, aby zdefiniować niestandardowy dziennik zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="7c27a-131">Edit the constructor to define a custom event log:</span></span>

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

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="7c27a-132">Określić zachowanie występujące podczas uruchamiania usługi</span><span class="sxs-lookup"><span data-stu-id="7c27a-132">Define what occurs when the service starts</span></span>

<span data-ttu-id="7c27a-133">W edytorze kodu zlokalizuj <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodę, która została zastąpiona automatycznie podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="7c27a-133">In the code editor, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method that was automatically overridden when you created the project.</span></span> <span data-ttu-id="7c27a-134">Dodaj wiersz kodu, który zapisuje wpis dziennika zdarzeń podczas uruchamiania usługi:</span><span class="sxs-lookup"><span data-stu-id="7c27a-134">Add a line of code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

<span data-ttu-id="7c27a-135">Aplikacja usługi jest przeznaczony jako długotrwałych, dzięki czemu zwykle sonduje lub monitoruje coś w systemie.</span><span class="sxs-lookup"><span data-stu-id="7c27a-135">A service application is designed to be long-running, so it usually polls or monitors something in the system.</span></span> <span data-ttu-id="7c27a-136">Monitorowanie jest skonfigurowana w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7c27a-136">The monitoring is set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="7c27a-137">Jednak <xref:System.ServiceProcess.ServiceBase.OnStart%2A> faktycznie nie wykonuje monitorowania.</span><span class="sxs-lookup"><span data-stu-id="7c27a-137">However, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> doesn’t actually do the monitoring.</span></span> <span data-ttu-id="7c27a-138"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> Metoda musi powrócić do systemu operacyjnego, po rozpoczęciu operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="7c27a-138">The <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method must return to the operating system after the service's operation has begun.</span></span> <span data-ttu-id="7c27a-139">Nie może być wykonywana bezterminowo w pętli ani nakładać żadnych blokad.</span><span class="sxs-lookup"><span data-stu-id="7c27a-139">It must not loop forever or block.</span></span> <span data-ttu-id="7c27a-140">Aby skonfigurować prosty mechanizm sondowania, można użyć <xref:System.Timers.Timer?displayProperty=nameWithType> składnika w następujący sposób: W <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody, ustawianie parametrów na części, a następnie ustaw <xref:System.Timers.Timer.Enabled%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="7c27a-140">To set up a simple polling mechanism, you can use the <xref:System.Timers.Timer?displayProperty=nameWithType> component as follows: In the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, set parameters on the component, and then set the <xref:System.Timers.Timer.Enabled%2A> property to `true`.</span></span> <span data-ttu-id="7c27a-141">Czasomierz wywołuje zdarzenia w kodzie okresowo, co usługa może zrobić, jego monitorowanie.</span><span class="sxs-lookup"><span data-stu-id="7c27a-141">The timer raises events in your code periodically, at which time your service could do its monitoring.</span></span> <span data-ttu-id="7c27a-142">Aby to zrobić, można użyć następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="7c27a-142">You can use the following code to do this:</span></span>

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

<span data-ttu-id="7c27a-143">Dodaj zmienną składową do klasy.</span><span class="sxs-lookup"><span data-stu-id="7c27a-143">Add a member variable to the class.</span></span> <span data-ttu-id="7c27a-144">Zawiera ona identyfikator następne zdarzenie do zapisu do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7c27a-144">It contains the identifier of the next event to write into the event log.</span></span>

```csharp
private int eventId = 1;
```

```vb
Private eventId As Integer = 1
```

<span data-ttu-id="7c27a-145">Dodaj nową metodę, aby obsłużyć zdarzenie czasomierza:</span><span class="sxs-lookup"><span data-stu-id="7c27a-145">Add a new method to handle the timer event:</span></span>

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

<span data-ttu-id="7c27a-146">Można wykonywać zadania za pomocą wątków procesów roboczych w tle zamiast uruchamiać swoją pracę w wątku głównym.</span><span class="sxs-lookup"><span data-stu-id="7c27a-146">You might want to perform tasks by using background worker threads instead of running all your work on the main thread.</span></span> <span data-ttu-id="7c27a-147">Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="7c27a-147">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="7c27a-148">Określić zachowanie występujące podczas zatrzymywania usługi</span><span class="sxs-lookup"><span data-stu-id="7c27a-148">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="7c27a-149">Dodaj wiersz kodu do <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metodę, która dodaje wpis w dzienniku zdarzeń, gdy usługa zostanie zatrzymana:</span><span class="sxs-lookup"><span data-stu-id="7c27a-149">Add a line of code to the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

```csharp
eventLog1.WriteEntry("In OnStop.");
```

[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="7c27a-150">Zdefiniuj inne akcje usługi</span><span class="sxs-lookup"><span data-stu-id="7c27a-150">Define other actions for the service</span></span>

<span data-ttu-id="7c27a-151">Można zastąpić <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, i <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> metody, aby zdefiniować dodatkowe przetwarzanie składnika.</span><span class="sxs-lookup"><span data-stu-id="7c27a-151">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span> <span data-ttu-id="7c27a-152">W poniższym kodzie pokazano, jak można zastąpić <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="7c27a-152">The following code shows how you can override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

<span data-ttu-id="7c27a-153">Pewne niestandardowe czynności muszą występować po zainstalowaniu usługi Windows przez <xref:System.Configuration.Install.Installer> klasy.</span><span class="sxs-lookup"><span data-stu-id="7c27a-153">Some custom actions have to occur when a Windows service is installed by the <xref:System.Configuration.Install.Installer> class.</span></span> <span data-ttu-id="7c27a-154">Program Visual Studio może utworzyć te instalatory specjalnie dla usługi systemu Windows i dodać je do projektu.</span><span class="sxs-lookup"><span data-stu-id="7c27a-154">Visual Studio can create these installers specifically for a Windows service and add them to your project.</span></span>

## <a name="set-service-status"></a><span data-ttu-id="7c27a-155">Ustaw stan usługi</span><span class="sxs-lookup"><span data-stu-id="7c27a-155">Set service status</span></span>

<span data-ttu-id="7c27a-156">Usługi zgłaszają swój stan do menedżera kontroli usług, dzięki czemu użytkownicy można stwierdzić, czy usługa działa poprawnie.</span><span class="sxs-lookup"><span data-stu-id="7c27a-156">Services report their status to the Service Control Manager, so that users can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="7c27a-157">Domyślnie, usług, które dziedziczą z <xref:System.ServiceProcess.ServiceBase> ograniczony zestaw ustawień stanu, w tym zatrzymana, wstrzymana i uruchamianie raportu.</span><span class="sxs-lookup"><span data-stu-id="7c27a-157">By default, services that inherit from <xref:System.ServiceProcess.ServiceBase> report a limited set of status settings, including Stopped, Paused, and Running.</span></span> <span data-ttu-id="7c27a-158">Jeśli usługa ma nieco podczas uruchamiania go może być przydatne do raportowania stanu Start oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="7c27a-158">If a service takes a little while to start up, it might be helpful to report a Start Pending status.</span></span> <span data-ttu-id="7c27a-159">Możesz również wdrożyć ustawienia stanu Start oczekujące i Zatrzymaj oczekiwanie przez dodanie kodu, która wywołuje Windows [funkcji SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).</span><span class="sxs-lookup"><span data-stu-id="7c27a-159">You can also implement the Start Pending and Stop Pending status settings by adding code that calls into the Windows [SetServiceStatus function](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).</span></span>

<span data-ttu-id="7c27a-160">Aby zaimplementować usługę w stanie oczekiwania:</span><span class="sxs-lookup"><span data-stu-id="7c27a-160">To implement service pending status:</span></span>

1. <span data-ttu-id="7c27a-161">Dodaj `using` instrukcji lub `Imports` deklaracji pod kątem <xref:System.Runtime.InteropServices?displayProperty=nameWithType> przestrzeni nazw w pliku MyNewService.cs lub MyNewService.vb:</span><span class="sxs-lookup"><span data-stu-id="7c27a-161">Add a `using` statement or `Imports` declaration for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace in the MyNewService.cs or MyNewService.vb file:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="7c27a-162">Dodaj następujący kod do MyNewService.cs do deklarowania `ServiceState` wartości i można dodać struktury stanu, która będzie używana na platformie wywołania wywołania:</span><span class="sxs-lookup"><span data-stu-id="7c27a-162">Add the following code to MyNewService.cs to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

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

3. <span data-ttu-id="7c27a-163">Teraz w `MyNewService` klasy, Zadeklaruj [funkcji SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) przy użyciu [wywołania platformy](../interop/consuming-unmanaged-dll-functions.md):</span><span class="sxs-lookup"><span data-stu-id="7c27a-163">Now, in the `MyNewService` class, declare the [SetServiceStatus function](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="7c27a-164">Aby zaimplementować Rozpocznij oczekiwanie stanu, Dodaj następujący kod na początku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="7c27a-164">To implement the Start Pending status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

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

5. <span data-ttu-id="7c27a-165">Dodaj kod, aby ustawić stan uruchomione na końcu <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7c27a-165">Add code to set the status to Running at the end of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span>

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

6. <span data-ttu-id="7c27a-166">(Opcjonalnie) Powtórz tę procedurę dla <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7c27a-166">(Optional) Repeat this procedure for the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method.</span></span>

> [!NOTE]
> <span data-ttu-id="7c27a-167">[Menedżera sterowania usługami](/windows/desktop/Services/service-control-manager) używa `dwWaitHint` i `dwCheckpoint` członkowie [struktury SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status) określić ilość czasu oczekiwania dla usługi Windows uruchomić lub zamknąć.</span><span class="sxs-lookup"><span data-stu-id="7c27a-167">The [Service Control Manager](/windows/desktop/Services/service-control-manager) uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/desktop/api/winsvc/ns-winsvc-_service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="7c27a-168">Jeśli Twoje <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody trwają długo, usługi mogą żądać więcej czasu, przez wywołanie metody [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) ponownie, używając zwiększona `dwCheckPoint` wartość.</span><span class="sxs-lookup"><span data-stu-id="7c27a-168">If your <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods run long, your service can request more time by calling [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) again with an incremented `dwCheckPoint` value.</span></span>

## <a name="add-installers-to-the-service"></a><span data-ttu-id="7c27a-169">Dodawanie instalatorów do usługi</span><span class="sxs-lookup"><span data-stu-id="7c27a-169">Add installers to the service</span></span>

<span data-ttu-id="7c27a-170">Przed uruchomieniem usługi Windows, musisz zainstalować go, który rejestruje je z Menedżerem sterowania usługami.</span><span class="sxs-lookup"><span data-stu-id="7c27a-170">Before you can run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="7c27a-171">Możesz dodać instalatory projektu, które obsługi szczegółów rejestracji.</span><span class="sxs-lookup"><span data-stu-id="7c27a-171">You can add installers to your project that handle the registration details.</span></span>

1. <span data-ttu-id="7c27a-172">W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **MyNewService.cs** lub **MyNewService.vb**, a następnie wybierz **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-172">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>

2. <span data-ttu-id="7c27a-173">Kliknij tło projektanta, aby zaznaczyć samą usługę, a nie jakąkolwiek jej zawartość.</span><span class="sxs-lookup"><span data-stu-id="7c27a-173">Click the background of the designer to select the service itself, instead of any of its contents.</span></span>

3. <span data-ttu-id="7c27a-174">Otwórz menu kontekstowe okna Projektanta (Jeśli używasz urządzenia wskazującego, kliknij prawym przyciskiem myszy wewnątrz okna), a następnie wybierz **Dodaj Instalatora**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-174">Open the context menu for the designer window (if you’re using a pointing device, right-click inside the window), and then choose **Add Installer**.</span></span>

   <span data-ttu-id="7c27a-175">Domyślnie do projektu zostanie dodana klasa składnika zawierająca dwa instalatory.</span><span class="sxs-lookup"><span data-stu-id="7c27a-175">By default, a component class that contains two installers is added to your project.</span></span> <span data-ttu-id="7c27a-176">Składnik nazywa **ProjectInstaller**, zawiera pliki instalacyjne są Instalatora usługi i procesu skojarzonego Instalatora usługi.</span><span class="sxs-lookup"><span data-stu-id="7c27a-176">The component is named **ProjectInstaller**, and the installers it contains are the installer for your service and the installer for the service's associated process.</span></span>

4. <span data-ttu-id="7c27a-177">W **projektowania** wyświetlić **ProjectInstaller**, wybierz **serviceInstaller1** dla projektu Visual C# lub **ServiceInstaller1** dla wizualizacji Podstawowy projekt.</span><span class="sxs-lookup"><span data-stu-id="7c27a-177">In **Design** view for **ProjectInstaller**, choose **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project.</span></span>

5. <span data-ttu-id="7c27a-178">W **właściwości** okna, upewnij się, że <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość jest ustawiona na **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-178">In the **Properties** window, make sure the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

6. <span data-ttu-id="7c27a-179">Ustaw **opis** właściwość jakiś tekst, na przykład "Przykładowej usługi".</span><span class="sxs-lookup"><span data-stu-id="7c27a-179">Set the **Description** property to some text, such as "A sample service".</span></span> <span data-ttu-id="7c27a-180">Ten tekst pojawia się okno usługi i pomaga użytkownikom identyfikować usługi i zrozumieć, co to jest używany.</span><span class="sxs-lookup"><span data-stu-id="7c27a-180">This text appears in the Services window and helps the user identify the service and understand what it’s used for.</span></span>

7. <span data-ttu-id="7c27a-181">Ustaw <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> właściwość tekst, który ma być wyświetlany w oknie usługi **nazwa** kolumny.</span><span class="sxs-lookup"><span data-stu-id="7c27a-181">Set the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property to the text that you want to appear in the Services window in the **Name** column.</span></span> <span data-ttu-id="7c27a-182">Na przykład można wprowadzić "MyNewService Display Name".</span><span class="sxs-lookup"><span data-stu-id="7c27a-182">For example, you can enter "MyNewService Display Name".</span></span> <span data-ttu-id="7c27a-183">Ta nazwa może różnić się od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość, która jest to nazwa używana przez system (na przykład, kiedy używasz `net start` polecenie, aby uruchomić usługę).</span><span class="sxs-lookup"><span data-stu-id="7c27a-183">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name used by the system (for example, when you use the `net start` command to start your service).</span></span>

8. <span data-ttu-id="7c27a-184">Ustaw <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwość <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="7c27a-184">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span></span>

     <span data-ttu-id="7c27a-185">![Właściwości Instalatora usługi Windows](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span><span class="sxs-lookup"><span data-stu-id="7c27a-185">![Installer Properties for a Windows service](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span></span>

9. <span data-ttu-id="7c27a-186">W projektancie, wybierz **serviceProcessInstaller1** dla projektu Visual C# lub **ServiceProcessInstaller1** dla projektów języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7c27a-186">In the designer, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project.</span></span> <span data-ttu-id="7c27a-187">Ustaw <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> właściwość <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span><span class="sxs-lookup"><span data-stu-id="7c27a-187">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span></span> <span data-ttu-id="7c27a-188">Powoduje to usługa, można zainstalować i uruchomić przy użyciu lokalnego konta systemowego.</span><span class="sxs-lookup"><span data-stu-id="7c27a-188">This causes the service to be installed and to run using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7c27a-189"><xref:System.ServiceProcess.ServiceAccount.LocalSystem> Konto ma szerokie uprawnienia, w tym możliwość zapisu do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7c27a-189">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="7c27a-190">Należy go używać ostrożnie, ponieważ może zwiększyć ryzyko ataku przez złośliwe oprogramowanie.</span><span class="sxs-lookup"><span data-stu-id="7c27a-190">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="7c27a-191">W przypadku innych zadań, należy wziąć pod uwagę przy użyciu <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, które działa jako użytkownik bez uprawnień na komputerze lokalnym i przedstawia poświadczenia anonimowe każdemu zdalnemu serwerowi.</span><span class="sxs-lookup"><span data-stu-id="7c27a-191">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="7c27a-192">W tym przykładzie zakończy się niepowodzeniem, jeśli zostanie podjęta próba użycia <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, ponieważ wymaga uprawnień do zapisu w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7c27a-192">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="7c27a-193">Aby uzyskać więcej informacji na temat instalatory zobacz [jak: Dodawanie instalatorów do usługi aplikacji](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="7c27a-193">For more information about installers, see [How to: Add Installers to Your service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="7c27a-194">(Opcjonalnie) Ustaw parametry uruchamiania</span><span class="sxs-lookup"><span data-stu-id="7c27a-194">(Optional) Set startup parameters</span></span>

<span data-ttu-id="7c27a-195">Do usług Windows, takich jak każdego innego pliku wykonywalnego, może akceptować argumentów wiersza polecenia lub parametry uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="7c27a-195">A Windows service, like any other executable, can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="7c27a-196">Po dodaniu kodu z parametrami uruchamiania procesu użytkownicy mogą uruchamiać własne parametry niestandardowe uruchomienia usługi przy użyciu okna usługi w Panelu sterowania Windows.</span><span class="sxs-lookup"><span data-stu-id="7c27a-196">When you add code to process startup parameters, users can start your service with their own custom startup parameters by using the Services window in the Windows Control Panel.</span></span> <span data-ttu-id="7c27a-197">Jednak te parametry uruchamiania nie są zachowywane podczas następnego uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="7c27a-197">However, these startup parameters are not persisted the next time the service starts.</span></span> <span data-ttu-id="7c27a-198">Aby ustawić parametry uruchamiania trwale, można ustawić je w rejestrze, jak pokazano w tej procedurze.</span><span class="sxs-lookup"><span data-stu-id="7c27a-198">To set startup parameters permanently, you can set them in the registry, as shown in this procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="7c27a-199">Przed podjęciem decyzji o Dodaj parametry uruchamiania, należy wziąć pod uwagę niezależnie czy dotyczyć to najlepszy sposób przekazywania informacji do usługi.</span><span class="sxs-lookup"><span data-stu-id="7c27a-199">Before you decide to add startup parameters, consider whether that is the best way to pass information to your service.</span></span> <span data-ttu-id="7c27a-200">Mimo, że parametry uruchamiania są łatwe w użyciu i do analizy, a użytkownicy mogą łatwo je zastąpić, może być trudne dla użytkowników do użytku bez dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="7c27a-200">Although startup parameters are easy to use and to parse, and users can easily override them, they might be harder for users to discover and use without documentation.</span></span> <span data-ttu-id="7c27a-201">Ogólnie rzecz biorąc Jeśli usługa wymaga więcej niż kilku Parametry uruchamiania, należy rozważyć użycie rejestru lub pliku konfiguracji zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="7c27a-201">Generally, if your service requires more than just a few startup parameters, you should consider using the registry or a configuration file instead.</span></span> <span data-ttu-id="7c27a-202">Każda usługa Windows ma wpis w kluczu rejestru **klucza HKLM\System\CurrentControlSet\services**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-202">Every Windows service has an entry in the registry under **HKLM\System\CurrentControlSet\services**.</span></span> <span data-ttu-id="7c27a-203">W kluczu usługi można użyć **parametry** podklucz do przechowywania informacji, które mogą uzyskiwać dostęp do usługi.</span><span class="sxs-lookup"><span data-stu-id="7c27a-203">Under the service's key, you can use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="7c27a-204">Może używać plików konfiguracji aplikacji dla usługi Windows w taki sam sposób jak w przypadku innych programów.</span><span class="sxs-lookup"><span data-stu-id="7c27a-204">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="7c27a-205">Przykładowy kod, zobacz <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span><span class="sxs-lookup"><span data-stu-id="7c27a-205">For example code, see <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span></span>

<span data-ttu-id="7c27a-206">Aby dodać parametry uruchamiania:</span><span class="sxs-lookup"><span data-stu-id="7c27a-206">To add startup parameters:</span></span>

1. <span data-ttu-id="7c27a-207">W `Main` metody w pliku Program.cs lub MyNewService.Designer.vb, Dodawanie parametru wejściowego do przekazania do konstruktora usługi:</span><span class="sxs-lookup"><span data-stu-id="7c27a-207">In the `Main` method in Program.cs or in MyNewService.Designer.vb, add an input parameter to pass to the service constructor:</span></span>

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

2. <span data-ttu-id="7c27a-208">Zmiana `MyNewService` konstruktora w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7c27a-208">Change the `MyNewService` constructor as follows:</span></span>

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

   <span data-ttu-id="7c27a-209">Ten kod ustawia nazwę źródła i dziennik zdarzeń, zgodnie z Parametry uruchamiania podane lub używa wartości domyślnych, jeśli zostały dostarczone żadne argumenty.</span><span class="sxs-lookup"><span data-stu-id="7c27a-209">This code sets the event source and log name according to the supplied startup parameters, or uses default values if no arguments are supplied.</span></span>

3. <span data-ttu-id="7c27a-210">Aby określić argumenty wiersza polecenia, Dodaj następujący kod, aby `ProjectInstaller` klasy ProjectInstaller.cs lub ProjectInstaller.vb:</span><span class="sxs-lookup"><span data-stu-id="7c27a-210">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in ProjectInstaller.cs or ProjectInstaller.vb:</span></span>

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

   <span data-ttu-id="7c27a-211">Ten kod modyfikuje **ImagePath** klucz rejestru zwykle zawiera pełną ścieżkę do pliku wykonywalnego dla usługi Windows przez dodanie wartości domyślne parametrów.</span><span class="sxs-lookup"><span data-stu-id="7c27a-211">This code modifies the **ImagePath** registry key, which typically contains the full path to the executable for the Windows service, by adding the default parameter values.</span></span> <span data-ttu-id="7c27a-212">Znaki cudzysłowu wokół ścieżki (i wokół każdego parametru poszczególnych) są wymagane dla usługi została prawidłowo uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="7c27a-212">The quotation marks around the path (and around each individual parameter) are required for the service to start up correctly.</span></span> <span data-ttu-id="7c27a-213">Aby zmienić parametry uruchamiania dla tej usługi Windows, użytkownicy mogą zmieniać parametrów podanych w **ImagePath** klucz rejestru, mimo że lepszy sposób jest programowe zmienianie i udostępniają funkcje dla użytkowników w przyjazne sposób (na przykład narzędzie do zarządzania lub konfiguracji).</span><span class="sxs-lookup"><span data-stu-id="7c27a-213">To change the startup parameters for this Windows service, users can change the parameters given in the **ImagePath** registry key, although the better way is to change it programmatically and expose the functionality to users in a friendly way (for example, in a management or configuration utility).</span></span>

## <a name="build-the-service"></a><span data-ttu-id="7c27a-214">Tworzenie usługi</span><span class="sxs-lookup"><span data-stu-id="7c27a-214">Build the service</span></span>

1. <span data-ttu-id="7c27a-215">W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla projektu, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-215">In **Solution Explorer**, open the context menu for your project, and then choose **Properties**.</span></span>

   <span data-ttu-id="7c27a-216">Są wyświetlane na stronach właściwości projektu.</span><span class="sxs-lookup"><span data-stu-id="7c27a-216">The property pages for your project appear.</span></span>

2. <span data-ttu-id="7c27a-217">Na **aplikacji** na karcie **obiekt początkowy** wybierz **MyNewService.Program**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-217">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**.</span></span>

3. <span data-ttu-id="7c27a-218">W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla projektu, a następnie wybierz **kompilacji** do skompilowania projektu (lub naciśnij **Ctrl**+**Shift**  + **B**).</span><span class="sxs-lookup"><span data-stu-id="7c27a-218">In **Solution Explorer**, open the context menu for your project, and then choose **Build** to build the project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="7c27a-219">Instalowanie usługi</span><span class="sxs-lookup"><span data-stu-id="7c27a-219">Install the service</span></span>

<span data-ttu-id="7c27a-220">Teraz, gdy masz utworzoną usługę Windows, należy ją zainstalować.</span><span class="sxs-lookup"><span data-stu-id="7c27a-220">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="7c27a-221">Aby zainstalować usługę Windows, musi mieć poświadczenia administratora na komputerze, na którym instalujesz go.</span><span class="sxs-lookup"><span data-stu-id="7c27a-221">To install a Windows service, you must have administrator credentials on the computer on which you're installing it.</span></span>

1. <span data-ttu-id="7c27a-222">Otwórz **wiersz polecenia programisty dla programu Visual Studio** przy użyciu poświadczeń administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="7c27a-222">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span> <span data-ttu-id="7c27a-223">Jeśli używasz myszy, kliknij prawym przyciskiem myszy **wiersz polecenia programisty dla programu VS 2017** w Windows z menu Start, a następnie wybierz **więcej** > **Uruchom jako Administrator** .</span><span class="sxs-lookup"><span data-stu-id="7c27a-223">If you’re using a mouse, right-click on **Developer Command Prompt for VS 2017** in the Windows Start menu, and then choose **More** > **Run as Administrator**.</span></span>

2. <span data-ttu-id="7c27a-224">W **wiersz polecenia dla deweloperów** okna, przejdź do folderu, który zawiera dane wyjściowe projektu (domyślnie jest *\bin\Debug* podkatalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="7c27a-224">In the **Developer Command Prompt** window, navigate to the folder that contains your project's output (by default, it's the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="7c27a-225">Wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="7c27a-225">Enter the following command:</span></span>

    ```shell
    installutil.exe MyNewService.exe
    ```

    <span data-ttu-id="7c27a-226">Jeśli usługa zostanie zainstalowana pomyślnie, **installutil.exe** zgłosi powodzenie operacji.</span><span class="sxs-lookup"><span data-stu-id="7c27a-226">If the service installs successfully, **installutil.exe** reports success.</span></span> <span data-ttu-id="7c27a-227">Jeśli system nie może odnaleźć **InstallUtil.exe**, upewnij się, że istnieje na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7c27a-227">If the system could not find **InstallUtil.exe**, make sure that it exists on your computer.</span></span> <span data-ttu-id="7c27a-228">To narzędzie jest instalowane z .NET Framework do folderu *% windir%\Microsoft.NET\Framework[64]\\[framework w wersji]*.</span><span class="sxs-lookup"><span data-stu-id="7c27a-228">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\[framework version]*.</span></span> <span data-ttu-id="7c27a-229">Na przykład jest domyślna ścieżka dla 32-bitowej wersji *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="7c27a-229">For example, the default path for the 32-bit version is *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="7c27a-230">Jeśli **installutil.exe** przetwarzać raporty o awarii, sprawdź dziennik instalacji, aby dowiedzieć się, dlaczego.</span><span class="sxs-lookup"><span data-stu-id="7c27a-230">If the **installutil.exe** process reports failure, check the install log to find out why.</span></span> <span data-ttu-id="7c27a-231">Domyślnie dziennik jest w tym samym folderze co plik wykonywalny usługi.</span><span class="sxs-lookup"><span data-stu-id="7c27a-231">By default the log is in the same folder as the service executable.</span></span> <span data-ttu-id="7c27a-232">Instalacja może zakończyć się niepowodzeniem, jeśli <xref:System.ComponentModel.RunInstallerAttribute> klasy nie znajduje się na `ProjectInstaller` klasy, jeśli ten atrybut nie jest równa **true**, lub jeśli `ProjectInstaller` klasy nie jest oznaczony jako **publicznych**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-232">The installation can fail if  the <xref:System.ComponentModel.RunInstallerAttribute> Class is not present on the `ProjectInstaller` class, if the attribute is not set to **true**, or if the `ProjectInstaller` class is not marked **public**.</span></span>

<span data-ttu-id="7c27a-233">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="7c27a-233">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="7c27a-234">Uruchom program i uruchom usługę</span><span class="sxs-lookup"><span data-stu-id="7c27a-234">Start and run the service</span></span>

1. <span data-ttu-id="7c27a-235">Windows, otwórz **usług** aplikacji klasycznej.</span><span class="sxs-lookup"><span data-stu-id="7c27a-235">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="7c27a-236">Naciśnij klawisz **Windows**+**R** otworzyć **Uruchom** , a następnie wprowadź **services.msc** i naciśnij klawisz **Enter**  lub kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-236">Press **Windows**+**R** to open the **Run** box, and then enter **services.msc** and press **Enter** or click **OK**.</span></span>

     <span data-ttu-id="7c27a-237">Powinien zostać wyświetlony na liście usługi **usług**, wyświetlane alfabetycznie według nazwy wyświetlanej, ustaw dla niego.</span><span class="sxs-lookup"><span data-stu-id="7c27a-237">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![MyNewService w oknie usług.](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="7c27a-239">W **usług**, otwórz menu skrótów dla usługi, a następnie wybierz **Start**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-239">In **Services**, open the shortcut menu for your service, and then choose **Start**.</span></span>

3. <span data-ttu-id="7c27a-240">Aby zatrzymać usługę, otwórz menu skrótów dla usługi, a następnie wybierz **zatrzymać**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-240">To stop the service, open the shortcut menu for the service, and then choose **Stop**.</span></span>

4. <span data-ttu-id="7c27a-241">(Opcjonalnie) W wierszu polecenia można użyć poleceń `net start ServiceName` i `net stop ServiceName` uruchamianie i zatrzymywanie usługi.</span><span class="sxs-lookup"><span data-stu-id="7c27a-241">(Optional) From the command line, you can use the commands `net start ServiceName` and `net stop ServiceName` to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="7c27a-242">Sprawdź dane wyjściowe dziennika zdarzeń, usługi</span><span class="sxs-lookup"><span data-stu-id="7c27a-242">Verify the event log output of your service</span></span>

1. <span data-ttu-id="7c27a-243">Otwórz **Podgląd zdarzeń** , zaczynając wpisywanie **Podgląd zdarzeń** w polu wyszukiwania na pasku zadań Windows, a następnie wybierając pozycję **Podgląd zdarzeń** w wynikach wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="7c27a-243">Open **Event Viewer** by starting to type **Event Viewer** in the search box on the Windows task bar, and then selecting **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="7c27a-244">W programie Visual Studio są dostępne dzienniki zdarzeń, otwierając **Eksploratora serwera** (klawiatury: **CTRL**+**Alt**+**S**) i rozwijając **dzienniki zdarzeń** węzła na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="7c27a-244">In Visual Studio, you can access event logs by opening **Server Explorer** (Keyboard: **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="7c27a-245">W **Podgląd zdarzeń**, rozwiń węzeł **Dzienniki aplikacji i usług**.</span><span class="sxs-lookup"><span data-stu-id="7c27a-245">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="7c27a-246">Odszukaj **MyNewLog** (lub **MyLogFile1**, po wykonaniu procedury opcjonalnej można dodać argumenty wiersza polecenia) i rozwiń go.</span><span class="sxs-lookup"><span data-stu-id="7c27a-246">Locate the listing for **MyNewLog** (or **MyLogFile1**, if you followed the optional procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="7c27a-247">Powinny być widoczne wpisy dwie akcje (rozpoczęcie i zakończenie), wykonanych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="7c27a-247">You should see entries for the two actions (start and stop) that your service performed.</span></span>

     ![Użyj podglądu zdarzeń, aby wyświetlić wpisy dziennika zdarzeń](../../../docs/framework/windows-services/media/windows-service-event-viewer.png)

## <a name="uninstall-the-service"></a><span data-ttu-id="7c27a-249">Odinstaluj usługę</span><span class="sxs-lookup"><span data-stu-id="7c27a-249">Uninstall the service</span></span>

1. <span data-ttu-id="7c27a-250">Otwórz **wiersz polecenia programisty dla programu Visual Studio** przy użyciu poświadczeń administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="7c27a-250">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="7c27a-251">W oknie wiersza polecenia przejdź do folderu, który zawiera dane wyjściowe projektu.</span><span class="sxs-lookup"><span data-stu-id="7c27a-251">In the command prompt window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="7c27a-252">Wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="7c27a-252">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="7c27a-253">Jeśli usługa zostanie pomyślnie, odinstalowana **installutil.exe** raporty usługi został pomyślnie usunięty.</span><span class="sxs-lookup"><span data-stu-id="7c27a-253">If the service uninstalls successfully, **installutil.exe** reports that your service was successfully removed.</span></span> <span data-ttu-id="7c27a-254">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="7c27a-254">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7c27a-255">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7c27a-255">Next steps</span></span>

<span data-ttu-id="7c27a-256">Teraz, po utworzeniu usługi, można utworzyć program instalacyjny autonomicznego, który inne można użyć do zainstalowania usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="7c27a-256">Now that you've created the service, you might want to create a standalone setup program that others can use to install your Windows service.</span></span> <span data-ttu-id="7c27a-257">Funkcja ClickOnce nie obsługuje usług Windows, ale można użyć [zestaw narzędzi WiX](http://wixtoolset.org/) możliwość utworzenia Instalatora usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="7c27a-257">ClickOnce doesn't support Windows services, but you can use the [WiX Toolset](http://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="7c27a-258">Zapoznać się z pomysłami z innymi zobacz [Utwórz pakiet instalacyjny](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="7c27a-258">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

<span data-ttu-id="7c27a-259">Może zbadać użycie <xref:System.ServiceProcess.ServiceController> składnik, który umożliwia wysyłanie poleceń do usługi, po zainstalowaniu.</span><span class="sxs-lookup"><span data-stu-id="7c27a-259">You might explore the use of a <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

<span data-ttu-id="7c27a-260">Odpowiednio konfigurując instalatora, można spowodować generowanie dziennika zdarzeń podczas instalowania aplikacji, a nie jej działania.</span><span class="sxs-lookup"><span data-stu-id="7c27a-260">You can use an installer to create an event log when the application is installed instead of creating the event log when the application runs.</span></span> <span data-ttu-id="7c27a-261">Ponadto z chwilą odinstalowania aplikacji dziennik zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="7c27a-261">Additionally, the event log will be deleted by the installer when the application is uninstalled.</span></span> <span data-ttu-id="7c27a-262">Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.EventLogInstaller> odwołania do stron.</span><span class="sxs-lookup"><span data-stu-id="7c27a-262">For more information, see the <xref:System.Diagnostics.EventLogInstaller> reference page.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c27a-263">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c27a-263">See also</span></span>

- [<span data-ttu-id="7c27a-264">Aplikacje usług Windows</span><span class="sxs-lookup"><span data-stu-id="7c27a-264">Windows service applications</span></span>](../../../docs/framework/windows-services/index.md)
- [<span data-ttu-id="7c27a-265">Wprowadzenie do aplikacji usług Windows</span><span class="sxs-lookup"><span data-stu-id="7c27a-265">Introduction to Windows service applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="7c27a-266">Instrukcje: Debugowanie aplikacji usług Windows</span><span class="sxs-lookup"><span data-stu-id="7c27a-266">How to: Debug Windows service applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="7c27a-267">Usługi (Windows)</span><span class="sxs-lookup"><span data-stu-id="7c27a-267">Services (Windows)</span></span>](/windows/desktop/Services/services)
