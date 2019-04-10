---
title: Tworzenie aplikacji klienckich programu .NET Framework (WCF Data Services — Szybki Start)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: efea92fa5176641ac64265dfffd44a088115bb61
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305939"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a><span data-ttu-id="2d335-102">Tworzenie aplikacji klienckich programu .NET Framework (WCF Data Services — Szybki Start)</span><span class="sxs-lookup"><span data-stu-id="2d335-102">Creating the .NET Framework Client Application (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="2d335-103">To jest ostatnim zadaniem tego przewodnika Szybki Start usług danych WCF.</span><span class="sxs-lookup"><span data-stu-id="2d335-103">This is the final task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="2d335-104">W ramach tego zadania będzie dodać aplikację konsolową w języku z rozwiązaniem, Dodaj odwołanie do [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych do tej nowej aplikacji klienta i dostępu do źródła danych z aplikacji klienckiej przy użyciu klas usługi danych wygenerowanego klienta i bibliotek klienta OData .</span><span class="sxs-lookup"><span data-stu-id="2d335-104">In this task, you will add a console application to the solution, add a reference to the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed into this new client application, and access the OData feed from the client application by using the generated client data service classes and client libraries.</span></span>

> [!NOTE]
> <span data-ttu-id="2d335-105">Aplikacja kliencka oparte na programie .NET Framework nie jest wymagany dostęp do danych z kanału informacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2d335-105">A .NET Framework-based client application is not required to access a data feed.</span></span> <span data-ttu-id="2d335-106">Usługa danych jest możliwy przez dowolny składnik aplikacji, który zużywa źródła danych OData.</span><span class="sxs-lookup"><span data-stu-id="2d335-106">The data service can be accessed by any application component that consumes an OData feed.</span></span> <span data-ttu-id="2d335-107">Aby uzyskać więcej informacji, zobacz [przy użyciu usługi danych w aplikacji klienckiej](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="2d335-107">For more information, see [Using a Data Service in a Client Application](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).</span></span>

## <a name="to-create-the-client-application-by-using-visual-studio"></a><span data-ttu-id="2d335-108">Aby utworzyć aplikację klienta w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2d335-108">To create the client application by using Visual Studio</span></span>

1. <span data-ttu-id="2d335-109">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="2d335-109">In **Solution Explorer**, right-click the solution, click **Add**, and then click **New Project**.</span></span>

2. <span data-ttu-id="2d335-110">W okienku po lewej stronie wybierz **zainstalowane** > [**Visual C#**  lub **języka Visual Basic**] > **pulpitu Windows**, a następnie wybierz pozycję  **Aplikacja WPF** szablonu.</span><span class="sxs-lookup"><span data-stu-id="2d335-110">In the left pane, select **Installed** > [**Visual C#** or **Visual Basic**] > **Windows Desktop**, and then select the **WPF App** template.</span></span>

3. <span data-ttu-id="2d335-111">Wprowadź `NorthwindClient` nazwę projektu, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2d335-111">Enter `NorthwindClient` for the project name, and then click **OK**.</span></span>

4. <span data-ttu-id="2d335-112">Otwórz plik MainWindow.xaml i Zastąp kod XAML następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="2d335-112">Open the file MainWindow.xaml and replace the XAML code with the following code:</span></span>

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a><span data-ttu-id="2d335-113">Aby dodać odwołanie do usługi danych, do projektu</span><span class="sxs-lookup"><span data-stu-id="2d335-113">To add a data service reference to the project</span></span>

1. <span data-ttu-id="2d335-114">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt NorthwindClient, kliknij przycisk **Dodaj** > **odwołanie do usługi**, a następnie kliknij przycisk **odnajdowania** .</span><span class="sxs-lookup"><span data-stu-id="2d335-114">In **Solution Explorer**, right-click the NorthwindClient project, click **Add** > **Service Reference**, and then click **Discover**.</span></span>

     <span data-ttu-id="2d335-115">Spowoduje to wyświetlenie Usługa danych Northwind, który został utworzony w pierwszym zadaniu.</span><span class="sxs-lookup"><span data-stu-id="2d335-115">This displays the Northwind data service that you created in the first task.</span></span>

2. <span data-ttu-id="2d335-116">W **Namespace** polu tekstowym `Northwind`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2d335-116">In the **Namespace** text box, type `Northwind`, and then click **OK**.</span></span>

     <span data-ttu-id="2d335-117">To dodaje nowy plik kodu do projektu, który zawiera klasy danych, które są używane do uzyskania dostępu i korzystać z zasobów usługi danych jako obiekty.</span><span class="sxs-lookup"><span data-stu-id="2d335-117">This adds a new code file to the project, which contains the data classes that are used to access and interact with data service resources as objects.</span></span> <span data-ttu-id="2d335-118">Klasy danych są tworzone w przestrzeni nazw `NorthwindClient.Northwind`.</span><span class="sxs-lookup"><span data-stu-id="2d335-118">The data classes are created in the namespace `NorthwindClient.Northwind`.</span></span>

## <a name="to-access-data-service-data-in-the-wpf-application"></a><span data-ttu-id="2d335-119">Dostęp do danych usługi danych w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="2d335-119">To access data service data in the WPF application</span></span>

1. <span data-ttu-id="2d335-120">W **Eksploratora rozwiązań** w obszarze **NorthwindClient**, kliknij prawym przyciskiem myszy projekt i kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="2d335-120">In **Solution Explorer** under **NorthwindClient**, right-click the project and click **Add Reference**.</span></span>

2. <span data-ttu-id="2d335-121">W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET** karty, wybierz zestaw System.Data.Services.Client.dll, a następnie kliknij **OK**.</span><span class="sxs-lookup"><span data-stu-id="2d335-121">In the **Add Reference** dialog box, click the **.NET** tab, select the System.Data.Services.Client.dll assembly, and then click **OK**.</span></span>

3. <span data-ttu-id="2d335-122">W **Eksploratora rozwiązań** w obszarze **NorthwindClient**, otwórz stronę kodową dla pliku MainWindow.xaml i Dodaj następujący kod `using` — instrukcja (`Imports` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2d335-122">In **Solution Explorer** under **NorthwindClient**, open the code page for the MainWindow.xaml file, and add the following `using` statement (`Imports` in Visual Basic).</span></span>

     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]

3. <span data-ttu-id="2d335-123">Wstaw następujący kod, który wykonuje kwerendę usługi danych i wiąże wynik, który ma <xref:System.Data.Services.Client.DataServiceCollection%601> do `MainWindow` klasy:</span><span class="sxs-lookup"><span data-stu-id="2d335-123">Insert the following code that queries that data service and binds the result to a <xref:System.Data.Services.Client.DataServiceCollection%601> into the `MainWindow` class:</span></span>

    > [!NOTE]
    > <span data-ttu-id="2d335-124">Należy zastąpić nazwę hosta `localhost:12345` za pomocą serwera i port, który jest hostem Twoje wystąpienie usługi danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="2d335-124">You must replace the host name `localhost:12345` with the server and port that is hosting your instance of the Northwind data service.</span></span>

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]

4. <span data-ttu-id="2d335-125">Wstaw następujący kod, który zapisuje zmiany w `MainWindow` klasy:</span><span class="sxs-lookup"><span data-stu-id="2d335-125">Insert the following code that saves changes into the `MainWindow` class:</span></span>

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a><span data-ttu-id="2d335-126">Aby skompilować i uruchomić aplikację NorthwindClient</span><span class="sxs-lookup"><span data-stu-id="2d335-126">To build and run the NorthwindClient application</span></span>

1. <span data-ttu-id="2d335-127">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt NorthwindClient i wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="2d335-127">In **Solution Explorer**, right-click the NorthwindClient project and select **Set as startup project**.</span></span>

2. <span data-ttu-id="2d335-128">Naciśnij klawisz **F5** do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2d335-128">Press **F5** to start the application.</span></span>

     <span data-ttu-id="2d335-129">Kompiluje rozwiązanie i uruchamia aplikację klienta.</span><span class="sxs-lookup"><span data-stu-id="2d335-129">This builds the solution and starts the client application.</span></span> <span data-ttu-id="2d335-130">Dane są wymagane usługi i wyświetlane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="2d335-130">Data is requested from the service and displayed in the console.</span></span>

3. <span data-ttu-id="2d335-131">Edytowanie wartości w **ilość** kolumny siatki danych, a następnie kliknij przycisk **Zapisz**.</span><span class="sxs-lookup"><span data-stu-id="2d335-131">Edit a value in the **Quantity** column of the data grid, and then click **Save**.</span></span>

     <span data-ttu-id="2d335-132">Zmiany są zapisywane do usługi danych.</span><span class="sxs-lookup"><span data-stu-id="2d335-132">Changes are saved to the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2d335-133">Ta wersja aplikacji NorthwindClient nie obsługuje dodawanie i usuwanie jednostek.</span><span class="sxs-lookup"><span data-stu-id="2d335-133">This version of the NorthwindClient application does not support adding and deleting of entities.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2d335-134">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="2d335-134">Next Steps</span></span>

<span data-ttu-id="2d335-135">Pomyślnie utworzono aplikację kliencką, która uzyskuje dostęp do przykładowej, którą Northwind strumieniowego źródła OData.</span><span class="sxs-lookup"><span data-stu-id="2d335-135">You have successfully created the client application that accesses the sample Northwind OData feed.</span></span> <span data-ttu-id="2d335-136">Również ukończono Przewodnik Szybki Start usług danych WCF!</span><span class="sxs-lookup"><span data-stu-id="2d335-136">You've also completed the WCF Data Services quickstart!</span></span>

<span data-ttu-id="2d335-137">Aby więcej informacji na temat uzyskiwania dostępu do OData Kanał informacyjny z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji, zobacz [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).</span><span class="sxs-lookup"><span data-stu-id="2d335-137">For more information about accessing an OData feed from a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application, see [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2d335-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d335-138">See also</span></span>

- [<span data-ttu-id="2d335-139">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="2d335-139">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [<span data-ttu-id="2d335-140">Zasoby</span><span class="sxs-lookup"><span data-stu-id="2d335-140">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
