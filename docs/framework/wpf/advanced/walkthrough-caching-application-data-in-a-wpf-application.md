---
title: "Wskazówki: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81d808b982852d5cc6dc187a3c8389748a0dc0bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a><span data-ttu-id="b4e28-102">Wskazówki: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="b4e28-102">Walkthrough: Caching Application Data in a WPF Application</span></span>
<span data-ttu-id="b4e28-103">Buforowanie umożliwia przechowywanie danych w pamięci, aby uzyskać szybki dostęp.</span><span class="sxs-lookup"><span data-stu-id="b4e28-103">Caching enables you to store data in memory for rapid access.</span></span> <span data-ttu-id="b4e28-104">Dostępie do danych ponownie, aplikacje można pobrać danych z pamięci podręcznej, zamiast tego podczas pobierania z oryginalnego źródła.</span><span class="sxs-lookup"><span data-stu-id="b4e28-104">When the data is accessed again, applications can get the data from the cache instead retrieving it from the original source.</span></span> <span data-ttu-id="b4e28-105">Może to poprawić wydajność i skalowalność.</span><span class="sxs-lookup"><span data-stu-id="b4e28-105">This can improve performance and scalability.</span></span> <span data-ttu-id="b4e28-106">Ponadto buforowanie sprawia, że nie są dostępne dane, gdy źródłem danych jest tymczasowo niedostępna.</span><span class="sxs-lookup"><span data-stu-id="b4e28-106">In addition, caching makes data available when the data source is temporarily unavailable.</span></span>  
  
 <span data-ttu-id="b4e28-107">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Udostępnia klasy, które umożliwiają używanie buforowania w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b4e28-107">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provides classes that enable you to use caching in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] applications.</span></span> <span data-ttu-id="b4e28-108">Te klasy znajdują się w <xref:System.Runtime.Caching> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b4e28-108">These classes are located in the <xref:System.Runtime.Caching> namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4e28-109"><xref:System.Runtime.Caching> Przestrzeń nazw jest nowa w [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4e28-109">The <xref:System.Runtime.Caching> namespace is new in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="b4e28-110">Ta przestrzeń nazw sprawia, że buforowanie jest dostępna dla wszystkich [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b4e28-110">This namespace makes caching is available to all [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] applications.</span></span> <span data-ttu-id="b4e28-111">W poprzednich wersjach [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], buforowanie była dostępna tylko w <xref:System.Web> przestrzeni nazw i w związku z tym wymagana zależność klasy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b4e28-111">In previous versions of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], caching was available only in the <xref:System.Web> namespace and therefore required a dependency on ASP.NET classes.</span></span>  
  
 <span data-ttu-id="b4e28-112">W tym przewodniku przedstawiono sposób korzystać z funkcji buforowania, która jest dostępna w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] jako część [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b4e28-112">This walkthrough shows you how to use the caching functionality that is available in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] as part of a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="b4e28-113">W tym przewodnikiem pamięci podręcznej zawartość pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="b4e28-113">In the walkthrough, you cache the contents of a text file.</span></span>  
  
 <span data-ttu-id="b4e28-114">Zadania przedstawione w niniejszym przewodniku to m.in.:</span><span class="sxs-lookup"><span data-stu-id="b4e28-114">Tasks illustrated in this walkthrough include the following:</span></span>  
  
-   <span data-ttu-id="b4e28-115">Tworzenie nowego projektu aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="b4e28-115">Creating a WPF application project.</span></span>  
  
-   <span data-ttu-id="b4e28-116">Dodawanie odwołania do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4e28-116">Adding a reference to the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
-   <span data-ttu-id="b4e28-117">Inicjowanie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b4e28-117">Initializing a cache.</span></span>  
  
-   <span data-ttu-id="b4e28-118">Dodanie wpisu pamięci podręcznej, którego zawartość pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="b4e28-118">Adding a cache entry that contains the contents of a text file.</span></span>  
  
-   <span data-ttu-id="b4e28-119">Zapewnienie zasad eksmisji dla wpisu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b4e28-119">Providing an eviction policy for the cache entry.</span></span>  
  
-   <span data-ttu-id="b4e28-120">Monitorowanie ścieżkę pliku pamięci podręcznej i powiadamiania wystąpienia pamięci podręcznej o zmiany monitorowania elementów.</span><span class="sxs-lookup"><span data-stu-id="b4e28-120">Monitoring the path of the cached file and notifying the cache instance about changes to the monitored item.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b4e28-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b4e28-121">Prerequisites</span></span>  
 <span data-ttu-id="b4e28-122">W celu przeprowadzenia tego instruktażu potrzebne są:</span><span class="sxs-lookup"><span data-stu-id="b4e28-122">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="b4e28-123">Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4e28-123">Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].</span></span>  
  
-   <span data-ttu-id="b4e28-124">Plik tekstowy zawierający mała ilość tekstu.</span><span class="sxs-lookup"><span data-stu-id="b4e28-124">A text file that contains a small amount of text.</span></span> <span data-ttu-id="b4e28-125">(W oknie komunikatu zostanie wyświetlona zawartość pliku tekstowego). Kod przedstawiony przewodnika zakłada użytkownik pracuje z następującego pliku:</span><span class="sxs-lookup"><span data-stu-id="b4e28-125">(You will display the contents of the text file in a message box.) The code illustrated in the walkthrough assumes that you are working with the following file:</span></span>  
  
     `c:\cache\cacheText.txt`  
  
     <span data-ttu-id="b4e28-126">Można jednak użyć dowolnego pliku tekstowego i wprowadzić niewielkich zmian w kodzie w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="b4e28-126">However, you can use any text file and make small changes to the code in this walkthrough.</span></span>  
  
## <a name="creating-a-wpf-application-project"></a><span data-ttu-id="b4e28-127">Tworzenie nowego projektu aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="b4e28-127">Creating a WPF Application Project</span></span>  
 <span data-ttu-id="b4e28-128">Zostanie rozpoczyna się od utworzenia projektu aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="b4e28-128">You will start by creating a WPF application project.</span></span>  
  
#### <a name="to-create-a-wpf-application"></a><span data-ttu-id="b4e28-129">Aby utworzyć aplikację programu WPF</span><span class="sxs-lookup"><span data-stu-id="b4e28-129">To create a WPF application</span></span>  
  
1.  <span data-ttu-id="b4e28-130">Uruchom [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4e28-130">Start [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
2.  <span data-ttu-id="b4e28-131">W **pliku** menu, kliknij przycisk **nowy**, a następnie kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="b4e28-131">In the **File** menu, click **New**, and then click **New Project**.</span></span>  
  
     <span data-ttu-id="b4e28-132">**Nowy projekt** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b4e28-132">The **New Project** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="b4e28-133">W obszarze **zainstalowane szablony**, wybierz język programowania, którego chcesz użyć (**Visual Basic** lub **Visual C#**).</span><span class="sxs-lookup"><span data-stu-id="b4e28-133">Under **Installed Templates**, select the programming language you want to use (**Visual Basic** or **Visual C#**).</span></span>  
  
4.  <span data-ttu-id="b4e28-134">W **nowy projekt** okno dialogowe, wybierz opcję **aplikacji WPF**.</span><span class="sxs-lookup"><span data-stu-id="b4e28-134">In the **New Project** dialog box, select **WPF Application**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b4e28-135">Jeśli nie widzisz **aplikacji WPF** szablonu, upewnij się, że ma być przeznaczona dla wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obsługującej WPF.</span><span class="sxs-lookup"><span data-stu-id="b4e28-135">If you do not see the **WPF Application** template, make sure that you are targeting a version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] that supports WPF.</span></span> <span data-ttu-id="b4e28-136">W **nowy projekt** okno dialogowe, wybierz opcję [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] z listy.</span><span class="sxs-lookup"><span data-stu-id="b4e28-136">In the **New Project** dialog box, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] from the list.</span></span>  
  
5.  <span data-ttu-id="b4e28-137">W **nazwa** tekst Wprowadź nazwę dla projektu.</span><span class="sxs-lookup"><span data-stu-id="b4e28-137">In the **Name** text box, enter a name for your project.</span></span> <span data-ttu-id="b4e28-138">Na przykład można wprowadzić **WPFCaching**.</span><span class="sxs-lookup"><span data-stu-id="b4e28-138">For example, you can enter **WPFCaching**.</span></span>  
  
6.  <span data-ttu-id="b4e28-139">Wybierz **Utwórz katalog rozwiązania** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="b4e28-139">Select the **Create directory for solution** check box.</span></span>  
  
7.  <span data-ttu-id="b4e28-140">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b4e28-140">Click **OK**.</span></span>  
  
     <span data-ttu-id="b4e28-141">Zostanie otwarty projektant WPF w **projekt** wyświetlanie i wyświetla plik MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="b4e28-141">The WPF Designer opens in **Design** view and displays the MainWindow.xaml file.</span></span> [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]<span data-ttu-id="b4e28-142">Tworzy **mój projekt** folder, plik Application.xaml i plik MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="b4e28-142"> creates the **My Project** folder, the Application.xaml file, and the MainWindow.xaml file.</span></span>  
  
## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a><span data-ttu-id="b4e28-143">Docelowy program .NET Framework i dodawanie odwołania do pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="b4e28-143">Targeting the .NET Framework and Adding a Reference to the Caching Assemblies</span></span>  
 <span data-ttu-id="b4e28-144">Domyślnie docelowej aplikacji WPF [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4e28-144">By default, WPF applications target the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span></span> <span data-ttu-id="b4e28-145">Aby użyć <xref:System.Runtime.Caching> przestrzeni nazw w aplikacji WPF, aplikacja musi wskazywać [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (nie [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) i musi zawierać odwołanie do przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b4e28-145">To use the <xref:System.Runtime.Caching> namespace in a WPF application, the application must target the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (not the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) and must include a reference to the namespace.</span></span>  
  
 <span data-ttu-id="b4e28-146">W związku z tym, następnym krokiem jest Zmień docelowy .NET Framework i Dodaj odwołanie do <xref:System.Runtime.Caching> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b4e28-146">Therefore, the next step is to change the .NET Framework target and add a reference to the <xref:System.Runtime.Caching> namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4e28-147">Procedura docelowy .NET Framework zmieniania różni się w projektach Visual Basic i w projektach Visual C#.</span><span class="sxs-lookup"><span data-stu-id="b4e28-147">The procedure for changing the .NET Framework target is different in a Visual Basic project and in a Visual C# project.</span></span>  
  
#### <a name="to-change-the-target-net-framework-in-visual-basic"></a><span data-ttu-id="b4e28-148">Aby zmienić docelowej platformy .NET Framework w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b4e28-148">To change the target .NET Framework in Visual Basic</span></span>  
  
1.  <span data-ttu-id="b4e28-149">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b4e28-149">In **Solutions Explorer**, right-click the project name, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="b4e28-150">Zostanie wyświetlone okno właściwości dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b4e28-150">The properties window for the application is displayed.</span></span>  
  
2.  <span data-ttu-id="b4e28-151">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="b4e28-151">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="b4e28-152">W dolnej części okna kliknij **zaawansowane opcje kompilacji...** .</span><span class="sxs-lookup"><span data-stu-id="b4e28-152">At the bottom of the window, click **Advanced Compile Options…**.</span></span>  
  
     <span data-ttu-id="b4e28-153">**Zaawansowane ustawienia kompilatora** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b4e28-153">The **Advanced Compiler Settings** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="b4e28-154">W **platformy docelowej (wszystkie konfiguracje)** listy, wybierz [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4e28-154">In the **Target framework (all configurations)** list, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="b4e28-155">(Nie należy wybierać [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span><span class="sxs-lookup"><span data-stu-id="b4e28-155">(Do not select [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span></span>  
  
5.  <span data-ttu-id="b4e28-156">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b4e28-156">Click **OK**.</span></span>  
  
     <span data-ttu-id="b4e28-157">**Zmianie docelowego Framework** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b4e28-157">The **Target Framework Change** dialog box is displayed.</span></span>  
  
6.  <span data-ttu-id="b4e28-158">W **zmianie docelowego Framework** okno dialogowe, kliknij przycisk **tak**.</span><span class="sxs-lookup"><span data-stu-id="b4e28-158">In the **Target Framework Change** dialog box, click **Yes**.</span></span>  
  
     <span data-ttu-id="b4e28-159">Projekt zostanie zamknięte, a następnie otwarciu.</span><span class="sxs-lookup"><span data-stu-id="b4e28-159">The project is closed and is then reopened.</span></span>  
  
7.  <span data-ttu-id="b4e28-160">Dodaj odwołanie do zestawu buforowania, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b4e28-160">Add a reference to the caching assembly by following these steps:</span></span>  
  
    1.  <span data-ttu-id="b4e28-161">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="b4e28-161">In **Solution Explorer**, right-click the name of the project and then click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="b4e28-162">Wybierz **.NET** wybierz opcję `System.Runtime.Caching`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b4e28-162">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>  
  
#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a><span data-ttu-id="b4e28-163">Aby zmienić docelowej platformy .NET Framework w projektach Visual C#</span><span class="sxs-lookup"><span data-stu-id="b4e28-163">To change the target .NET Framework in a Visual C# project</span></span>  
  
1.  <span data-ttu-id="b4e28-164">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b4e28-164">In **Solution Explorer**, right-click the project name and then click **Properties**.</span></span>  
  
     <span data-ttu-id="b4e28-165">Zostanie wyświetlone okno właściwości dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b4e28-165">The properties window for the application is displayed.</span></span>  
  
2.  <span data-ttu-id="b4e28-166">Kliknij przycisk **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="b4e28-166">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="b4e28-167">W **platformy docelowej** listy, wybierz [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4e28-167">In the **Target framework** list, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="b4e28-168">(Nie należy wybierać **.NET Framework 4 Client Profile**.)</span><span class="sxs-lookup"><span data-stu-id="b4e28-168">(Do not select **.NET Framework 4 Client Profile**.)</span></span>  
  
4.  <span data-ttu-id="b4e28-169">Dodaj odwołanie do zestawu buforowania, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b4e28-169">Add a reference to the caching assembly by following these steps:</span></span>  
  
    1.  <span data-ttu-id="b4e28-170">Kliknij prawym przyciskiem myszy **odwołania** folder, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="b4e28-170">Right-click the **References** folder and then click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="b4e28-171">Wybierz **.NET** wybierz opcję `System.Runtime.Caching`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b4e28-171">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>  
  
## <a name="adding-a-button-to-the-wpf-window"></a><span data-ttu-id="b4e28-172">Dodawanie przycisku do okna WPF</span><span class="sxs-lookup"><span data-stu-id="b4e28-172">Adding a Button to the WPF Window</span></span>  
 <span data-ttu-id="b4e28-173">Następnie zostanie dodać kontrolkę przycisku i utworzyć program obsługi zdarzeń dla przycisku `Click` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b4e28-173">Next, you will add a button control and create an event handler for the button's `Click` event.</span></span> <span data-ttu-id="b4e28-174">Później będzie Dodaj kod, więc po kliknięciu przycisku zawartość pliku tekstowego są buforowane i wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="b4e28-174">Later you will add code to so when you click the button, the contents of the text file are cached and displayed.</span></span>  
  
#### <a name="to-add-a-button-control"></a><span data-ttu-id="b4e28-175">Aby dodać kontrolkę przycisku</span><span class="sxs-lookup"><span data-stu-id="b4e28-175">To add a button control</span></span>  
  
1.  <span data-ttu-id="b4e28-176">W **Eksploratora rozwiązań**, kliknij dwukrotnie plik MainWindow.xaml, aby go otworzyć.</span><span class="sxs-lookup"><span data-stu-id="b4e28-176">In **Solution Explorer**, double-click the MainWindow.xaml file to open it.</span></span>  
  
2.  <span data-ttu-id="b4e28-177">Z **przybornika**w obszarze **wspólnych formantów WPF**, przeciągnij `Button` formant `MainWindow` okna.</span><span class="sxs-lookup"><span data-stu-id="b4e28-177">From the **Toolbox**, under **Common WPF Controls**, drag a `Button` control to the `MainWindow` window.</span></span>  
  
3.  <span data-ttu-id="b4e28-178">W **właściwości** ustaw `Content` właściwość `Button` formant **pobrać pamięci podręcznej**.</span><span class="sxs-lookup"><span data-stu-id="b4e28-178">In the **Properties** window, set the `Content` property of the `Button` control to **Get Cache**.</span></span>  
  
## <a name="initializing-the-cache-and-caching-an-entry"></a><span data-ttu-id="b4e28-179">Inicjowanie pamięci podręcznej i buforowania wpis</span><span class="sxs-lookup"><span data-stu-id="b4e28-179">Initializing the Cache and Caching an Entry</span></span>  
 <span data-ttu-id="b4e28-180">Następnie dodasz kod do wykonania następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="b4e28-180">Next, you will add the code to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="b4e28-181">Tworzenie wystąpienia klasy pamięci podręcznej — to znaczy będzie wystąpienia nowy <xref:System.Runtime.Caching.MemoryCache> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b4e28-181">Create an instance of the cache class—that is, you will instantiate a new <xref:System.Runtime.Caching.MemoryCache> object.</span></span>  
  
-   <span data-ttu-id="b4e28-182">Określ, czy korzysta z pamięci podręcznej <xref:System.Runtime.Caching.HostFileChangeMonitor> obiektu do monitorowania zmian w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="b4e28-182">Specify that the cache uses a <xref:System.Runtime.Caching.HostFileChangeMonitor> object to monitor changes in the text file.</span></span>  
  
-   <span data-ttu-id="b4e28-183">Odczytywanie pliku tekstowego i pamięci podręcznej zawartości jako wpis pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b4e28-183">Read the text file and cache its contents as a cache entry.</span></span>  
  
-   <span data-ttu-id="b4e28-184">Wyświetl zawartość pliku tekstowego w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b4e28-184">Display the contents of the cached text file.</span></span>  
  
#### <a name="to-create-the-cache-object"></a><span data-ttu-id="b4e28-185">Można utworzyć obiektu pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="b4e28-185">To create the cache object</span></span>  
  
1.  <span data-ttu-id="b4e28-186">Kliknij dwukrotnie przycisk, który właśnie został dodany w celu utworzenia programu obsługi zdarzeń w pliku MainWindow.xaml.cs lub MainWindow.Xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="b4e28-186">Double-click the button you just added in order to create an event handler in the MainWindow.xaml.cs or MainWindow.Xaml.vb file.</span></span>  
  
2.  <span data-ttu-id="b4e28-187">W górnej części pliku (przed deklaracją klasy), Dodaj następujący `Imports` (Visual Basic) lub `using` — instrukcje (C#):</span><span class="sxs-lookup"><span data-stu-id="b4e28-187">At the top of the file (before the class declaration), add the following `Imports` (Visual Basic) or `using` (C#) statements:</span></span>  
  
    ```csharp  
    using System.Runtime.Caching;  
    using System.IO;  
    ```  
  
    ```vb  
    Imports System.Runtime.Caching  
    Imports System.IO  
    ```  
  
3.  <span data-ttu-id="b4e28-188">W obsłudze zdarzeń Dodaj następujący kod, aby utworzyć wystąpienia obiektu pamięci podręcznej:</span><span class="sxs-lookup"><span data-stu-id="b4e28-188">In the event handler, add the following code to instantiate the cache object:</span></span>  
  
    ```csharp  
    ObjectCache cache = MemoryCache.Default;  
    ```  
  
    ```vb  
    Dim cache As ObjectCache = MemoryCache.Default  
    ```  
  
     <span data-ttu-id="b4e28-189"><xref:System.Runtime.Caching.ObjectCache> Klasa jest klasą wbudowana zapewniająca obiektu w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b4e28-189">The <xref:System.Runtime.Caching.ObjectCache> class is a built-in class that provides an in-memory object cache.</span></span>  
  
4.  <span data-ttu-id="b4e28-190">Dodaj następujący kod do odczytu treści wpis pamięci podręcznej o nazwie `filecontents`:</span><span class="sxs-lookup"><span data-stu-id="b4e28-190">Add the following code to read the contents of a cache entry named `filecontents`:</span></span>  
  
    ```vb  
    Dim fileContents As String = TryCast(cache("filecontents"), String)  
    ```  
  
    ```csharp  
    string fileContents = cache["filecontents"] as string;  
    ```  
  
5.  <span data-ttu-id="b4e28-191">Dodaj następujący kod, aby sprawdzić, czy wpis pamięci podręcznej o nazwie `filecontents` istnieje:</span><span class="sxs-lookup"><span data-stu-id="b4e28-191">Add the following code to check whether the cache entry named `filecontents` exists:</span></span>  
  
    ```vb  
    If fileContents Is Nothing Then  
  
    End If  
    ```  
  
    ```csharp  
    if (fileContents == null)  
    {  
  
    }  
    ```  
  
     <span data-ttu-id="b4e28-192">Wpis pamięci podręcznej określony nie istnieje, należy odczytać pliku tekstowego, dodaj go jako wpis pamięci podręcznej w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b4e28-192">If the specified cache entry does not exist, you must read the text file and add it as a cache entry to the cache.</span></span>  
  
6.  <span data-ttu-id="b4e28-193">W `if/then` bloków, Dodaj następujący kod, aby utworzyć nową <xref:System.Runtime.Caching.CacheItemPolicy> obiekt, który określa, że wpis pamięci podręcznej wygasa po 10 sekundach.</span><span class="sxs-lookup"><span data-stu-id="b4e28-193">In the `if/then` block, add the following code to create a new <xref:System.Runtime.Caching.CacheItemPolicy> object that specifies that the cache entry expires after 10 seconds.</span></span>  
  
    ```vb  
    Dim policy As New CacheItemPolicy()  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)  
    ```  
  
    ```csharp  
    CacheItemPolicy policy = new CacheItemPolicy();  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);  
    ```  
  
     <span data-ttu-id="b4e28-194">Jeśli podano żadnych informacji wykluczenia i wygaśnięcia, wartością domyślną jest <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, co oznacza, że wpisy w pamięci podręcznej nigdy nie wygasa oparte tylko na bezwzględnego czasu.</span><span class="sxs-lookup"><span data-stu-id="b4e28-194">If no eviction or expiration information is provided, the default is <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, which means the cache entries never expire based only on an absolute time.</span></span> <span data-ttu-id="b4e28-195">Zamiast tego wpisy w pamięci podręcznej wygasa tylko w przypadku wykorzystania pamięci.</span><span class="sxs-lookup"><span data-stu-id="b4e28-195">Instead, cache entries expire only when there is memory pressure.</span></span> <span data-ttu-id="b4e28-196">Jako najlepsze rozwiązanie należy zawsze jawnie Podaj bezwzględną lub wygaśnięcia elewacji.</span><span class="sxs-lookup"><span data-stu-id="b4e28-196">As a best practice, you should always explicitly provide either an absolute or a siding expiration.</span></span>  
  
7.  <span data-ttu-id="b4e28-197">Wewnątrz `if/then` blokować i po kodzie dodanym w poprzednim kroku, Dodaj następujący kod, aby utworzyć kolekcję dla ścieżki do plików, które chcesz monitorować i Dodaj ścieżkę do pliku tekstowego do kolekcji:</span><span class="sxs-lookup"><span data-stu-id="b4e28-197">Inside the `if/then` block and following the code you added in the previous step, add the following code to create a collection for the file paths that you want to monitor, and to add the path of the text file to the collection:</span></span>  
  
    ```vb  
    Dim filePaths As New List(Of String)()  
    filePaths.Add("c:\cache\cacheText.txt")  
    ```  
  
    ```csharp  
    List<string> filePaths = new List<string>();  
    filePaths.Add("c:\\cache\\cacheText.txt");  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b4e28-198">Jeśli nie jest plik tekstowy, którego chcesz użyć `c:\cache\cacheText.txt`, określ ścieżkę do pliku tekstowego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="b4e28-198">If the text file you want to use is not `c:\cache\cacheText.txt`, specify the path where the text file is that you want to use.</span></span>  
  
8.  <span data-ttu-id="b4e28-199">Po kodzie dodanym w poprzednim kroku, Dodaj następujący kod, aby dodać nowy <xref:System.Runtime.Caching.HostFileChangeMonitor> obiektu do kolekcji zmiany monitoruje wpisu pamięci podręcznej:</span><span class="sxs-lookup"><span data-stu-id="b4e28-199">Following the code that you added in the previous step, add the following code to add a new <xref:System.Runtime.Caching.HostFileChangeMonitor> object to the collection of change monitors for the cache entry:</span></span>  
  
    ```vb  
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))  
    ```  
  
    ```csharp  
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));  
    ```  
  
     <span data-ttu-id="b4e28-200"><xref:System.Runtime.Caching.HostFileChangeMonitor> Obiekt monitoruje ścieżka pliku tekstowego i powiadamia pamięci podręcznej w przypadku wystąpienia zmian.</span><span class="sxs-lookup"><span data-stu-id="b4e28-200">The <xref:System.Runtime.Caching.HostFileChangeMonitor> object monitors the text file's path and notifies the cache if changes occur.</span></span> <span data-ttu-id="b4e28-201">W tym przykładzie wpis pamięci podręcznej wygasa w przypadku zmiany zawartości pliku.</span><span class="sxs-lookup"><span data-stu-id="b4e28-201">In this example, the cache entry will expire if the content of the file changes.</span></span>  
  
9. <span data-ttu-id="b4e28-202">Po kodzie dodanym w poprzednim kroku dodaj następujący kod, aby odczytać zawartości pliku tekstowego:</span><span class="sxs-lookup"><span data-stu-id="b4e28-202">Following the code that you added in the previous step, add the following code to read the contents of the text file:</span></span>  
  
    ```vb  
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()  
    ```  
  
    ```csharp  
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + + "\n" + DateTime.Now;   
    ```  
  
     <span data-ttu-id="b4e28-203">Data i godzina sygnatury czasowej jest dodawany, dzięki czemu można będzie wyświetlić wygaśnięcia wpisu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b4e28-203">The date and time timestamp is added so that you will be able to see when the cache entry expires.</span></span>  
  
10. <span data-ttu-id="b4e28-204">Po kodzie dodanym w poprzednim kroku, Dodaj następujący kod, aby wstawić zawartość pliku do obiektu pamięci podręcznej jako <xref:System.Runtime.Caching.CacheItem> wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="b4e28-204">Following the code that you added in the previous step, add the following code to insert the contents of the file into the cache object as a <xref:System.Runtime.Caching.CacheItem> instance:</span></span>  
  
    ```vb  
    cache.Set("filecontents", fileContents, policy)  
    ```  
  
    ```csharp  
    cache.Set("filecontents", fileContents, policy);  
    ```  
  
     <span data-ttu-id="b4e28-205">Określ informacje o sposobie wykluczyć wpisu pamięci podręcznej przez przekazanie <xref:System.Runtime.Caching.CacheItemPolicy> obiekt, który został utworzony wcześniej jako parametr.</span><span class="sxs-lookup"><span data-stu-id="b4e28-205">You specify information about how the cache entry should be evicted by passing the <xref:System.Runtime.Caching.CacheItemPolicy> object that you created earlier as a parameter.</span></span>  
  
11. <span data-ttu-id="b4e28-206">Po `if/then` bloków, Dodaj następujący kod, aby wyświetlić zawartość plików w pamięci podręcznej w oknie komunikatu:</span><span class="sxs-lookup"><span data-stu-id="b4e28-206">After the `if/then` block, add the following code to display the cached file content in a message box:</span></span>  
  
    ```vb  
    MessageBox.Show(fileContents)  
    ```  
  
    ```csharp  
    MessageBox.Show(fileContents);  
    ```  
  
12. <span data-ttu-id="b4e28-207">W **kompilacji** menu, kliknij przycisk **kompilacji WPFCaching** Aby skompilować projekt.</span><span class="sxs-lookup"><span data-stu-id="b4e28-207">In the **Build** menu, click **Build WPFCaching** to build your project.</span></span>  
  
## <a name="testing-caching-in-the-wpf-application"></a><span data-ttu-id="b4e28-208">Testowanie buforowanie w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="b4e28-208">Testing Caching in the WPF Application</span></span>  
 <span data-ttu-id="b4e28-209">Teraz możesz przetestować aplikację.</span><span class="sxs-lookup"><span data-stu-id="b4e28-209">You can now test the application.</span></span>  
  
#### <a name="to-test-caching-in-the-wpf-application"></a><span data-ttu-id="b4e28-210">Aby przetestować buforowanie w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="b4e28-210">To test caching in the WPF application</span></span>  
  
1.  <span data-ttu-id="b4e28-211">Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b4e28-211">Press CTRL+F5 to run the application.</span></span>  
  
     <span data-ttu-id="b4e28-212">`MainWindow` Okno jest wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="b4e28-212">The `MainWindow` window is displayed.</span></span>  
  
2.  <span data-ttu-id="b4e28-213">Kliknij przycisk **pobrać pamięci podręcznej**.</span><span class="sxs-lookup"><span data-stu-id="b4e28-213">Click **Get Cache**.</span></span>  
  
     <span data-ttu-id="b4e28-214">Zawartości w pamięci podręcznej z pliku tekstowego jest wyświetlany w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b4e28-214">The cached content from the text file is displayed in a message box.</span></span> <span data-ttu-id="b4e28-215">Zwróć uwagę, znacznik czasu pliku.</span><span class="sxs-lookup"><span data-stu-id="b4e28-215">Notice the timestamp on the file.</span></span>  
  
3.  <span data-ttu-id="b4e28-216">Zamknij okno komunikatu, a następnie kliknij przycisk **pobrać pamięci podręcznej** ponownie**.**</span><span class="sxs-lookup"><span data-stu-id="b4e28-216">Close the message box and then click **Get Cache** again**.**</span></span>  
  
     <span data-ttu-id="b4e28-217">Sygnatura czasowa nie ulega zmianie.</span><span class="sxs-lookup"><span data-stu-id="b4e28-217">The timestamp is unchanged.</span></span> <span data-ttu-id="b4e28-218">Oznacza to, że jest wyświetlany zawartości w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b4e28-218">This indicates the cached content is displayed.</span></span>  
  
4.  <span data-ttu-id="b4e28-219">Zaczekaj 10 sekund lub więcej, a następnie kliknij przycisk **pobrać pamięci podręcznej** ponownie.</span><span class="sxs-lookup"><span data-stu-id="b4e28-219">Wait 10 seconds or more and then click **Get Cache** again.</span></span>  
  
     <span data-ttu-id="b4e28-220">Teraz zostanie wyświetlony nowy znacznik czasu.</span><span class="sxs-lookup"><span data-stu-id="b4e28-220">This time a new timestamp is displayed.</span></span> <span data-ttu-id="b4e28-221">Oznacza to, że zasady pozwalają wygaśnięcia wpisu pamięci podręcznej oraz czy jest wyświetlany nowej zawartości w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b4e28-221">This indicates that the policy let the cache entry expire and that new cached content is displayed.</span></span>  
  
5.  <span data-ttu-id="b4e28-222">W edytorze tekstów otwórz plik tekstowy, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="b4e28-222">In a text editor, open the text file that you created.</span></span> <span data-ttu-id="b4e28-223">Jeszcze nie wprowadzaj żadnych zmian.</span><span class="sxs-lookup"><span data-stu-id="b4e28-223">Do not make any changes yet.</span></span>  
  
6.  <span data-ttu-id="b4e28-224">Zamknij okno komunikatu, a następnie kliknij przycisk **pobrać pamięci podręcznej** ponownie**.**</span><span class="sxs-lookup"><span data-stu-id="b4e28-224">Close the message box and then click **Get Cache** again**.**</span></span>  
  
     <span data-ttu-id="b4e28-225">Zwróć uwagę sygnatura czasowa ponownie.</span><span class="sxs-lookup"><span data-stu-id="b4e28-225">Notice the timestamp again.</span></span>  
  
7.  <span data-ttu-id="b4e28-226">Zmiany w pliku tekstowym, a następnie zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="b4e28-226">Make a change to the text file and then save the file.</span></span>  
  
8.  <span data-ttu-id="b4e28-227">Zamknij okno komunikatu, a następnie kliknij przycisk **pobrać pamięci podręcznej** ponownie.</span><span class="sxs-lookup"><span data-stu-id="b4e28-227">Close the message box and then click **Get Cache** again.</span></span>  
  
     <span data-ttu-id="b4e28-228">Ten komunikat zawiera zaktualizowaną zawartość z pliku tekstowego i Nowa sygnatura czasowa.</span><span class="sxs-lookup"><span data-stu-id="b4e28-228">This message box contains the updated content from the text file and a new timestamp.</span></span> <span data-ttu-id="b4e28-229">Oznacza to, że monitor zmiany pliku hosta wykluczony wpisu pamięci podręcznej natychmiast po zmianie plików, nawet jeśli nie wygasło bezwzględny limit czasu.</span><span class="sxs-lookup"><span data-stu-id="b4e28-229">This indicates that the host-file change monitor evicted the cache entry immediately when you changed the file, even though the absolute timeout period had not expired.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b4e28-230">Można zwiększyć czas wykluczenia 20 sekund lub więcej należy poczekać do wprowadzania zmian w pliku.</span><span class="sxs-lookup"><span data-stu-id="b4e28-230">You can increase the eviction time to 20 seconds or more to allow more time for you to make a change in the file.</span></span>  
  
## <a name="code-example"></a><span data-ttu-id="b4e28-231">Przykład kodu</span><span class="sxs-lookup"><span data-stu-id="b4e28-231">Code Example</span></span>  
 <span data-ttu-id="b4e28-232">Po ukończeniu tego przewodnika, kodu dla projektu, utworzony zostanie podobne do następującego przykładu.</span><span class="sxs-lookup"><span data-stu-id="b4e28-232">After you have completed this walkthrough, the code for the project you created will resemble the following example.</span></span>  
  
 [!code-csharp[CachingWPFApplications#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b4e28-233">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4e28-233">See Also</span></span>  
 <xref:System.Runtime.Caching.MemoryCache>  
 <xref:System.Runtime.Caching.ObjectCache>  
 <xref:System.Runtime.Caching>  
 [<span data-ttu-id="b4e28-234">Buforowanie w aplikacjach .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b4e28-234">Caching in .NET Framework Applications</span></span>](../../../../docs/framework/performance/caching-in-net-framework-applications.md)
