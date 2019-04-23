---
title: Tworzenie usługi danych WCF w programie Visual Studio
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: e8d82ff8958af12842366911b6633ea6b2e0efbb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517229"
---
# <a name="create-the-data-service"></a><span data-ttu-id="75356-102">Utworzenie usługi danych</span><span class="sxs-lookup"><span data-stu-id="75356-102">Create the data service</span></span>

<span data-ttu-id="75356-103">W tym temacie utworzysz usługi danych przykładowych, która używa usługi danych WCF w celu udostępnienia [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych, który jest oparty na bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="75356-103">In this topic, you create a sample data service that uses WCF Data Services to expose an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed that's based on the Northwind sample database.</span></span> <span data-ttu-id="75356-104">Zadanie obejmuje następujące podstawowe kroki:</span><span class="sxs-lookup"><span data-stu-id="75356-104">The task involves the following basic steps:</span></span>

1. <span data-ttu-id="75356-105">Tworzenie aplikacji sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="75356-105">Create an ASP.NET Web application.</span></span>

2. <span data-ttu-id="75356-106">Zdefiniowanie modelu danych za pomocą narzędzi Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="75356-106">Define the data model by using the Entity Data Model tools.</span></span>

3. <span data-ttu-id="75356-107">Dodaj usługę danych do aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="75356-107">Add the data service to the Web application.</span></span>

4. <span data-ttu-id="75356-108">Zapewnianie dostępu do usługi danych.</span><span class="sxs-lookup"><span data-stu-id="75356-108">Enable access to the data service.</span></span>

## <a name="create-the-aspnet-web-app"></a><span data-ttu-id="75356-109">Tworzenie aplikacji sieci web platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="75356-109">Create the ASP.NET web app</span></span>

1. <span data-ttu-id="75356-110">W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="75356-110">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

1. <span data-ttu-id="75356-111">W **nowy projekt** okna dialogowego wybierz pozycję Visual Basic lub Visual C# **Web** kategorii, a następnie wybierz **aplikacji sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="75356-111">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** category, and then select **ASP.NET Web Application**.</span></span>

1. <span data-ttu-id="75356-112">Wprowadź `NorthwindService` jako nazwę projektu, a następnie wybierz pozycję **OK**.</span><span class="sxs-lookup"><span data-stu-id="75356-112">Enter `NorthwindService` as the name of the project and then select **OK**.</span></span>

1. <span data-ttu-id="75356-113">W **Nowa aplikacja internetowa ASP.NET** okno dialogowe, wybierz opcję **pusty** , a następnie wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="75356-113">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

1. <span data-ttu-id="75356-114">(Opcjonalnie) Określ określonego numeru portu dla aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="75356-114">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="75356-115">Uwaga: numer portu `12345` jest używany w tej serii tematy w przewodniku Szybki Start.</span><span class="sxs-lookup"><span data-stu-id="75356-115">Note: the port number `12345` is used in this series of quickstart topics.</span></span>

    1. <span data-ttu-id="75356-116">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy na projekt ASP.NET, który został utworzony, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="75356-116">In **Solution Explorer**, right-click on the ASP.NET project that you just created, and then choose **Properties**.</span></span>

    2. <span data-ttu-id="75356-117">Wybierz **Web** , a następnie ustaw wartość **określonego portu** pole tekstowe do `12345`.</span><span class="sxs-lookup"><span data-stu-id="75356-117">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="75356-118">Zdefiniowanie modelu danych</span><span class="sxs-lookup"><span data-stu-id="75356-118">Define the data model</span></span>

1. <span data-ttu-id="75356-119">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="75356-119">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="75356-120">W **Dodaj nowy element** okno dialogowe, wybierz opcję **danych** kategorii, a następnie wybierz **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="75356-120">In the **Add New Item** dialog box, select the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="75356-121">Nazwa modelu danych, można wprowadzić `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="75356-121">For the name of the data model, enter `Northwind.edmx`.</span></span>

4. <span data-ttu-id="75356-122">W **Kreator modelu Entity Data Model**, wybierz opcję **projektancie platformy EF z bazy danych**, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="75356-122">In the **Entity Data Model Wizard**, select **EF Designer from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="75356-123">Połączenia z bazą danych modelu danych, wykonując jedną z następujących czynności, a następnie kliknij przycisk **dalej**:</span><span class="sxs-lookup"><span data-stu-id="75356-123">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    -   <span data-ttu-id="75356-124">Jeśli nie masz połączenia z bazą danych już skonfigurowane, kliknij przycisk **nowe połączenie** i Utwórz nowe połączenie.</span><span class="sxs-lookup"><span data-stu-id="75356-124">If you don't have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="75356-125">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie połączeń bazy danych SQL Server](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="75356-125">For more information, see [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="75356-126">To wystąpienie programu SQL Server musi mieć bazie danych Northwind dołączone.</span><span class="sxs-lookup"><span data-stu-id="75356-126">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="75356-127">\- lub —</span><span class="sxs-lookup"><span data-stu-id="75356-127">\- or -</span></span>

    -   <span data-ttu-id="75356-128">Jeśli masz już skonfigurowane do łączenia z bazą danych Northwind połączenia z bazą danych, wybierz połączenie z listy połączeń.</span><span class="sxs-lookup"><span data-stu-id="75356-128">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="75356-129">Na ostatniej stronie kreatora zaznacz pola wyboru dla wszystkich tabel w bazie danych, a następnie usuń zaznaczenie pól wyboru dla widoków i procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="75356-129">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="75356-130">Kliknij przycisk **Zakończ** aby zamknąć kreatora.</span><span class="sxs-lookup"><span data-stu-id="75356-130">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-wcf-data-service"></a><span data-ttu-id="75356-131">Tworzenie usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="75356-131">Create the WCF data service</span></span>

1. <span data-ttu-id="75356-132">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem platformy ASP.NET, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="75356-132">In **Solution Explorer**, right-click on the ASP.NET project, and then choose **Add** > **New Item**.</span></span>

2. <span data-ttu-id="75356-133">W **Dodaj nowy element** okno dialogowe, wybierz opcję **usługi danych WCF** szablonu elementu z **Web** kategorii.</span><span class="sxs-lookup"><span data-stu-id="75356-133">In the **Add New Item** dialog box, select the **WCF Data Service** item template from the **Web** category.</span></span>

   ![Szablon elementu usługi danych WCF w programie Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="75356-135">**Usługi danych WCF** szablon jest dostępny w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="75356-135">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="75356-136">Aby uzyskać nazwę usługi, wpisz `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="75356-136">For the name of the service, type `Northwind`.</span></span>

     <span data-ttu-id="75356-137">Program Visual Studio tworzy pliki znaczników i kodu XML dla nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="75356-137">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="75356-138">Domyślnie zostanie otwarte okno edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="75356-138">By default, the code-editor window opens.</span></span> <span data-ttu-id="75356-139">W **Eksploratora rozwiązań**, usługa ma nazwę Northwind z rozszerzeniem *. svc.cs* lub *. svc.vb*.</span><span class="sxs-lookup"><span data-stu-id="75356-139">In **Solution Explorer**, the service has the name Northwind with the extension *.svc.cs* or *.svc.vb*.</span></span>

4. <span data-ttu-id="75356-140">W kodzie dla usługi danych, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych z typem, który jest kontenerem jednostki w modelu danych, który w tym przypadku jest `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="75356-140">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="75356-141">Definicja klasy powinna wyglądać to następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="75356-141">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a><span data-ttu-id="75356-142">Zapewnianie dostępu do zasobów usługi danych</span><span class="sxs-lookup"><span data-stu-id="75356-142">Enable access to data service resources</span></span>

1. <span data-ttu-id="75356-143">W kodzie dla usługi danych, Zastąp kod symbolu zastępczego `InitializeService` funkcji następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="75356-143">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     <span data-ttu-id="75356-144">Dzięki temu autoryzowanych klientów do odczytu i zapisu do zasobów dla określonej jednostki zestawów.</span><span class="sxs-lookup"><span data-stu-id="75356-144">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>

    > [!NOTE]
    > <span data-ttu-id="75356-145">Każdy klient, który może uzyskiwać dostęp do aplikacji ASP.NET również dostęp do zasobów udostępnianych przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="75356-145">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="75356-146">W środowisku produkcyjnym usługi danych Aby uniemożliwić nieautoryzowany dostęp do zasobów należy również zabezpieczyć samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="75356-146">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="75356-147">Aby uzyskać więcej informacji, zobacz [zabezpieczania usług danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="75356-147">For more information, see [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="75356-148">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="75356-148">Next steps</span></span>

<span data-ttu-id="75356-149">Pomyślnie utworzono nową usługę danych, która uwidoczni źródło OData opartego na bazie danych Northwind i włączono dostęp do źródła danych dla klientów, które mają uprawnienia do aplikacji sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="75356-149">You have successfully created a new data service that exposes an OData feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the ASP.NET Web application.</span></span> <span data-ttu-id="75356-150">Następnie będzie uruchomić usługi danych z programu Visual Studio i dostęp do źródła danych przez przesłanie żądania HTTP GET, za pośrednictwem przeglądarki sieci Web OData:</span><span class="sxs-lookup"><span data-stu-id="75356-150">Next, you'll start the data service from Visual Studio and access the OData feed by submitting HTTP GET requests through a Web browser:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="75356-151">Dostęp do usługi z przeglądarki sieci web</span><span class="sxs-lookup"><span data-stu-id="75356-151">Access the service from a web browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="75356-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75356-152">See also</span></span>

- <span data-ttu-id="75356-153">[Narzędzia do modelu danych jednostki ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="75356-153">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>