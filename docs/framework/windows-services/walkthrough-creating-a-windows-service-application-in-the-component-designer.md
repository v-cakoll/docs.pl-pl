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
# <a name="tutorial-create-a-windows-service-app"></a><span data-ttu-id="2c5c8-102">Samouczek: Tworzenie aplikacji usługi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2c5c8-102">Tutorial: Create a Windows service app</span></span>

<span data-ttu-id="2c5c8-103">W tym artykule pokazano, jak utworzyć aplikację usługi systemu Windows w programie Visual Studio, która zapisuje komunikaty w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-103">This article demonstrates how to create a Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="2c5c8-104">Tworzenie usługi</span><span class="sxs-lookup"><span data-stu-id="2c5c8-104">Create a service</span></span>

<span data-ttu-id="2c5c8-105">Aby rozpocząć, Utwórz projekt i ustaw wartości, które są wymagane do poprawnego działania usługi.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-105">To begin, create the project and set the values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="2c5c8-106">Z menu **plik** programu Visual Studio wybierz pozycję **Nowy** > **projekt** (lub naciśnij **klawisze CTRL**+**SHIFT**+**N**), aby otworzyć okno **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="2c5c8-106">From the Visual Studio **File** menu, select **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** window.</span></span>

2. <span data-ttu-id="2c5c8-107">Przejdź do i wybierz szablon projektu **usługi systemu Windows (.NET Framework)** .</span><span class="sxs-lookup"><span data-stu-id="2c5c8-107">Navigate to and select the **Windows Service (.NET Framework)** project template.</span></span> <span data-ttu-id="2c5c8-108">Aby go znaleźć, rozwiń węzeł **zainstalowane** i **Wizualizacja C#**  lub **Visual Basic**, a następnie wybierz pozycję **Windows Desktop**.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-108">To find it, expand **Installed** and **Visual C#** or **Visual Basic**, then select **Windows Desktop**.</span></span> <span data-ttu-id="2c5c8-109">Lub wprowadź *usługę systemu Windows* w polu wyszukiwania w prawym górnym rogu, a następnie naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-109">Or, enter *Windows Service* in the search box on the upper right and press **Enter**.</span></span>

   ![Szablon usługi systemu Windows w oknie dialogowym Nowy projekt w programie Visual Studio](media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="2c5c8-111">Jeśli szablon **usługi systemu Windows** nie jest widoczny, może być konieczne zainstalowanie obciążeń **programistycznych programu .NET Desktop** :</span><span class="sxs-lookup"><span data-stu-id="2c5c8-111">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload:</span></span>
   >
   > <span data-ttu-id="2c5c8-112">W oknie dialogowym **Nowy projekt** wybierz pozycję **Otwórz Instalator programu Visual Studio** w lewym dolnym rogu.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-112">In the **New Project** dialog, select **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="2c5c8-113">Wybierz obciążenie **Programowanie aplikacji klasycznych platformy .NET** , a następnie wybierz pozycję **Modyfikuj**.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-113">Select the **.NET desktop development** workload, and then select **Modify**.</span></span>

3. <span data-ttu-id="2c5c8-114">W obszarze **Nazwa**wpisz *MyNewService*, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-114">For **Name**, enter *MyNewService*, and then select **OK**.</span></span>

   <span data-ttu-id="2c5c8-115">Zostanie wyświetlona karta **projektowanie** (**Service1.cs [projekt]** lub **Service1. vb [projekt]** ).</span><span class="sxs-lookup"><span data-stu-id="2c5c8-115">The **Design** tab appears (**Service1.cs [Design]** or **Service1.vb [Design]**).</span></span>

   <span data-ttu-id="2c5c8-116">Szablon projektu zawiera klasę składnika o nazwie `Service1` , która dziedziczy z. <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2c5c8-116">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2c5c8-117">Zawiera on wiele podstawowych kodów usług, takich jak kod do uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-117">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="2c5c8-118">Zmień nazwę usługi</span><span class="sxs-lookup"><span data-stu-id="2c5c8-118">Rename the service</span></span>

<span data-ttu-id="2c5c8-119">Zmień nazwę usługi z **Service1** na **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-119">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="2c5c8-120">W **Eksplorator rozwiązań**wybierz pozycję **Service1.cs**lub **Service1. vb**i wybierz polecenie **Zmień nazwę** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-120">In **Solution Explorer**, select **Service1.cs**, or **Service1.vb**, and choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="2c5c8-121">Zmień nazwę pliku na **MyNewService.cs**lub **MyNewService. vb**, a następnie naciśnij klawisz **Enter** .</span><span class="sxs-lookup"><span data-stu-id="2c5c8-121">Rename the file to **MyNewService.cs**, or **MyNewService.vb**, and then press **Enter**</span></span>

    <span data-ttu-id="2c5c8-122">Zostanie wyświetlone okno podręczne z pytaniem, czy chcesz zmienić nazwy wszystkich odwołań do elementu kodu *Service1*.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-122">A pop-up window appears asking whether you would like to rename all references to the code element *Service1*.</span></span>

2. <span data-ttu-id="2c5c8-123">W oknie podręcznym wybierz pozycję **tak**.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-123">In the pop-up window, select **Yes**.</span></span>

    <span data-ttu-id="2c5c8-124">![Zmień nazwę monitu](media/windows-service-rename.png "Monit o zmianę nazwy usługi systemu Windows")</span><span class="sxs-lookup"><span data-stu-id="2c5c8-124">![Rename prompt](media/windows-service-rename.png "Windows service rename prompt")</span></span>

3. <span data-ttu-id="2c5c8-125">Na karcie **projektowanie** wybierz pozycję **Właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-125">In the **Design** tab, select **Properties** from the shortcut menu.</span></span> <span data-ttu-id="2c5c8-126">W oknie **Właściwości** Zmień wartość właściwości **ServiceName** na *MyNewService*.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-126">From the **Properties** window, change the **ServiceName** value to *MyNewService*.</span></span>

    <span data-ttu-id="2c5c8-127">![Właściwości usługi](media/windows-service-properties.png "Właściwości usługi systemu Windows")</span><span class="sxs-lookup"><span data-stu-id="2c5c8-127">![Service properties](media/windows-service-properties.png "Windows service properties")</span></span>

4. <span data-ttu-id="2c5c8-128">Wybierz pozycję **Zapisz wszystko** w menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="2c5c8-128">Select **Save All** from the **File** menu.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="2c5c8-129">Dodawanie funkcji do usługi</span><span class="sxs-lookup"><span data-stu-id="2c5c8-129">Add features to the service</span></span>

<span data-ttu-id="2c5c8-130">W tej sekcji dodasz niestandardowy dziennik zdarzeń do usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-130">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="2c5c8-131"><xref:System.Diagnostics.EventLog> Składnik jest przykładem typu składnika, który można dodać do usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-131">The <xref:System.Diagnostics.EventLog> component is an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="2c5c8-132">Dodaj niestandardową funkcję dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="2c5c8-132">Add custom event log functionality</span></span>

1. <span data-ttu-id="2c5c8-133">W **Eksplorator rozwiązań**z menu skrótów dla **MyNewService.cs**lub **MyNewService. vb**wybierz polecenie **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-133">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="2c5c8-134">W **przyborniku**rozwiń węzeł **składniki**, a następnie przeciągnij składnik **EventLog** do karty **Service1.cs [Design]** lub **Service1. vb [Design]** .</span><span class="sxs-lookup"><span data-stu-id="2c5c8-134">In **Toolbox**, expand **Components**, and then drag the **EventLog** component to the **Service1.cs [Design]**, or **Service1.vb [Design]** tab.</span></span>

3. <span data-ttu-id="2c5c8-135">W **Eksplorator rozwiązań**z menu skrótów dla **MyNewService.cs**lub **MyNewService. vb**wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-135">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Code**.</span></span>

4. <span data-ttu-id="2c5c8-136">Zdefiniuj niestandardowy dziennik zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-136">Define a custom event log.</span></span> <span data-ttu-id="2c5c8-137">W C#przypadku, Edytuj istniejący `MyNewService()` Konstruktor; dla `New()` Visual Basic Dodaj Konstruktor:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-137">For C#, edit the existing `MyNewService()` constructor; for Visual Basic, add the `New()` constructor:</span></span>

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. <span data-ttu-id="2c5c8-138">`Imports` <xref:System.Diagnostics?displayProperty=nameWithType>Dodaj instrukcję do MyNewService.cs (jeśli jeszcze nie istnieje) lub instrukcji MyNewService. vb dla przestrzeni nazw: `using`</span><span class="sxs-lookup"><span data-stu-id="2c5c8-138">Add a `using` statement to **MyNewService.cs** (if it doesn't already exist), or an `Imports` statement **MyNewService.vb**, for the <xref:System.Diagnostics?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. <span data-ttu-id="2c5c8-139">Wybierz pozycję **Zapisz wszystko** w menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="2c5c8-139">Select **Save All** from the **File** menu.</span></span>

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="2c5c8-140">Zdefiniuj, co ma miejsce w przypadku uruchomienia usługi</span><span class="sxs-lookup"><span data-stu-id="2c5c8-140">Define what occurs when the service starts</span></span>

<span data-ttu-id="2c5c8-141">W edytorze kodu dla **MyNewService.cs** lub **MyNewService. vb**Znajdź <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodę; Program Visual Studio automatycznie utworzył pustą definicję metody podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-141">In the code editor for **MyNewService.cs** or **MyNewService.vb**, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method; Visual Studio automatically created an empty method definition when you created the project.</span></span> <span data-ttu-id="2c5c8-142">Dodaj kod, który zapisuje wpis w dzienniku zdarzeń po uruchomieniu usługi:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-142">Add code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a><span data-ttu-id="2c5c8-143">Sondowania</span><span class="sxs-lookup"><span data-stu-id="2c5c8-143">Polling</span></span>

<span data-ttu-id="2c5c8-144">Ponieważ aplikacja usługi jest zaprojektowana tak, aby była długotrwała, zwykle sonduje lub monitoruje system, który został skonfigurowany w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodzie.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-144">Because a service application is designed to be long-running, it usually polls or monitors the system, which you set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="2c5c8-145">`OnStart` Metoda musi powrócić do systemu operacyjnego po rozpoczęciu operacji usługi, aby system nie został zablokowany.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-145">The `OnStart` method must return to the operating system after the service's operation has begun so that the system isn't blocked.</span></span>

<span data-ttu-id="2c5c8-146">Aby skonfigurować prosty mechanizm sondowania, użyj <xref:System.Timers.Timer?displayProperty=nameWithType> składnika.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-146">To set up a simple polling mechanism, use the <xref:System.Timers.Timer?displayProperty=nameWithType> component.</span></span> <span data-ttu-id="2c5c8-147">Czasomierz zgłasza <xref:System.Timers.Timer.Elapsed> zdarzenie w regularnych odstępach czasu, w którym usługa może przeprowadzić monitorowanie.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-147">The timer raises an <xref:System.Timers.Timer.Elapsed> event at regular intervals, at which time your service can do its monitoring.</span></span> <span data-ttu-id="2c5c8-148"><xref:System.Timers.Timer> Składnik jest używany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-148">You use the <xref:System.Timers.Timer> component as follows:</span></span>

- <span data-ttu-id="2c5c8-149">Ustaw właściwości <xref:System.Timers.Timer> składnika `MyNewService.OnStart` w metodzie.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-149">Set the properties of the <xref:System.Timers.Timer> component in the `MyNewService.OnStart` method.</span></span>
- <span data-ttu-id="2c5c8-150">Uruchom czasomierz, wywołując <xref:System.Timers.Timer.Start%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-150">Start the timer by calling the <xref:System.Timers.Timer.Start%2A> method.</span></span>

##### <a name="set-up-the-polling-mechanism"></a><span data-ttu-id="2c5c8-151">Skonfiguruj mechanizm sondowania.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-151">Set up the polling mechanism.</span></span>

1. <span data-ttu-id="2c5c8-152">Dodaj następujący kod w `MyNewService.OnStart` zdarzeniu, aby skonfigurować mechanizm sondowania:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-152">Add the following code in the `MyNewService.OnStart` event to set up the polling mechanism:</span></span>

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

2. <span data-ttu-id="2c5c8-153">`Imports` Dodajinstrukcjędo<xref:System.Timers?displayProperty=nameWithType> MyNewService.cs lub instrukcję do **MyNewService. vb**dla przestrzeni nazw: `using`</span><span class="sxs-lookup"><span data-stu-id="2c5c8-153">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Timers?displayProperty=nameWithType> namespace:</span></span>

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. <span data-ttu-id="2c5c8-154">W klasie Dodaj metodę, aby obsłużyć <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> zdarzenie: `OnTimer` `MyNewService`</span><span class="sxs-lookup"><span data-stu-id="2c5c8-154">In the `MyNewService` class, add the `OnTimer` method to handle the <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> event:</span></span>

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

4. <span data-ttu-id="2c5c8-155">`MyNewService` W klasie Dodaj zmienną członkowską.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-155">In the `MyNewService` class, add a member variable.</span></span> <span data-ttu-id="2c5c8-156">Zawiera identyfikator następnego zdarzenia do zapisu w dzienniku zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-156">It contains the identifier of the next event to write into the event log:</span></span>

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

<span data-ttu-id="2c5c8-157">Zamiast uruchamiać wszystkie prace w głównym wątku, można uruchamiać zadania przy użyciu wątków roboczych w tle.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-157">Instead of running all your work on the main thread, you can run tasks by using background worker threads.</span></span> <span data-ttu-id="2c5c8-158">Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-158">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="2c5c8-159">Określ, co ma miejsce w przypadku zatrzymania usługi</span><span class="sxs-lookup"><span data-stu-id="2c5c8-159">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="2c5c8-160">Wstaw wiersz kodu w <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metodzie, która dodaje wpis do dziennika zdarzeń po zatrzymaniu usługi:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-160">Insert a line of code in the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="2c5c8-161">Zdefiniuj inne akcje dla usługi</span><span class="sxs-lookup"><span data-stu-id="2c5c8-161">Define other actions for the service</span></span>

<span data-ttu-id="2c5c8-162">Można zastąpić <xref:System.ServiceProcess.ServiceBase.OnPause%2A>metody, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>i <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> , aby zdefiniować dodatkowe przetwarzanie dla składnika.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-162">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span>

<span data-ttu-id="2c5c8-163">Poniższy kod pokazuje, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> jak zastąpić metodę `MyNewService` w klasie:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-163">The following code shows how you to override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method in the `MyNewService` class:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a><span data-ttu-id="2c5c8-164">Ustawianie stanu usługi</span><span class="sxs-lookup"><span data-stu-id="2c5c8-164">Set service status</span></span>

<span data-ttu-id="2c5c8-165">Usługi raportują swój stan do [Menedżera kontroli usług](/windows/desktop/Services/service-control-manager) , aby użytkownik mógł stwierdzić, czy usługa działa poprawnie.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-165">Services report their status to the [Service Control Manager](/windows/desktop/Services/service-control-manager) so that a user can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="2c5c8-166">Domyślnie usługa, która dziedziczy z <xref:System.ServiceProcess.ServiceBase> raportów, zawiera ograniczony zestaw ustawień stanu, takich jak SERVICE_STOPPED, SERVICE_PAUSED i SERVICE_RUNNING.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-166">By default, a service that inherits from <xref:System.ServiceProcess.ServiceBase> reports a limited set of status settings, which include SERVICE_STOPPED, SERVICE_PAUSED, and SERVICE_RUNNING.</span></span> <span data-ttu-id="2c5c8-167">Jeśli uruchomienie usługi trwa dłużej, warto zgłosić status SERVICE_START_PENDING.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-167">If a service takes a while to start up, it's useful to report a SERVICE_START_PENDING status.</span></span>

<span data-ttu-id="2c5c8-168">Ustawienia stanu SERVICE_START_PENDING i SERVICE_STOP_PENDING można zaimplementować, dodając kod, który wywołuje funkcję [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-168">You can implement the SERVICE_START_PENDING and SERVICE_STOP_PENDING status settings by adding code that calls the Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function.</span></span>

### <a name="implement-service-pending-status"></a><span data-ttu-id="2c5c8-169">Zaimplementuj stan oczekiwania usługi</span><span class="sxs-lookup"><span data-stu-id="2c5c8-169">Implement service pending status</span></span>

1. <span data-ttu-id="2c5c8-170">`Imports` Dodajinstrukcjędo<xref:System.Runtime.InteropServices?displayProperty=nameWithType> MyNewService.cs lub instrukcję do **MyNewService. vb**dla przestrzeni nazw: `using`</span><span class="sxs-lookup"><span data-stu-id="2c5c8-170">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="2c5c8-171">Dodaj następujący kod do **MyNewService.cs**lub **MyNewService. vb**, `ServiceState` aby zadeklarować wartości i dodać strukturę dla stanu, który będzie używany w wywołaniu wywołania platformy:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-171">Add the following code to **MyNewService.cs**, or **MyNewService.vb**, to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

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
    > <span data-ttu-id="2c5c8-172">Menedżer sterowania usługami używa `dwWaitHint` i `dwCheckpoint` składowych [struktury SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) , aby określić czas oczekiwania na uruchomienie lub wyłączenie usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-172">The Service Control Manager uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/win32/api/winsvc/ns-winsvc-service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="2c5c8-173">Jeśli metody `OnStop` `dwCheckPoint` i są wykonywane długo, usługa może zażądać więcej czasu, wywołując `SetServiceStatus` ponownie z wartością przyrostową. `OnStart`</span><span class="sxs-lookup"><span data-stu-id="2c5c8-173">If your `OnStart` and `OnStop` methods run long, your service can request more time by calling `SetServiceStatus` again with an incremented `dwCheckPoint` value.</span></span>

3. <span data-ttu-id="2c5c8-174">W klasie deklaruj funkcję [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) przy użyciu [wywołania platformy:](../interop/consuming-unmanaged-dll-functions.md) `MyNewService`</span><span class="sxs-lookup"><span data-stu-id="2c5c8-174">In the `MyNewService` class, declare the [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="2c5c8-175">Aby zaimplementować stan SERVICE_START_PENDING, Dodaj następujący kod na początku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-175">To implement the SERVICE_START_PENDING status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

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

5. <span data-ttu-id="2c5c8-176">Dodaj kod na końcu `OnStart` metody, aby ustawić stan na SERVICE_RUNNING:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-176">Add code to the end of the `OnStart` method to set the status to SERVICE_RUNNING:</span></span>

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

6. <span data-ttu-id="2c5c8-177">Obowiązkowe Jeśli <xref:System.ServiceProcess.ServiceBase.OnStop%2A> jest metodą długotrwałą, powtórz tę procedurę `OnStop` w metodzie.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-177">(Optional) If <xref:System.ServiceProcess.ServiceBase.OnStop%2A> is a long-running method, repeat this procedure in the `OnStop` method.</span></span> <span data-ttu-id="2c5c8-178">Zaimplementuj stan SERVICE_STOP_PENDING i zwróć stan SERVICE_STOPPED przed wyjściem `OnStop` z metody.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-178">Implement the SERVICE_STOP_PENDING status and return the SERVICE_STOPPED status before the `OnStop` method exits.</span></span>

   <span data-ttu-id="2c5c8-179">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-179">For example:</span></span>

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

## <a name="add-installers-to-the-service"></a><span data-ttu-id="2c5c8-180">Dodawanie instalatorów do usługi</span><span class="sxs-lookup"><span data-stu-id="2c5c8-180">Add installers to the service</span></span>

<span data-ttu-id="2c5c8-181">Przed uruchomieniem usługi systemu Windows należy ją zainstalować, co spowoduje zarejestrowanie jej w Menedżerze kontroli usług.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-181">Before you run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="2c5c8-182">Dodaj Instalatory do projektu, aby obsłużyć szczegóły rejestracji.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-182">Add installers to your project to handle the registration details.</span></span>

1. <span data-ttu-id="2c5c8-183">W **Eksplorator rozwiązań**z menu skrótów dla **MyNewService.cs**lub **MyNewService. vb**wybierz polecenie **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-183">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="2c5c8-184">W widoku **projekt** wybierz obszar tła, a następnie wybierz polecenie **Dodaj Instalatora** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-184">In the **Design** view, select the background area, then choose **Add Installer** from the shortcut menu.</span></span>

     <span data-ttu-id="2c5c8-185">Domyślnie program Visual Studio dodaje klasę składnika o nazwie `ProjectInstaller`, która zawiera dwóch instalatorów do projektu.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-185">By default, Visual Studio adds a component class named `ProjectInstaller`, which contains two installers, to your project.</span></span> <span data-ttu-id="2c5c8-186">Te Instalatory są przeznaczone dla usługi i dla procesu związanego z usługą.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-186">These installers are for your service and for the service's associated process.</span></span>

3. <span data-ttu-id="2c5c8-187">W widoku **projekt** dla **ProjectInstaller**wybierz pozycję **serviceInstaller1** dla projektu wizualnego C# lub **serviceInstaller1** dla projektu Visual Basic, a następnie wybierz **Właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-187">In the **Design** view for **ProjectInstaller**, select **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="2c5c8-188">W oknie **Właściwości** Sprawdź, czy <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość jest ustawiona na **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-188">In the **Properties** window, verify the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

5. <span data-ttu-id="2c5c8-189">Dodaj tekst do <xref:System.ServiceProcess.ServiceInstaller.Description%2A> właściwości, takiej jak *Przykładowa usługa*.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-189">Add text to the <xref:System.ServiceProcess.ServiceInstaller.Description%2A> property, such as *A sample service*.</span></span>

     <span data-ttu-id="2c5c8-190">Ten tekst jest wyświetlany w kolumnie **Opis** okna **usługi** i zawiera opis usługi dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-190">This text appears in the **Description** column of the **Services** window and describes the service to the user.</span></span>

    <span data-ttu-id="2c5c8-191">![Opis usługi w oknie usługi.](media/windows-service-description.png "Opis usługi")</span><span class="sxs-lookup"><span data-stu-id="2c5c8-191">![Service description in the Services window.](media/windows-service-description.png "Service description")</span></span>

6. <span data-ttu-id="2c5c8-192">Dodaj tekst do <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-192">Add text to the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property.</span></span> <span data-ttu-id="2c5c8-193">Na przykład *MyNewService nazwa wyświetlana*.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-193">For example, *MyNewService Display Name*.</span></span>

     <span data-ttu-id="2c5c8-194">Ten tekst jest wyświetlany w kolumnie **Nazwa wyświetlana** okna **usługi** .</span><span class="sxs-lookup"><span data-stu-id="2c5c8-194">This text appears in the **Display Name** column of the **Services** window.</span></span> <span data-ttu-id="2c5c8-195">Ta nazwa może się różnić od <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwości, która jest nazwą używaną przez system (na przykład nazwę używaną `net start` przez polecenie w celu uruchomienia usługi).</span><span class="sxs-lookup"><span data-stu-id="2c5c8-195">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name the system uses (for example, the name you use for the `net start` command to start your service).</span></span>

7. <span data-ttu-id="2c5c8-196">Ustaw właściwość na <xref:System.ServiceProcess.ServiceStartMode.Automatic> wartość z listy rozwijanej. <xref:System.ServiceProcess.ServiceInstaller.StartType%2A></span><span class="sxs-lookup"><span data-stu-id="2c5c8-196">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic> from the drop-down list.</span></span>

8. <span data-ttu-id="2c5c8-197">Po zakończeniu okna **Właściwości** powinny wyglądać tak, jak na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-197">When you're finished, the **Properties** windows should look like the following figure:</span></span>

     <span data-ttu-id="2c5c8-198">![Właściwości Instalatora dla usługi systemu Windows](media/windows-service-installer-properties.png "Właściwości Instalatora usługi systemu Windows")</span><span class="sxs-lookup"><span data-stu-id="2c5c8-198">![Installer Properties for a Windows service](media/windows-service-installer-properties.png "Windows service installer properties")</span></span>

9. <span data-ttu-id="2c5c8-199">W widoku **projekt** dla **ProjectInstaller**wybierz pozycję **ServiceProcessInstaller1** dla projektu wizualnego C# lub **ServiceProcessInstaller1** dla projektu Visual Basic, a następnie wybierz **Właściwości** z menu skrótów. .</span><span class="sxs-lookup"><span data-stu-id="2c5c8-199">In the **Design** view for **ProjectInstaller**, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span> <span data-ttu-id="2c5c8-200">Ustaw właściwość na <xref:System.ServiceProcess.ServiceAccount.LocalSystem> wartość z listy rozwijanej. <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A></span><span class="sxs-lookup"><span data-stu-id="2c5c8-200">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem> from the drop-down list.</span></span>

     <span data-ttu-id="2c5c8-201">To ustawienie powoduje zainstalowanie usługi i uruchomienie jej przy użyciu lokalnego konta systemowego.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-201">This setting installs the service and runs it by using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="2c5c8-202"><xref:System.ServiceProcess.ServiceAccount.LocalSystem> Konto ma szerokie uprawnienia, w tym możliwość zapisu w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-202">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="2c5c8-203">Należy go używać ostrożnie, ponieważ może zwiększyć ryzyko ataku przez złośliwe oprogramowanie.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-203">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="2c5c8-204">W przypadku innych zadań należy rozważyć użycie <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, które działa jako użytkownik nieuprzywilejowany na komputerze lokalnym i prezentuje anonimowe poświadczenia na dowolnym serwerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-204">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="2c5c8-205">Ten przykład kończy się niepowodzeniem, jeśli spróbujesz użyć <xref:System.ServiceProcess.ServiceAccount.LocalService> konta, ponieważ wymaga ono uprawnienia do zapisu w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-205">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="2c5c8-206">Aby uzyskać więcej informacji na temat instalatorów [, zobacz How to: Dodaj Instalatory do aplikacji](how-to-add-installers-to-your-service-application.md)usługi.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-206">For more information about installers, see [How to: Add installers to your service application](how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="2c5c8-207">Obowiązkowe Ustaw parametry uruchamiania</span><span class="sxs-lookup"><span data-stu-id="2c5c8-207">(Optional) Set startup parameters</span></span>

> [!NOTE]
> <span data-ttu-id="2c5c8-208">Przed podjęciem decyzji o dodaniu parametrów uruchamiania należy rozważyć, czy jest to najlepszy sposób przekazywania informacji do usługi.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-208">Before you decide to add startup parameters, consider whether it's the best way to pass information to your service.</span></span> <span data-ttu-id="2c5c8-209">Mimo że jest to łatwe w użyciu i przeanalizowanie, a użytkownik może je łatwo przesłonić, może być trudniejsze dla użytkownika do odnalezienia i użycia bez dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-209">Although they're easy to use and parse, and a user can easily override them, they might be harder for a user to discover and use without documentation.</span></span> <span data-ttu-id="2c5c8-210">Ogólnie rzecz biorąc, jeśli usługa wymaga więcej niż kilku parametrów uruchamiania, zamiast tego należy użyć rejestru lub pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-210">Generally, if your service requires more than just a few startup parameters, you should use the registry or a configuration file instead.</span></span>

<span data-ttu-id="2c5c8-211">Usługa systemu Windows może akceptować argumenty wiersza polecenia lub parametry uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-211">A Windows service can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="2c5c8-212">Po dodaniu kodu do przetwarzania parametrów uruchamiania, użytkownik może uruchomić usługę z własnymi własnymi parametrami uruchamiania w oknie właściwości usługi.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-212">When you add code to process startup parameters, a user can start your service with their own custom startup parameters in the service properties window.</span></span> <span data-ttu-id="2c5c8-213">Jednak te Parametry uruchomieniowe nie są zachowywane podczas następnego uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-213">However, these startup parameters aren't persisted the next time the service starts.</span></span> <span data-ttu-id="2c5c8-214">Aby trwale ustawić parametry uruchamiania, ustaw je w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-214">To set startup parameters permanently, set them in the registry.</span></span>

<span data-ttu-id="2c5c8-215">Każda usługa systemu Windows ma wpis rejestru w podkluczu **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** .</span><span class="sxs-lookup"><span data-stu-id="2c5c8-215">Each Windows service has a registry entry under the **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** subkey.</span></span> <span data-ttu-id="2c5c8-216">W obszarze podklucza każdego usługi Użyj podklucza **Parameters** do przechowywania informacji, do których usługa może uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-216">Under each service's subkey, use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="2c5c8-217">Można używać plików konfiguracji aplikacji dla usługi systemu Windows w taki sam sposób jak w przypadku innych typów programów.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-217">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="2c5c8-218">Aby zapoznać się z przykładowym kodem, zobacz <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-218">For sample code, see <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span></span>

### <a name="to-add-startup-parameters"></a><span data-ttu-id="2c5c8-219">Aby dodać parametry uruchamiania</span><span class="sxs-lookup"><span data-stu-id="2c5c8-219">To add startup parameters</span></span>

1. <span data-ttu-id="2c5c8-220">Wybierz pozycję **program.cs**lub **MyNewService. Designer. vb**, a następnie wybierz pozycję **Wyświetl kod** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-220">Select **Program.cs**, or **MyNewService.Designer.vb**, then choose **View Code** from the shortcut menu.</span></span> <span data-ttu-id="2c5c8-221">`Main` W metodzie Zmień kod, aby dodać parametr wejściowy i przekazać go do konstruktora usługi:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-221">In the `Main` method, change the code to add an input parameter and pass it to the service constructor:</span></span>

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. <span data-ttu-id="2c5c8-222">W **MyNewService.cs**lub **MyNewService. vb**Zmień `MyNewService` konstruktora, aby przetworzyć parametr wejściowy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-222">In **MyNewService.cs**, or **MyNewService.vb**, change the `MyNewService` constructor to process the input parameter as follows:</span></span>

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

   <span data-ttu-id="2c5c8-223">Ten kod ustawia Źródło zdarzenia i nazwę dziennika zgodnie z parametrami uruchamiania dostarczanymi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-223">This code sets the event source and log name according to the startup parameters that the user supplies.</span></span> <span data-ttu-id="2c5c8-224">Jeśli nie podano argumentów, używa wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-224">If no arguments are supplied, it uses default values.</span></span>

3. <span data-ttu-id="2c5c8-225">Aby określić argumenty wiersza polecenia, Dodaj następujący kod do `ProjectInstaller` klasy w **ProjectInstaller.cs**lub **ProjectInstaller. vb**:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-225">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in **ProjectInstaller.cs**, or **ProjectInstaller.vb**:</span></span>

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

   <span data-ttu-id="2c5c8-226">Zazwyczaj ta wartość zawiera pełną ścieżkę do pliku wykonywalnego dla usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-226">Typically, this value contains the full path to the executable for the Windows service.</span></span> <span data-ttu-id="2c5c8-227">Aby usługa została prawidłowo uruchomiona, użytkownik musi podać znaki cudzysłowu dla ścieżki i każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-227">For the service to start up correctly, the user must supply quotation marks for the path and each individual parameter.</span></span> <span data-ttu-id="2c5c8-228">Aby zmienić parametry uruchamiania usługi systemu Windows, użytkownik może zmienić parametry w wpisie w rejestrze **ImagePath** .</span><span class="sxs-lookup"><span data-stu-id="2c5c8-228">A user can change the parameters in the **ImagePath** registry entry to change the startup parameters for the Windows service.</span></span> <span data-ttu-id="2c5c8-229">Lepszym sposobem jest jednak zmiana wartości programowo i udostępnienie funkcji w sposób przyjazny dla użytkownika, na przykład za pomocą narzędzia do zarządzania lub konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-229">However, a better way is to change the value programmatically and expose the functionality in a user-friendly way, such as by using a management or configuration utility.</span></span>

## <a name="build-the-service"></a><span data-ttu-id="2c5c8-230">Tworzenie usługi</span><span class="sxs-lookup"><span data-stu-id="2c5c8-230">Build the service</span></span>

1. <span data-ttu-id="2c5c8-231">W **Eksplorator rozwiązań**, wybierz **Właściwości** z menu skrótów dla projektu **MyNewService** .</span><span class="sxs-lookup"><span data-stu-id="2c5c8-231">In **Solution Explorer**, choose **Properties** from the shortcut menu for the **MyNewService** project.</span></span>

   <span data-ttu-id="2c5c8-232">Pojawią się strony właściwości projektu.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-232">The property pages for your project appear.</span></span>

2. <span data-ttu-id="2c5c8-233">Na karcie **aplikacja** na liście **obiekt początkowy** wybierz **MyNewService. program**lub **Sub Main** dla projektów Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-233">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**, or **Sub Main** for Visual Basic projects.</span></span>

3. <span data-ttu-id="2c5c8-234">Aby skompilować projekt, w **Eksplorator rozwiązań**wybierz opcję **Kompiluj** z menu skrótów dla projektu (lub naciśnij **klawisze CTRL**+**SHIFT**+**B**).</span><span class="sxs-lookup"><span data-stu-id="2c5c8-234">To build the project, in **Solution Explorer**, choose **Build** from the shortcut menu for your project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="2c5c8-235">Instalowanie usługi</span><span class="sxs-lookup"><span data-stu-id="2c5c8-235">Install the service</span></span>

<span data-ttu-id="2c5c8-236">Teraz, gdy została skompilowana usługa systemu Windows, możesz ją zainstalować.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-236">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="2c5c8-237">Aby zainstalować usługę systemu Windows, musisz mieć poświadczenia administratora na komputerze, na którym jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-237">To install a Windows service, you must have administrator credentials on the computer where it's installed.</span></span>

1. <span data-ttu-id="2c5c8-238">Otwórz [wiersz polecenia dla deweloperów dla programu Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) z poświadczeniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-238">Open [Developer Command Prompt for Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) with administrative credentials.</span></span> <span data-ttu-id="2c5c8-239">Z menu **Start** systemu Windows wybierz opcję **wiersz polecenia dla deweloperów dla programu vs 2017** w folderze Visual Studio, a następnie wybierz pozycję **więcej** > **Uruchom jako administrator** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-239">From the Windows **Start** menu, select **Developer Command Prompt for VS 2017** in the Visual Studio folder, then select **More** > **Run as Administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="2c5c8-240">W oknie **wiersz polecenia dla deweloperów dla programu Visual Studio** przejdź do folderu, który zawiera dane wyjściowe projektu (domyślnie podkatalog *\bin\debug* projektu).</span><span class="sxs-lookup"><span data-stu-id="2c5c8-240">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output (by default, the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="2c5c8-241">Wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-241">Enter the following command:</span></span>

    ```shell
    installutil MyNewService.exe
    ```

    <span data-ttu-id="2c5c8-242">Jeśli usługa zostanie pomyślnie zainstalowana, polecenie zgłosi powodzenie.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-242">If the service installs successfully, the command reports success.</span></span>

    <span data-ttu-id="2c5c8-243">Jeśli system nie może odnaleźć pliku *Installutil. exe*, upewnij się, że istnieje on na komputerze.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-243">If the system can't find *installutil.exe*, make sure that it exists on your computer.</span></span> <span data-ttu-id="2c5c8-244">To narzędzie jest instalowane z .NET Framework do folderu *%windir%\Microsoft.NET\Framework [64]\\&lt;&gt;Framework wersja*.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-244">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\&lt;framework version&gt;*.</span></span> <span data-ttu-id="2c5c8-245">Na przykład domyślną ścieżką dla wersji 64-bitowej jest *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-245">For example, the default path for the 64-bit version is *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="2c5c8-246">Jeśli proces **Installutil. exe** nie powiedzie się, sprawdź dziennik instalacji, aby dowiedzieć się, dlaczego.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-246">If the **installutil.exe** process fails, check the install log to find out why.</span></span> <span data-ttu-id="2c5c8-247">Domyślnie dziennik znajduje się w tym samym folderze co plik wykonywalny usługi.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-247">By default, the log is in the same folder as the service executable.</span></span> <span data-ttu-id="2c5c8-248">Instalacja może zakończyć się niepowodzeniem, jeśli:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-248">The installation can fail if:</span></span>
    - <span data-ttu-id="2c5c8-249">Klasa nie jest obecna `ProjectInstaller` w klasie. <xref:System.ComponentModel.RunInstallerAttribute></span><span class="sxs-lookup"><span data-stu-id="2c5c8-249">The <xref:System.ComponentModel.RunInstallerAttribute> class isn't present on the `ProjectInstaller` class.</span></span>
    - <span data-ttu-id="2c5c8-250">Atrybut nie jest ustawiony na `true`.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-250">The attribute isn't set to `true`.</span></span>
    - <span data-ttu-id="2c5c8-251">Klasa nie jest zdefiniowana jako `public`. `ProjectInstaller`</span><span class="sxs-lookup"><span data-stu-id="2c5c8-251">The `ProjectInstaller` class isn't defined as `public`.</span></span>

<span data-ttu-id="2c5c8-252">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie](how-to-install-and-uninstall-services.md)usług.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-252">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="2c5c8-253">Uruchom i uruchom usługę</span><span class="sxs-lookup"><span data-stu-id="2c5c8-253">Start and run the service</span></span>

1. <span data-ttu-id="2c5c8-254">W systemie Windows otwórz aplikację Desktop **Services** .</span><span class="sxs-lookup"><span data-stu-id="2c5c8-254">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="2c5c8-255">Naciśnij pozycję **Windows**+**R** , aby otworzyć okno **uruchamiania** , wpisz *Services. msc*, a następnie naciśnij klawisz **Enter** lub wybierz **przycisk OK**.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-255">Press **Windows**+**R** to open the **Run** box, enter *services.msc*, and then press **Enter** or select **OK**.</span></span>

     <span data-ttu-id="2c5c8-256">Twoja usługa powinna zostać wyświetlona na liście **usługi**, w kolejności alfabetycznej według nazwy wyświetlanej, która została ustawiona dla tego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-256">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![MyNewService w oknie usługi.](media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="2c5c8-258">Aby uruchomić usługę, wybierz pozycję **Rozpocznij** od menu skrótów usługi.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-258">To start the service, choose **Start** from the service's shortcut menu.</span></span>

3. <span data-ttu-id="2c5c8-259">Aby zatrzymać usługę, wybierz pozycję **Zatrzymaj** w menu skrótów usługi.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-259">To stop the service, choose **Stop** from the service's shortcut menu.</span></span>

4. <span data-ttu-id="2c5c8-260">Obowiązkowe W wierszu polecenia Użyj poleceń **net start &lt;Service Name&gt;**  i **net stop &lt;Service Name&gt;**  , aby uruchomić i zatrzymać usługę.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-260">(Optional) From the command line, use the commands **net start &lt;service name&gt;** and **net stop &lt;service name&gt;** to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="2c5c8-261">Weryfikowanie danych wyjściowych dziennika zdarzeń usługi</span><span class="sxs-lookup"><span data-stu-id="2c5c8-261">Verify the event log output of your service</span></span>

1. <span data-ttu-id="2c5c8-262">W systemie Windows otwórz aplikację klasyczną **Podgląd zdarzeń** .</span><span class="sxs-lookup"><span data-stu-id="2c5c8-262">In Windows, open the **Event Viewer** desktop app.</span></span> <span data-ttu-id="2c5c8-263">Wprowadź *Podgląd zdarzeń* na pasku wyszukiwania systemu Windows, a następnie wybierz **Podgląd zdarzeń** z wyników wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-263">Enter *Event Viewer* in the Windows search bar, and then select **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="2c5c8-264">W programie Visual Studio można uzyskać dostęp do dzienników zdarzeń, **otwierając Eksplorator serwera** z **menu Widok** (lub naciskając klawisze **Ctrl**+**Alt**+**S**) i rozszerzając węzeł **dzienniki zdarzeń** dla komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-264">In Visual Studio, you can access event logs by opening **Server Explorer** from the **View** menu (or press **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="2c5c8-265">W **Podgląd zdarzeń**rozwiń węzeł **Dzienniki aplikacji i usług**.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-265">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="2c5c8-266">Znajdź listę dla **myNewLog** (lub **MyLogFile1** , jeśli wykonano procedurę dodawania argumentów wiersza polecenia) i rozwiń ją.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-266">Locate the listing for **MyNewLog** (or **MyLogFile1** if you followed the procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="2c5c8-267">Powinny zostać wyświetlone wpisy dotyczące dwóch akcji (uruchamiania i zatrzymywania) wykonywanych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-267">You should see the entries for the two actions (start and stop) that your service performed.</span></span>

     ![Użyj Podgląd zdarzeń, aby wyświetlić wpisy dziennika zdarzeń](media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a><span data-ttu-id="2c5c8-269">Oczyszczanie zasobów</span><span class="sxs-lookup"><span data-stu-id="2c5c8-269">Clean up resources</span></span>

<span data-ttu-id="2c5c8-270">Jeśli aplikacja usługi systemu Windows nie jest już potrzebna, można ją usunąć.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-270">If you no longer need the Windows service app, you can remove it.</span></span>

1. <span data-ttu-id="2c5c8-271">Otwórz **wiersz polecenia dla deweloperów dla programu Visual Studio** z poświadczeniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-271">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="2c5c8-272">W oknie **wiersz polecenia dla deweloperów dla programu Visual Studio** przejdź do folderu, który zawiera dane wyjściowe projektu.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-272">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="2c5c8-273">Wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-273">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="2c5c8-274">Jeśli usługa została pomyślnie odinstalowana, polecenie zgłosi, że usługa została pomyślnie usunięta.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-274">If the service uninstalls successfully, the command reports that your service was successfully removed.</span></span> <span data-ttu-id="2c5c8-275">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie](how-to-install-and-uninstall-services.md)usług.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-275">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2c5c8-276">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="2c5c8-276">Next steps</span></span>

<span data-ttu-id="2c5c8-277">Teraz, gdy została utworzona usługa, możesz:</span><span class="sxs-lookup"><span data-stu-id="2c5c8-277">Now that you've created the service, you can:</span></span>

- <span data-ttu-id="2c5c8-278">Utwórz autonomiczny program instalacyjny, który będzie używany przez inne osoby do instalacji usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-278">Create a standalone setup program for others to use to install your Windows service.</span></span> <span data-ttu-id="2c5c8-279">Użyj zestawu [narzędzi WIX](https://wixtoolset.org/) , aby utworzyć Instalatora dla usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-279">Use the [WiX Toolset](https://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="2c5c8-280">Aby poznać inne pomysły, zobacz [Tworzenie pakietu Instalatora](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="2c5c8-280">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

- <span data-ttu-id="2c5c8-281"><xref:System.ServiceProcess.ServiceController> Eksploruj składnik, który umożliwia wysyłanie poleceń do zainstalowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-281">Explore the <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

- <span data-ttu-id="2c5c8-282">Zamiast tworzyć dziennik zdarzeń, gdy aplikacja jest uruchomiona, użyj Instalatora, aby utworzyć dziennik zdarzeń podczas instalowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-282">Instead of creating the event log when the application runs, use an installer to create an event log when you install the application.</span></span> <span data-ttu-id="2c5c8-283">Dziennik zdarzeń jest usuwany przez Instalatora podczas odinstalowywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-283">The event log is deleted by the installer when you uninstall the application.</span></span> <span data-ttu-id="2c5c8-284">Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.EventLogInstaller>.</span><span class="sxs-lookup"><span data-stu-id="2c5c8-284">For more information, see <xref:System.Diagnostics.EventLogInstaller>.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c5c8-285">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c5c8-285">See also</span></span>

- [<span data-ttu-id="2c5c8-286">Aplikacje usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2c5c8-286">Windows service applications</span></span>](index.md)
- [<span data-ttu-id="2c5c8-287">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2c5c8-287">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="2c5c8-288">Instrukcje: Debuguj aplikacje usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2c5c8-288">How to: Debug Windows service applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="2c5c8-289">Usługi (Windows)</span><span class="sxs-lookup"><span data-stu-id="2c5c8-289">Services (Windows)</span></span>](/windows/desktop/Services/services)
