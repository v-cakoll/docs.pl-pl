---
title: 'Wskazówki: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: f0082bd99b154f87ab90bee7a89afdb8405f6623
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920317"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a><span data-ttu-id="b0bd2-102">Wskazówki: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="b0bd2-102">Walkthrough: Caching Application Data in a WPF Application</span></span>
<span data-ttu-id="b0bd2-103">Buforowanie umożliwia przechowywanie danych w pamięci w celu szybkiego dostępu.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-103">Caching enables you to store data in memory for rapid access.</span></span> <span data-ttu-id="b0bd2-104">Po ponownym uzyskaniu dostępu do danych aplikacje mogą pobrać dane z pamięci podręcznej, zamiast pobierać je z oryginalnego źródła.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-104">When the data is accessed again, applications can get the data from the cache instead of retrieving it from the original source.</span></span> <span data-ttu-id="b0bd2-105">Może to poprawić wydajność i skalowalność.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-105">This can improve performance and scalability.</span></span> <span data-ttu-id="b0bd2-106">Ponadto buforowanie sprawia, że dane są dostępne, gdy źródło danych jest tymczasowo niedostępne.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-106">In addition, caching makes data available when the data source is temporarily unavailable.</span></span>

 <span data-ttu-id="b0bd2-107">.NET Framework zawiera klasy, które umożliwiają korzystanie z buforowania w aplikacjach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-107">The .NET Framework provides classes that enable you to use caching in .NET Framework applications.</span></span> <span data-ttu-id="b0bd2-108">Klasy te znajdują się w przestrzeni nazw <xref:System.Runtime.Caching>.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-108">These classes are located in the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="b0bd2-109">Przestrzeń nazw <xref:System.Runtime.Caching> jest nowa w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-109">The <xref:System.Runtime.Caching> namespace is new in the .NET Framework 4.</span></span> <span data-ttu-id="b0bd2-110">Ta przestrzeń nazw sprawia, że buforowanie jest dostępne dla wszystkich aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-110">This namespace makes caching is available to all .NET Framework applications.</span></span> <span data-ttu-id="b0bd2-111">W poprzednich wersjach .NET Framework buforowanie było dostępne tylko w przestrzeni nazw <xref:System.Web> i dlatego wymaga zależności od klas ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-111">In previous versions of the .NET Framework, caching was available only in the <xref:System.Web> namespace and therefore required a dependency on ASP.NET classes.</span></span>

 <span data-ttu-id="b0bd2-112">W tym instruktażu pokazano, jak używać funkcji buforowania dostępnej w .NET Framework w ramach aplikacji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0bd2-112">This walkthrough shows you how to use the caching functionality that is available in the .NET Framework as part of a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="b0bd2-113">W tym przewodniku zawartość pliku tekstowego jest buforowana.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-113">In the walkthrough, you cache the contents of a text file.</span></span>

 <span data-ttu-id="b0bd2-114">Zadania przedstawione w niniejszym przewodniku to m.in.:</span><span class="sxs-lookup"><span data-stu-id="b0bd2-114">Tasks illustrated in this walkthrough include the following:</span></span>

- <span data-ttu-id="b0bd2-115">Tworzenie projektu aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-115">Creating a WPF application project.</span></span>

- <span data-ttu-id="b0bd2-116">Dodawanie odwołania do .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-116">Adding a reference to the .NET Framework 4.</span></span>

- <span data-ttu-id="b0bd2-117">Inicjowanie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-117">Initializing a cache.</span></span>

- <span data-ttu-id="b0bd2-118">Dodawanie wpisu pamięci podręcznej, który zawiera zawartość pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-118">Adding a cache entry that contains the contents of a text file.</span></span>

- <span data-ttu-id="b0bd2-119">Dostarczanie zasad wykluczania dla wpisu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-119">Providing an eviction policy for the cache entry.</span></span>

- <span data-ttu-id="b0bd2-120">Monitorowanie ścieżki w pliku buforowanym i powiadamianie wystąpienia pamięci podręcznej o zmianach monitorowanego elementu.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-120">Monitoring the path of the cached file and notifying the cache instance about changes to the monitored item.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b0bd2-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b0bd2-121">Prerequisites</span></span>
 <span data-ttu-id="b0bd2-122">Aby ukończyć ten Instruktaż, potrzebne są:</span><span class="sxs-lookup"><span data-stu-id="b0bd2-122">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="b0bd2-123">Program Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-123">Visual Studio 2010.</span></span>

- <span data-ttu-id="b0bd2-124">Plik tekstowy, który zawiera niewielką ilość tekstu.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-124">A text file that contains a small amount of text.</span></span> <span data-ttu-id="b0bd2-125">(Zawartość pliku tekstowego zostanie wyświetlona w oknie komunikatu). Kod przedstawiony w instruktażu założono, że pracujesz z następującym plikiem:</span><span class="sxs-lookup"><span data-stu-id="b0bd2-125">(You will display the contents of the text file in a message box.) The code illustrated in the walkthrough assumes that you are working with the following file:</span></span>

     `c:\cache\cacheText.txt`

     <span data-ttu-id="b0bd2-126">Można jednak użyć dowolnego pliku tekstowego i wprowadzić niewielkie zmiany w kodzie w tym instruktażu.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-126">However, you can use any text file and make small changes to the code in this walkthrough.</span></span>

## <a name="creating-a-wpf-application-project"></a><span data-ttu-id="b0bd2-127">Tworzenie projektu aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="b0bd2-127">Creating a WPF Application Project</span></span>
 <span data-ttu-id="b0bd2-128">Zacznij od utworzenia projektu aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-128">You will start by creating a WPF application project.</span></span>

#### <a name="to-create-a-wpf-application"></a><span data-ttu-id="b0bd2-129">Aby utworzyć aplikację WPF</span><span class="sxs-lookup"><span data-stu-id="b0bd2-129">To create a WPF application</span></span>

1. <span data-ttu-id="b0bd2-130">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-130">Start Visual Studio.</span></span>

2. <span data-ttu-id="b0bd2-131">W menu **plik** kliknij pozycję **Nowy**, a następnie kliknij pozycję **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-131">In the **File** menu, click **New**, and then click **New Project**.</span></span>

     <span data-ttu-id="b0bd2-132">Zostanie wyświetlone okno dialogowe **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="b0bd2-132">The **New Project** dialog box is displayed.</span></span>

3. <span data-ttu-id="b0bd2-133">W obszarze **zainstalowane szablony**wybierz język programowania, który ma być używany (**Visual Basic** lub **Wizualizacja C#** ).</span><span class="sxs-lookup"><span data-stu-id="b0bd2-133">Under **Installed Templates**, select the programming language you want to use (**Visual Basic** or **Visual C#**).</span></span>

4. <span data-ttu-id="b0bd2-134">W oknie dialogowym **Nowy projekt** wybierz pozycję **Aplikacja WPF**.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-134">In the **New Project** dialog box, select **WPF Application**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b0bd2-135">Jeśli szablon **aplikacji WPF** nie jest wyświetlany, należy się upewnić, że jest przeznaczona do wersji .NET Framework, która obsługuje platformę WPF.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-135">If you do not see the **WPF Application** template, make sure that you are targeting a version of the .NET Framework that supports WPF.</span></span> <span data-ttu-id="b0bd2-136">W oknie dialogowym **Nowy projekt** wybierz z listy .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-136">In the **New Project** dialog box, select .NET Framework 4 from the list.</span></span>

5. <span data-ttu-id="b0bd2-137">W polu tekstowym **Nazwa** wprowadź nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-137">In the **Name** text box, enter a name for your project.</span></span> <span data-ttu-id="b0bd2-138">Na przykład możesz wprowadzić **WPFCaching**.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-138">For example, you can enter **WPFCaching**.</span></span>

6. <span data-ttu-id="b0bd2-139">Zaznacz pole wyboru **Utwórz katalog dla rozwiązania** .</span><span class="sxs-lookup"><span data-stu-id="b0bd2-139">Select the **Create directory for solution** check box.</span></span>

7. <span data-ttu-id="b0bd2-140">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-140">Click **OK**.</span></span>

     <span data-ttu-id="b0bd2-141">Projektant WPF zostanie otwarty w widoku **projektu** i zostanie wyświetlony plik MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-141">The WPF Designer opens in **Design** view and displays the MainWindow.xaml file.</span></span> <span data-ttu-id="b0bd2-142">Program Visual Studio tworzy folder **My Project** , plik Application. XAML i plik MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-142">Visual Studio creates the **My Project** folder, the Application.xaml file, and the MainWindow.xaml file.</span></span>

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a><span data-ttu-id="b0bd2-143">Kierowanie .NET Framework i Dodawanie odwołania do zestawów buforowania</span><span class="sxs-lookup"><span data-stu-id="b0bd2-143">Targeting the .NET Framework and Adding a Reference to the Caching Assemblies</span></span>
 <span data-ttu-id="b0bd2-144">Domyślnie aplikacje WPF są przeznaczone dla [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0bd2-144">By default, WPF applications target the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span></span> <span data-ttu-id="b0bd2-145">Aby użyć przestrzeni nazw <xref:System.Runtime.Caching> w aplikacji WPF, aplikacja musi być ukierunkowana na .NET Framework 4 (nie [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) i musi zawierać odwołanie do przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-145">To use the <xref:System.Runtime.Caching> namespace in a WPF application, the application must target the .NET Framework 4 (not the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) and must include a reference to the namespace.</span></span>

 <span data-ttu-id="b0bd2-146">W związku z tym następnym krokiem jest zmiana elementu docelowego .NET Framework i dodanie odwołania do <xref:System.Runtime.Caching> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-146">Therefore, the next step is to change the .NET Framework target and add a reference to the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="b0bd2-147">Procedura zmiany .NET Framework celu jest inna w projekcie Visual Basic i w projekcie wizualnym C# .</span><span class="sxs-lookup"><span data-stu-id="b0bd2-147">The procedure for changing the .NET Framework target is different in a Visual Basic project and in a Visual C# project.</span></span>

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a><span data-ttu-id="b0bd2-148">Aby zmienić .NET Framework docelowy w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0bd2-148">To change the target .NET Framework in Visual Basic</span></span>

1. <span data-ttu-id="b0bd2-149">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-149">In **Solutions Explorer**, right-click the project name, and then click **Properties**.</span></span>

     <span data-ttu-id="b0bd2-150">Zostanie wyświetlone okno właściwości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-150">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="b0bd2-151">Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="b0bd2-151">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="b0bd2-152">W dolnej części okna kliknij pozycję **Zaawansowane opcje kompilacji.** .</span><span class="sxs-lookup"><span data-stu-id="b0bd2-152">At the bottom of the window, click **Advanced Compile Options…**.</span></span>

     <span data-ttu-id="b0bd2-153">Zostanie wyświetlone okno dialogowe **Zaawansowane ustawienia kompilatora** .</span><span class="sxs-lookup"><span data-stu-id="b0bd2-153">The **Advanced Compiler Settings** dialog box is displayed.</span></span>

4. <span data-ttu-id="b0bd2-154">Na liście **platformy docelowej (wszystkie konfiguracje)** wybierz pozycję .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-154">In the **Target framework (all configurations)** list, select .NET Framework 4.</span></span> <span data-ttu-id="b0bd2-155">(Nie wybieraj [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span><span class="sxs-lookup"><span data-stu-id="b0bd2-155">(Do not select [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span></span>

5. <span data-ttu-id="b0bd2-156">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-156">Click **OK**.</span></span>

     <span data-ttu-id="b0bd2-157">Zostanie wyświetlone okno dialogowe **zmiana platformy docelowej** .</span><span class="sxs-lookup"><span data-stu-id="b0bd2-157">The **Target Framework Change** dialog box is displayed.</span></span>

6. <span data-ttu-id="b0bd2-158">W oknie dialogowym **zmiana platformy docelowej** kliknij przycisk **tak**.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-158">In the **Target Framework Change** dialog box, click **Yes**.</span></span>

     <span data-ttu-id="b0bd2-159">Projekt zostanie zamknięty i ponownie otwarty.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-159">The project is closed and is then reopened.</span></span>

7. <span data-ttu-id="b0bd2-160">Dodaj odwołanie do zestawu buforowania, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b0bd2-160">Add a reference to the caching assembly by following these steps:</span></span>

    1. <span data-ttu-id="b0bd2-161">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-161">In **Solution Explorer**, right-click the name of the project and then click **Add Reference**.</span></span>

    2. <span data-ttu-id="b0bd2-162">Wybierz kartę **.NET** , wybierz pozycję `System.Runtime.Caching`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-162">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a><span data-ttu-id="b0bd2-163">Aby zmienić .NET Framework docelowy w projekcie wizualizacji C#</span><span class="sxs-lookup"><span data-stu-id="b0bd2-163">To change the target .NET Framework in a Visual C# project</span></span>

1. <span data-ttu-id="b0bd2-164">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-164">In **Solution Explorer**, right-click the project name and then click **Properties**.</span></span>

     <span data-ttu-id="b0bd2-165">Zostanie wyświetlone okno właściwości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-165">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="b0bd2-166">Kliknij kartę **aplikacja** .</span><span class="sxs-lookup"><span data-stu-id="b0bd2-166">Click the **Application** tab.</span></span>

3. <span data-ttu-id="b0bd2-167">Na liście **platforma docelowa** wybierz pozycję .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-167">In the **Target framework** list, select .NET Framework 4.</span></span> <span data-ttu-id="b0bd2-168">(Nie wybieraj **.NET Framework 4 profilu klienta**).</span><span class="sxs-lookup"><span data-stu-id="b0bd2-168">(Do not select **.NET Framework 4 Client Profile**.)</span></span>

4. <span data-ttu-id="b0bd2-169">Dodaj odwołanie do zestawu buforowania, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b0bd2-169">Add a reference to the caching assembly by following these steps:</span></span>

    1. <span data-ttu-id="b0bd2-170">Kliknij prawym przyciskiem myszy folder **odwołania** , a następnie kliknij polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-170">Right-click the **References** folder and then click **Add Reference**.</span></span>

    2. <span data-ttu-id="b0bd2-171">Wybierz kartę **.NET** , wybierz pozycję `System.Runtime.Caching`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-171">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

## <a name="adding-a-button-to-the-wpf-window"></a><span data-ttu-id="b0bd2-172">Dodawanie przycisku do okna WPF</span><span class="sxs-lookup"><span data-stu-id="b0bd2-172">Adding a Button to the WPF Window</span></span>
 <span data-ttu-id="b0bd2-173">Następnie dodasz kontrolkę Button i utworzysz procedurę obsługi zdarzeń dla zdarzenia `Click` przycisku.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-173">Next, you will add a button control and create an event handler for the button's `Click` event.</span></span> <span data-ttu-id="b0bd2-174">Później dodasz kod do tego, gdy klikniesz przycisk, zawartość pliku tekstowego jest buforowana i wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-174">Later you will add code to so when you click the button, the contents of the text file are cached and displayed.</span></span>

#### <a name="to-add-a-button-control"></a><span data-ttu-id="b0bd2-175">Aby dodać kontrolkę przycisku</span><span class="sxs-lookup"><span data-stu-id="b0bd2-175">To add a button control</span></span>

1. <span data-ttu-id="b0bd2-176">W **Eksplorator rozwiązań**kliknij dwukrotnie plik MainWindow. XAML, aby go otworzyć.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-176">In **Solution Explorer**, double-click the MainWindow.xaml file to open it.</span></span>

2. <span data-ttu-id="b0bd2-177">Z **przybornika**w obszarze **typowe formanty WPF**przeciągnij kontrolkę `Button` do okna `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-177">From the **Toolbox**, under **Common WPF Controls**, drag a `Button` control to the `MainWindow` window.</span></span>

3. <span data-ttu-id="b0bd2-178">W oknie **Właściwości** ustaw właściwość `Content` formantu `Button`, aby **uzyskać pamięć podręczną**.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-178">In the **Properties** window, set the `Content` property of the `Button` control to **Get Cache**.</span></span>

## <a name="initializing-the-cache-and-caching-an-entry"></a><span data-ttu-id="b0bd2-179">Inicjowanie pamięci podręcznej i buforowanie wpisu</span><span class="sxs-lookup"><span data-stu-id="b0bd2-179">Initializing the Cache and Caching an Entry</span></span>
 <span data-ttu-id="b0bd2-180">Następnie dodasz kod w celu wykonania następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="b0bd2-180">Next, you will add the code to perform the following tasks:</span></span>

- <span data-ttu-id="b0bd2-181">Utwórz wystąpienie klasy pamięci podręcznej — to znaczy, że utworzysz wystąpienie nowego obiektu <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-181">Create an instance of the cache class—that is, you will instantiate a new <xref:System.Runtime.Caching.MemoryCache> object.</span></span>

- <span data-ttu-id="b0bd2-182">Określ, że pamięć podręczna używa obiektu <xref:System.Runtime.Caching.HostFileChangeMonitor> do monitorowania zmian w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-182">Specify that the cache uses a <xref:System.Runtime.Caching.HostFileChangeMonitor> object to monitor changes in the text file.</span></span>

- <span data-ttu-id="b0bd2-183">Przeczytaj plik tekstowy i Buforuj jego zawartość jako wpis pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-183">Read the text file and cache its contents as a cache entry.</span></span>

- <span data-ttu-id="b0bd2-184">Wyświetl zawartość pliku tekstowego w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-184">Display the contents of the cached text file.</span></span>

#### <a name="to-create-the-cache-object"></a><span data-ttu-id="b0bd2-185">Aby utworzyć obiekt pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="b0bd2-185">To create the cache object</span></span>

1. <span data-ttu-id="b0bd2-186">Kliknij dwukrotnie dodany przycisk, aby utworzyć procedurę obsługi zdarzeń w pliku MainWindow.xaml.cs lub MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-186">Double-click the button you just added in order to create an event handler in the MainWindow.xaml.cs or MainWindow.Xaml.vb file.</span></span>

2. <span data-ttu-id="b0bd2-187">W górnej części pliku (przed deklaracją klasy) Dodaj następujące instrukcje `Imports` (Visual Basic) lub `using` (C#):</span><span class="sxs-lookup"><span data-stu-id="b0bd2-187">At the top of the file (before the class declaration), add the following `Imports` (Visual Basic) or `using` (C#) statements:</span></span>

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. <span data-ttu-id="b0bd2-188">W programie obsługi zdarzeń Dodaj następujący kod, aby utworzyć wystąpienie obiektu pamięci podręcznej:</span><span class="sxs-lookup"><span data-stu-id="b0bd2-188">In the event handler, add the following code to instantiate the cache object:</span></span>

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <span data-ttu-id="b0bd2-189">Klasa <xref:System.Runtime.Caching.ObjectCache> jest wbudowaną klasą, która udostępnia pamięć podręczną obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-189">The <xref:System.Runtime.Caching.ObjectCache> class is a built-in class that provides an in-memory object cache.</span></span>

4. <span data-ttu-id="b0bd2-190">Dodaj następujący kod, aby odczytać zawartość wpisu pamięci podręcznej o nazwie `filecontents`:</span><span class="sxs-lookup"><span data-stu-id="b0bd2-190">Add the following code to read the contents of a cache entry named `filecontents`:</span></span>

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. <span data-ttu-id="b0bd2-191">Dodaj następujący kod, aby sprawdzić, czy wpis pamięci podręcznej o nazwie `filecontents` istnieje:</span><span class="sxs-lookup"><span data-stu-id="b0bd2-191">Add the following code to check whether the cache entry named `filecontents` exists:</span></span>

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     <span data-ttu-id="b0bd2-192">Jeśli określony wpis pamięci podręcznej nie istnieje, należy odczytać plik tekstowy i dodać go jako wpis pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-192">If the specified cache entry does not exist, you must read the text file and add it as a cache entry to the cache.</span></span>

6. <span data-ttu-id="b0bd2-193">W bloku `if/then` Dodaj następujący kod, aby utworzyć nowy obiekt <xref:System.Runtime.Caching.CacheItemPolicy>, który określa, że wpis pamięci podręcznej wygasa po 10 sekundach.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-193">In the `if/then` block, add the following code to create a new <xref:System.Runtime.Caching.CacheItemPolicy> object that specifies that the cache entry expires after 10 seconds.</span></span>

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     <span data-ttu-id="b0bd2-194">Jeśli nie zostaną podane żadne informacje o wykluczeniu lub wygaśnięciu, wartość domyślna to <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, co oznacza, że wpisy pamięci podręcznej nigdy nie wygasają w oparciu o czas bezwzględny.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-194">If no eviction or expiration information is provided, the default is <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, which means the cache entries never expire based only on an absolute time.</span></span> <span data-ttu-id="b0bd2-195">Zamiast tego wpisy pamięci podręcznej wygasają tylko wtedy, gdy występuje wykorzystanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-195">Instead, cache entries expire only when there is memory pressure.</span></span> <span data-ttu-id="b0bd2-196">Najlepszym rozwiązaniem jest zawsze jawne zapewnienie bezwzględnej lub ruchomej daty ważności.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-196">As a best practice, you should always explicitly provide either an absolute or a sliding expiration.</span></span>

7. <span data-ttu-id="b0bd2-197">Wewnątrz bloku `if/then` i po kodzie dodanym w poprzednim kroku Dodaj następujący kod, aby utworzyć kolekcję dla ścieżek plików, które chcesz monitorować, a następnie dodaj ścieżkę do pliku tekstowego do kolekcji:</span><span class="sxs-lookup"><span data-stu-id="b0bd2-197">Inside the `if/then` block and following the code you added in the previous step, add the following code to create a collection for the file paths that you want to monitor, and to add the path of the text file to the collection:</span></span>

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    > <span data-ttu-id="b0bd2-198">Jeśli plik tekstowy, którego chcesz użyć, nie jest `c:\cache\cacheText.txt`, określ ścieżkę, w której ma zostać użyty plik tekstowy.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-198">If the text file you want to use is not `c:\cache\cacheText.txt`, specify the path where the text file is that you want to use.</span></span>

8. <span data-ttu-id="b0bd2-199">Po kodzie dodanym w poprzednim kroku Dodaj następujący kod, aby dodać nowy obiekt <xref:System.Runtime.Caching.HostFileChangeMonitor> do kolekcji monitorów zmian dla wpisu pamięci podręcznej:</span><span class="sxs-lookup"><span data-stu-id="b0bd2-199">Following the code that you added in the previous step, add the following code to add a new <xref:System.Runtime.Caching.HostFileChangeMonitor> object to the collection of change monitors for the cache entry:</span></span>

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <span data-ttu-id="b0bd2-200">Obiekt <xref:System.Runtime.Caching.HostFileChangeMonitor> służy do monitorowania ścieżki pliku tekstowego i powiadamiania pamięci podręcznej w przypadku wystąpienia zmian.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-200">The <xref:System.Runtime.Caching.HostFileChangeMonitor> object monitors the text file's path and notifies the cache if changes occur.</span></span> <span data-ttu-id="b0bd2-201">W tym przykładzie wpis pamięci podręcznej utraci ważność, jeśli zawartość pliku ulegnie zmianie.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-201">In this example, the cache entry will expire if the content of the file changes.</span></span>

9. <span data-ttu-id="b0bd2-202">Po kodzie, który został dodany w poprzednim kroku, Dodaj następujący kod, aby odczytać zawartość pliku tekstowego:</span><span class="sxs-lookup"><span data-stu-id="b0bd2-202">Following the code that you added in the previous step, add the following code to read the contents of the text file:</span></span>

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     <span data-ttu-id="b0bd2-203">Zostanie dodana sygnatura czasowa daty i godziny, dzięki czemu będzie można zobaczyć, kiedy wygasa wpis pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-203">The date and time timestamp is added so that you will be able to see when the cache entry expires.</span></span>

10. <span data-ttu-id="b0bd2-204">Po kodzie, który został dodany w poprzednim kroku, Dodaj następujący kod, aby wstawić zawartość pliku do obiektu pamięci podręcznej jako wystąpienie <xref:System.Runtime.Caching.CacheItem>:</span><span class="sxs-lookup"><span data-stu-id="b0bd2-204">Following the code that you added in the previous step, add the following code to insert the contents of the file into the cache object as a <xref:System.Runtime.Caching.CacheItem> instance:</span></span>

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     <span data-ttu-id="b0bd2-205">Należy określić informacje dotyczące sposobu wykluczenia wpisu pamięci podręcznej przez przekazanie obiektu <xref:System.Runtime.Caching.CacheItemPolicy> utworzonego wcześniej jako parametr.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-205">You specify information about how the cache entry should be evicted by passing the <xref:System.Runtime.Caching.CacheItemPolicy> object that you created earlier as a parameter.</span></span>

11. <span data-ttu-id="b0bd2-206">Po bloku `if/then` Dodaj następujący kod, aby wyświetlić zawartość pliku w pamięci podręcznej w oknie komunikatu:</span><span class="sxs-lookup"><span data-stu-id="b0bd2-206">After the `if/then` block, add the following code to display the cached file content in a message box:</span></span>

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. <span data-ttu-id="b0bd2-207">W menu **kompilacja** kliknij pozycję **Kompiluj WPFCaching** , aby skompilować projekt.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-207">In the **Build** menu, click **Build WPFCaching** to build your project.</span></span>

## <a name="testing-caching-in-the-wpf-application"></a><span data-ttu-id="b0bd2-208">Testowanie buforowania w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="b0bd2-208">Testing Caching in the WPF Application</span></span>
 <span data-ttu-id="b0bd2-209">Teraz można testować aplikację.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-209">You can now test the application.</span></span>

#### <a name="to-test-caching-in-the-wpf-application"></a><span data-ttu-id="b0bd2-210">Aby przetestować buforowanie w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="b0bd2-210">To test caching in the WPF application</span></span>

1. <span data-ttu-id="b0bd2-211">Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-211">Press CTRL+F5 to run the application.</span></span>

     <span data-ttu-id="b0bd2-212">Zostanie wyświetlone okno `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-212">The `MainWindow` window is displayed.</span></span>

2. <span data-ttu-id="b0bd2-213">Kliknij pozycję **Pobierz pamięć podręczną**.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-213">Click **Get Cache**.</span></span>

     <span data-ttu-id="b0bd2-214">Zawartość z pamięci podręcznej z pliku tekstowego zostanie wyświetlona w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-214">The cached content from the text file is displayed in a message box.</span></span> <span data-ttu-id="b0bd2-215">Zwróć uwagę na sygnaturę czasową pliku.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-215">Notice the timestamp on the file.</span></span>

3. <span data-ttu-id="b0bd2-216">Zamknij okno komunikatu, a następnie kliknij ponownie przycisk **Pobierz pamięć podręczną** .</span><span class="sxs-lookup"><span data-stu-id="b0bd2-216">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="b0bd2-217">Sygnatura czasowa nie została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-217">The timestamp is unchanged.</span></span> <span data-ttu-id="b0bd2-218">Wskazuje to, że buforowana zawartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-218">This indicates the cached content is displayed.</span></span>

4. <span data-ttu-id="b0bd2-219">Odczekaj 10 sekund lub więcej, a następnie kliknij ponownie przycisk **Pobierz pamięć podręczną** .</span><span class="sxs-lookup"><span data-stu-id="b0bd2-219">Wait 10 seconds or more and then click **Get Cache** again.</span></span>

     <span data-ttu-id="b0bd2-220">Tym razem zostanie wyświetlona nowa Sygnatura czasowa.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-220">This time a new timestamp is displayed.</span></span> <span data-ttu-id="b0bd2-221">Oznacza to, że zasady pozwalają na wygaśnięcie wpisu pamięci podręcznej i wyświetlanie nowej zawartości w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-221">This indicates that the policy let the cache entry expire and that new cached content is displayed.</span></span>

5. <span data-ttu-id="b0bd2-222">W edytorze tekstów Otwórz utworzony plik tekstowy.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-222">In a text editor, open the text file that you created.</span></span> <span data-ttu-id="b0bd2-223">Nie wprowadzaj jeszcze żadnych zmian.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-223">Do not make any changes yet.</span></span>

6. <span data-ttu-id="b0bd2-224">Zamknij okno komunikatu, a następnie kliknij ponownie przycisk **Pobierz pamięć podręczną** .</span><span class="sxs-lookup"><span data-stu-id="b0bd2-224">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="b0bd2-225">Zwróć uwagę na ponowną sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-225">Notice the timestamp again.</span></span>

7. <span data-ttu-id="b0bd2-226">Wprowadź zmiany do pliku tekstowego, a następnie Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-226">Make a change to the text file and then save the file.</span></span>

8. <span data-ttu-id="b0bd2-227">Zamknij okno komunikatu, a następnie kliknij ponownie przycisk **Pobierz pamięć podręczną** .</span><span class="sxs-lookup"><span data-stu-id="b0bd2-227">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="b0bd2-228">To okno komunikatu zawiera zaktualizowaną zawartość z pliku tekstowego i nową sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-228">This message box contains the updated content from the text file and a new timestamp.</span></span> <span data-ttu-id="b0bd2-229">Oznacza to, że monitor zmiany plików hosta wykluczony z wpisu pamięci podręcznej natychmiast po zmianie pliku, nawet jeśli bezwzględny limit czasu nie upłynął.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-229">This indicates that the host-file change monitor evicted the cache entry immediately when you changed the file, even though the absolute timeout period had not expired.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b0bd2-230">Możesz wydłużyć czas wykluczenia na 20 sekund lub więcej, aby zapewnić więcej czasu na wprowadzenie zmian w pliku.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-230">You can increase the eviction time to 20 seconds or more to allow more time for you to make a change in the file.</span></span>

## <a name="code-example"></a><span data-ttu-id="b0bd2-231">Przykład kodu</span><span class="sxs-lookup"><span data-stu-id="b0bd2-231">Code Example</span></span>
 <span data-ttu-id="b0bd2-232">Po zakończeniu tego instruktażu kod utworzonego projektu będzie wyglądać podobnie do poniższego przykładu.</span><span class="sxs-lookup"><span data-stu-id="b0bd2-232">After you have completed this walkthrough, the code for the project you created will resemble the following example.</span></span>

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="b0bd2-233">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0bd2-233">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [<span data-ttu-id="b0bd2-234">Buforowanie w aplikacjach .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b0bd2-234">Caching in .NET Framework Applications</span></span>](../../performance/caching-in-net-framework-applications.md)
