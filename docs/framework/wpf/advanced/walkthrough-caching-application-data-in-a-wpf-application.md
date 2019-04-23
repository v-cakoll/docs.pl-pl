---
title: 'Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: 1d00c222dabf446c7c102307c3b904d3f1ff4bca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314400"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a><span data-ttu-id="59980-102">Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="59980-102">Walkthrough: Caching Application Data in a WPF Application</span></span>
<span data-ttu-id="59980-103">Pamięć podręczna umożliwia przechowywanie danych w pamięci, aby uzyskać szybki dostęp.</span><span class="sxs-lookup"><span data-stu-id="59980-103">Caching enables you to store data in memory for rapid access.</span></span> <span data-ttu-id="59980-104">Gdy dane są używane ponownie, aplikacje można uzyskać danych z pamięci podręcznej, zamiast pobierania z oryginalnego źródła.</span><span class="sxs-lookup"><span data-stu-id="59980-104">When the data is accessed again, applications can get the data from the cache instead of retrieving it from the original source.</span></span> <span data-ttu-id="59980-105">Może to poprawić wydajność i skalowalność.</span><span class="sxs-lookup"><span data-stu-id="59980-105">This can improve performance and scalability.</span></span> <span data-ttu-id="59980-106">Ponadto buforowania sprawia, że dane dostępne, gdy źródłem danych jest tymczasowo niedostępna.</span><span class="sxs-lookup"><span data-stu-id="59980-106">In addition, caching makes data available when the data source is temporarily unavailable.</span></span>

 <span data-ttu-id="59980-107">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Udostępnia klasy, które umożliwiają używanie buforowania w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="59980-107">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provides classes that enable you to use caching in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] applications.</span></span> <span data-ttu-id="59980-108">W ramach tych zajęć, znajdują się w <xref:System.Runtime.Caching> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="59980-108">These classes are located in the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
>  <span data-ttu-id="59980-109"><xref:System.Runtime.Caching> Przestrzeń nazw jest nowa w [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="59980-109">The <xref:System.Runtime.Caching> namespace is new in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="59980-110">Ta przestrzeń nazw sprawia, że pamięć podręczna jest dostępna dla wszystkich [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="59980-110">This namespace makes caching is available to all [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] applications.</span></span> <span data-ttu-id="59980-111">W poprzednich wersjach [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], pamięć podręczna była dostępna tylko w <xref:System.Web> przestrzeni nazw i dlatego wymagane zależności klas programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="59980-111">In previous versions of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], caching was available only in the <xref:System.Web> namespace and therefore required a dependency on ASP.NET classes.</span></span>

 <span data-ttu-id="59980-112">W tym instruktażu pokazano, jak korzystać z funkcji buforowania, która jest dostępna w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] jako część [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="59980-112">This walkthrough shows you how to use the caching functionality that is available in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] as part of a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="59980-113">W instruktażu pamięci podręcznej zawartość pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="59980-113">In the walkthrough, you cache the contents of a text file.</span></span>

 <span data-ttu-id="59980-114">Zadania przedstawione w niniejszym przewodniku to m.in.:</span><span class="sxs-lookup"><span data-stu-id="59980-114">Tasks illustrated in this walkthrough include the following:</span></span>

-   <span data-ttu-id="59980-115">Tworzenie projektu aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="59980-115">Creating a WPF application project.</span></span>

-   <span data-ttu-id="59980-116">Dodawanie odwołania do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="59980-116">Adding a reference to the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>

-   <span data-ttu-id="59980-117">Inicjowanie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="59980-117">Initializing a cache.</span></span>

-   <span data-ttu-id="59980-118">Dodawanie wpisu pamięci podręcznej, który zawiera zawartość pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="59980-118">Adding a cache entry that contains the contents of a text file.</span></span>

-   <span data-ttu-id="59980-119">Zapewnianie zasady eksmisji dla wpisu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="59980-119">Providing an eviction policy for the cache entry.</span></span>

-   <span data-ttu-id="59980-120">Monitorowanie ścieżkę do pliku pamięci podręcznej i powiadamiania wystąpienie pamięci podręcznej o zmiany monitorowania elementów.</span><span class="sxs-lookup"><span data-stu-id="59980-120">Monitoring the path of the cached file and notifying the cache instance about changes to the monitored item.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="59980-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="59980-121">Prerequisites</span></span>
 <span data-ttu-id="59980-122">Aby ukończyć ten przewodnik, potrzebne są:</span><span class="sxs-lookup"><span data-stu-id="59980-122">In order to complete this walkthrough, you will need:</span></span>

-   <span data-ttu-id="59980-123">Microsoft Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="59980-123">Microsoft Visual Studio 2010.</span></span>

-   <span data-ttu-id="59980-124">Plik tekstowy, który zawiera niewielkiej ilości tekstu.</span><span class="sxs-lookup"><span data-stu-id="59980-124">A text file that contains a small amount of text.</span></span> <span data-ttu-id="59980-125">(W oknie komunikatu zostanie wyświetlona zawartość pliku tekstowego). Kod zilustrowane w instruktażu przyjęto założenie, że pracujesz z następującego pliku:</span><span class="sxs-lookup"><span data-stu-id="59980-125">(You will display the contents of the text file in a message box.) The code illustrated in the walkthrough assumes that you are working with the following file:</span></span>

     `c:\cache\cacheText.txt`

     <span data-ttu-id="59980-126">Można jednak użyć dowolnego pliku tekstowego i wprowadzać niewielkie zmiany w kodzie, w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="59980-126">However, you can use any text file and make small changes to the code in this walkthrough.</span></span>

## <a name="creating-a-wpf-application-project"></a><span data-ttu-id="59980-127">Tworzenie projektu aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="59980-127">Creating a WPF Application Project</span></span>
 <span data-ttu-id="59980-128">Rozpoczniesz od utworzenia projektu aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="59980-128">You will start by creating a WPF application project.</span></span>

#### <a name="to-create-a-wpf-application"></a><span data-ttu-id="59980-129">Aby utworzyć aplikację WPF</span><span class="sxs-lookup"><span data-stu-id="59980-129">To create a WPF application</span></span>

1. <span data-ttu-id="59980-130">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59980-130">Start Visual Studio.</span></span>

2. <span data-ttu-id="59980-131">W **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="59980-131">In the **File** menu, click **New**, and then click **New Project**.</span></span>

     <span data-ttu-id="59980-132">**Nowy projekt** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="59980-132">The **New Project** dialog box is displayed.</span></span>

3. <span data-ttu-id="59980-133">W obszarze **zainstalowane szablony**, wybierz język programowania, którego chcesz użyć (**języka Visual Basic** lub **Visual C#**).</span><span class="sxs-lookup"><span data-stu-id="59980-133">Under **Installed Templates**, select the programming language you want to use (**Visual Basic** or **Visual C#**).</span></span>

4. <span data-ttu-id="59980-134">W **nowy projekt** okno dialogowe, wybierz opcję **aplikacji WPF**.</span><span class="sxs-lookup"><span data-stu-id="59980-134">In the **New Project** dialog box, select **WPF Application**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="59980-135">Jeśli nie widzisz **aplikacji WPF** szablonu, upewnij się, że są przeznaczone dla wersji programu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] WPF, która obsługuje.</span><span class="sxs-lookup"><span data-stu-id="59980-135">If you do not see the **WPF Application** template, make sure that you are targeting a version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] that supports WPF.</span></span> <span data-ttu-id="59980-136">W **nowy projekt** okno dialogowe, wybierz opcję [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] z listy.</span><span class="sxs-lookup"><span data-stu-id="59980-136">In the **New Project** dialog box, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] from the list.</span></span>

5. <span data-ttu-id="59980-137">W **nazwa** tekstu wprowadź nazwę dla projektu.</span><span class="sxs-lookup"><span data-stu-id="59980-137">In the **Name** text box, enter a name for your project.</span></span> <span data-ttu-id="59980-138">Na przykład można wprowadzić **WPFCaching**.</span><span class="sxs-lookup"><span data-stu-id="59980-138">For example, you can enter **WPFCaching**.</span></span>

6. <span data-ttu-id="59980-139">Wybierz **Utwórz katalog rozwiązania** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="59980-139">Select the **Create directory for solution** check box.</span></span>

7. <span data-ttu-id="59980-140">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="59980-140">Click **OK**.</span></span>

     <span data-ttu-id="59980-141">Zostanie otwarty projektant WPF w **projektowania** służy do wyświetlania i wyświetla pliku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="59980-141">The WPF Designer opens in **Design** view and displays the MainWindow.xaml file.</span></span> <span data-ttu-id="59980-142">Program Visual Studio tworzy **mój projekt** folder, plik Application.xaml i pliku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="59980-142">Visual Studio creates the **My Project** folder, the Application.xaml file, and the MainWindow.xaml file.</span></span>

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a><span data-ttu-id="59980-143">Zgodne z .NET Framework i dodanie odwołania do pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="59980-143">Targeting the .NET Framework and Adding a Reference to the Caching Assemblies</span></span>
 <span data-ttu-id="59980-144">Domyślnie docelowych aplikacji programu WPF [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="59980-144">By default, WPF applications target the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span></span> <span data-ttu-id="59980-145">Aby użyć <xref:System.Runtime.Caching> przestrzeni nazw w aplikacji WPF, aplikacja musi być przeznaczony dla [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (nie [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) i może zawierać odwołanie do przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="59980-145">To use the <xref:System.Runtime.Caching> namespace in a WPF application, the application must target the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (not the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) and must include a reference to the namespace.</span></span>

 <span data-ttu-id="59980-146">W związku z tym, następnym krokiem jest zmienić docelową .NET Framework i Dodaj odwołanie do <xref:System.Runtime.Caching> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="59980-146">Therefore, the next step is to change the .NET Framework target and add a reference to the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
>  <span data-ttu-id="59980-147">Procedury dotyczące zmieniania obiektu docelowego .NET Framework różni się w projekcie języka Visual Basic, jak i w projektach Visual C#.</span><span class="sxs-lookup"><span data-stu-id="59980-147">The procedure for changing the .NET Framework target is different in a Visual Basic project and in a Visual C# project.</span></span>

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a><span data-ttu-id="59980-148">Aby zmienić docelową aplikację .NET Framework w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59980-148">To change the target .NET Framework in Visual Basic</span></span>

1. <span data-ttu-id="59980-149">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="59980-149">In **Solutions Explorer**, right-click the project name, and then click **Properties**.</span></span>

     <span data-ttu-id="59980-150">Zostanie wyświetlone okno właściwości dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="59980-150">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="59980-151">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="59980-151">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="59980-152">W dolnej części okna kliknij **zaawansowane opcje kompilacji...** .</span><span class="sxs-lookup"><span data-stu-id="59980-152">At the bottom of the window, click **Advanced Compile Options…**.</span></span>

     <span data-ttu-id="59980-153">**Zaawansowane ustawienia kompilatora** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="59980-153">The **Advanced Compiler Settings** dialog box is displayed.</span></span>

4. <span data-ttu-id="59980-154">W **platformy docelowej (wszystkie konfiguracje)** listy wybierz [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="59980-154">In the **Target framework (all configurations)** list, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="59980-155">(Nie należy wybierać [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span><span class="sxs-lookup"><span data-stu-id="59980-155">(Do not select [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span></span>

5. <span data-ttu-id="59980-156">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="59980-156">Click **OK**.</span></span>

     <span data-ttu-id="59980-157">**Zmiana platformy docelowej** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="59980-157">The **Target Framework Change** dialog box is displayed.</span></span>

6. <span data-ttu-id="59980-158">W **zmiana platformy docelowej** okno dialogowe, kliknij przycisk **tak**.</span><span class="sxs-lookup"><span data-stu-id="59980-158">In the **Target Framework Change** dialog box, click **Yes**.</span></span>

     <span data-ttu-id="59980-159">Projekt jest zamknięty, a następnie ponownego otworzenia.</span><span class="sxs-lookup"><span data-stu-id="59980-159">The project is closed and is then reopened.</span></span>

7. <span data-ttu-id="59980-160">Dodaj odwołanie do pamięci podręcznej zestawów, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="59980-160">Add a reference to the caching assembly by following these steps:</span></span>

    1.  <span data-ttu-id="59980-161">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="59980-161">In **Solution Explorer**, right-click the name of the project and then click **Add Reference**.</span></span>

    2.  <span data-ttu-id="59980-162">Wybierz **.NET** zaznacz `System.Runtime.Caching`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="59980-162">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a><span data-ttu-id="59980-163">Aby zmienić docelową aplikację .NET Framework w projektach Visual C#</span><span class="sxs-lookup"><span data-stu-id="59980-163">To change the target .NET Framework in a Visual C# project</span></span>

1. <span data-ttu-id="59980-164">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="59980-164">In **Solution Explorer**, right-click the project name and then click **Properties**.</span></span>

     <span data-ttu-id="59980-165">Zostanie wyświetlone okno właściwości dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="59980-165">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="59980-166">Kliknij przycisk **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="59980-166">Click the **Application** tab.</span></span>

3. <span data-ttu-id="59980-167">W **platformę docelową** listy wybierz [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="59980-167">In the **Target framework** list, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="59980-168">(Nie należy wybierać **.NET Framework 4 Client Profile**.)</span><span class="sxs-lookup"><span data-stu-id="59980-168">(Do not select **.NET Framework 4 Client Profile**.)</span></span>

4. <span data-ttu-id="59980-169">Dodaj odwołanie do pamięci podręcznej zestawów, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="59980-169">Add a reference to the caching assembly by following these steps:</span></span>

    1.  <span data-ttu-id="59980-170">Kliknij prawym przyciskiem myszy **odwołania** folder, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="59980-170">Right-click the **References** folder and then click **Add Reference**.</span></span>

    2.  <span data-ttu-id="59980-171">Wybierz **.NET** zaznacz `System.Runtime.Caching`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="59980-171">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

## <a name="adding-a-button-to-the-wpf-window"></a><span data-ttu-id="59980-172">Dodawanie przycisku do okna WPF</span><span class="sxs-lookup"><span data-stu-id="59980-172">Adding a Button to the WPF Window</span></span>
 <span data-ttu-id="59980-173">Następnie będzie dodać formant przycisku i utworzyć program obsługi zdarzeń dla przycisku `Click` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="59980-173">Next, you will add a button control and create an event handler for the button's `Click` event.</span></span> <span data-ttu-id="59980-174">Później dodasz kod, po kliknięciu przycisku, zawartość pliku tekstowego są buforowane i wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="59980-174">Later you will add code to so when you click the button, the contents of the text file are cached and displayed.</span></span>

#### <a name="to-add-a-button-control"></a><span data-ttu-id="59980-175">Aby dodać kontrolkę przycisku</span><span class="sxs-lookup"><span data-stu-id="59980-175">To add a button control</span></span>

1. <span data-ttu-id="59980-176">W **Eksploratora rozwiązań**, kliknij dwukrotnie plik MainWindow.xaml, aby go otworzyć.</span><span class="sxs-lookup"><span data-stu-id="59980-176">In **Solution Explorer**, double-click the MainWindow.xaml file to open it.</span></span>

2. <span data-ttu-id="59980-177">Z **przybornika**w obszarze **wspólnych formantów WPF**, przeciągnij `Button` kontrolę `MainWindow` okna.</span><span class="sxs-lookup"><span data-stu-id="59980-177">From the **Toolbox**, under **Common WPF Controls**, drag a `Button` control to the `MainWindow` window.</span></span>

3. <span data-ttu-id="59980-178">W **właściwości** oknie `Content` właściwość `Button` kontrolę **Pobieranie pamięci podręcznej**.</span><span class="sxs-lookup"><span data-stu-id="59980-178">In the **Properties** window, set the `Content` property of the `Button` control to **Get Cache**.</span></span>

## <a name="initializing-the-cache-and-caching-an-entry"></a><span data-ttu-id="59980-179">Inicjowanie pamięci podręcznej i buforowania wpis</span><span class="sxs-lookup"><span data-stu-id="59980-179">Initializing the Cache and Caching an Entry</span></span>
 <span data-ttu-id="59980-180">Następnie dodasz kod do wykonywania następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="59980-180">Next, you will add the code to perform the following tasks:</span></span>

-   <span data-ttu-id="59980-181">Tworzenie wystąpienia klasy pamięci podręcznej — oznacza to, można będzie utworzyć <xref:System.Runtime.Caching.MemoryCache> obiektu.</span><span class="sxs-lookup"><span data-stu-id="59980-181">Create an instance of the cache class—that is, you will instantiate a new <xref:System.Runtime.Caching.MemoryCache> object.</span></span>

-   <span data-ttu-id="59980-182">Korzysta z pamięci podręcznej <xref:System.Runtime.Caching.HostFileChangeMonitor> obiektów do monitorowania zmian w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="59980-182">Specify that the cache uses a <xref:System.Runtime.Caching.HostFileChangeMonitor> object to monitor changes in the text file.</span></span>

-   <span data-ttu-id="59980-183">Odczyt pliku tekstowego i jego zawartość w pamięci podręcznej jako wpis pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="59980-183">Read the text file and cache its contents as a cache entry.</span></span>

-   <span data-ttu-id="59980-184">Wyświetl zawartość pliku tekstowego pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="59980-184">Display the contents of the cached text file.</span></span>

#### <a name="to-create-the-cache-object"></a><span data-ttu-id="59980-185">Można utworzyć obiektu pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="59980-185">To create the cache object</span></span>

1. <span data-ttu-id="59980-186">Kliknij dwukrotnie przycisk, który właśnie został dodany w celu utworzenia programu obsługi zdarzeń w pliku MainWindow.xaml.cs lub MainWindow.Xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="59980-186">Double-click the button you just added in order to create an event handler in the MainWindow.xaml.cs or MainWindow.Xaml.vb file.</span></span>

2. <span data-ttu-id="59980-187">W górnej części pliku (przed deklaracją klasy), Dodaj następujący kod `Imports` (Visual Basic) lub `using` instrukcje (C#):</span><span class="sxs-lookup"><span data-stu-id="59980-187">At the top of the file (before the class declaration), add the following `Imports` (Visual Basic) or `using` (C#) statements:</span></span>

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. <span data-ttu-id="59980-188">W procedurze obsługi zdarzeń Dodaj następujący kod, aby utworzyć wystąpienie obiektu pamięci podręcznej:</span><span class="sxs-lookup"><span data-stu-id="59980-188">In the event handler, add the following code to instantiate the cache object:</span></span>

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <span data-ttu-id="59980-189"><xref:System.Runtime.Caching.ObjectCache> Klasy jest klasą wbudowanych, która udostępnia pamięć podręczną obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="59980-189">The <xref:System.Runtime.Caching.ObjectCache> class is a built-in class that provides an in-memory object cache.</span></span>

4. <span data-ttu-id="59980-190">Dodaj następujący kod, aby odczytać zawartość wpisu pamięci podręcznej, o nazwie `filecontents`:</span><span class="sxs-lookup"><span data-stu-id="59980-190">Add the following code to read the contents of a cache entry named `filecontents`:</span></span>

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. <span data-ttu-id="59980-191">Dodaj następujący kod, aby sprawdzić, czy wpis pamięci podręcznej o nazwie `filecontents` istnieje:</span><span class="sxs-lookup"><span data-stu-id="59980-191">Add the following code to check whether the cache entry named `filecontents` exists:</span></span>

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     <span data-ttu-id="59980-192">Jeśli nie istnieje wpis określony w pamięci podręcznej, należy odczytać plik tekstowy i dodać go jako wpis pamięci podręcznej w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="59980-192">If the specified cache entry does not exist, you must read the text file and add it as a cache entry to the cache.</span></span>

6. <span data-ttu-id="59980-193">W `if/then` zablokować, Dodaj następujący kod, aby utworzyć nowy <xref:System.Runtime.Caching.CacheItemPolicy> obiektu, który określa, że wpis pamięci podręcznej wygaśnie po 10 sekundach.</span><span class="sxs-lookup"><span data-stu-id="59980-193">In the `if/then` block, add the following code to create a new <xref:System.Runtime.Caching.CacheItemPolicy> object that specifies that the cache entry expires after 10 seconds.</span></span>

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     <span data-ttu-id="59980-194">Jeśli nie podano żadnych informacji eksmisji lub data jej wygaśnięcia, wartość domyślna to <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, co oznacza, że wpisy w pamięci podręcznej nigdy nie wygasa oparte tylko na bezwzględnego czasu.</span><span class="sxs-lookup"><span data-stu-id="59980-194">If no eviction or expiration information is provided, the default is <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, which means the cache entries never expire based only on an absolute time.</span></span> <span data-ttu-id="59980-195">Zamiast tego wpisy w pamięci podręcznej wygasa tylko wtedy, gdy wykorzystanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="59980-195">Instead, cache entries expire only when there is memory pressure.</span></span> <span data-ttu-id="59980-196">Najlepszym rozwiązaniem należy zawsze jawnie określić bezwzględną lub wygaśniecie.</span><span class="sxs-lookup"><span data-stu-id="59980-196">As a best practice, you should always explicitly provide either an absolute or a sliding expiration.</span></span>

7. <span data-ttu-id="59980-197">Wewnątrz `if/then` blokowania i po kodzie dodanym w poprzednim kroku, Dodaj następujący kod, aby utworzyć kolekcję dla ścieżki do plików, które chcesz monitorować i Dodaj ścieżkę do pliku tekstowego do kolekcji:</span><span class="sxs-lookup"><span data-stu-id="59980-197">Inside the `if/then` block and following the code you added in the previous step, add the following code to create a collection for the file paths that you want to monitor, and to add the path of the text file to the collection:</span></span>

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    >  <span data-ttu-id="59980-198">Jeśli nie jest plik tekstowy, którego chcesz użyć `c:\cache\cacheText.txt`, określ ścieżkę do pliku tekstowego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="59980-198">If the text file you want to use is not `c:\cache\cacheText.txt`, specify the path where the text file is that you want to use.</span></span>

8. <span data-ttu-id="59980-199">Po kodzie dodanym w poprzednim kroku, Dodaj następujący kod, aby dodać nowy <xref:System.Runtime.Caching.HostFileChangeMonitor> do kolekcji zmiany monitoruje wpisu pamięci podręcznej:</span><span class="sxs-lookup"><span data-stu-id="59980-199">Following the code that you added in the previous step, add the following code to add a new <xref:System.Runtime.Caching.HostFileChangeMonitor> object to the collection of change monitors for the cache entry:</span></span>

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <span data-ttu-id="59980-200"><xref:System.Runtime.Caching.HostFileChangeMonitor> Obiekt monitoruje ścieżka do pliku tekstowego i powiadamia o pamięci podręcznej, jeśli występują zmiany.</span><span class="sxs-lookup"><span data-stu-id="59980-200">The <xref:System.Runtime.Caching.HostFileChangeMonitor> object monitors the text file's path and notifies the cache if changes occur.</span></span> <span data-ttu-id="59980-201">W tym przykładzie wpis pamięci podręcznej wygaśnie, jeśli zmieni się zawartość pliku.</span><span class="sxs-lookup"><span data-stu-id="59980-201">In this example, the cache entry will expire if the content of the file changes.</span></span>

9. <span data-ttu-id="59980-202">Po kodzie dodanym w poprzednim kroku dodaj następujący kod, aby odczytać zawartość pliku tekstowego:</span><span class="sxs-lookup"><span data-stu-id="59980-202">Following the code that you added in the previous step, add the following code to read the contents of the text file:</span></span>

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     <span data-ttu-id="59980-203">Sygnatura czasowa daty i godziny jest dodawany, dzięki czemu będą mogli zobaczyć po wygaśnięciu wpisu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="59980-203">The date and time timestamp is added so that you will be able to see when the cache entry expires.</span></span>

10. <span data-ttu-id="59980-204">Po kodzie dodanym w poprzednim kroku, Dodaj następujący kod, aby wstawić zawartość pliku do obiektu pamięci podręcznej jako <xref:System.Runtime.Caching.CacheItem> wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="59980-204">Following the code that you added in the previous step, add the following code to insert the contents of the file into the cache object as a <xref:System.Runtime.Caching.CacheItem> instance:</span></span>

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     <span data-ttu-id="59980-205">Określ informacje o jak wykluczyć wpisu pamięci podręcznej, przekazując <xref:System.Runtime.Caching.CacheItemPolicy> obiektu, który został utworzony wcześniej jako parametr.</span><span class="sxs-lookup"><span data-stu-id="59980-205">You specify information about how the cache entry should be evicted by passing the <xref:System.Runtime.Caching.CacheItemPolicy> object that you created earlier as a parameter.</span></span>

11. <span data-ttu-id="59980-206">Po `if/then` zablokować, Dodaj następujący kod, aby wyświetlić zawartość pliku pamięci podręcznej w oknie komunikatu:</span><span class="sxs-lookup"><span data-stu-id="59980-206">After the `if/then` block, add the following code to display the cached file content in a message box:</span></span>

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. <span data-ttu-id="59980-207">W **kompilacji** menu, kliknij przycisk **kompilacji WPFCaching** do kompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="59980-207">In the **Build** menu, click **Build WPFCaching** to build your project.</span></span>

## <a name="testing-caching-in-the-wpf-application"></a><span data-ttu-id="59980-208">Testowanie buforowania w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="59980-208">Testing Caching in the WPF Application</span></span>
 <span data-ttu-id="59980-209">Teraz można przetestować aplikację.</span><span class="sxs-lookup"><span data-stu-id="59980-209">You can now test the application.</span></span>

#### <a name="to-test-caching-in-the-wpf-application"></a><span data-ttu-id="59980-210">Aby przetestować buforowania w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="59980-210">To test caching in the WPF application</span></span>

1. <span data-ttu-id="59980-211">Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="59980-211">Press CTRL+F5 to run the application.</span></span>

     <span data-ttu-id="59980-212">`MainWindow` Zostanie wyświetlone okno.</span><span class="sxs-lookup"><span data-stu-id="59980-212">The `MainWindow` window is displayed.</span></span>

2. <span data-ttu-id="59980-213">Kliknij przycisk **Pobieranie pamięci podręcznej**.</span><span class="sxs-lookup"><span data-stu-id="59980-213">Click **Get Cache**.</span></span>

     <span data-ttu-id="59980-214">Zawartości w pamięci podręcznej w pliku tekstowym jest wyświetlany w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="59980-214">The cached content from the text file is displayed in a message box.</span></span> <span data-ttu-id="59980-215">Zwróć uwagę, znacznik czasu: w pliku.</span><span class="sxs-lookup"><span data-stu-id="59980-215">Notice the timestamp on the file.</span></span>

3. <span data-ttu-id="59980-216">Zamknij okno komunikatu, a następnie kliknij przycisk **Pobieranie pamięci podręcznej** ponownie.</span><span class="sxs-lookup"><span data-stu-id="59980-216">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="59980-217">Sygnatura czasowa pozostaje bez zmian.</span><span class="sxs-lookup"><span data-stu-id="59980-217">The timestamp is unchanged.</span></span> <span data-ttu-id="59980-218">Oznacza to, że jest wyświetlana zawartość z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="59980-218">This indicates the cached content is displayed.</span></span>

4. <span data-ttu-id="59980-219">Poczekaj 10 sekund lub więcej, a następnie kliknij przycisk **Pobieranie pamięci podręcznej** ponownie.</span><span class="sxs-lookup"><span data-stu-id="59980-219">Wait 10 seconds or more and then click **Get Cache** again.</span></span>

     <span data-ttu-id="59980-220">Tym razem zostanie wyświetlona nowa sygnatura czasowa.</span><span class="sxs-lookup"><span data-stu-id="59980-220">This time a new timestamp is displayed.</span></span> <span data-ttu-id="59980-221">Oznacza to, że zasady umożliwiają wygaśnięcia wpisu pamięci podręcznej i czy jest wyświetlana nowa zawartość pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="59980-221">This indicates that the policy let the cache entry expire and that new cached content is displayed.</span></span>

5. <span data-ttu-id="59980-222">W edytorze tekstu Otwórz plik tekstowy, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="59980-222">In a text editor, open the text file that you created.</span></span> <span data-ttu-id="59980-223">Jeszcze nie wprowadzaj żadnych zmian.</span><span class="sxs-lookup"><span data-stu-id="59980-223">Do not make any changes yet.</span></span>

6. <span data-ttu-id="59980-224">Zamknij okno komunikatu, a następnie kliknij przycisk **Pobieranie pamięci podręcznej** ponownie.</span><span class="sxs-lookup"><span data-stu-id="59980-224">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="59980-225">Ponownie Zwróć uwagę sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="59980-225">Notice the timestamp again.</span></span>

7. <span data-ttu-id="59980-226">Wprowadź zmianę do pliku tekstowego, a następnie zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="59980-226">Make a change to the text file and then save the file.</span></span>

8. <span data-ttu-id="59980-227">Zamknij okno komunikatu, a następnie kliknij przycisk **Pobieranie pamięci podręcznej** ponownie.</span><span class="sxs-lookup"><span data-stu-id="59980-227">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="59980-228">To okno komunikatu zawiera zaktualizowaną zawartość z pliku tekstowego i Nowa sygnatura czasowa.</span><span class="sxs-lookup"><span data-stu-id="59980-228">This message box contains the updated content from the text file and a new timestamp.</span></span> <span data-ttu-id="59980-229">Oznacza to, że monitor zmiany pliku hosta wykluczona wpisu pamięci podręcznej natychmiast, gdy zmienisz plik, mimo że nie wygasło bezwzględny limit czasu.</span><span class="sxs-lookup"><span data-stu-id="59980-229">This indicates that the host-file change monitor evicted the cache entry immediately when you changed the file, even though the absolute timeout period had not expired.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="59980-230">Możesz zwiększyć czas eksmisji 20 sekund lub więcej, aby dać więcej czasu, możesz wprowadzać zmiany w pliku.</span><span class="sxs-lookup"><span data-stu-id="59980-230">You can increase the eviction time to 20 seconds or more to allow more time for you to make a change in the file.</span></span>

## <a name="code-example"></a><span data-ttu-id="59980-231">Przykład kodu</span><span class="sxs-lookup"><span data-stu-id="59980-231">Code Example</span></span>
 <span data-ttu-id="59980-232">Po zakończeniu tego instruktażu kodu dla projektu, który został utworzony będą podobne do następującego przykładu.</span><span class="sxs-lookup"><span data-stu-id="59980-232">After you have completed this walkthrough, the code for the project you created will resemble the following example.</span></span>

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="59980-233">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59980-233">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [<span data-ttu-id="59980-234">Buforowanie w aplikacjach .NET Framework</span><span class="sxs-lookup"><span data-stu-id="59980-234">Caching in .NET Framework Applications</span></span>](../../performance/caching-in-net-framework-applications.md)
