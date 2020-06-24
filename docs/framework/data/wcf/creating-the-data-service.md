---
title: Tworzenie usługi danych programu WCF w programie Visual Studio
description: Dowiedz się, jak utworzyć przykładową usługę danych, która używa Usługi danych programu WCF, aby udostępnić strumieniowe dane OData na podstawie przykładowej bazy danych.
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: 739cb6971209792724a2e939ca4f4821d5879c8c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247794"
---
# <a name="create-the-data-service"></a><span data-ttu-id="9da0d-103">Utworzenie usługi danych</span><span class="sxs-lookup"><span data-stu-id="9da0d-103">Create the data service</span></span>

<span data-ttu-id="9da0d-104">W tym temacie opisano Tworzenie przykładowej usługi danych korzystającej z Usługi danych programu WCF w celu udostępnienia kanału informacyjnego protokołu Open Data Protocol (OData), który jest oparty na przykładowej bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="9da0d-104">In this topic, you create a sample data service that uses WCF Data Services to expose an Open Data Protocol (OData) feed that's based on the Northwind sample database.</span></span> <span data-ttu-id="9da0d-105">Zadanie obejmuje następujące podstawowe kroki:</span><span class="sxs-lookup"><span data-stu-id="9da0d-105">The task involves the following basic steps:</span></span>

1. <span data-ttu-id="9da0d-106">Utwórz aplikację sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9da0d-106">Create an ASP.NET Web application.</span></span>

2. <span data-ttu-id="9da0d-107">Zdefiniuj model danych przy użyciu narzędzi Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="9da0d-107">Define the data model by using the Entity Data Model tools.</span></span>

3. <span data-ttu-id="9da0d-108">Dodaj usługę danych do aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9da0d-108">Add the data service to the Web application.</span></span>

4. <span data-ttu-id="9da0d-109">Włącz dostęp do usługi danych.</span><span class="sxs-lookup"><span data-stu-id="9da0d-109">Enable access to the data service.</span></span>

## <a name="create-the-aspnet-web-app"></a><span data-ttu-id="9da0d-110">Tworzenie aplikacji sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9da0d-110">Create the ASP.NET web app</span></span>

1. <span data-ttu-id="9da0d-111">W programie Visual Studio w menu **plik** wybierz pozycję **Nowy**  >  **projekt**.</span><span class="sxs-lookup"><span data-stu-id="9da0d-111">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

1. <span data-ttu-id="9da0d-112">W oknie dialogowym **Nowy projekt** w obszarze Visual Basic lub Visual C# wybierz kategorię **sieci Web** , a następnie wybierz pozycję **aplikacja sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="9da0d-112">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** category, and then select **ASP.NET Web Application**.</span></span>

1. <span data-ttu-id="9da0d-113">Wprowadź `NorthwindService` jako nazwę projektu, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9da0d-113">Enter `NorthwindService` as the name of the project and then select **OK**.</span></span>

1. <span data-ttu-id="9da0d-114">W oknie dialogowym **Nowa aplikacja sieci Web ASP.NET** wybierz opcję **pusty** , a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9da0d-114">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

1. <span data-ttu-id="9da0d-115">Obowiązkowe Określ konkretny numer portu dla aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9da0d-115">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="9da0d-116">Uwaga: numer portu `12345` jest używany w tej serii tematów szybkiego startu.</span><span class="sxs-lookup"><span data-stu-id="9da0d-116">Note: the port number `12345` is used in this series of quickstart topics.</span></span>

    1. <span data-ttu-id="9da0d-117">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt ASP.NET, który właśnie został utworzony, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9da0d-117">In **Solution Explorer**, right-click on the ASP.NET project that you just created, and then choose **Properties**.</span></span>

    2. <span data-ttu-id="9da0d-118">Wybierz kartę **Sieć Web** , a następnie ustaw wartość pola tekstowego **określony port** na `12345` .</span><span class="sxs-lookup"><span data-stu-id="9da0d-118">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="9da0d-119">Zdefiniowanie modelu danych</span><span class="sxs-lookup"><span data-stu-id="9da0d-119">Define the data model</span></span>

1. <span data-ttu-id="9da0d-120">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij pozycję **Dodaj**  >  **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="9da0d-120">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="9da0d-121">W oknie dialogowym **Dodaj nowy element** wybierz kategorię **dane** , a następnie wybierz pozycję **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="9da0d-121">In the **Add New Item** dialog box, select the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="9da0d-122">W polu Nazwa modelu danych wprowadź `Northwind.edmx` .</span><span class="sxs-lookup"><span data-stu-id="9da0d-122">For the name of the data model, enter `Northwind.edmx`.</span></span>

4. <span data-ttu-id="9da0d-123">W **kreatorze Entity Data Model**wybierz pozycję **Dr Designer z bazy danych**, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="9da0d-123">In the **Entity Data Model Wizard**, select **EF Designer from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="9da0d-124">Aby połączyć model danych z bazą danych, wykonaj jedną z następujących czynności, a następnie kliknij przycisk **dalej**:</span><span class="sxs-lookup"><span data-stu-id="9da0d-124">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="9da0d-125">Jeśli nie masz już skonfigurowanego połączenia z bazą danych, kliknij pozycję **nowe połączenie** i Utwórz nowe połączenie.</span><span class="sxs-lookup"><span data-stu-id="9da0d-125">If you don't have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="9da0d-126">Aby uzyskać więcej informacji, zobacz [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="9da0d-126">For more information, see [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="9da0d-127">To wystąpienie SQL Server musi mieć dołączoną przykładową bazę danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="9da0d-127">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="9da0d-128">\-oraz</span><span class="sxs-lookup"><span data-stu-id="9da0d-128">\- or -</span></span>

    - <span data-ttu-id="9da0d-129">Jeśli masz już połączenie z bazą danych do łączenia się z bazą danych Northwind, wybierz to połączenie z listy połączeń.</span><span class="sxs-lookup"><span data-stu-id="9da0d-129">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="9da0d-130">Na ostatniej stronie kreatora zaznacz pola wyboru dla wszystkich tabel w bazie danych, a następnie wyczyść pola wyboru dla widoków i procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="9da0d-130">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="9da0d-131">Kliknij przycisk **Zakończ** , aby zamknąć kreatora.</span><span class="sxs-lookup"><span data-stu-id="9da0d-131">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-wcf-data-service"></a><span data-ttu-id="9da0d-132">Tworzenie usługi danych programu WCF</span><span class="sxs-lookup"><span data-stu-id="9da0d-132">Create the WCF data service</span></span>

1. <span data-ttu-id="9da0d-133">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt ASP.NET, a następnie wybierz polecenie **Dodaj**  >  **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="9da0d-133">In **Solution Explorer**, right-click on the ASP.NET project, and then choose **Add** > **New Item**.</span></span>

2. <span data-ttu-id="9da0d-134">W oknie dialogowym **Dodaj nowy element** wybierz szablon elementu **usługi danych programu WCF** z kategorii **sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="9da0d-134">In the **Add New Item** dialog box, select the **WCF Data Service** item template from the **Web** category.</span></span>

   ![Szablon elementu usługi danych programu WCF w programie Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="9da0d-136">Szablon **usługi danych programu WCF** jest dostępny w programie visual Studio 2015, ale nie w programie visual Studio 2017 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="9da0d-136">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="9da0d-137">W polu Nazwa usługi wpisz `Northwind` .</span><span class="sxs-lookup"><span data-stu-id="9da0d-137">For the name of the service, type `Northwind`.</span></span>

     <span data-ttu-id="9da0d-138">Program Visual Studio tworzy znaczniki XML i pliki kodu dla nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="9da0d-138">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="9da0d-139">Domyślnie zostanie otwarte okno edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="9da0d-139">By default, the code-editor window opens.</span></span> <span data-ttu-id="9da0d-140">W **Eksplorator rozwiązań**usługa ma nazwę Northwind z rozszerzeniem *. svc.cs* lub *. svc. vb*.</span><span class="sxs-lookup"><span data-stu-id="9da0d-140">In **Solution Explorer**, the service has the name Northwind with the extension *.svc.cs* or *.svc.vb*.</span></span>

4. <span data-ttu-id="9da0d-141">W kodzie usługi danych Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych z typem, który jest kontenerem jednostek modelu danych, w tym przypadku `NorthwindEntities` .</span><span class="sxs-lookup"><span data-stu-id="9da0d-141">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="9da0d-142">Definicja klasy powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="9da0d-142">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a><span data-ttu-id="9da0d-143">Zapewnianie dostępu do zasobów usługi danych</span><span class="sxs-lookup"><span data-stu-id="9da0d-143">Enable access to data service resources</span></span>

1. <span data-ttu-id="9da0d-144">W kodzie usługi danych Zastąp symbol zastępczy w `InitializeService` funkcji następującymi elementami:</span><span class="sxs-lookup"><span data-stu-id="9da0d-144">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     <span data-ttu-id="9da0d-145">Dzięki temu autoryzowani klienci mają dostęp do odczytu i zapisu do zasobów dla określonych zestawów jednostek.</span><span class="sxs-lookup"><span data-stu-id="9da0d-145">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9da0d-146">Każdy klient, który może uzyskać dostęp do aplikacji ASP.NET, może również uzyskać dostęp do zasobów udostępnianych przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="9da0d-146">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="9da0d-147">W usłudze danych produkcyjnych aby zapobiec nieautoryzowanemu dostępowi do zasobów, należy również zabezpieczyć samą aplikację.</span><span class="sxs-lookup"><span data-stu-id="9da0d-147">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="9da0d-148">Aby uzyskać więcej informacji, zobacz [zabezpieczanie usługi danych programu WCF](securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="9da0d-148">For more information, see [Securing WCF Data Services](securing-wcf-data-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9da0d-149">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="9da0d-149">Next steps</span></span>

<span data-ttu-id="9da0d-150">Pomyślnie utworzono nową usługę danych, która udostępnia strumieniowe dane OData oparte na przykładowej bazie danych Northwind, i włączono dostęp do kanału informacyjnego dla klientów, którzy mają uprawnienia do aplikacji sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9da0d-150">You have successfully created a new data service that exposes an OData feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the ASP.NET Web application.</span></span> <span data-ttu-id="9da0d-151">Następnie należy uruchomić usługę danych z programu Visual Studio i uzyskać dostęp do źródła strumieniowego OData przez przesłanie żądań HTTP GET za pośrednictwem przeglądarki sieci Web:</span><span class="sxs-lookup"><span data-stu-id="9da0d-151">Next, you'll start the data service from Visual Studio and access the OData feed by submitting HTTP GET requests through a Web browser:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9da0d-152">Uzyskiwanie dostępu do usługi z przeglądarki sieci Web</span><span class="sxs-lookup"><span data-stu-id="9da0d-152">Access the service from a web browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="9da0d-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9da0d-153">See also</span></span>

- <span data-ttu-id="9da0d-154">[Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9da0d-154">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
