---
title: Tworzenie aplikacji klienckiej .NET Framework (Usługi danych programu WCF Szybki Start)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 9995a509bf997298d991a1f66cfdf3cae6cd0395
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790966"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a><span data-ttu-id="f77cc-102">Tworzenie aplikacji klienckiej .NET Framework (Usługi danych programu WCF Szybki Start)</span><span class="sxs-lookup"><span data-stu-id="f77cc-102">Creating the .NET Framework Client Application (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="f77cc-103">To jest końcowe zadanie Usługi danych programu WCF szybkiego startu.</span><span class="sxs-lookup"><span data-stu-id="f77cc-103">This is the final task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="f77cc-104">W tym zadaniu zostanie dodana Aplikacja konsolowa do rozwiązania, Dodaj odwołanie do [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanału informacyjnego do tej nowej aplikacji klienckiej i dostęp do źródła strumieniowego OData z aplikacji klienckiej przy użyciu wygenerowanych klas usługi danych klienta i bibliotek klienckich .</span><span class="sxs-lookup"><span data-stu-id="f77cc-104">In this task, you will add a console application to the solution, add a reference to the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed into this new client application, and access the OData feed from the client application by using the generated client data service classes and client libraries.</span></span>

> [!NOTE]
> <span data-ttu-id="f77cc-105">Aplikacja kliencka oparta na .NET Framework nie jest wymagana w celu uzyskania dostępu do strumieniowego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f77cc-105">A .NET Framework-based client application is not required to access a data feed.</span></span> <span data-ttu-id="f77cc-106">Dostęp do usługi danych mogą uzyskać każdy składnik aplikacji korzystający z kanału informacyjnego OData.</span><span class="sxs-lookup"><span data-stu-id="f77cc-106">The data service can be accessed by any application component that consumes an OData feed.</span></span> <span data-ttu-id="f77cc-107">Aby uzyskać więcej informacji, zobacz [Korzystanie z usługi danych w aplikacji klienckiej](using-a-data-service-in-a-client-application-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="f77cc-107">For more information, see [Using a Data Service in a Client Application](using-a-data-service-in-a-client-application-wcf-data-services.md).</span></span>

## <a name="to-create-the-client-application-by-using-visual-studio"></a><span data-ttu-id="f77cc-108">Aby utworzyć aplikację kliencką przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f77cc-108">To create the client application by using Visual Studio</span></span>

1. <span data-ttu-id="f77cc-109">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie, kliknij polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="f77cc-109">In **Solution Explorer**, right-click the solution, click **Add**, and then click **New Project**.</span></span>

2. <span data-ttu-id="f77cc-110">W lewym okienku wybierz pozycję **zainstalowane** > [ **C# Visual** lub **Visual Basic**] > **Windows Desktop**, a następnie wybierz szablon **Aplikacja WPF** .</span><span class="sxs-lookup"><span data-stu-id="f77cc-110">In the left pane, select **Installed** > [**Visual C#** or **Visual Basic**] > **Windows Desktop**, and then select the **WPF App** template.</span></span>

3. <span data-ttu-id="f77cc-111">Wprowadź `NorthwindClient` nazwę projektu, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="f77cc-111">Enter `NorthwindClient` for the project name, and then click **OK**.</span></span>

4. <span data-ttu-id="f77cc-112">Otwórz plik MainWindow. XAML i Zastąp kod XAML następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="f77cc-112">Open the file MainWindow.xaml and replace the XAML code with the following code:</span></span>

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a><span data-ttu-id="f77cc-113">Aby dodać odwołanie do usługi danych do projektu</span><span class="sxs-lookup"><span data-stu-id="f77cc-113">To add a data service reference to the project</span></span>

1. <span data-ttu-id="f77cc-114">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt NorthwindClient, kliknij polecenie **Dodaj** > **odwołanie do usługi**, a następnie kliknij przycisk **odkryj**.</span><span class="sxs-lookup"><span data-stu-id="f77cc-114">In **Solution Explorer**, right-click the NorthwindClient project, click **Add** > **Service Reference**, and then click **Discover**.</span></span>

     <span data-ttu-id="f77cc-115">Spowoduje to wyświetlenie usługi danych Northwind utworzonej w pierwszym zadaniu.</span><span class="sxs-lookup"><span data-stu-id="f77cc-115">This displays the Northwind data service that you created in the first task.</span></span>

2. <span data-ttu-id="f77cc-116">W polu tekstowym **przestrzeń nazw** wpisz `Northwind`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="f77cc-116">In the **Namespace** text box, type `Northwind`, and then click **OK**.</span></span>

     <span data-ttu-id="f77cc-117">Spowoduje to dodanie nowego pliku kodu do projektu, który zawiera klasy danych, które są używane do uzyskiwania dostępu do zasobów usługi danych i korzystania z nich jako obiekty.</span><span class="sxs-lookup"><span data-stu-id="f77cc-117">This adds a new code file to the project, which contains the data classes that are used to access and interact with data service resources as objects.</span></span> <span data-ttu-id="f77cc-118">Klasy danych są tworzone w przestrzeni nazw `NorthwindClient.Northwind`.</span><span class="sxs-lookup"><span data-stu-id="f77cc-118">The data classes are created in the namespace `NorthwindClient.Northwind`.</span></span>

## <a name="to-access-data-service-data-in-the-wpf-application"></a><span data-ttu-id="f77cc-119">Aby uzyskać dostęp do danych usługi danych w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="f77cc-119">To access data service data in the WPF application</span></span>

1. <span data-ttu-id="f77cc-120">W **Eksplorator rozwiązań** w obszarze **NorthwindClient**kliknij prawym przyciskiem myszy projekt, a następnie kliknij pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="f77cc-120">In **Solution Explorer** under **NorthwindClient**, right-click the project and click **Add Reference**.</span></span>

2. <span data-ttu-id="f77cc-121">W oknie dialogowym **Dodaj odwołanie** kliknij kartę **.NET** , wybierz zestaw system. Data. Services. Client. dll, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="f77cc-121">In the **Add Reference** dialog box, click the **.NET** tab, select the System.Data.Services.Client.dll assembly, and then click **OK**.</span></span>

3. <span data-ttu-id="f77cc-122">W **Eksplorator rozwiązań** w obszarze **NorthwindClient**Otwórz stronę kodową dla pliku MainWindow. XAML i Dodaj następującą `using` instrukcję (`Imports` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f77cc-122">In **Solution Explorer** under **NorthwindClient**, open the code page for the MainWindow.xaml file, and add the following `using` statement (`Imports` in Visual Basic).</span></span>

    [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#using)]
    [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#using)]

4. <span data-ttu-id="f77cc-123">Wstaw następujący kod, który wysyła zapytanie do tej usługi danych i wiąże wynik z <xref:System.Data.Services.Client.DataServiceCollection%601> `MainWindow` klasą:</span><span class="sxs-lookup"><span data-stu-id="f77cc-123">Insert the following code that queries that data service and binds the result to a <xref:System.Data.Services.Client.DataServiceCollection%601> into the `MainWindow` class:</span></span>

    > [!NOTE]
    > <span data-ttu-id="f77cc-124">Należy zastąpić nazwę `localhost:12345` hosta serwerem i portem, który hostuje wystąpienie usługi danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="f77cc-124">You must replace the host name `localhost:12345` with the server and port that is hosting your instance of the Northwind data service.</span></span>

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#querycode)]

5. <span data-ttu-id="f77cc-125">Wstaw następujący kod, który zapisuje zmiany w `MainWindow` klasie:</span><span class="sxs-lookup"><span data-stu-id="f77cc-125">Insert the following code that saves changes into the `MainWindow` class:</span></span>

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a><span data-ttu-id="f77cc-126">Aby skompilować i uruchomić aplikację NorthwindClient</span><span class="sxs-lookup"><span data-stu-id="f77cc-126">To build and run the NorthwindClient application</span></span>

1. <span data-ttu-id="f77cc-127">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt NorthwindClient i wybierz pozycję **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="f77cc-127">In **Solution Explorer**, right-click the NorthwindClient project and select **Set as startup project**.</span></span>

2. <span data-ttu-id="f77cc-128">Naciśnij klawisz **F5** , aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="f77cc-128">Press **F5** to start the application.</span></span>

     <span data-ttu-id="f77cc-129">Spowoduje to skompilowanie rozwiązania i uruchomienie aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="f77cc-129">This builds the solution and starts the client application.</span></span> <span data-ttu-id="f77cc-130">Dane są żądane z usługi i wyświetlane w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="f77cc-130">Data is requested from the service and displayed in the console.</span></span>

3. <span data-ttu-id="f77cc-131">Edytuj wartość w kolumnie **ilość** siatki danych, a następnie kliknij przycisk **Zapisz**.</span><span class="sxs-lookup"><span data-stu-id="f77cc-131">Edit a value in the **Quantity** column of the data grid, and then click **Save**.</span></span>

     <span data-ttu-id="f77cc-132">Zmiany są zapisywane w usłudze danych.</span><span class="sxs-lookup"><span data-stu-id="f77cc-132">Changes are saved to the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f77cc-133">Ta wersja aplikacji NorthwindClient nie obsługuje dodawania i usuwania jednostek.</span><span class="sxs-lookup"><span data-stu-id="f77cc-133">This version of the NorthwindClient application does not support adding and deleting of entities.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f77cc-134">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f77cc-134">Next Steps</span></span>

<span data-ttu-id="f77cc-135">Pomyślnie utworzono aplikację kliencką, która uzyskuje dostęp do przykładowego źródła danych Northwind OData.</span><span class="sxs-lookup"><span data-stu-id="f77cc-135">You have successfully created the client application that accesses the sample Northwind OData feed.</span></span> <span data-ttu-id="f77cc-136">Ukończono również Usługi danych programu WCF przewodnika Szybki Start.</span><span class="sxs-lookup"><span data-stu-id="f77cc-136">You've also completed the WCF Data Services quickstart!</span></span>

<span data-ttu-id="f77cc-137">Aby uzyskać więcej informacji na temat uzyskiwania dostępu do źródła danych OData z aplikacji .NET Framework, zobacz [usługi danych programu WCF Library Client](wcf-data-services-client-library.md).</span><span class="sxs-lookup"><span data-stu-id="f77cc-137">For more information about accessing an OData feed from a .NET Framework application, see [WCF Data Services Client Library](wcf-data-services-client-library.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f77cc-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f77cc-138">See also</span></span>

- [<span data-ttu-id="f77cc-139">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f77cc-139">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
- [<span data-ttu-id="f77cc-140">Zasoby</span><span class="sxs-lookup"><span data-stu-id="f77cc-140">Resources</span></span>](wcf-data-services-resources.md)
