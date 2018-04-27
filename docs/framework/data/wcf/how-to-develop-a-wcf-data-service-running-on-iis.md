---
title: 'Porady: Tworzenie usługi danych WCF działającą na serwerze IIS'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f9df38d200be864ab24efdb0d002fe7b75cfc3e4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="cae27-102">Porady: Tworzenie usługi danych WCF działającą na serwerze IIS</span><span class="sxs-lookup"><span data-stu-id="cae27-102">How to: Develop a WCF Data Service Running on IIS</span></span>
<span data-ttu-id="cae27-103">W tym temacie przedstawiono sposób użycia [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Aby utworzyć usługę danych, która jest oparta na bazie danych Northwind hostowanej przez aplikacji sieci Web ASP.NET, która działa na Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="cae27-103">This topic shows how to use [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to create a data service that is based on the Northwind sample database that is hosted by an ASP.NET Web application that is running on Internet Information Services (IIS).</span></span> <span data-ttu-id="cae27-104">Na przykład sposobu tworzenia tej samej usługi danych Northwind jako aplikacji sieci Web ASP.NET, która działa w ASP.NET Development Server zobacz [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="cae27-104">For an example of how to create the same Northwind data service as an ASP.NET Web application that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cae27-105">Aby utworzyć usługę danych Northwind, musi zainstalowano przykładowej bazy danych Northwind na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="cae27-105">To create the Northwind data service, you must have installed the Northwind sample database on the local computer.</span></span> <span data-ttu-id="cae27-106">Aby pobrać tej przykładowej bazy danych, zobacz stronę pobierania [przykładowe bazy danych programu SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="cae27-106">To download this sample database, see the download page, [Sample Databases for SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span></span>  
  
 <span data-ttu-id="cae27-107">W tym temacie przedstawiono sposób tworzenia usługi danych przy użyciu dostawcy programu Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="cae27-107">This topic shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="cae27-108">Innych dostawców usług danych są dostępne.</span><span class="sxs-lookup"><span data-stu-id="cae27-108">Other data services providers are available.</span></span> <span data-ttu-id="cae27-109">Aby uzyskać więcej informacji, zobacz [dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="cae27-109">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="cae27-110">Po utworzeniu usługi musi jawnie zapewniają dostęp do zasobów usługi danych.</span><span class="sxs-lookup"><span data-stu-id="cae27-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="cae27-111">Aby uzyskać więcej informacji, zobacz [porady: Włączanie dostępu do usługi Data](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="cae27-111">For more information, see [How to: Enable Access to the Data Service](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>  
  
### <a name="to-create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="cae27-112">Aby utworzyć aplikację sieci Web programu ASP.NET, która działa na serwerze IIS</span><span class="sxs-lookup"><span data-stu-id="cae27-112">To create the ASP.NET Web application that runs on IIS</span></span>  
  
1.  <span data-ttu-id="cae27-113">W programie Visual Studio na **pliku** menu, wybierz opcję **nowy**, a następnie wybierz **projektu**.</span><span class="sxs-lookup"><span data-stu-id="cae27-113">In Visual Studio, on the **File** menu, select **New**, and then select **Project**.</span></span>  
  
2.  <span data-ttu-id="cae27-114">W **nowy projekt** oknie dialogowym wybierz jako język programowania Visual Basic lub Visual C#.</span><span class="sxs-lookup"><span data-stu-id="cae27-114">In the **New Project** dialog box, select either Visual Basic or Visual C# as the programming language.</span></span>  
  
3.  <span data-ttu-id="cae27-115">W **szablony** okienku wybierz **aplikacji sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="cae27-115">In the **Templates** pane, select **ASP.NET Web Application**.</span></span> <span data-ttu-id="cae27-116">Uwaga: Jeśli używasz programu Visual Studio Web Developer, należy utworzyć nową witrynę sieci Web zamiast nowej aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cae27-116">Note: If you use Visual Studio Web Developer, you must create a new Web site instead of a new Web application.</span></span>  
  
4.  <span data-ttu-id="cae27-117">Typ `NorthwindService` jako nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="cae27-117">Type `NorthwindService` as the name of the project.</span></span>  
  
5.  <span data-ttu-id="cae27-118">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="cae27-118">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="cae27-119">Na **projektu** menu, wybierz opcję **NorthwindService właściwości**.</span><span class="sxs-lookup"><span data-stu-id="cae27-119">On the **Project** menu, select **NorthwindService Properties**.</span></span>  
  
7.  <span data-ttu-id="cae27-120">Wybierz **Web** , a następnie wybierz **użycia lokalnego serwera sieci Web usług IIS**.</span><span class="sxs-lookup"><span data-stu-id="cae27-120">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>  
  
8.  <span data-ttu-id="cae27-121">Kliknij przycisk **utworzyć katalog wirtualny** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="cae27-121">Click **Create Virtual Directory** and then click **OK**.</span></span>  
  
9. <span data-ttu-id="cae27-122">W wierszu polecenia z uprawnieniami administratora wykonaj jedną z następujących poleceń (w zależności od systemu operacyjnego):</span><span class="sxs-lookup"><span data-stu-id="cae27-122">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>  
  
    -   <span data-ttu-id="cae27-123">systemy 32-bitowe:</span><span class="sxs-lookup"><span data-stu-id="cae27-123">32-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
    -   <span data-ttu-id="cae27-124">systemy 64-bitowe:</span><span class="sxs-lookup"><span data-stu-id="cae27-124">64-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
     <span data-ttu-id="cae27-125">Dzięki temu czy Windows Communication Foundation (WCF) jest zarejestrowana na komputerze.</span><span class="sxs-lookup"><span data-stu-id="cae27-125">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>  
  
10. <span data-ttu-id="cae27-126">W wierszu polecenia z uprawnieniami administratora wykonaj jedną z następujących poleceń (w zależności od systemu operacyjnego):</span><span class="sxs-lookup"><span data-stu-id="cae27-126">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>  
  
    -   <span data-ttu-id="cae27-127">systemy 32-bitowe:</span><span class="sxs-lookup"><span data-stu-id="cae27-127">32-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
    -   <span data-ttu-id="cae27-128">systemy 64-bitowe:</span><span class="sxs-lookup"><span data-stu-id="cae27-128">64-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
     <span data-ttu-id="cae27-129">Dzięki temu czy programu IIS działa poprawnie po zainstalowaniu na komputerze usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="cae27-129">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="cae27-130">Może być również ponowne uruchomienie usług IIS.</span><span class="sxs-lookup"><span data-stu-id="cae27-130">You might have to also restart IIS.</span></span>  
  
11. <span data-ttu-id="cae27-131">Po uruchomieniu aplikacji ASP.NET w usługach IIS7, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cae27-131">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="cae27-132">Otwórz Menedżera usług IIS i przejdź do aplikacji PhotoService **domyślna witryna sieci Web**.</span><span class="sxs-lookup"><span data-stu-id="cae27-132">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>  
  
    2.  <span data-ttu-id="cae27-133">W **widoku funkcji**, kliknij dwukrotnie **uwierzytelniania**.</span><span class="sxs-lookup"><span data-stu-id="cae27-133">In **Features View**, double-click **Authentication**.</span></span>  
  
    3.  <span data-ttu-id="cae27-134">Na **uwierzytelniania** wybierz pozycję **uwierzytelnianie anonimowe**.</span><span class="sxs-lookup"><span data-stu-id="cae27-134">On the **Authentication** page, select **Anonymous Authentication**.</span></span>  
  
    4.  <span data-ttu-id="cae27-135">W **akcje** okienku, kliknij przycisk **Edytuj** można ustawić zabezpieczeń, podmiotu zabezpieczeń, w których użytkownicy anonimowi będą połączyć się z witryną.</span><span class="sxs-lookup"><span data-stu-id="cae27-135">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>  
  
    5.  <span data-ttu-id="cae27-136">W **edytowanie poświadczeń uwierzytelniania anonimowego** okno dialogowe, wybierz opcję **tożsamość puli aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="cae27-136">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="cae27-137">Gdy używasz konta Usługa sieciowa, udzielasz anonimowym wszystkich dostępu do sieci wewnętrznej powiązanej z tym kontem.</span><span class="sxs-lookup"><span data-stu-id="cae27-137">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>  
  
12. <span data-ttu-id="cae27-138">Za pomocą programu SQL Server Management Studio, narzędzia sqlcmd.exe lub edytor języka Transact-SQL w programie Visual Studio, uruchom następujące polecenie języka Transact-SQL dla wystąpienia programu SQL Server, która ma dołączyć bazy danych Northwind:</span><span class="sxs-lookup"><span data-stu-id="cae27-138">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>  
  
    ```sql  
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;  
    GO   
    ```  
  
     <span data-ttu-id="cae27-139">Spowoduje to utworzenie nazwy logowania w wystąpieniu programu SQL Server dla konta systemu Windows używane do uruchamiania usług IIS.</span><span class="sxs-lookup"><span data-stu-id="cae27-139">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="cae27-140">Dzięki temu usług IIS nawiązać połączenie z wystąpieniem serwera SQL.</span><span class="sxs-lookup"><span data-stu-id="cae27-140">This enables IIS to connect to the SQL Server instance.</span></span>  
  
13. <span data-ttu-id="cae27-141">Z bazy danych Northwind dołączonej wykonaj następujące polecenia języka Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="cae27-141">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>  
  
    ```sql  
    USE Northwind  
    GO  
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]   
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];  
    GO  
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]   
    WITH DEFAULT_DATABASE=[Northwind];   
    GO  
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'  
    GO  
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'  
    GO   
    ```  
  
     <span data-ttu-id="cae27-142">Spowoduje to przydzielenie uprawnień do nowego identyfikatora użytkownika, który umożliwia usługom IIS do odczytu i zapisu danych do bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="cae27-142">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>  
  
### <a name="to-define-the-data-model"></a><span data-ttu-id="cae27-143">Aby zdefiniować modelu danych</span><span class="sxs-lookup"><span data-stu-id="cae27-143">To define the data model</span></span>  
  
1.  <span data-ttu-id="cae27-144">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij przycisk **Dodaj nowy element.**</span><span class="sxs-lookup"><span data-stu-id="cae27-144">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add New Item.**</span></span>  
  
2.  <span data-ttu-id="cae27-145">W **Dodaj nowy element** okno dialogowe, wybierz opcję **modelu danych jednostki ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="cae27-145">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="cae27-146">Wpisz nazwę modelu danych, `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="cae27-146">For the name of the data model, type `Northwind.edmx`.</span></span>  
  
4.  <span data-ttu-id="cae27-147">W kreatorze modelu danych jednostki, wybierz **generowania z bazy danych**, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="cae27-147">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="cae27-148">Połączenia z bazą danych modelu danych, wykonując jedną z następujących czynności, a następnie kliknij przycisk **dalej**:</span><span class="sxs-lookup"><span data-stu-id="cae27-148">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>  
  
    -   <span data-ttu-id="cae27-149">Jeśli nie masz już skonfigurowane połączenie z bazą danych, kliknij przycisk **nowe połączenie** i Utwórz nowe połączenie.</span><span class="sxs-lookup"><span data-stu-id="cae27-149">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="cae27-150">Aby uzyskać więcej informacji, zobacz [porady: tworzenie połączeń bazy danych programu SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631).</span><span class="sxs-lookup"><span data-stu-id="cae27-150">For more information, see [How to: Create Connections to SQL Server Databases](http://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="cae27-151">To wystąpienie programu SQL Server musi mieć bazie danych Northwind dołączony.</span><span class="sxs-lookup"><span data-stu-id="cae27-151">This SQL Server instance must have the Northwind sample database attached.</span></span>  
  
         <span data-ttu-id="cae27-152">\- lub -</span><span class="sxs-lookup"><span data-stu-id="cae27-152">\- or -</span></span>  
  
    -   <span data-ttu-id="cae27-153">Jeśli masz już skonfigurowana do łączenia z bazą danych Northwind połączenia z bazą danych, wybierz połączenie z listy połączeń.</span><span class="sxs-lookup"><span data-stu-id="cae27-153">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>  
  
6.  <span data-ttu-id="cae27-154">Na ostatniej stronie kreatora zaznacz pola wyboru dla wszystkich tabel w bazie danych, a następnie usuń zaznaczenie pól wyboru dla widoków i procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="cae27-154">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>  
  
7.  <span data-ttu-id="cae27-155">Kliknij przycisk **Zakończ** aby zamknąć kreatora.</span><span class="sxs-lookup"><span data-stu-id="cae27-155">Click **Finish** to close the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cae27-156">Ten model danych wygenerowanych przedstawia właściwości klucza obcego w typach jednostek.</span><span class="sxs-lookup"><span data-stu-id="cae27-156">This generated data model exposes foreign key properties on entity types.</span></span> <span data-ttu-id="cae27-157">Modeli danych utworzone za pomocą programu Visual Studio 2008 nie zawierają tych właściwości klucza obcego.</span><span class="sxs-lookup"><span data-stu-id="cae27-157">Data models created using Visual Studio 2008 do not include these foreign key properties.</span></span> <span data-ttu-id="cae27-158">W związku z tym należy zaktualizować żadnych aplikacji klienckich, które zostały utworzone w celu uzyskania dostępu do usługi danych Northwind, który został utworzony przy użyciu programu Visual Studio 2008 przed podjęciem próby wykonania tej wersji usługi danych Northwind dostępu do klasy usługi danych klienta.</span><span class="sxs-lookup"><span data-stu-id="cae27-158">Because of this, you must update the client data service classes of any client applications that were created to access the Northwind data service that was created using Visual Studio 2008 before attempting to access this version of the Northwind data service.</span></span>  
  
### <a name="to-create-the-data-service"></a><span data-ttu-id="cae27-159">Aby utworzyć usługę danych</span><span class="sxs-lookup"><span data-stu-id="cae27-159">To create the data service</span></span>  
  
1.  <span data-ttu-id="cae27-160">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="cae27-160">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="cae27-161">W **Dodaj nowy element** okno dialogowe, wybierz opcję **usług danych ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="cae27-161">In the **Add New Item** dialog box, select **ADO.NET Data Service**.</span></span>  
  
3.  <span data-ttu-id="cae27-162">Wpisz nazwę usługi, `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="cae27-162">For the name of the service, type `Northwind`.</span></span>  
  
     <span data-ttu-id="cae27-163">Program Visual Studio tworzy pliki znaczników i kodu XML dla nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="cae27-163">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="cae27-164">Domyślnie zostanie otwarte okno edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="cae27-164">By default, the code-editor window opens.</span></span> <span data-ttu-id="cae27-165">W **Eksploratora rozwiązań**, usługa będzie mieć nazwę, Northwind, z rozszerzeniem. svc.cs lub. svc.vb.</span><span class="sxs-lookup"><span data-stu-id="cae27-165">In **Solution Explorer**, the service will have the name, Northwind, with the extension .svc.cs or .svc.vb.</span></span>  
  
4.  <span data-ttu-id="cae27-166">W kodzie dla usługi data, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych o typie kontenera jednostek w modelu danych, który w tym przypadku jest `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="cae27-166">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="cae27-167">Definicja klasy powinien wyglądać to następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cae27-167">The class definition should look this the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
## <a name="see-also"></a><span data-ttu-id="cae27-168">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cae27-168">See Also</span></span>  
 [<span data-ttu-id="cae27-169">Udostępnianie danych jako usługi</span><span class="sxs-lookup"><span data-stu-id="cae27-169">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
