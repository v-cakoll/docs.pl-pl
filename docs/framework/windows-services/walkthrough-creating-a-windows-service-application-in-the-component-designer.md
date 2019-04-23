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
# <a name="tutorial-create-a-windows-service-app"></a><span data-ttu-id="42ec0-102">Samouczek: Tworzenie aplikacji usługi Windows</span><span class="sxs-lookup"><span data-stu-id="42ec0-102">Tutorial: Create a Windows service app</span></span>

<span data-ttu-id="42ec0-103">W tym artykule pokazano, jak utworzyć aplikację usługi Windows w programie Visual Studio, która wypisuje komunikaty w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="42ec0-103">This article demonstrates how to create a Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="42ec0-104">Tworzenie usługi</span><span class="sxs-lookup"><span data-stu-id="42ec0-104">Create a service</span></span>

<span data-ttu-id="42ec0-105">Aby rozpocząć, Utwórz projekt i ustaw wartości, które są niezbędne do poprawnego działania usługi.</span><span class="sxs-lookup"><span data-stu-id="42ec0-105">To begin, create the project and set the values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="42ec0-106">W programie Visual Studio **pliku** menu, wybierz opcję **New** > **projektu** (lub naciśnij **Ctrl** + **Shift**+**N**) aby otworzyć **nowy projekt** okna.</span><span class="sxs-lookup"><span data-stu-id="42ec0-106">From the Visual Studio **File** menu, select **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** window.</span></span>

2. <span data-ttu-id="42ec0-107">Przejdź do, a następnie wybierz pozycję **usługi Windows (.NET Framework)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="42ec0-107">Navigate to and select the **Windows Service (.NET Framework)** project template.</span></span> <span data-ttu-id="42ec0-108">Aby ją znaleźć, rozwiń węzeł **zainstalowane** i **Visual C#**  lub **języka Visual Basic**, a następnie wybierz **pulpitu Windows**.</span><span class="sxs-lookup"><span data-stu-id="42ec0-108">To find it, expand **Installed** and **Visual C#** or **Visual Basic**, then select **Windows Desktop**.</span></span> <span data-ttu-id="42ec0-109">Lub wprowadź *usługi Windows* w polu wyszukiwania w prawym górnym rogu, a następnie naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="42ec0-109">Or, enter *Windows Service* in the search box on the upper right and press **Enter**.</span></span>

   ![Szablon usługi Windows w oknie dialogowym Nowy projekt, w programie Visual Studio](media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="42ec0-111">Jeśli nie widzisz **usługi Windows** szablonu, użytkownik może być konieczne zainstalowanie **programowanie aplikacji klasycznych dla platformy .NET** obciążenia:</span><span class="sxs-lookup"><span data-stu-id="42ec0-111">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload:</span></span>
   >  
   > <span data-ttu-id="42ec0-112">W **nowy projekt** okno dialogowe, wybierz opcję **Otwórz Instalator programu Visual Studio** w lewym dolnym rogu.</span><span class="sxs-lookup"><span data-stu-id="42ec0-112">In the **New Project** dialog, select **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="42ec0-113">Wybierz **programowanie aplikacji klasycznych dla platformy .NET** obciążenia, a następnie wybierz **Modyfikuj**.</span><span class="sxs-lookup"><span data-stu-id="42ec0-113">Select the **.NET desktop development** workload, and then select **Modify**.</span></span>

3. <span data-ttu-id="42ec0-114">Aby uzyskać **nazwa**, wprowadź *MyNewService*, a następnie wybierz pozycję **OK**.</span><span class="sxs-lookup"><span data-stu-id="42ec0-114">For **Name**, enter *MyNewService*, and then select **OK**.</span></span>

   <span data-ttu-id="42ec0-115">**Projektowania** zostanie wyświetlona karta (**Service1.cs [projekt]** lub **Service1.vb [projekt]**).</span><span class="sxs-lookup"><span data-stu-id="42ec0-115">The **Design** tab appears (**Service1.cs [Design]** or **Service1.vb [Design]**).</span></span>
   
   <span data-ttu-id="42ec0-116">Szablon projektu zawiera klasę składnika o nazwie `Service1` tej, która dziedziczy <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="42ec0-116">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="42ec0-117">Zawiera ona większość podstawowego kodu usługi, takie jak kod, aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="42ec0-117">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="42ec0-118">Zmień nazwę usługi</span><span class="sxs-lookup"><span data-stu-id="42ec0-118">Rename the service</span></span>

<span data-ttu-id="42ec0-119">Zmień nazwę usługi z **Service1** do **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="42ec0-119">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="42ec0-120">W **Eksploratora rozwiązań**, wybierz opcję **Service1.cs**, lub **Service1.vb**i wybierz polecenie **Zmień nazwę** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="42ec0-120">In **Solution Explorer**, select **Service1.cs**, or **Service1.vb**, and choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="42ec0-121">Zmień nazwę pliku do **MyNewService.cs**, lub **MyNewService.vb**, a następnie naciśnij klawisz **Enter**</span><span class="sxs-lookup"><span data-stu-id="42ec0-121">Rename the file to **MyNewService.cs**, or **MyNewService.vb**, and then press **Enter**</span></span>

    <span data-ttu-id="42ec0-122">Okno wyskakujące pojawia się pytaniem, czy chcesz zmienić wszystkie odwołania do elementu kodu *Service1*.</span><span class="sxs-lookup"><span data-stu-id="42ec0-122">A pop-up window appears asking whether you would like to rename all references to the code element *Service1*.</span></span>

2. <span data-ttu-id="42ec0-123">W oknie podręcznym wybierz **tak**.</span><span class="sxs-lookup"><span data-stu-id="42ec0-123">In the pop-up window, select **Yes**.</span></span>

    <span data-ttu-id="42ec0-124">![Zmień nazwę wiersza](media/windows-service-rename.png "usługi Windows zmień nazwę wiersza")</span><span class="sxs-lookup"><span data-stu-id="42ec0-124">![Rename prompt](media/windows-service-rename.png "Windows service rename prompt")</span></span>

2. <span data-ttu-id="42ec0-125">W **projektowania** zaznacz **właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="42ec0-125">In the **Design** tab, select **Properties** from the shortcut menu.</span></span> <span data-ttu-id="42ec0-126">Z **właściwości** oknie zmiany **ServiceName** wartość *MyNewService*.</span><span class="sxs-lookup"><span data-stu-id="42ec0-126">From the **Properties** window, change the **ServiceName** value to *MyNewService*.</span></span>

    <span data-ttu-id="42ec0-127">![Właściwości usługi](media/windows-service-properties.png "właściwości usługi Windows")</span><span class="sxs-lookup"><span data-stu-id="42ec0-127">![Service properties](media/windows-service-properties.png "Windows service properties")</span></span>

3. <span data-ttu-id="42ec0-128">Wybierz **Zapisz wszystko** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="42ec0-128">Select **Save All** from the **File** menu.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="42ec0-129">Dodawanie funkcji do usługi</span><span class="sxs-lookup"><span data-stu-id="42ec0-129">Add features to the service</span></span>

<span data-ttu-id="42ec0-130">W tej sekcji dodasz niestandardowy dziennik zdarzeń do usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="42ec0-130">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="42ec0-131"><xref:System.Diagnostics.EventLog> Składnik jest przykładem typu składnika można dodać do usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="42ec0-131">The <xref:System.Diagnostics.EventLog> component is an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="42ec0-132">Dodać funkcjonalność niestandardowego dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="42ec0-132">Add custom event log functionality</span></span>

1. <span data-ttu-id="42ec0-133">W **Eksploratora rozwiązań**, z menu skrótów dla **MyNewService.cs**, lub **MyNewService.vb**, wybierz **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="42ec0-133">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="42ec0-134">W **przybornika**, rozwiń węzeł **składniki**, a następnie przeciągnij **dziennika zdarzeń** do **Service1.cs [projekt]**, lub  **Service1.VB [projekt]** kartę.</span><span class="sxs-lookup"><span data-stu-id="42ec0-134">In **Toolbox**, expand **Components**, and then drag the **EventLog** component to the **Service1.cs [Design]**, or **Service1.vb [Design]** tab.</span></span>

3. <span data-ttu-id="42ec0-135">W **Eksploratora rozwiązań**, z menu skrótów dla **MyNewService.cs**, lub **MyNewService.vb**, wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="42ec0-135">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Code**.</span></span>

4. <span data-ttu-id="42ec0-136">Zdefiniować niestandardowy dziennik zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="42ec0-136">Define a custom event log.</span></span> <span data-ttu-id="42ec0-137">Aby uzyskać C#, zmodyfikować istniejący `MyNewService()` Konstruktor; dla języka Visual Basic należy dodać `New()` konstruktora:</span><span class="sxs-lookup"><span data-stu-id="42ec0-137">For C#, edit the existing `MyNewService()` constructor; for Visual Basic, add the `New()` constructor:</span></span>

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. <span data-ttu-id="42ec0-138">Dodaj `using` instrukcję, aby **MyNewService.cs** (jeśli jeszcze nie istnieje), lub `Imports` instrukcji **MyNewService.vb**, dla <xref:System.Diagnostics?displayProperty=nameWithType> przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="42ec0-138">Add a `using` statement to **MyNewService.cs** (if it doesn't already exist), or an `Imports` statement **MyNewService.vb**, for the <xref:System.Diagnostics?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. <span data-ttu-id="42ec0-139">Wybierz **Zapisz wszystko** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="42ec0-139">Select **Save All** from the **File** menu.</span></span>

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="42ec0-140">Określić zachowanie występujące podczas uruchamiania usługi</span><span class="sxs-lookup"><span data-stu-id="42ec0-140">Define what occurs when the service starts</span></span>

<span data-ttu-id="42ec0-141">W edytorze kodu dla **MyNewService.cs** lub **MyNewService.vb**, zlokalizuj <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody. Podczas tworzenia projektu programu Visual Studio automatycznie tworzony definicję metody pusty.</span><span class="sxs-lookup"><span data-stu-id="42ec0-141">In the code editor for **MyNewService.cs** or **MyNewService.vb**, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method; Visual Studio automatically created an empty method definition when you created the project.</span></span> <span data-ttu-id="42ec0-142">Dodaj kod, który zapisuje wpis dziennika zdarzeń, podczas uruchamiania usługi:</span><span class="sxs-lookup"><span data-stu-id="42ec0-142">Add code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a><span data-ttu-id="42ec0-143">Sondowanie</span><span class="sxs-lookup"><span data-stu-id="42ec0-143">Polling</span></span>

<span data-ttu-id="42ec0-144">Ponieważ aplikacja usługi została zaprojektowana jako długotrwałych, zazwyczaj sonduje lub monitoruje system, który został skonfigurowany w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="42ec0-144">Because a service application is designed to be long-running, it usually polls or monitors the system, which you set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="42ec0-145">`OnStart` Metoda musi powrócić do systemu operacyjnego, po rozpoczęciu operacji usługi, tak aby system nie jest zablokowany.</span><span class="sxs-lookup"><span data-stu-id="42ec0-145">The `OnStart` method must return to the operating system after the service's operation has begun so that the system isn't blocked.</span></span> 

<span data-ttu-id="42ec0-146">Aby skonfigurować prosty mechanizm sondowania, użyj <xref:System.Timers.Timer?displayProperty=nameWithType> składnika.</span><span class="sxs-lookup"><span data-stu-id="42ec0-146">To set up a simple polling mechanism, use the <xref:System.Timers.Timer?displayProperty=nameWithType> component.</span></span> <span data-ttu-id="42ec0-147">Wywołuje czasomierza <xref:System.Timers.Timer.Elapsed> zdarzeń w regularnych odstępach czasu, co Twoja usługa mogła wykonać jego monitorowanie.</span><span class="sxs-lookup"><span data-stu-id="42ec0-147">The timer raises an <xref:System.Timers.Timer.Elapsed> event at regular intervals, at which time your service can do its monitoring.</span></span> <span data-ttu-id="42ec0-148">Możesz użyć <xref:System.Timers.Timer> składnika w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="42ec0-148">You use the <xref:System.Timers.Timer> component as follows:</span></span>

- <span data-ttu-id="42ec0-149">Ustawianie właściwości <xref:System.Timers.Timer> składnika w `MyNewService.OnStart` metody.</span><span class="sxs-lookup"><span data-stu-id="42ec0-149">Set the properties of the <xref:System.Timers.Timer> component in the `MyNewService.OnStart` method.</span></span>
- <span data-ttu-id="42ec0-150">Uruchomienia czasomierza, wywołując <xref:System.Timers.Timer.Start%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="42ec0-150">Start the timer by calling the <xref:System.Timers.Timer.Start%2A> method.</span></span>

##### <a name="set-up-the-polling-mechanism"></a><span data-ttu-id="42ec0-151">Konfigurowanie mechanizmu sondowania.</span><span class="sxs-lookup"><span data-stu-id="42ec0-151">Set up the polling mechanism.</span></span>

1. <span data-ttu-id="42ec0-152">Dodaj następujący kod w `MyNewService.OnStart` zdarzenie, aby ustawić mechanizm sondowania:</span><span class="sxs-lookup"><span data-stu-id="42ec0-152">Add the following code in the `MyNewService.OnStart` event to set up the polling mechanism:</span></span>

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

2. <span data-ttu-id="42ec0-153">Dodaj `using` instrukcję, aby **MyNewService.cs**, lub `Imports` instrukcję, aby **MyNewService.vb**, aby uzyskać <xref:System.Timers?displayProperty=nameWithType> przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="42ec0-153">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Timers?displayProperty=nameWithType> namespace:</span></span>

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. <span data-ttu-id="42ec0-154">W `MyNewService` klasy, Dodaj `OnTimer` metody, aby obsłużyć <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="42ec0-154">In the `MyNewService` class, add the `OnTimer` method to handle the <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> event:</span></span>

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

4. <span data-ttu-id="42ec0-155">W `MyNewService` klasy, Dodaj zmienną składową.</span><span class="sxs-lookup"><span data-stu-id="42ec0-155">In the `MyNewService` class, add a member variable.</span></span> <span data-ttu-id="42ec0-156">Zawiera identyfikator następne zdarzenie do zapisu do dziennika zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="42ec0-156">It contains the identifier of the next event to write into the event log:</span></span>

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

<span data-ttu-id="42ec0-157">Zamiast uruchamiać swoją pracę w wątku głównym, można uruchamiać zadania za pomocą wątków w tle proces roboczy.</span><span class="sxs-lookup"><span data-stu-id="42ec0-157">Instead of running all your work on the main thread, you can run tasks by using background worker threads.</span></span> <span data-ttu-id="42ec0-158">Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="42ec0-158">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="42ec0-159">Określić zachowanie występujące podczas zatrzymywania usługi</span><span class="sxs-lookup"><span data-stu-id="42ec0-159">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="42ec0-160">Wstaw wiersz kodu w <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metodę, która dodaje wpis w dzienniku zdarzeń, gdy usługa zostanie zatrzymana:</span><span class="sxs-lookup"><span data-stu-id="42ec0-160">Insert a line of code in the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="42ec0-161">Zdefiniuj inne akcje usługi</span><span class="sxs-lookup"><span data-stu-id="42ec0-161">Define other actions for the service</span></span>

<span data-ttu-id="42ec0-162">Można zastąpić <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, i <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> metody, aby zdefiniować dodatkowe przetwarzanie składnika.</span><span class="sxs-lookup"><span data-stu-id="42ec0-162">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span> 

<span data-ttu-id="42ec0-163">Poniższy kod przedstawia sposób na zastąpienie <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method in Class metoda `MyNewService` klasy:</span><span class="sxs-lookup"><span data-stu-id="42ec0-163">The following code shows how you to override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method in the `MyNewService` class:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a><span data-ttu-id="42ec0-164">Ustaw stan usługi</span><span class="sxs-lookup"><span data-stu-id="42ec0-164">Set service status</span></span>

<span data-ttu-id="42ec0-165">Usługi raportowania ich stanu do [Menedżera sterowania usługami](/windows/desktop/Services/service-control-manager) , dzięki czemu użytkownik może stwierdzić, czy usługa działa poprawnie.</span><span class="sxs-lookup"><span data-stu-id="42ec0-165">Services report their status to the [Service Control Manager](/windows/desktop/Services/service-control-manager) so that a user can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="42ec0-166">Domyślnie usługa tej, która dziedziczy <xref:System.ServiceProcess.ServiceBase> ograniczony zestaw stan ustawienia, które obejmują SERVICE_STOPPED, SERVICE_PAUSED i SERVICE_RUNNING raportów.</span><span class="sxs-lookup"><span data-stu-id="42ec0-166">By default, a service that inherits from <xref:System.ServiceProcess.ServiceBase> reports a limited set of status settings, which include SERVICE_STOPPED, SERVICE_PAUSED, and SERVICE_RUNNING.</span></span> <span data-ttu-id="42ec0-167">Jeśli usługa może trochę mogła się uruchomić, jest przydatne do raportowania stanu SERVICE_START_PENDING.</span><span class="sxs-lookup"><span data-stu-id="42ec0-167">If a service takes a while to start up, it's useful to report a SERVICE_START_PENDING status.</span></span> 

<span data-ttu-id="42ec0-168">Ustawienia stanu SERVICE_START_PENDING i SERVICE_STOP_PENDING można zaimplementować, dodając kod, który wywołuje Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) funkcji.</span><span class="sxs-lookup"><span data-stu-id="42ec0-168">You can implement the SERVICE_START_PENDING and SERVICE_STOP_PENDING status settings by adding code that calls the Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function.</span></span>

### <a name="implement-service-pending-status"></a><span data-ttu-id="42ec0-169">Implementowanie usługi w stanie oczekiwania</span><span class="sxs-lookup"><span data-stu-id="42ec0-169">Implement service pending status</span></span>

1. <span data-ttu-id="42ec0-170">Dodaj `using` instrukcję, aby **MyNewService.cs**, lub `Imports` instrukcję, aby **MyNewService.vb**, aby uzyskać <xref:System.Runtime.InteropServices?displayProperty=nameWithType> przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="42ec0-170">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="42ec0-171">Dodaj następujący kod do **MyNewService.cs**, lub **MyNewService.vb**, aby zadeklarować `ServiceState` wartości i można dodać struktury stanu, która będzie używana na platformie wywołania wywołania:</span><span class="sxs-lookup"><span data-stu-id="42ec0-171">Add the following code to **MyNewService.cs**, or **MyNewService.vb**, to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

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
    > <span data-ttu-id="42ec0-172">Korzysta z Menedżera sterowania usługami `dwWaitHint` i `dwCheckpoint` członkowie [struktury SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status) określić ilość czasu oczekiwania dla usługi Windows uruchomić lub zamknąć.</span><span class="sxs-lookup"><span data-stu-id="42ec0-172">The Service Control Manager uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/desktop/api/winsvc/ns-winsvc-_service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="42ec0-173">Jeśli Twoje `OnStart` i `OnStop` metody trwają długo, usługi mogą żądać więcej czasu, przez wywołanie metody `SetServiceStatus` ponownie, używając zwiększona `dwCheckPoint` wartość.</span><span class="sxs-lookup"><span data-stu-id="42ec0-173">If your `OnStart` and `OnStop` methods run long, your service can request more time by calling `SetServiceStatus` again with an incremented `dwCheckPoint` value.</span></span>

3. <span data-ttu-id="42ec0-174">W `MyNewService` klasy, Zadeklaruj [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) funkcji przy użyciu [wywołania platformy](../interop/consuming-unmanaged-dll-functions.md):</span><span class="sxs-lookup"><span data-stu-id="42ec0-174">In the `MyNewService` class, declare the [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="42ec0-175">Aby zaimplementować stan SERVICE_START_PENDING, Dodaj następujący kod na początku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="42ec0-175">To implement the SERVICE_START_PENDING status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

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

5. <span data-ttu-id="42ec0-176">Dodaj kod na końcu `OnStart` metodę, aby ustawić stan na SERVICE_RUNNING:</span><span class="sxs-lookup"><span data-stu-id="42ec0-176">Add code to the end of the `OnStart` method to set the status to SERVICE_RUNNING:</span></span>

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

6. <span data-ttu-id="42ec0-177">(Opcjonalnie) Jeśli <xref:System.ServiceProcess.ServiceBase.OnStop%2A> jest metoda długotrwałych, powtórz tę procedurę w `OnStop` metody.</span><span class="sxs-lookup"><span data-stu-id="42ec0-177">(Optional) If <xref:System.ServiceProcess.ServiceBase.OnStop%2A> is a long-running method, repeat this procedure in the `OnStop` method.</span></span> <span data-ttu-id="42ec0-178">Implementowanie stan SERVICE_STOP_PENDING i zwrócony stan SERVICE_STOPPED przed `OnStop` wyjścia metody.</span><span class="sxs-lookup"><span data-stu-id="42ec0-178">Implement the SERVICE_STOP_PENDING status and return the SERVICE_STOPPED status before the `OnStop` method exits.</span></span>

   <span data-ttu-id="42ec0-179">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="42ec0-179">For example:</span></span>

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

## <a name="add-installers-to-the-service"></a><span data-ttu-id="42ec0-180">Dodawanie instalatorów do usługi</span><span class="sxs-lookup"><span data-stu-id="42ec0-180">Add installers to the service</span></span>

<span data-ttu-id="42ec0-181">Przed uruchomieniem usługi Windows, musisz zainstalować go, który rejestruje je z Menedżerem sterowania usługami.</span><span class="sxs-lookup"><span data-stu-id="42ec0-181">Before you run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="42ec0-182">Dodawanie instalatorów do projektu w celu obsługi szczegółów rejestracji.</span><span class="sxs-lookup"><span data-stu-id="42ec0-182">Add installers to your project to handle the registration details.</span></span>

1. <span data-ttu-id="42ec0-183">W **Eksploratora rozwiązań**, z menu skrótów dla **MyNewService.cs**, lub **MyNewService.vb**, wybierz **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="42ec0-183">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="42ec0-184">W **projektowania** wyświetlić, wybierz obszar tła, a następnie wybierz **Dodaj Instalatora** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="42ec0-184">In the **Design** view, select the background area, then choose **Add Installer** from the shortcut menu.</span></span>

     <span data-ttu-id="42ec0-185">Domyślnie program Visual Studio dodana Klasa składnika o nazwie `ProjectInstaller`, który zawiera dwa pliki instalacyjne do projektu.</span><span class="sxs-lookup"><span data-stu-id="42ec0-185">By default, Visual Studio adds a component class named `ProjectInstaller`, which contains two installers, to your project.</span></span> <span data-ttu-id="42ec0-186">Te instalatory są usługi i procesu skojarzonego z usługi.</span><span class="sxs-lookup"><span data-stu-id="42ec0-186">These installers are for your service and for the service's associated process.</span></span>

4. <span data-ttu-id="42ec0-187">W **projektowania** wyświetlić **ProjectInstaller**, wybierz opcję **serviceInstaller1** dla wizualizacji C# projektu, lub **ServiceInstaller1**projektu języka Visual Basic, następnie wybierz **właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="42ec0-187">In the **Design** view for **ProjectInstaller**, select **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span>

5. <span data-ttu-id="42ec0-188">W **właściwości** oknie Sprawdź <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość jest ustawiona na **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="42ec0-188">In the **Properties** window, verify the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

6. <span data-ttu-id="42ec0-189">Dodawanie tekstu do <xref:System.ServiceProcess.ServiceInstaller.Description%2A> właściwości, takie jak *usługi przykładowe*.</span><span class="sxs-lookup"><span data-stu-id="42ec0-189">Add text to the <xref:System.ServiceProcess.ServiceInstaller.Description%2A> property, such as *A sample service*.</span></span> 

     <span data-ttu-id="42ec0-190">Ten tekst jest wyświetlany w **opis** kolumny **usług** okna i zawiera opis usługi dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="42ec0-190">This text appears in the **Description** column of the **Services** window and describes the service to the user.</span></span>

    <span data-ttu-id="42ec0-191">![Opis usługi, w oknie usług. ](media/windows-service-description.png "Opis usługi")</span><span class="sxs-lookup"><span data-stu-id="42ec0-191">![Service description in the Services window.](media/windows-service-description.png "Service description")</span></span>

7. <span data-ttu-id="42ec0-192">Dodawanie tekstu do <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="42ec0-192">Add text to the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property.</span></span> <span data-ttu-id="42ec0-193">Na przykład *nazwę wyświetlaną MyNewService*.</span><span class="sxs-lookup"><span data-stu-id="42ec0-193">For example, *MyNewService Display Name*.</span></span> 

     <span data-ttu-id="42ec0-194">Ten tekst jest wyświetlany w **nazwę wyświetlaną** kolumny **usług** okna.</span><span class="sxs-lookup"><span data-stu-id="42ec0-194">This text appears in the **Display Name** column of the **Services** window.</span></span> <span data-ttu-id="42ec0-195">Ta nazwa może różnić się od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość, która jest nazwą, wówczas system używa (na przykład nazwy można użyć dla `net start` polecenie, aby uruchomić usługę).</span><span class="sxs-lookup"><span data-stu-id="42ec0-195">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name the system uses (for example, the name you use for the `net start` command to start your service).</span></span>

8. <span data-ttu-id="42ec0-196">Ustaw <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwość <xref:System.ServiceProcess.ServiceStartMode.Automatic> z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="42ec0-196">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic> from the drop-down list.</span></span>

9. <span data-ttu-id="42ec0-197">Gdy skończysz, **właściwości** windows powinno wyglądać podobnie do poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="42ec0-197">When you're finished, the **Properties** windows should look like the following figure:</span></span>

     <span data-ttu-id="42ec0-198">![Właściwości Instalatora usługi Windows](media/windows-service-installer-properties.png "właściwości Instalatora usługi Windows")</span><span class="sxs-lookup"><span data-stu-id="42ec0-198">![Installer Properties for a Windows service](media/windows-service-installer-properties.png "Windows service installer properties")</span></span>

9. <span data-ttu-id="42ec0-199">W **projektowania** wyświetlić **ProjectInstaller**, wybierz **serviceProcessInstaller1** dla wizualizacji C# projektu, lub **ServiceProcessInstaller1**  projektu języka Visual Basic, następnie wybierz **właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="42ec0-199">In the **Design** view for **ProjectInstaller**, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span> <span data-ttu-id="42ec0-200">Ustaw <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> właściwość <xref:System.ServiceProcess.ServiceAccount.LocalSystem> z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="42ec0-200">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem> from the drop-down list.</span></span> 

     <span data-ttu-id="42ec0-201">To ustawienie instaluje usługę i uruchamia je przy użyciu konta systemu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="42ec0-201">This setting installs the service and runs it by using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="42ec0-202"><xref:System.ServiceProcess.ServiceAccount.LocalSystem> Konto ma szerokie uprawnienia, w tym możliwość zapisu do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="42ec0-202">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="42ec0-203">Należy go używać ostrożnie, ponieważ może zwiększyć ryzyko ataku przez złośliwe oprogramowanie.</span><span class="sxs-lookup"><span data-stu-id="42ec0-203">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="42ec0-204">W przypadku innych zadań, należy wziąć pod uwagę przy użyciu <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, które działa jako użytkownik bez uprawnień na komputerze lokalnym i przedstawia poświadczenia anonimowe każdemu zdalnemu serwerowi.</span><span class="sxs-lookup"><span data-stu-id="42ec0-204">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="42ec0-205">W tym przykładzie zakończy się niepowodzeniem, jeśli zostanie podjęta próba użycia <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, ponieważ wymaga uprawnień do zapisu w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="42ec0-205">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="42ec0-206">Aby uzyskać więcej informacji na temat instalatory zobacz [jak: Dodawanie instalatorów od aplikacji usług](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="42ec0-206">For more information about installers, see [How to: Add installers to your service application](how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="42ec0-207">(Opcjonalnie) Ustaw parametry uruchamiania</span><span class="sxs-lookup"><span data-stu-id="42ec0-207">(Optional) Set startup parameters</span></span>

> [!NOTE]
> <span data-ttu-id="42ec0-208">Przed podjęciem decyzji o Dodaj parametry uruchamiania, należy rozważyć, czy jest najlepszym sposobem przekazywania informacji do usługi.</span><span class="sxs-lookup"><span data-stu-id="42ec0-208">Before you decide to add startup parameters, consider whether it's the best way to pass information to your service.</span></span> <span data-ttu-id="42ec0-209">Mimo że są one łatwe w użyciu i analizy, a użytkownik może łatwo je zastąpić, może być trudniejsze dla użytkownika do użytku bez dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="42ec0-209">Although they're easy to use and parse, and a user can easily override them, they might be harder for a user to discover and use without documentation.</span></span> <span data-ttu-id="42ec0-210">Ogólnie rzecz biorąc Jeśli usługa wymaga więcej niż kilku Parametry uruchamiania, należy użyć rejestru lub pliku konfiguracji zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="42ec0-210">Generally, if your service requires more than just a few startup parameters, you should use the registry or a configuration file instead.</span></span> 

<span data-ttu-id="42ec0-211">Usługa Windows może akceptować argumentów wiersza polecenia lub parametry uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="42ec0-211">A Windows service can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="42ec0-212">Po dodaniu kodu z parametrami uruchomienia procesu, użytkownik może uruchomić usługi za pomocą ich własnych parametrów startowy niestandardowe w oknie dialogowym właściwości usługi.</span><span class="sxs-lookup"><span data-stu-id="42ec0-212">When you add code to process startup parameters, a user can start your service with their own custom startup parameters in the service properties window.</span></span> <span data-ttu-id="42ec0-213">Jednak te parametry uruchamiania nie są zachowywane podczas następnego uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="42ec0-213">However, these startup parameters aren't persisted the next time the service starts.</span></span> <span data-ttu-id="42ec0-214">Aby ustawić parametry uruchamiania trwale, należy ustawić je w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="42ec0-214">To set startup parameters permanently, set them in the registry.</span></span>

<span data-ttu-id="42ec0-215">Każda usługa Windows ma wpis rejestru, w obszarze **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** podklucza.</span><span class="sxs-lookup"><span data-stu-id="42ec0-215">Each Windows service has a registry entry under the **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** subkey.</span></span> <span data-ttu-id="42ec0-216">W podkluczu każdej z tych usług użyj **parametry** podklucz do przechowywania informacji, które mogą uzyskiwać dostęp do usługi.</span><span class="sxs-lookup"><span data-stu-id="42ec0-216">Under each service's subkey, use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="42ec0-217">Może używać plików konfiguracji aplikacji dla usługi Windows w taki sam sposób jak w przypadku innych programów.</span><span class="sxs-lookup"><span data-stu-id="42ec0-217">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="42ec0-218">Przykładowy kod, zobacz <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="42ec0-218">For sample code, see <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span></span>

### <a name="to-add-startup-parameters"></a><span data-ttu-id="42ec0-219">Aby dodać parametry uruchamiania</span><span class="sxs-lookup"><span data-stu-id="42ec0-219">To add startup parameters</span></span>

1. <span data-ttu-id="42ec0-220">Wybierz **Program.cs**, lub **MyNewService.Designer.vb**, następnie wybierz **Wyświetl kod** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="42ec0-220">Select **Program.cs**, or **MyNewService.Designer.vb**, then choose **View Code** from the shortcut menu.</span></span> <span data-ttu-id="42ec0-221">W `Main` metodę, Zmień kod, aby dodać parametr wejściowy i przekaż go do konstruktora usługi:</span><span class="sxs-lookup"><span data-stu-id="42ec0-221">In the `Main` method, change the code to add an input parameter and pass it to the service constructor:</span></span>

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. <span data-ttu-id="42ec0-222">W **MyNewService.cs**, lub **MyNewService.vb**, zmień `MyNewService` konstruktora, aby przetworzyć parametr wejściowy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="42ec0-222">In **MyNewService.cs**, or **MyNewService.vb**, change the `MyNewService` constructor to process the input parameter as follows:</span></span>

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

   <span data-ttu-id="42ec0-223">Ten kod ustawia nazwę źródła i dziennik zdarzeń, zgodnie z Parametry uruchamiania, które użytkownik podaje.</span><span class="sxs-lookup"><span data-stu-id="42ec0-223">This code sets the event source and log name according to the startup parameters that the user supplies.</span></span> <span data-ttu-id="42ec0-224">Jeśli zostały dostarczone żadne argumenty, używa domyślnych wartości.</span><span class="sxs-lookup"><span data-stu-id="42ec0-224">If no arguments are supplied, it uses default values.</span></span>

3. <span data-ttu-id="42ec0-225">Aby określić argumenty wiersza polecenia, Dodaj następujący kod do `ProjectInstaller` klasy w **ProjectInstaller.cs**, lub **ProjectInstaller.vb**:</span><span class="sxs-lookup"><span data-stu-id="42ec0-225">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in **ProjectInstaller.cs**, or **ProjectInstaller.vb**:</span></span>

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

   <span data-ttu-id="42ec0-226">Zazwyczaj ta wartość zawiera pełną ścieżkę do pliku wykonywalnego dla usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="42ec0-226">Typically, this value contains the full path to the executable for the Windows service.</span></span> <span data-ttu-id="42ec0-227">Dla usługi została prawidłowo uruchomiona że użytkownik musi podać znaki cudzysłowu dla ścieżki i wszystkich poszczególnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="42ec0-227">For the service to start up correctly, the user must supply quotation marks for the path and each individual parameter.</span></span> <span data-ttu-id="42ec0-228">Użytkownik może zmienić parametry w **ImagePath** wpis rejestru, aby zmienić parametry uruchamiania usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="42ec0-228">A user can change the parameters in the **ImagePath** registry entry to change the startup parameters for the Windows service.</span></span> <span data-ttu-id="42ec0-229">Jednak lepszy sposób jest programowe Zmienianie wartości i udostępniają funkcje w sposób, przyjazny dla użytkownika, takie jak za pomocą narzędzia zarządzania lub konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="42ec0-229">However, a better way is to change the value programmatically and expose the functionality in a user-friendly way, such as by using a management or configuration utility.</span></span>

## <a name="build-the-service"></a><span data-ttu-id="42ec0-230">Tworzenie usługi</span><span class="sxs-lookup"><span data-stu-id="42ec0-230">Build the service</span></span>

1. <span data-ttu-id="42ec0-231">W **Eksploratora rozwiązań**, wybierz **właściwości** z menu skrótów dla **MyNewService** projektu.</span><span class="sxs-lookup"><span data-stu-id="42ec0-231">In **Solution Explorer**, choose **Properties** from the shortcut menu for the **MyNewService** project.</span></span>

   <span data-ttu-id="42ec0-232">Są wyświetlane na stronach właściwości projektu.</span><span class="sxs-lookup"><span data-stu-id="42ec0-232">The property pages for your project appear.</span></span>

2. <span data-ttu-id="42ec0-233">Na **aplikacji** na karcie **obiekt początkowy** wybierz **MyNewService.Program**, lub **Sub Main** dla projektów języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="42ec0-233">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**, or **Sub Main** for Visual Basic projects.</span></span>

3. <span data-ttu-id="42ec0-234">Aby skompilować projekt, w **Eksploratora rozwiązań**, wybierz **kompilacji** z menu skrótów dla projektu (lub naciśnij **Ctrl**+**Shift** + **B**).</span><span class="sxs-lookup"><span data-stu-id="42ec0-234">To build the project, in **Solution Explorer**, choose **Build** from the shortcut menu for your project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="42ec0-235">Instalowanie usługi</span><span class="sxs-lookup"><span data-stu-id="42ec0-235">Install the service</span></span>

<span data-ttu-id="42ec0-236">Teraz, gdy masz utworzoną usługę Windows, należy ją zainstalować.</span><span class="sxs-lookup"><span data-stu-id="42ec0-236">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="42ec0-237">Aby zainstalować usługę Windows, musi mieć poświadczenia administratora na komputerze, na którym jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="42ec0-237">To install a Windows service, you must have administrator credentials on the computer where it's installed.</span></span>

1. <span data-ttu-id="42ec0-238">Otwórz [wiersz polecenia programisty dla programu Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) przy użyciu poświadczeń administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="42ec0-238">Open [Developer Command Prompt for Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) with administrative credentials.</span></span> <span data-ttu-id="42ec0-239">Od Windows **Start** menu, wybierz opcję **wiersz polecenia programisty dla programu VS 2017** w folderze programu Visual Studio, a następnie zaznacz **więcej** > **Uruchom jako Administrator** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="42ec0-239">From the Windows **Start** menu, select **Developer Command Prompt for VS 2017** in the Visual Studio folder, then select **More** > **Run as Administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="42ec0-240">W **wiersz polecenia programisty dla programu Visual Studio** okna, przejdź do folderu, który zawiera dane wyjściowe projektu (domyślnie *\bin\Debug* podkatalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="42ec0-240">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output (by default, the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="42ec0-241">Wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="42ec0-241">Enter the following command:</span></span>

    ```shell
    installutil MyNewService.exe
    ```

    <span data-ttu-id="42ec0-242">Jeśli usługa zostanie zainstalowana pomyślnie, polecenie zgłosi powodzenie operacji.</span><span class="sxs-lookup"><span data-stu-id="42ec0-242">If the service installs successfully, the command reports success.</span></span> 

    <span data-ttu-id="42ec0-243">Jeśli system nie może znaleźć *installutil.exe*, upewnij się, że istnieje na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="42ec0-243">If the system can't find *installutil.exe*, make sure that it exists on your computer.</span></span> <span data-ttu-id="42ec0-244">To narzędzie jest instalowane z .NET Framework do folderu *% windir%\Microsoft.NET\Framework[64]\\&lt;framework w wersji&gt;*.</span><span class="sxs-lookup"><span data-stu-id="42ec0-244">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\&lt;framework version&gt;*.</span></span> <span data-ttu-id="42ec0-245">Na przykład jest domyślna ścieżka dla 64-bitowej wersji *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="42ec0-245">For example, the default path for the 64-bit version is *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="42ec0-246">Jeśli **installutil.exe** przetwarzania zakończy się niepowodzeniem, sprawdź dziennik instalacji, aby dowiedzieć się, dlaczego.</span><span class="sxs-lookup"><span data-stu-id="42ec0-246">If the **installutil.exe** process fails, check the install log to find out why.</span></span> <span data-ttu-id="42ec0-247">Domyślnie dziennik jest w tym samym folderze co pliku wykonywalnego usługi.</span><span class="sxs-lookup"><span data-stu-id="42ec0-247">By default, the log is in the same folder as the service executable.</span></span> <span data-ttu-id="42ec0-248">Instalacja może zakończyć się niepowodzeniem, jeśli:</span><span class="sxs-lookup"><span data-stu-id="42ec0-248">The installation can fail if:</span></span> 
    - <span data-ttu-id="42ec0-249"><xref:System.ComponentModel.RunInstallerAttribute> Klasy nie znajduje się w `ProjectInstaller` klasy.</span><span class="sxs-lookup"><span data-stu-id="42ec0-249">The <xref:System.ComponentModel.RunInstallerAttribute> class isn't present on the `ProjectInstaller` class.</span></span>
    -  <span data-ttu-id="42ec0-250">Atrybut nie jest ustawiony na `true`.</span><span class="sxs-lookup"><span data-stu-id="42ec0-250">The attribute isn't set to `true`.</span></span> 
    - <span data-ttu-id="42ec0-251">`ProjectInstaller` Klasa nie jest zdefiniowana jako `public`.</span><span class="sxs-lookup"><span data-stu-id="42ec0-251">The `ProjectInstaller` class isn't defined as `public`.</span></span>

<span data-ttu-id="42ec0-252">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie usług](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="42ec0-252">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="42ec0-253">Uruchom program i uruchom usługę</span><span class="sxs-lookup"><span data-stu-id="42ec0-253">Start and run the service</span></span>

1. <span data-ttu-id="42ec0-254">Windows, otwórz **usług** aplikacji klasycznej.</span><span class="sxs-lookup"><span data-stu-id="42ec0-254">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="42ec0-255">Naciśnij klawisz **Windows**+**R** otworzyć **Uruchom** wprowadź *services.msc*, a następnie naciśnij klawisz **Enter** lub wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="42ec0-255">Press **Windows**+**R** to open the **Run** box, enter *services.msc*, and then press **Enter** or select **OK**.</span></span>

     <span data-ttu-id="42ec0-256">Powinien zostać wyświetlony na liście usługi **usług**, wyświetlane alfabetycznie według nazwy wyświetlanej, ustaw dla niego.</span><span class="sxs-lookup"><span data-stu-id="42ec0-256">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![MyNewService w oknie usług.](media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="42ec0-258">Aby uruchomić usługę, wybierz opcję **Start** z menu skrótów usługi.</span><span class="sxs-lookup"><span data-stu-id="42ec0-258">To start the service, choose **Start** from the service's shortcut menu.</span></span>

3. <span data-ttu-id="42ec0-259">Aby zatrzymać usługę, wybierz opcję **zatrzymać** z menu skrótów usługi.</span><span class="sxs-lookup"><span data-stu-id="42ec0-259">To stop the service, choose **Stop** from the service's shortcut menu.</span></span>

4. <span data-ttu-id="42ec0-260">(Opcjonalnie) W wierszu polecenia należy użyć poleceń **net start &lt;nazwa usługi&gt;**  i **net stop &lt;nazwa usługi&gt;**  uruchamianie i zatrzymywanie usługi.</span><span class="sxs-lookup"><span data-stu-id="42ec0-260">(Optional) From the command line, use the commands **net start &lt;service name&gt;** and **net stop &lt;service name&gt;** to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="42ec0-261">Sprawdź dane wyjściowe dziennika zdarzeń, usługi</span><span class="sxs-lookup"><span data-stu-id="42ec0-261">Verify the event log output of your service</span></span>

1. <span data-ttu-id="42ec0-262">Windows, otwórz **Podgląd zdarzeń** aplikacji klasycznej.</span><span class="sxs-lookup"><span data-stu-id="42ec0-262">In Windows, open the **Event Viewer** desktop app.</span></span> <span data-ttu-id="42ec0-263">Wprowadź *Podgląd zdarzeń* w wyszukiwaniu Windows paska, a następnie wybierz pozycję **Podgląd zdarzeń** w wynikach wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="42ec0-263">Enter *Event Viewer* in the Windows search bar, and then select **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="42ec0-264">W programie Visual Studio są dostępne dzienniki zdarzeń, otwierając **Eksploratora serwera** z **widoku** menu (lub naciśnij **Ctrl**+**Alt** + **S**) i rozwijając **dzienniki zdarzeń** węzła na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="42ec0-264">In Visual Studio, you can access event logs by opening **Server Explorer** from the **View** menu (or press **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="42ec0-265">W **Podgląd zdarzeń**, rozwiń węzeł **Dzienniki aplikacji i usług**.</span><span class="sxs-lookup"><span data-stu-id="42ec0-265">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="42ec0-266">Odszukaj **MyNewLog** (lub **MyLogFile1** po wykonaniu procedury, aby dodać argumenty wiersza polecenia) i rozwiń go.</span><span class="sxs-lookup"><span data-stu-id="42ec0-266">Locate the listing for **MyNewLog** (or **MyLogFile1** if you followed the procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="42ec0-267">Powinny być widoczne wpisy dwie akcje (rozpoczęcie i zakończenie), wykonanych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="42ec0-267">You should see the entries for the two actions (start and stop) that your service performed.</span></span>

     ![Użyj podglądu zdarzeń, aby wyświetlić wpisy dziennika zdarzeń](media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a><span data-ttu-id="42ec0-269">Oczyszczanie zasobów</span><span class="sxs-lookup"><span data-stu-id="42ec0-269">Clean up resources</span></span>

<span data-ttu-id="42ec0-270">Jeśli nie potrzebujesz już Windows service app, możesz go usunąć.</span><span class="sxs-lookup"><span data-stu-id="42ec0-270">If you no longer need the Windows service app, you can remove it.</span></span> 

1. <span data-ttu-id="42ec0-271">Otwórz **wiersz polecenia programisty dla programu Visual Studio** przy użyciu poświadczeń administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="42ec0-271">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="42ec0-272">W **wiersz polecenia programisty dla programu Visual Studio** okna, przejdź do folderu, który zawiera dane wyjściowe projektu.</span><span class="sxs-lookup"><span data-stu-id="42ec0-272">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="42ec0-273">Wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="42ec0-273">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="42ec0-274">Jeśli usługa zostanie pomyślnie odinstalowana polecenia Raporty z usługą został pomyślnie usunięty.</span><span class="sxs-lookup"><span data-stu-id="42ec0-274">If the service uninstalls successfully, the command reports that your service was successfully removed.</span></span> <span data-ttu-id="42ec0-275">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie usług](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="42ec0-275">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="42ec0-276">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="42ec0-276">Next steps</span></span>

<span data-ttu-id="42ec0-277">Teraz, po utworzeniu usługi, możesz wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="42ec0-277">Now that you've created the service, you can:</span></span>

- <span data-ttu-id="42ec0-278">Utwórz autonomiczny program instalacyjny dla innych użytkowników, aby zainstalować usługę Windows.</span><span class="sxs-lookup"><span data-stu-id="42ec0-278">Create a standalone setup program for others to use to install your Windows service.</span></span> <span data-ttu-id="42ec0-279">Użyj [zestaw narzędzi WiX](http://wixtoolset.org/) możliwość utworzenia Instalatora usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="42ec0-279">Use the [WiX Toolset](http://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="42ec0-280">Zapoznać się z pomysłami z innymi zobacz [Utwórz pakiet instalacyjny](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="42ec0-280">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

- <span data-ttu-id="42ec0-281">Zapoznaj się z <xref:System.ServiceProcess.ServiceController> składnik, który umożliwia wysyłanie poleceń do usługi, po zainstalowaniu.</span><span class="sxs-lookup"><span data-stu-id="42ec0-281">Explore the <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

- <span data-ttu-id="42ec0-282">Zamiast tworzenia dziennika zdarzeń, gdy aplikacja zostanie uruchomiona, należy użyć Instalatora do tworzenia dziennika zdarzeń podczas instalowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42ec0-282">Instead of creating the event log when the application runs, use an installer to create an event log when you install the application.</span></span> <span data-ttu-id="42ec0-283">Dziennik zdarzeń jest usunięte przez Instalatora po odinstalowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42ec0-283">The event log is deleted by the installer when you uninstall the application.</span></span> <span data-ttu-id="42ec0-284">Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.EventLogInstaller>.</span><span class="sxs-lookup"><span data-stu-id="42ec0-284">For more information, see <xref:System.Diagnostics.EventLogInstaller>.</span></span>

## <a name="see-also"></a><span data-ttu-id="42ec0-285">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42ec0-285">See also</span></span>

- [<span data-ttu-id="42ec0-286">Aplikacje usług Windows</span><span class="sxs-lookup"><span data-stu-id="42ec0-286">Windows service applications</span></span>](index.md)
- [<span data-ttu-id="42ec0-287">Wprowadzenie do aplikacji usług Windows</span><span class="sxs-lookup"><span data-stu-id="42ec0-287">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="42ec0-288">Instrukcje: Debugowanie aplikacji usług Windows</span><span class="sxs-lookup"><span data-stu-id="42ec0-288">How to: Debug Windows service applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="42ec0-289">Usługi (Windows)</span><span class="sxs-lookup"><span data-stu-id="42ec0-289">Services (Windows)</span></span>](/windows/desktop/Services/services)
