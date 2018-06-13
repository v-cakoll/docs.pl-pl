---
title: Tworzenie aplikacji klienckich programu .NET Framework (Szybki Start usługi danych WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 09981a7aee2db24d8464bbc7412b82a57ec8115b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365358"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a><span data-ttu-id="49acc-102">Tworzenie aplikacji klienckich programu .NET Framework (Szybki Start usługi danych WCF)</span><span class="sxs-lookup"><span data-stu-id="49acc-102">Creating the .NET Framework Client Application (WCF Data Services Quickstart)</span></span>
<span data-ttu-id="49acc-103">To zadanie końcowego [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Szybki Start.</span><span class="sxs-lookup"><span data-stu-id="49acc-103">This is the final task of the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] quickstart.</span></span> <span data-ttu-id="49acc-104">W tym zadaniu zostanie dodać aplikację konsoli do rozwiązania, Dodaj odwołanie do [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych w tym nową aplikację klienta, a dostęp [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych z aplikacji klienta przy użyciu klasy usługi danych wygenerowanego klienta i klienta biblioteki.</span><span class="sxs-lookup"><span data-stu-id="49acc-104">In this task, you will add a console application to the solution, add a reference to the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed into this new client application, and access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from the client application by using the generated client data service classes and client libraries.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49acc-105">Aplikacja kliencka opartych na programie .NET Framework nie jest wymagane dostępu do danych, źródła danych.</span><span class="sxs-lookup"><span data-stu-id="49acc-105">A .NET Framework-based client application is not required to access a data feed.</span></span> <span data-ttu-id="49acc-106">Usługi danych są dostępne dla każdego składnika aplikacji, który wykorzystuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych.</span><span class="sxs-lookup"><span data-stu-id="49acc-106">The data service can be accessed by any application component that consumes an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="49acc-107">Aby uzyskać więcej informacji, zobacz [przy użyciu usługi danych w aplikacji klienckiej](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="49acc-107">For more information, see [Using a Data Service in a Client Application](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).</span></span>  
  
### <a name="to-create-the-client-application-by-using-visual-studio"></a><span data-ttu-id="49acc-108">Aby utworzyć aplikację klienta przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="49acc-108">To create the client application by using Visual Studio</span></span>  
  
1.  <span data-ttu-id="49acc-109">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="49acc-109">In **Solution Explorer**, right-click the solution, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="49acc-110">W **typy projektów**, kliknij przycisk **Windows**, a następnie wybierz **aplikacji WPF** w **szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="49acc-110">In **Project types**, click **Windows**, and then select **WPF Application** in the **Templates** pane.</span></span>  
  
3.  <span data-ttu-id="49acc-111">Wprowadź `NorthwindClient` nazwę projektu, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="49acc-111">Enter `NorthwindClient` for the project name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="49acc-112">Otwórz plik MainWindow.xaml i Zastąp kod XAML z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="49acc-112">Open the file MainWindow.xaml and replace the XAML code with the following code:</span></span>  
  
     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]  
  
### <a name="to-add-a-data-service-reference-to-the-project"></a><span data-ttu-id="49acc-113">Aby dodać odwołania do danych usługi do projektu</span><span class="sxs-lookup"><span data-stu-id="49acc-113">To add a data service reference to the project</span></span>  
  
1.  <span data-ttu-id="49acc-114">Kliknij prawym przyciskiem myszy projekt NorthwindClient, kliknij przycisk **Dodaj odwołanie do usługi**, a następnie kliknij przycisk **odnajdowania**.</span><span class="sxs-lookup"><span data-stu-id="49acc-114">Right-click the NorthwindClient project, click **Add Service Reference**, and then click **Discover**.</span></span>  
  
     <span data-ttu-id="49acc-115">Spowoduje to wyświetlenie utworzoną w pierwszym zadaniu usługę danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="49acc-115">This displays the Northwind data service that you created in the first task.</span></span>  
  
2.  <span data-ttu-id="49acc-116">W **Namespace** polu tekstowym `Northwind`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="49acc-116">In the **Namespace** text box, type `Northwind`, and then click **OK**.</span></span>  
  
     <span data-ttu-id="49acc-117">Spowoduje to dodanie nowego pliku kodu projektu, który zawiera klasy danych, które są używane do uzyskania dostępu i interakcji z zasobami usługi danych jako obiekty.</span><span class="sxs-lookup"><span data-stu-id="49acc-117">This adds a new code file to the project, which contains the data classes that are used to access and interact with data service resources as objects.</span></span> <span data-ttu-id="49acc-118">Klasy danych są tworzone w obszarze nazw `NorthwindClient.Northwind`.</span><span class="sxs-lookup"><span data-stu-id="49acc-118">The data classes are created in the namespace `NorthwindClient.Northwind`.</span></span>  
  
### <a name="to-access-data-service-data-in-the-wpf-application"></a><span data-ttu-id="49acc-119">Dostęp do danych usługi danych w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="49acc-119">To access data service data in the WPF application</span></span>  
  
1.  <span data-ttu-id="49acc-120">W **Eksploratora rozwiązań** w obszarze **NorthwindClient**, kliknij prawym przyciskiem myszy projekt i kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="49acc-120">In **Solution Explorer** under **NorthwindClient**, right-click the project and click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="49acc-121">W oknie dialogowym Dodawanie odwołania, kliknij przycisk **.NET** , wybierz zestaw System.Data.Services.Client.dll, a następnie kliknij **OK**.</span><span class="sxs-lookup"><span data-stu-id="49acc-121">In the Add Reference dialog box, click the **.NET** tab, select the System.Data.Services.Client.dll assembly, and then click **OK**.</span></span> <span data-ttu-id="49acc-122">W **Eksploratora rozwiązań** w obszarze **NorthwindClient**, otwórz stronę kodu dla pliku MainWindow.xaml i Dodaj następujący `using` instrukcji (`Imports` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="49acc-122">In **Solution Explorer** under **NorthwindClient**, open the code page for the MainWindow.xaml file, and add the following `using` statement (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]  
  
3.  <span data-ttu-id="49acc-123">Wstaw następujący kod, który wysyła zapytanie do tej usługi danych i wiąże wynik, który ma <xref:System.Data.Services.Client.DataServiceCollection%601> do `MainWindow` klasy:</span><span class="sxs-lookup"><span data-stu-id="49acc-123">Insert the following code that queries that data service and binds the result to a <xref:System.Data.Services.Client.DataServiceCollection%601> into the `MainWindow` class:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49acc-124">Należy zastąpić nazwą hosta `localhost:12345` z serwera i port, który jest hostem Twoje wystąpienie usługi danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="49acc-124">You must replace the host name `localhost:12345` with the server and port that is hosting your instance of the Northwind data service.</span></span>  
  
     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]  
  
4.  <span data-ttu-id="49acc-125">Wstaw następujący kod, który zapisuje zmiany w `MainWindow` klasy:</span><span class="sxs-lookup"><span data-stu-id="49acc-125">Insert the following code that saves changes into the `MainWindow` class:</span></span>  
  
     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]  
  
### <a name="to-build-and-run-the-northwindclient-application"></a><span data-ttu-id="49acc-126">Aby skompilować i uruchomić aplikację NorthwindClient</span><span class="sxs-lookup"><span data-stu-id="49acc-126">To build and run the NorthwindClient application</span></span>  
  
1.  <span data-ttu-id="49acc-127">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt NorthwindClient i wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="49acc-127">In **Solution Explorer**, right-click the NorthwindClient project and select **Set as startup project**.</span></span>  
  
2.  <span data-ttu-id="49acc-128">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="49acc-128">Press F5 to start the application.</span></span>  
  
     <span data-ttu-id="49acc-129">Buduje rozwiązanie i uruchamia aplikację klienta.</span><span class="sxs-lookup"><span data-stu-id="49acc-129">This builds the solution and starts the client application.</span></span> <span data-ttu-id="49acc-130">Dane są wymagane przez usługę i wyświetlane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="49acc-130">Data is requested from the service and displayed in the console.</span></span>  
  
3.  <span data-ttu-id="49acc-131">Edytowanie wartości w **ilość** kolumny Siatka danych, a następnie kliknij przycisk **zapisać**.</span><span class="sxs-lookup"><span data-stu-id="49acc-131">Edit a value in the **Quantity** column of the data grid, and then click **Save**.</span></span>  
  
     <span data-ttu-id="49acc-132">Zmiany są zapisywane do usługi danych.</span><span class="sxs-lookup"><span data-stu-id="49acc-132">Changes are saved to the data service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49acc-133">Ta wersja aplikacji NorthwindClient nie obsługuje dodawania i usuwania jednostek.</span><span class="sxs-lookup"><span data-stu-id="49acc-133">This version of the NorthwindClient application does not support adding and deleting of entities.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="49acc-134">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="49acc-134">Next Steps</span></span>  
 <span data-ttu-id="49acc-135">Pomyślnie utworzono aplikacji klienckiej, która uzyskuje dostęp do przykładowej Northwind [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych.</span><span class="sxs-lookup"><span data-stu-id="49acc-135">You have successfully created the client application that accesses the sample Northwind [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="49acc-136">Ukończono również [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Szybki Start.</span><span class="sxs-lookup"><span data-stu-id="49acc-136">You have also completed the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] quickstart.</span></span> <span data-ttu-id="49acc-137">Aby uzyskać więcej informacji na temat uzyskiwania dostępu do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji, zobacz [biblioteki klienta usługi danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).</span><span class="sxs-lookup"><span data-stu-id="49acc-137">For more information about accessing an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application, see [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49acc-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49acc-138">See Also</span></span>  
 [<span data-ttu-id="49acc-139">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="49acc-139">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [<span data-ttu-id="49acc-140">Zasoby</span><span class="sxs-lookup"><span data-stu-id="49acc-140">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
