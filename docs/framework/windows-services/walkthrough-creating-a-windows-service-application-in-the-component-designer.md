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
ms.openlocfilehash: 6d70db7139d82b6e219e2c417282333f950ef402
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509856"
---
# <a name="walkthrough-creating-a-windows-service-application-in-the-component-designer"></a><span data-ttu-id="e6a5a-102">Wskazówki: tworzenie aplikacji usługowej systemu Windows w Projektancie składników</span><span class="sxs-lookup"><span data-stu-id="e6a5a-102">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>
<span data-ttu-id="e6a5a-103">W tym artykule pokazano, jak utworzyć prostą aplikację Windows Service w programie Visual Studio, która wypisuje komunikaty w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-103">This article demonstrates how to create a simple Windows Service application in Visual Studio that writes messages to an event log.</span></span> <span data-ttu-id="e6a5a-104">Poniżej przedstawiono podstawowe kroki, które należy wykonać w celu tworzenia i używania usługi:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-104">Here are the basic steps that you perform to create and use your service:</span></span>  
  
1.  <span data-ttu-id="e6a5a-105">[Tworzenie usługi](#BK_CreateProject) przy użyciu **usługi Windows** szablonu projektu i skonfigurowania go.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-105">[Creating a Service](#BK_CreateProject) by using the **Windows Service** project template, and configure it.</span></span> <span data-ttu-id="e6a5a-106">Ten szablon tworzy klasę dla Ciebie, która dziedziczy <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> oraz zapisze dużą część podstawowego kodu usługi, takie jak kod, aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-106">This template creates a class for you that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> and writes much of the basic service code, such as the code to start the service.</span></span>  
  
2.  <span data-ttu-id="e6a5a-107">[Dodawanie funkcji do usługi](#BK_WriteCode) dla <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedur i zastąpienie wszelkich innych metod, które mają zostać zmienione.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-107">[Adding Features to the Service](#BK_WriteCode) for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures, and override any other methods that you want to redefine.</span></span>  
  
3.  <span data-ttu-id="e6a5a-108">[Ustawianie stanu usługi](#BK_SetStatus).</span><span class="sxs-lookup"><span data-stu-id="e6a5a-108">[Setting Service Status](#BK_SetStatus).</span></span> <span data-ttu-id="e6a5a-109">Domyślnie usługi tworzone przy użyciu <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> zaimplementować tylko podzbiór flagi stanu dostępności.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-109">By default, services created with <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> implement only a subset of the available status flags.</span></span> <span data-ttu-id="e6a5a-110">Jeśli usługa zajmuje dużo czasu, aby rozpocząć, wstrzymać lub zatrzymać, można zaimplementować wartości stanu, takie jak Start Oczekiwanie lub Zatrzymaj oczekiwanie, aby wskazać, czy działa w przypadku operacji.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-110">If your service takes a long time to start up, pause, or stop, you can implement status values such as Start Pending or Stop Pending to indicate that it's working on an operation.</span></span>  
  
4.  <span data-ttu-id="e6a5a-111">[Dodawanie instalatorów do usługi](#BK_AddInstallers) dla aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-111">[Adding Installers to the Service](#BK_AddInstallers) for your service application.</span></span>  
  
5.  <span data-ttu-id="e6a5a-112">(Opcjonalnie) [Ustaw parametry uruchamiania](#BK_StartupParameters)określ argumenty uruchomienia domyślne, a użytkownicy mogą zastąpić ustawienia domyślne, podczas uruchamiania usługi ręcznie.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-112">(Optional) [Set Startup Parameters](#BK_StartupParameters), specify default startup arguments, and enable users to override default settings when they start your service manually.</span></span>  
  
6.  <span data-ttu-id="e6a5a-113">[Tworzenie usługi](#BK_Build).</span><span class="sxs-lookup"><span data-stu-id="e6a5a-113">[Building the Service](#BK_Build).</span></span>  
  
7.  <span data-ttu-id="e6a5a-114">[Instalowanie usługi](#BK_Install) na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-114">[Installing the Service](#BK_Install) on the local machine.</span></span>  
  
8.  <span data-ttu-id="e6a5a-115">Dostęp do Menedżera sterowania usługami Windows i [co spowoduje uruchomienie usługi](#BK_StartService).</span><span class="sxs-lookup"><span data-stu-id="e6a5a-115">Access the Windows Service Control Manager and [Starting and Running the Service](#BK_StartService).</span></span>  
  
9. <span data-ttu-id="e6a5a-116">[Odinstalowywanie usługi Windows](#BK_Uninstall).</span><span class="sxs-lookup"><span data-stu-id="e6a5a-116">[Uninstalling a Windows Service](#BK_Uninstall).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="e6a5a-117">Szablon projektu usług systemu Windows Services wymagany w tym instruktażu jest niedostępny w wydaniu Express programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-117">The Windows Services project template that is required for this walkthrough is not available in the Express edition of Visual Studio.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]  
  
<a name="BK_CreateProject"></a>   
## <a name="creating-a-service"></a><span data-ttu-id="e6a5a-118">Tworzenie usługi</span><span class="sxs-lookup"><span data-stu-id="e6a5a-118">Creating a Service</span></span>  
 <span data-ttu-id="e6a5a-119">Na początku utworzysz projekt i skonfigurujesz wartości niezbędne do poprawnego działania usługi.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-119">To begin, you create the project and set values that are required for the service to function correctly.</span></span>  
  
#### <a name="to-create-and-configure-your-service"></a><span data-ttu-id="e6a5a-120">Aby utworzyć i skonfigurować usługę</span><span class="sxs-lookup"><span data-stu-id="e6a5a-120">To create and configure your service</span></span>  
  
1.  <span data-ttu-id="e6a5a-121">W programie Visual Studio, na pasku menu wybierz **pliku**, **New**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-121">In Visual Studio, on the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="e6a5a-122">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-122">The **New Project** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="e6a5a-123">Na liście szablony projektów Visual Basic lub Visual C#, wybierz opcję **usługi Windows**i nazwij projekt **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-123">In the list of Visual Basic or Visual C# project templates, choose **Windows Service**, and name the project **MyNewService**.</span></span> <span data-ttu-id="e6a5a-124">Wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-124">Choose **OK**.</span></span>  
  
     <span data-ttu-id="e6a5a-125">Szablon projektu automatycznie dodana Klasa składnika o nazwie `Service1` tej, która dziedziczy <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-125">The project template automatically adds a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span>  
  
3.  <span data-ttu-id="e6a5a-126">Na **Edytuj** menu, wybierz **Znajdź i Zamień**, **Znajdź w plikach** (klawiatura: Ctrl + Shift + F).</span><span class="sxs-lookup"><span data-stu-id="e6a5a-126">On the **Edit** menu, choose **Find and Replace**, **Find in Files** (Keyboard: Ctrl+Shift+F).</span></span> <span data-ttu-id="e6a5a-127">Zamień wszystkie wystąpienia klasy `Service1` do `MyNewService`.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-127">Change all occurrences of `Service1` to `MyNewService`.</span></span> <span data-ttu-id="e6a5a-128">W Service1.cs, pliku Program.cs i Service1.Designer.cs (lub ich odpowiedników .vb) można znaleźć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-128">You’ll find instances in Service1.cs, Program.cs, and Service1.Designer.cs (or their .vb equivalents).</span></span>  
  
4.  <span data-ttu-id="e6a5a-129">W **właściwości** okno **Service1.cs [projekt]** lub **Service1.vb [projekt]** ustaw <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> i **(nazwa)** Właściwość `Service1` do **MyNewService**, jeśli jeszcze nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-129">In the **Properties** window for **Service1.cs [Design]** or **Service1.vb [Design]**, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> and the **(Name)** property for `Service1` to **MyNewService**, if it's not already set.</span></span>  
  
5.  <span data-ttu-id="e6a5a-130">W Eksploratorze rozwiązań, zmienianie nazwy **Service1.cs** do **MyNewService.cs**, lub **Service1.vb** do **MyNewService.vb**.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-130">In Solution Explorer, rename **Service1.cs** to **MyNewService.cs**, or **Service1.vb** to **MyNewService.vb**.</span></span>  
  
<a name="BK_WriteCode"></a>   
## <a name="adding-features-to-the-service"></a><span data-ttu-id="e6a5a-131">Dodawanie funkcji do usługi</span><span class="sxs-lookup"><span data-stu-id="e6a5a-131">Adding Features to the Service</span></span>  
 <span data-ttu-id="e6a5a-132">W tej sekcji dodasz niestandardowy dziennik zdarzeń do usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-132">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="e6a5a-133">Dzienniki zdarzeń nie w żaden sposób powiązane z usługami systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-133">Event logs are not associated in any way with Windows services.</span></span> <span data-ttu-id="e6a5a-134">W tym miejscu <xref:System.Diagnostics.EventLog> składnik jest używany na przykład typ składnika, można dodać do usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-134">Here the <xref:System.Diagnostics.EventLog> component is used as an example of the type of component you could add to a Windows service.</span></span>  
  
#### <a name="to-add-custom-event-log-functionality-to-your-service"></a><span data-ttu-id="e6a5a-135">Aby dodać funkcjonalność niestandardowego dziennika zdarzeń do usługi</span><span class="sxs-lookup"><span data-stu-id="e6a5a-135">To add custom event log functionality to your service</span></span>  
  
1.  <span data-ttu-id="e6a5a-136">W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **MyNewService.cs** lub **MyNewService.vb**, a następnie wybierz **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-136">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>  
  
2.  <span data-ttu-id="e6a5a-137">Z **składniki** części **przybornika**, przeciągnij <xref:System.Diagnostics.EventLog> składnik do projektanta.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-137">From the **Components** section of the **Toolbox**, drag an <xref:System.Diagnostics.EventLog> component to the designer.</span></span>  
  
3.  <span data-ttu-id="e6a5a-138">W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **MyNewService.cs** lub **MyNewService.vb**, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-138">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Code**.</span></span>  
  
4.  <span data-ttu-id="e6a5a-139">Dodaj deklarację dla **eventLog** obiektu `MyNewService` klasy, od razu po wierszu, który deklaruje `components` zmiennej:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-139">Add a declaration for the **eventLog** object in the `MyNewService` class, right after the line that declares the `components` variable:</span></span>  
  
     [!code-csharp[VbRadconService#16](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#16)]
     [!code-vb[VbRadconService#16](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#16)]  
  
5.  <span data-ttu-id="e6a5a-140">Dodaj lub zmodyfikuj konstruktora, aby zdefiniować niestandardowy dziennik zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-140">Add or edit the constructor to define a custom event log:</span></span>  
  
     [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
     [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]  
  
#### <a name="to-define-what-occurs-when-the-service-starts"></a><span data-ttu-id="e6a5a-141">Aby określić zachowanie występujące podczas uruchamiania usługi</span><span class="sxs-lookup"><span data-stu-id="e6a5a-141">To define what occurs when the service starts</span></span>  
  
-   <span data-ttu-id="e6a5a-142">W edytorze kodu zlokalizuj <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodę, która została zastąpiona automatycznie podczas tworzenia projektu i Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-142">In the Code Editor, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method that was automatically overridden when you created the project, and replace the code with the following.</span></span> <span data-ttu-id="e6a5a-143">Spowoduje to dodanie wpisu w dzienniku zdarzeń podczas uruchamiania usługi:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-143">This adds an entry to the event log when the service starts running:</span></span>  
  
     [!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
     [!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]  
  
     <span data-ttu-id="e6a5a-144">Aplikacja usługi jest przeznaczony jako długotrwałych, dzięki czemu zwykle sonduje lub monitoruje coś w systemie.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-144">A service application is designed to be long-running, so it usually polls or monitors something in the system.</span></span> <span data-ttu-id="e6a5a-145">Monitorowanie jest skonfigurowana w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-145">The monitoring is set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="e6a5a-146">Jednak <xref:System.ServiceProcess.ServiceBase.OnStart%2A> faktycznie nie wykonuje monitorowania.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-146">However, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> doesn’t actually do the monitoring.</span></span> <span data-ttu-id="e6a5a-147"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> Metoda musi powrócić do systemu operacyjnego, po rozpoczęciu operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-147">The <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method must return to the operating system after the service's operation has begun.</span></span> <span data-ttu-id="e6a5a-148">Nie może być wykonywana bezterminowo w pętli ani nakładać żadnych blokad.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-148">It must not loop forever or block.</span></span> <span data-ttu-id="e6a5a-149">Aby skonfigurować prosty mechanizm sondowania, można użyć <xref:System.Timers.Timer?displayProperty=nameWithType> składnika w następujący sposób: W <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody, ustawianie parametrów na części, a następnie ustaw <xref:System.Timers.Timer.Enabled%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-149">To set up a simple polling mechanism, you can use the <xref:System.Timers.Timer?displayProperty=nameWithType> component as follows: In the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, set parameters on the component, and then set the <xref:System.Timers.Timer.Enabled%2A> property to `true`.</span></span> <span data-ttu-id="e6a5a-150">Czasomierz wywołuje zdarzenia w kodzie okresowo, co usługa może zrobić, jego monitorowanie.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-150">The timer raises events in your code periodically, at which time your service could do its monitoring.</span></span> <span data-ttu-id="e6a5a-151">Aby to zrobić, można użyć następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-151">You can use the following code to do this:</span></span>  
  
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
     <span data-ttu-id="e6a5a-152">Dodaj zmienną składową do klasy.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-152">Add a member variable to the class.</span></span> <span data-ttu-id="e6a5a-153">Będzie zawierać identyfikator następne zdarzenie do zapisu do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-153">It will contain the identifier of the next event to write into the event log.</span></span>

    ```csharp
    private int eventId = 1;
    ```

    ```vb
    Private eventId As Integer = 1
    ```

     <span data-ttu-id="e6a5a-154">Dodaj kod, aby obsłużyć zdarzenie czasomierza:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-154">Add code to handle the timer event:</span></span>  
  
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
  
     <span data-ttu-id="e6a5a-155">Można wykonywać zadania za pomocą wątków procesów roboczych w tle zamiast uruchamiać swoją pracę w wątku głównym.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-155">You might want to perform tasks by using background worker threads instead of running all your work on the main thread.</span></span> <span data-ttu-id="e6a5a-156">Aby na przykład, zobacz <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> odwołania do stron.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-156">For an example of this, see the <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> reference page.</span></span>  
  
#### <a name="to-define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="e6a5a-157">Aby określić zachowanie występujące podczas zatrzymywania usługi</span><span class="sxs-lookup"><span data-stu-id="e6a5a-157">To define what occurs when the service is stopped</span></span>  
  
-   <span data-ttu-id="e6a5a-158">Zastąp kod <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metoda następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-158">Replace the code for the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method with the following.</span></span> <span data-ttu-id="e6a5a-159">Spowoduje to dodanie wpisu w dzienniku zdarzeń po zatrzymaniu usługi:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-159">This adds an entry to the event log when the service is stopped:</span></span>  
  
     [!code-csharp[VbRadconService#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
     [!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]  
  
 <span data-ttu-id="e6a5a-160">W następnej sekcji, możesz zastąpić <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, i <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> metody, aby zdefiniować dodatkowe przetwarzanie składnika.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-160">In the next section, you can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span>  
  
#### <a name="to-define-other-actions-for-the-service"></a><span data-ttu-id="e6a5a-161">Aby zdefiniować inne czynności do wykonania w usłudze</span><span class="sxs-lookup"><span data-stu-id="e6a5a-161">To define other actions for the service</span></span>  
  
-   <span data-ttu-id="e6a5a-162">Zlokalizuj metodę, która ma obsługiwać i zastąpić, aby zdefiniować, co ma być wykonywana.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-162">Locate the method that you want to handle, and override it to define what you want to occur.</span></span>  
  
     <span data-ttu-id="e6a5a-163">W poniższym kodzie pokazano, jak można zastąpić <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-163">The following code shows how you can override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method:</span></span>  
  
     [!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
     [!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]  
  
 <span data-ttu-id="e6a5a-164">Pewne niestandardowe czynności muszą występować po zainstalowaniu usługi Windows przez <xref:System.Configuration.Install.Installer> klasy.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-164">Some custom actions have to occur when a Windows service is installed by the <xref:System.Configuration.Install.Installer> class.</span></span> <span data-ttu-id="e6a5a-165">Program Visual Studio może utworzyć te instalatory specjalnie dla usługi systemu Windows i dodać je do projektu.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-165">Visual Studio can create these installers specifically for a Windows service and add them to your project.</span></span>  
  
<a name="BK_SetStatus"></a>   
## <a name="setting-service-status"></a><span data-ttu-id="e6a5a-166">Ustawienie stanu usługi</span><span class="sxs-lookup"><span data-stu-id="e6a5a-166">Setting Service Status</span></span>  
 <span data-ttu-id="e6a5a-167">Usługi zgłaszają swój stan do menedżera kontroli usług, dzięki czemu użytkownicy można stwierdzić, czy usługa działa poprawnie.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-167">Services report their status to the Service Control Manager, so that users can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="e6a5a-168">Domyślnie, usług, które dziedziczą z <xref:System.ServiceProcess.ServiceBase> ograniczony zestaw ustawień stanu, w tym zatrzymana, wstrzymana i uruchamianie raportu.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-168">By default, services that inherit from <xref:System.ServiceProcess.ServiceBase> report a limited set of status settings, including Stopped, Paused, and Running.</span></span> <span data-ttu-id="e6a5a-169">Jeśli usługa ma nieco podczas uruchamiania go może być przydatne do raportowania stanu Start oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-169">If a service takes a little while to start up, it might be helpful to report a Start Pending status.</span></span> <span data-ttu-id="e6a5a-170">Możesz również wdrożyć ustawienia stanu Start oczekujące i Zatrzymaj oczekiwanie przez dodanie kodu, która wywołuje Windows [funkcji SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).</span><span class="sxs-lookup"><span data-stu-id="e6a5a-170">You can also implement the Start Pending and Stop Pending status settings by adding code that calls into the Windows [SetServiceStatus function](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).</span></span>  
  
#### <a name="to-implement-service-pending-status"></a><span data-ttu-id="e6a5a-171">Aby zaimplementować usługę w stanie oczekiwania</span><span class="sxs-lookup"><span data-stu-id="e6a5a-171">To implement service pending status</span></span>  
  
1.  <span data-ttu-id="e6a5a-172">Dodaj `using` instrukcji lub `Imports` deklaracji <xref:System.Runtime.InteropServices?displayProperty=nameWithType> przestrzeni nazw w pliku MyNewService.cs lub MyNewService.vb:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-172">Add a `using` statement or `Imports` declaration to the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace in the MyNewService.cs or MyNewService.vb file:</span></span>  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    ```  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    ```  
  
2.  <span data-ttu-id="e6a5a-173">Dodaj następujący kod do MyNewService.cs do deklarowania `ServiceState` wartości i można dodać struktury stanu, która będzie używana na platformie wywołania wywołania:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-173">Add the following code to MyNewService.cs to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>  
  
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
  
3.  <span data-ttu-id="e6a5a-174">Teraz w `MyNewService` klasy, Zadeklaruj [funkcji SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) przy użyciu platformy wywołania:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-174">Now, in the `MyNewService` class, declare the [SetServiceStatus function](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) by using platform invoke:</span></span>  
  
    ```csharp  
    [DllImport("advapi32.dll", SetLastError=true)]  
            private static extern bool SetServiceStatus(IntPtr handle, ref ServiceStatus serviceStatus);  
    ```  
  
    ```vb  
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean  
    ```  
  
4.  <span data-ttu-id="e6a5a-175">Aby zaimplementować Rozpocznij oczekiwanie stanu, Dodaj następujący kod na początku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-175">To implement the Start Pending status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>  
  
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
  
5.  <span data-ttu-id="e6a5a-176">Dodaj kod, aby ustawić stan uruchomione na końcu <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-176">Add code to set the status to Running at the end of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span>  
  
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
  
6.  <span data-ttu-id="e6a5a-177">(Opcjonalnie) Powtórz tę procedurę dla <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-177">(Optional) Repeat this procedure for the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e6a5a-178">[Menedżera sterowania usługami](/windows/desktop/Services/service-control-manager) używa `dwWaitHint` i `dwCheckpoint` członkowie [struktury SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status) określić ilość czasu oczekiwania dla usługi Windows uruchomić lub zamknąć.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-178">The [Service Control Manager](/windows/desktop/Services/service-control-manager) uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/desktop/api/winsvc/ns-winsvc-_service_status) to determine how much time to wait for a Windows Service to start or shut down.</span></span> <span data-ttu-id="e6a5a-179">Jeśli Twoje <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody trwają długo, usługi mogą żądać więcej czasu, przez wywołanie metody [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) ponownie, używając zwiększona `dwCheckPoint` wartość.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-179">If your <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods run long, your service can request more time by calling [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) again with an incremented `dwCheckPoint` value.</span></span>  
  
<a name="BK_AddInstallers"></a>   
## <a name="adding-installers-to-the-service"></a><span data-ttu-id="e6a5a-180">Dodawanie instalatorów do usługi</span><span class="sxs-lookup"><span data-stu-id="e6a5a-180">Adding Installers to the Service</span></span>  
 <span data-ttu-id="e6a5a-181">Przed uruchomieniem usługi Windows, musisz zainstalować go, który rejestruje je z Menedżerem sterowania usługami.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-181">Before you can run a Windows Service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="e6a5a-182">Możesz dodać instalatory projektu, które obsługi szczegółów rejestracji.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-182">You can add installers to your project that handle the registration details.</span></span>  
  
#### <a name="to-create-the-installers-for-your-service"></a><span data-ttu-id="e6a5a-183">Aby utworzyć instalatory dla usługi</span><span class="sxs-lookup"><span data-stu-id="e6a5a-183">To create the installers for your service</span></span>  
  
1.  <span data-ttu-id="e6a5a-184">W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **MyNewService.cs** lub **MyNewService.vb**, a następnie wybierz **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-184">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>  
  
2.  <span data-ttu-id="e6a5a-185">Kliknij tło projektanta, aby zaznaczyć samą usługę, a nie jakąkolwiek jej zawartość.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-185">Click the background of the designer to select the service itself, instead of any of its contents.</span></span>  
  
3.  <span data-ttu-id="e6a5a-186">Otwórz menu kontekstowe okna Projektanta (Jeśli używasz urządzenia wskazującego, kliknij prawym przyciskiem myszy wewnątrz okna), a następnie wybierz **Dodaj Instalatora**.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-186">Open the context menu for the designer window (if you’re using a pointing device, right-click inside the window), and then choose **Add Installer**.</span></span>  
  
     <span data-ttu-id="e6a5a-187">Domyślnie do projektu zostanie dodana klasa składnika zawierająca dwa instalatory.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-187">By default, a component class that contains two installers is added to your project.</span></span> <span data-ttu-id="e6a5a-188">Składnik nazywa **ProjectInstaller**, zawiera pliki instalacyjne są Instalatora usługi i procesu skojarzonego Instalatora usługi.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-188">The component is named **ProjectInstaller**, and the installers it contains are the installer for your service and the installer for the service's associated process.</span></span>  
  
4.  <span data-ttu-id="e6a5a-189">W **projektowania** wyświetlić **ProjectInstaller**, wybierz **serviceInstaller1** dla projektu Visual C# lub **ServiceInstaller1** dla wizualizacji Podstawowy projekt.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-189">In **Design** view for **ProjectInstaller**, choose **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project.</span></span>  
  
5.  <span data-ttu-id="e6a5a-190">W **właściwości** okna, upewnij się, że <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość jest ustawiona na **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-190">In the **Properties** window, make sure the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>  
  
6.  <span data-ttu-id="e6a5a-191">Ustaw **opis** właściwość jakiś tekst, na przykład "Przykładowej usługi".</span><span class="sxs-lookup"><span data-stu-id="e6a5a-191">Set the **Description** property to some text, such as "A sample service".</span></span> <span data-ttu-id="e6a5a-192">Ten tekst pojawia się okno usługi i pomaga użytkownikom identyfikować usługi i zrozumieć, co to jest używany.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-192">This text appears in the Services window and helps the user identify the service and understand what it’s used for.</span></span>  
  
7.  <span data-ttu-id="e6a5a-193">Ustaw <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> właściwość tekst, który ma być wyświetlany w oknie usługi **nazwa** kolumny.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-193">Set the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property to the text that you want to appear in the Services window in the **Name** column.</span></span> <span data-ttu-id="e6a5a-194">Na przykład można wprowadzić "MyNewService Display Name".</span><span class="sxs-lookup"><span data-stu-id="e6a5a-194">For example, you can enter "MyNewService Display Name".</span></span> <span data-ttu-id="e6a5a-195">Ta nazwa może różnić się od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość, która jest to nazwa używana przez system (na przykład, kiedy używasz `net start` polecenie, aby uruchomić usługę).</span><span class="sxs-lookup"><span data-stu-id="e6a5a-195">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name used by the system (for example, when you use the `net start` command to start your service).</span></span>  
  
8.  <span data-ttu-id="e6a5a-196">Ustaw <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwość <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-196">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span></span>  
  
     <span data-ttu-id="e6a5a-197">![Właściwości Instalatora usługi Windows](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span><span class="sxs-lookup"><span data-stu-id="e6a5a-197">![Installer Properties for a Windows Service](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span></span>  
  
9. <span data-ttu-id="e6a5a-198">W projektancie, wybierz **serviceProcessInstaller1** dla projektu Visual C# lub **ServiceProcessInstaller1** dla projektów języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-198">In the designer, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project.</span></span> <span data-ttu-id="e6a5a-199">Ustaw <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> właściwość <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-199">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span></span> <span data-ttu-id="e6a5a-200">Spowoduje to zainstalowanie i uruchamianie usługi w kontekście konta usługi lokalnej.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-200">This will cause the service to be installed and to run on a local service account.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e6a5a-201"><xref:System.ServiceProcess.ServiceAccount.LocalSystem> Konto ma szerokie uprawnienia, w tym możliwość zapisu do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-201">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="e6a5a-202">Należy go używać ostrożnie, ponieważ może zwiększyć ryzyko ataku przez złośliwe oprogramowanie.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-202">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="e6a5a-203">W przypadku innych zadań, należy wziąć pod uwagę przy użyciu <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, które działa jako użytkownik bez uprawnień na komputerze lokalnym i przedstawia poświadczenia anonimowe każdemu zdalnemu serwerowi.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-203">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="e6a5a-204">W tym przykładzie zakończy się niepowodzeniem, jeśli zostanie podjęta próba użycia <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, ponieważ wymaga uprawnień do zapisu w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-204">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>  
  
     <span data-ttu-id="e6a5a-205">Aby uzyskać więcej informacji na temat instalatory zobacz [porady: Dodawanie instalatorów do aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="e6a5a-205">For more information about installers, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
<a name="BK_StartupParameters"></a>   
## <a name="set-startup-parameters"></a><span data-ttu-id="e6a5a-206">Ustaw parametry uruchamiania</span><span class="sxs-lookup"><span data-stu-id="e6a5a-206">Set Startup Parameters</span></span>  
 <span data-ttu-id="e6a5a-207">Do usług Windows, takich jak każdego innego pliku wykonywalnego, może akceptować argumentów wiersza polecenia lub parametry uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-207">A Windows Service, like any other executable, can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="e6a5a-208">Po dodaniu kodu z parametrami uruchamiania procesu użytkownicy mogą uruchamiać własne parametry niestandardowe uruchomienia usługi przy użyciu okna usługi w Panelu sterowania Windows.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-208">When you add code to process startup parameters, users can start your service with their own custom startup parameters by using the Services window in the Windows Control Panel.</span></span> <span data-ttu-id="e6a5a-209">Jednak te parametry uruchamiania nie są zachowywane podczas następnego uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-209">However, these startup parameters are not persisted the next time the service starts.</span></span> <span data-ttu-id="e6a5a-210">Aby ustawić parametry uruchamiania trwale, można ustawić je w rejestrze, jak pokazano w tej procedurze.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-210">To set startup parameters permanently, you can set them in the registry, as shown in this procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6a5a-211">Przed podjęciem decyzji o Dodaj parametry uruchamiania, należy wziąć pod uwagę niezależnie czy dotyczyć to najlepszy sposób przekazywania informacji do usługi.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-211">Before you decide to add startup parameters, consider whether that is the best way to pass information to your service.</span></span> <span data-ttu-id="e6a5a-212">Mimo, że parametry uruchamiania są łatwe w użyciu i do analizy, a użytkownicy mogą łatwo je zastąpić, może być trudne dla użytkowników do użytku bez dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-212">Although startup parameters are easy to use and to parse, and users can easily override them, they might be harder for users to discover and use without documentation.</span></span> <span data-ttu-id="e6a5a-213">Ogólnie rzecz biorąc Jeśli usługa wymaga więcej niż kilku Parametry uruchamiania, należy rozważyć użycie rejestru lub pliku konfiguracji zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-213">Generally, if your service requires more than just a few startup parameters, you should consider using the registry or a configuration file instead.</span></span> <span data-ttu-id="e6a5a-214">Każda usługa Windows ma wpis w rejestrze w obszarze klucza HKLM\System\CurrentControlSet\services.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-214">Every Windows Service has an entry in the registry under HKLM\System\CurrentControlSet\services.</span></span> <span data-ttu-id="e6a5a-215">W kluczu usługi można użyć **parametry** podklucz do przechowywania informacji, które mogą uzyskiwać dostęp do usługi.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-215">Under the service's key, you can use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="e6a5a-216">Można używać plików konfiguracji aplikacji dla usługi Windows taki sam sposób jak w przypadku innych programów.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-216">You can use application configuration files for a Windows Service the same way you do for other types of programs.</span></span> <span data-ttu-id="e6a5a-217">Przykładowy kod, zobacz <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-217">For example code, see <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span></span>  
  
#### <a name="adding-startup-parameters"></a><span data-ttu-id="e6a5a-218">Dodawanie parametrów do uruchomienia</span><span class="sxs-lookup"><span data-stu-id="e6a5a-218">Adding startup parameters</span></span>  
  
1.  <span data-ttu-id="e6a5a-219">W `Main` metody w pliku Program.cs lub MyNewService.Designer.vb, Dodaj argument w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-219">In the `Main` method in Program.cs or in MyNewService.Designer.vb, add an argument for the command line:</span></span>  
  
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
  
2.  <span data-ttu-id="e6a5a-220">Zmiana `MyNewService` konstruktora w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-220">Change the `MyNewService` constructor as follows:</span></span>  
  
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
  
<span data-ttu-id="e6a5a-221">Ten kod ustawia nazwę źródła i dziennik zdarzeń, zgodnie z Parametry uruchamiania podane lub używa wartości domyślnych, jeśli zostały dostarczone żadne argumenty.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-221">This code sets the event source and log name according to the supplied startup parameters, or uses default values if no arguments are supplied.</span></span>  
  
3. <span data-ttu-id="e6a5a-222">Aby określić argumenty wiersza polecenia, Dodaj następujący kod, aby `ProjectInstaller` klasy ProjectInstaller.cs lub ProjectInstaller.vb:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-222">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in ProjectInstaller.cs or ProjectInstaller.vb:</span></span>  
  
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
  
<span data-ttu-id="e6a5a-223">Ten kod modyfikuje **ImagePath** klucz rejestru zwykle zawiera pełną ścieżkę do pliku wykonywalnego dla usługi Windows poprzez dodanie wartości domyślne parametrów.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-223">This code modifies the **ImagePath** registry key, which typically contains the full path to the executable for the Windows Service, by adding the default parameter values.</span></span> <span data-ttu-id="e6a5a-224">Znaki cudzysłowu wokół ścieżki (i wokół każdego parametru poszczególnych) są wymagane dla usługi została prawidłowo uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-224">The quotation marks around the path (and around each individual parameter) are required for the service to start up correctly.</span></span> <span data-ttu-id="e6a5a-225">Aby zmienić parametry uruchamiania dla tej usługi Windows, użytkownicy mogą zmieniać parametrów podanych w **ImagePath** klucz rejestru, mimo że lepszy sposób jest programowe zmienianie i udostępniają funkcje dla użytkowników w przyjazne sposób (na przykład narzędzie do zarządzania lub konfiguracji).</span><span class="sxs-lookup"><span data-stu-id="e6a5a-225">To change the startup parameters for this Windows Service, users can change the parameters given in the **ImagePath** registry key, although the better way is to change it programmatically and expose the functionality to users in a friendly way (for example, in a management or configuration utility).</span></span>  
  
<a name="BK_Build"></a>   
## <a name="building-the-service"></a><span data-ttu-id="e6a5a-226">Tworzenie usługi</span><span class="sxs-lookup"><span data-stu-id="e6a5a-226">Building the Service</span></span>  
  
#### <a name="to-build-your-service-project"></a><span data-ttu-id="e6a5a-227">Aby skompilować projekt usługi</span><span class="sxs-lookup"><span data-stu-id="e6a5a-227">To build your service project</span></span>  
  
1.  <span data-ttu-id="e6a5a-228">W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla projektu, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-228">In **Solution Explorer**, open the context menu for your project, and then choose **Properties**.</span></span> <span data-ttu-id="e6a5a-229">Są wyświetlane na stronach właściwości projektu.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-229">The property pages for your project  appear.</span></span>  
  
2.  <span data-ttu-id="e6a5a-230">Na karcie aplikacja w **obiekt początkowy** wybierz **MyNewService.Program**.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-230">On the Application tab, in the **Startup object** list, choose **MyNewService.Program**.</span></span>  
  
3.  <span data-ttu-id="e6a5a-231">W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla projektu, a następnie wybierz **kompilacji** Aby skompilować projekt (klawiatura: Ctrl + Shift + B).</span><span class="sxs-lookup"><span data-stu-id="e6a5a-231">In **Solution Explorer**, open the context menu for your project, and then choose **Build** to build the project (Keyboard: Ctrl+Shift+B).</span></span>  
  
<a name="BK_Install"></a>   
## <a name="installing-the-service"></a><span data-ttu-id="e6a5a-232">Instalowanie usługi</span><span class="sxs-lookup"><span data-stu-id="e6a5a-232">Installing the Service</span></span>  
 <span data-ttu-id="e6a5a-233">Teraz, gdy masz utworzoną usługę Windows, należy ją zainstalować.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-233">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="e6a5a-234">Aby zainstalować usługę Windows, musisz mieć poświadczenia administracyjne na komputerze, na którym instalujesz go.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-234">To install a Windows service, you must have administrative credentials on the computer on which you're installing it.</span></span>  
  
#### <a name="to-install-a-windows-service"></a><span data-ttu-id="e6a5a-235">Aby zainstalować usługę Windows</span><span class="sxs-lookup"><span data-stu-id="e6a5a-235">To install a Windows Service</span></span>  
  
1.  <span data-ttu-id="e6a5a-236">Windows 7 i Windows Server otwórz **wiersz polecenia dla deweloperów** w obszarze **Visual Studio Tools** w **Start** menu.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-236">In Windows 7 and Windows Server, open the **Developer Command Prompt** under **Visual Studio Tools** in the **Start** menu.</span></span> <span data-ttu-id="e6a5a-237">W systemie Windows 8 lub Windows 8.1, wybierz **Visual Studio Tools** kafelków na **Start** ekranu, a następnie uruchom wiersz polecenia dla deweloperów przy użyciu poświadczeń administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-237">In Windows 8 or Windows 8.1, choose the **Visual Studio Tools** tile on the **Start** screen, and then run Developer Command Prompt with administrative credentials.</span></span> <span data-ttu-id="e6a5a-238">(Jeśli używasz myszy, kliknij prawym przyciskiem myszy **wiersz polecenia dla deweloperów**, a następnie wybierz **Uruchom jako Administrator**.)</span><span class="sxs-lookup"><span data-stu-id="e6a5a-238">(If you’re using a mouse, right-click on **Developer Command Prompt**, and then choose **Run as Administrator**.)</span></span>  
  
2.  <span data-ttu-id="e6a5a-239">W oknie wiersza polecenia przejdź do folderu, który zawiera dane wyjściowe projektu.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-239">In the Command Prompt window, navigate to the folder that contains your project's output.</span></span> <span data-ttu-id="e6a5a-240">Na przykład w folderze Moje dokumenty przejdź do folderu Visual Studio 2013\Projects\MyNewService\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-240">For example, under your My Documents folder, navigate to Visual Studio 2013\Projects\MyNewService\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="e6a5a-241">Wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-241">Enter the following command:</span></span>  
  
    ```  
    installutil.exe MyNewService.exe  
    ```  
  
     <span data-ttu-id="e6a5a-242">Jeśli usługa zostanie zainstalowana pomyślnie, narzędzie installutil.exe zakomunikuje sukces.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-242">If the service installs successfully, installutil.exe will report success.</span></span> <span data-ttu-id="e6a5a-243">Jeśli system nie znalazł InstallUtil.exe, upewnij się, który znajduje się na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-243">If the system could not find InstallUtil.exe, make sure that it exists on your computer.</span></span> <span data-ttu-id="e6a5a-244">To narzędzie jest instalowane z .NET Framework do folderu `%WINDIR%\Microsoft.NET\Framework[64]\` *framework_version*.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-244">This tool is installed with the .NET Framework to the folder `%WINDIR%\Microsoft.NET\Framework[64]\`*framework_version*.</span></span> <span data-ttu-id="e6a5a-245">Na przykład jest domyślna ścieżka dla 32-bitowej wersji programu .NET Framework 4, 4.5, 4.5.1 i 4.5.2 `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-245">For example, the default path for the 32-bit version of the .NET Framework 4, 4.5, 4.5.1, and 4.5.2 is `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span></span>  
  
     <span data-ttu-id="e6a5a-246">Jeśli proces installutil.exe zgłasza błąd, sprawdź dziennik instalacji, aby dowiedzieć się, dlaczego.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-246">If the installutil.exe process reports failure, check the install log to find out why.</span></span> <span data-ttu-id="e6a5a-247">Domyślnie dziennik jest w tym samym folderze co plik wykonywalny usługi.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-247">By default the log is in the same folder as the service executable.</span></span> <span data-ttu-id="e6a5a-248">Instalacja może zakończyć się niepowodzeniem, jeśli <xref:System.ComponentModel.RunInstallerAttribute> klasy nie znajduje się na `ProjectInstaller` klasy; w przeciwnym razie ten atrybut nie jest ustawiony na `true`, w przeciwnym razie `ProjectInstaller` klasa nie jest `public`.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-248">The installation can fail if  the <xref:System.ComponentModel.RunInstallerAttribute> Class is not present on the `ProjectInstaller` class, or else the attribute is not set to `true`, or else the `ProjectInstaller` class is not `public`.</span></span>  
  
     <span data-ttu-id="e6a5a-249">Aby uzyskać więcej informacji, zobacz [porady: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="e6a5a-249">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
<a name="BK_StartService"></a>   
## <a name="starting-and-running-the-service"></a><span data-ttu-id="e6a5a-250">Co spowoduje uruchomienie usługi</span><span class="sxs-lookup"><span data-stu-id="e6a5a-250">Starting and Running the Service</span></span>  
  
#### <a name="to-start-and-stop-your-service"></a><span data-ttu-id="e6a5a-251">Aby uruchomić i zatrzymać usługę</span><span class="sxs-lookup"><span data-stu-id="e6a5a-251">To start and stop your service</span></span>  
  
1.  <span data-ttu-id="e6a5a-252">Windows, otwórz **Start** ekranu lub **Start** menu i wpisz `services.msc`.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-252">In Windows, open the **Start** screen or **Start** menu, and type `services.msc`.</span></span>  
  
     <span data-ttu-id="e6a5a-253">Powinien zostać wyświetlony **MyNewService** na liście **usług** okna.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-253">You should now see **MyNewService** listed in the **Services** window.</span></span>  
  
     <span data-ttu-id="e6a5a-254">![MyNewService w oknie usług. ](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG "WindowsServices_ServicesWindow")</span><span class="sxs-lookup"><span data-stu-id="e6a5a-254">![MyNewService in the Services window.](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG "WindowsServices_ServicesWindow")</span></span>  
  
2.  <span data-ttu-id="e6a5a-255">W **usług** , otwórz menu skrótów dla usługi, a następnie wybierz **Start**.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-255">In the **Services** window, open the shortcut menu for your service, and then choose **Start**.</span></span>  
  
3.  <span data-ttu-id="e6a5a-256">Otwórz menu skrótów dla usługi, a następnie wybierz **zatrzymać**.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-256">Open the shortcut menu for the service, and then choose **Stop**.</span></span>  
  
4.  <span data-ttu-id="e6a5a-257">(Opcjonalnie) W wierszu polecenia można użyć poleceń `net start``ServiceName` i `net stop``ServiceName` uruchamianie i zatrzymywanie usługi.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-257">(Optional) From the command line, you can use the commands `net start``ServiceName` and `net stop``ServiceName` to start and stop your service.</span></span>  
  
#### <a name="to-verify-the-event-log-output-of-your-service"></a><span data-ttu-id="e6a5a-258">Aby zweryfikować informacje o efektach działania usługi znajdujące się w dzienniku zdarzeń</span><span class="sxs-lookup"><span data-stu-id="e6a5a-258">To verify the event log output of your service</span></span>  
  
1.  <span data-ttu-id="e6a5a-259">W programie Visual Studio, otwórz **Eksploratora serwera** (klawiatura: Ctrl + Alt + S) i uzyskiwać dostęp do **dzienniki zdarzeń** węzła na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-259">In Visual Studio, open **Server Explorer** (Keyboard: Ctrl+Alt+S), and access the **Event Logs** node for the local computer.</span></span>  
  
2.  <span data-ttu-id="e6a5a-260">Odszukaj **MyNewLog** (lub **MyLogFile1**, jeśli użyto procedury opcjonalnej można dodać argumenty wiersza polecenia) i rozwiń go.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-260">Locate the listing for **MyNewLog** (or **MyLogFile1**, if you used the optional procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="e6a5a-261">Powinny być widoczne wpisy dla dwie akcje (rozpoczęcie i zakończenie) przeprowadził usługi.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-261">You should see entries for the two actions (start and stop) your service has performed.</span></span>  
  
     <span data-ttu-id="e6a5a-262">![Aby wyświetlić wpisy dziennika zdarzeń można znaleźć w Podglądzie zdarzeń. ](../../../docs/framework/windows-services/media/windowsservices-eventviewer.PNG "WindowsServices_EventViewer")</span><span class="sxs-lookup"><span data-stu-id="e6a5a-262">![Use the Event Viewer to see the event log entries.](../../../docs/framework/windows-services/media/windowsservices-eventviewer.PNG "WindowsServices_EventViewer")</span></span>  
  
<a name="BK_Uninstall"></a>   
## <a name="uninstalling-a-windows-service"></a><span data-ttu-id="e6a5a-263">Odinstalowywanie usługi Windows</span><span class="sxs-lookup"><span data-stu-id="e6a5a-263">Uninstalling a Windows Service</span></span>  
  
#### <a name="to-uninstall-your-service"></a><span data-ttu-id="e6a5a-264">Aby odinstalować usługę</span><span class="sxs-lookup"><span data-stu-id="e6a5a-264">To uninstall your service</span></span>  
  
1.  <span data-ttu-id="e6a5a-265">Otwórz wiersz polecenia dla deweloperów przy użyciu poświadczeń administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-265">Open a developer command prompt with administrative credentials.</span></span>  
  
2.  <span data-ttu-id="e6a5a-266">W oknie wiersza polecenia przejdź do folderu, który zawiera dane wyjściowe projektu.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-266">In the Command Prompt window, navigate to the folder that contains your project's output.</span></span> <span data-ttu-id="e6a5a-267">Na przykład w folderze Moje dokumenty przejdź do folderu Visual Studio 2013\Projects\MyNewService\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-267">For example, under your My Documents folder, navigate to Visual Studio 2013\Projects\MyNewService\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="e6a5a-268">Wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="e6a5a-268">Enter the following command:</span></span>  
  
    ```  
    installutil.exe /u MyNewService.exe  
    ```  
  
     <span data-ttu-id="e6a5a-269">Jeśli usługa zostanie pomyślnie odinstalowana, narzędzie installutil.exe zakomunikuje jej usunięcie.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-269">If the service uninstalls successfully, installutil.exe will report that your service was successfully removed.</span></span> <span data-ttu-id="e6a5a-270">Aby uzyskać więcej informacji, zobacz [porady: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="e6a5a-270">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e6a5a-271">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e6a5a-271">Next Steps</span></span>  
 <span data-ttu-id="e6a5a-272">Można utworzyć program instalacyjny autonomicznego, który inne można użyć do zainstalowania usługi Windows, ale wymaga dodatkowych kroków.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-272">You can create a standalone setup program that others can use to install your Windows service, but it requires additional steps.</span></span> <span data-ttu-id="e6a5a-273">Funkcja ClickOnce nie obsługuje usług systemu Windows, dlatego nie można używać Kreatora publikacji.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-273">ClickOnce doesn't support Windows services, so you can't use the Publish Wizard.</span></span> <span data-ttu-id="e6a5a-274">Można używać pełnego wydania narzędzia InstallShield, którego nie dostarcza firma Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-274">You can use a full edition of InstallShield, which Microsoft doesn't provide.</span></span> <span data-ttu-id="e6a5a-275">Aby uzyskać więcej informacji o narzędziu InstallShield, zobacz [InstallShield Limited Edition](/visualstudio/deployment/installshield-limited-edition).</span><span class="sxs-lookup"><span data-stu-id="e6a5a-275">For more information about InstallShield, see [InstallShield Limited Edition](/visualstudio/deployment/installshield-limited-edition).</span></span> <span data-ttu-id="e6a5a-276">Można również użyć [zestaw narzędzi XML Instalatora Windows](https://go.microsoft.com/fwlink/?LinkId=249067) możliwość utworzenia Instalatora usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-276">You can also use the [Windows Installer XML Toolset](https://go.microsoft.com/fwlink/?LinkId=249067) to create an installer for a Windows service.</span></span>  
  
 <span data-ttu-id="e6a5a-277">Może zbadać użycie <xref:System.ServiceProcess.ServiceController> składnik, który umożliwia wysyłanie poleceń do zainstalowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-277">You might explore the use of a <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you have installed.</span></span>  
  
 <span data-ttu-id="e6a5a-278">Odpowiednio konfigurując instalatora, można spowodować generowanie dziennika zdarzeń podczas instalowania aplikacji, a nie jej działania.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-278">You can use an installer to create an event log when the application is installed instead of creating the event log when the application runs.</span></span> <span data-ttu-id="e6a5a-279">Ponadto z chwilą odinstalowania aplikacji dziennik zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-279">Additionally, the event log will be deleted by the installer when the application is uninstalled.</span></span> <span data-ttu-id="e6a5a-280">Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.EventLogInstaller> odwołania do stron.</span><span class="sxs-lookup"><span data-stu-id="e6a5a-280">For more information, see the <xref:System.Diagnostics.EventLogInstaller> reference page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6a5a-281">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e6a5a-281">See Also</span></span>  
 [<span data-ttu-id="e6a5a-282">Aplikacje usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e6a5a-282">Windows Service Applications</span></span>](../../../docs/framework/windows-services/index.md)  
 [<span data-ttu-id="e6a5a-283">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e6a5a-283">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="e6a5a-284">Instrukcje: debugowanie aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e6a5a-284">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="e6a5a-285">Usługi (Windows)</span><span class="sxs-lookup"><span data-stu-id="e6a5a-285">Services (Windows)</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)
