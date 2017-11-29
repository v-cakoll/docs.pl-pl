---
title: "Tworzenie usługi danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 37d32d938f49d0767594e0f141d5a463ad5fc95f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="creating-the-data-service"></a><span data-ttu-id="16582-102">Tworzenie usługi danych</span><span class="sxs-lookup"><span data-stu-id="16582-102">Creating the Data Service</span></span>
<span data-ttu-id="16582-103">W ramach tego zadania spowoduje utworzenie usługa dane przykładowe z wykorzystaniem [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] do udostępnienia [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych, która jest oparta na bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="16582-103">In this task, you will create a sample data service that uses [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to expose an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed that is based on the Northwind sample database.</span></span> <span data-ttu-id="16582-104">Zadanie obejmuje następujące podstawowe czynności:</span><span class="sxs-lookup"><span data-stu-id="16582-104">The task involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="16582-105">Utwórz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="16582-105">Create an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application.</span></span>  
  
2.  <span data-ttu-id="16582-106">Zdefiniuj modelu danych przy użyciu [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] narzędzia.</span><span class="sxs-lookup"><span data-stu-id="16582-106">Define the data model by using the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] tools.</span></span>  
  
3.  <span data-ttu-id="16582-107">Dodaj usługę danych do aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="16582-107">Add the data service to the Web application.</span></span>  
  
4.  <span data-ttu-id="16582-108">Zapewnianie dostępu do usługi danych.</span><span class="sxs-lookup"><span data-stu-id="16582-108">Enable access to the data service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16582-109">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Aplikacji sieci Web, który jest tworzony podczas wykonania tego zadania jest uruchamiany [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server udostępnione przez [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="16582-109">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application that you create when you complete this task runs on the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server provided by [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="16582-110">Programowanie serwer obsługuje tylko dostęp z komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="16582-110"> Development Server only supports access from the local computer.</span></span> <span data-ttu-id="16582-111">Można również ułatwić testowanie i rozwiązywanie problemów z usługą danych podczas tworzenia, Rozważ uruchomienie aplikacji, która obsługuje usługę danych przy użyciu usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="16582-111">To also make it easier to test and troubleshoot the data service during development, consider running the application that hosts the data service by using Internet Information Services (IIS).</span></span> <span data-ttu-id="16582-112">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi danych WCF działającą na serwerze IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).</span><span class="sxs-lookup"><span data-stu-id="16582-112">For more information, see [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).</span></span>  
  
### <a name="to-create-the-aspnet-web-application"></a><span data-ttu-id="16582-113">Aby utworzyć aplikację sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="16582-113">To create the ASP.NET Web application</span></span>  
  
1.  <span data-ttu-id="16582-114">W [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]na **pliku** menu, wybierz opcję **nowy**, a następnie wybierz **projektu**.</span><span class="sxs-lookup"><span data-stu-id="16582-114">In [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], on the **File** menu, select **New**, and then select **Project**.</span></span>  
  
2.  <span data-ttu-id="16582-115">W **nowy projekt** okno dialogowe, w obszarze albo [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] wybierz **Web** szablonu, a następnie wybierz **aplikacji sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="16582-115">In the **New Project** dialog box, under either [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] select the **Web** template, and then select **ASP.NET Web Application**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="16582-116">Jeśli używasz [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] deweloperów sieci Web, należy utworzyć nową witrynę sieci Web zamiast nowej aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="16582-116">If you use [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web Developer, you must create a new Web site instead of a new Web application.</span></span>  
  
3.  <span data-ttu-id="16582-117">Typ `NorthwindService` jako nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="16582-117">Type `NorthwindService` as the name of the project.</span></span>  
  
4.  <span data-ttu-id="16582-118">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="16582-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="16582-119">(Opcjonalnie) Określ numer portu określonych dla aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="16582-119">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="16582-120">Uwaga: numer portu `12345` jest używany w pozostałej części szybkiego startu.</span><span class="sxs-lookup"><span data-stu-id="16582-120">Note: the port number `12345` is used in the rest of the quickstart.</span></span>  
  
    1.  <span data-ttu-id="16582-121">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu został właśnie utworzony, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="16582-121">In **Solution Explorer**, right-click the name of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project that you just created, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="16582-122">Wybierz **Web** , a następnie ustaw wartość **określonego portu** pole tekstowe służące do `12345`.</span><span class="sxs-lookup"><span data-stu-id="16582-122">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>  
  
### <a name="to-define-the-data-model"></a><span data-ttu-id="16582-123">Aby zdefiniować modelu danych</span><span class="sxs-lookup"><span data-stu-id="16582-123">To define the data model</span></span>  
  
1.  <span data-ttu-id="16582-124">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, a następnie kliknij przycisk **Dodaj nowy element.**</span><span class="sxs-lookup"><span data-stu-id="16582-124">In **Solution Explorer**, right-click the name of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item.**</span></span>  
  
2.  <span data-ttu-id="16582-125">W **Dodaj nowy element** okno dialogowe, kliknij przycisk **danych** szablonu, a następnie wybierz **modelu danych jednostki ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="16582-125">In the **Add New Item** dialog box, click the **Data** template and then select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="16582-126">Wpisz nazwę modelu danych, `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="16582-126">For the name of the data model, type `Northwind.edmx`.</span></span>  
  
4.  <span data-ttu-id="16582-127">W [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] kreatora wybierz opcję **generowania z bazy danych**, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="16582-127">In the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard, select **Generate from Database**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="16582-128">Połączenia z bazą danych modelu danych, wykonując jedną z następujących czynności, a następnie kliknij przycisk **dalej**:</span><span class="sxs-lookup"><span data-stu-id="16582-128">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>  
  
    -   <span data-ttu-id="16582-129">Jeśli nie masz już skonfigurowane połączenie z bazą danych, kliknij przycisk **nowe połączenie** i Utwórz nowe połączenie.</span><span class="sxs-lookup"><span data-stu-id="16582-129">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="16582-130">Aby uzyskać więcej informacji, zobacz [porady: tworzenie połączeń bazy danych programu SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631).</span><span class="sxs-lookup"><span data-stu-id="16582-130">For more information, see [How to: Create Connections to SQL Server Databases](http://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="16582-131">To [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] wystąpienie musi mieć bazie danych Northwind dołączony.</span><span class="sxs-lookup"><span data-stu-id="16582-131">This [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] instance must have the Northwind sample database attached.</span></span>  
  
         <span data-ttu-id="16582-132">\-lub -</span><span class="sxs-lookup"><span data-stu-id="16582-132">\- or -</span></span>  
  
    -   <span data-ttu-id="16582-133">Jeśli masz już skonfigurowana do łączenia z bazą danych Northwind połączenia z bazą danych, wybierz połączenie z listy połączeń.</span><span class="sxs-lookup"><span data-stu-id="16582-133">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>  
  
6.  <span data-ttu-id="16582-134">Na ostatniej stronie kreatora zaznacz pola wyboru dla wszystkich tabel w bazie danych, a następnie usuń zaznaczenie pól wyboru dla widoków i procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="16582-134">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>  
  
7.  <span data-ttu-id="16582-135">Kliknij przycisk **Zakończ** aby zamknąć kreatora.</span><span class="sxs-lookup"><span data-stu-id="16582-135">Click **Finish** to close the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="16582-136">Ten model danych wygenerowanych przedstawia właściwości klucza obcego w typach jednostek.</span><span class="sxs-lookup"><span data-stu-id="16582-136">This generated data model exposes foreign key properties on entity types.</span></span> <span data-ttu-id="16582-137">Utworzone przy użyciu modeli danych [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 nie ma tych właściwości klucza obcego.</span><span class="sxs-lookup"><span data-stu-id="16582-137">Data models created using [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 do not include these foreign key properties.</span></span> <span data-ttu-id="16582-138">W związku z tym należy zaktualizować wszystkie aplikacje klienckie, które zostały utworzone w celu uzyskania dostępu do usługi danych Northwind, który został utworzony przy użyciu klasy usługi danych klienta [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 przed podjęciem próby dostęp do tej wersji usługi danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="16582-138">Because of this, you must update the client data service classes of any client applications that were created to access the Northwind data service that was created using [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 before attempting to access this version of the Northwind data service.</span></span>  
  
### <a name="to-create-the-data-service"></a><span data-ttu-id="16582-139">Aby utworzyć usługę danych</span><span class="sxs-lookup"><span data-stu-id="16582-139">To create the data service</span></span>  
  
1.  <span data-ttu-id="16582-140">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę Twojej [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, a następnie kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="16582-140">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="16582-141">W **Dodaj nowy element** okno dialogowe, wybierz opcję **usługi danych WCF**.</span><span class="sxs-lookup"><span data-stu-id="16582-141">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
3.  <span data-ttu-id="16582-142">Wpisz nazwę usługi, `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="16582-142">For the name of the service, type `Northwind`.</span></span>  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]<span data-ttu-id="16582-143">Program Visual Studio tworzy pliki znaczników i kodu XML dla nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="16582-143">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="16582-144">Domyślnie zostanie otwarte okno edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="16582-144">By default, the code-editor window opens.</span></span> <span data-ttu-id="16582-145">W **Eksploratora rozwiązań**, usługa będzie mieć nazwę, Northwind, z rozszerzeniem. svc.cs lub. svc.vb.</span><span class="sxs-lookup"><span data-stu-id="16582-145">In **Solution Explorer**, the service will have the name, Northwind, with the extension .svc.cs or .svc.vb.</span></span>  
  
4.  <span data-ttu-id="16582-146">W kodzie dla usługi data, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych o typie kontenera jednostek w modelu danych, który w tym przypadku jest `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="16582-146">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="16582-147">Definicja klasy powinien wyglądać to następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="16582-147">The class definition should look this the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### <a name="to-enable-access-to-data-service-resources"></a><span data-ttu-id="16582-148">Aby umożliwić dostęp do zasobów usługi danych</span><span class="sxs-lookup"><span data-stu-id="16582-148">To enable access to data service resources</span></span>  
  
1.  <span data-ttu-id="16582-149">W kodzie dla usługi data, Zastąp kod symbol zastępczy w `InitializeService` funkcji z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="16582-149">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="16582-150">Dzięki temu autoryzowanych klientów miał do odczytu i zapisu do zasobów dla zestawów określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="16582-150">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="16582-151">Każdy klient, który można uzyskać dostępu do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji również dostęp do zasobów udostępnianych przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="16582-151">Any client that can access the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="16582-152">W usłudze danych w środowisku produkcyjnym aby uniemożliwić nieautoryzowany dostęp do zasobów należy również zabezpieczyć samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16582-152">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="16582-153">Aby uzyskać więcej informacji, zobacz [Zabezpieczanie usługi danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="16582-153">For more information, see [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="16582-154">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="16582-154">Next Steps</span></span>  
 <span data-ttu-id="16582-155">Pomyślnie utworzono nową usługę danych, który ujawnia [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych, która jest oparta na bazie danych Northwind, a ma włączony dostęp do źródła dla klientów, które mają uprawnienia do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="16582-155">You have successfully created a new data service that exposes an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application.</span></span> <span data-ttu-id="16582-156">Następnie powoduje uruchomienie usługi danych z [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] i będą uzyskiwać dostęp do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła strumieniowego poprzez przesłanie żądania HTTP GET za pośrednictwem przeglądarki sieci Web:</span><span class="sxs-lookup"><span data-stu-id="16582-156">Next, you will start the data service from [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and you will access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by submitting HTTP GET requests through a Web browser:</span></span>  
  
 [<span data-ttu-id="16582-157">Uzyskiwanie dostępu do usługi z przeglądarki sieci Web</span><span class="sxs-lookup"><span data-stu-id="16582-157">Accessing the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a><span data-ttu-id="16582-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16582-158">See Also</span></span>  
 [<span data-ttu-id="16582-159">ADO.NET Entity Data Model Tools</span><span class="sxs-lookup"><span data-stu-id="16582-159">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
