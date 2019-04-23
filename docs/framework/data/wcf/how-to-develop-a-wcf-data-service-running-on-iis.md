---
title: 'Instrukcje: Tworzenie usługi danych WCF działającej na serwerze IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 78e8c3cacd89f88cbfa062cb30e5b3474c2614ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517849"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="bd714-102">Instrukcje: Tworzenie usługi danych WCF działającej na serwerze IIS</span><span class="sxs-lookup"><span data-stu-id="bd714-102">How to: Develop a WCF data service running on IIS</span></span>

<span data-ttu-id="bd714-103">W tym temacie pokazano, jak używać usługi danych WCF w celu utworzenia usługi danych, która jest oparta na bazie danych Northwind, która jest hostowana przez aplikację sieci Web programu ASP.NET, która jest uruchomiona na Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="bd714-103">This topic shows how to use WCF Data Services to create a data service that is based on the Northwind sample database that is hosted by an ASP.NET Web application that is running on Internet Information Services (IIS).</span></span> <span data-ttu-id="bd714-104">Aby uzyskać przykład sposobu tworzenia tych samych Usługa danych Northwind jako aplikację sieci Web programu ASP.NET, która działa na serwerze ASP.NET Development Server, zobacz [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="bd714-104">For an example of how to create the same Northwind data service as an ASP.NET Web application that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="bd714-105">Aby utworzyć usługę danych Northwind, należy zainstalowano przykładowej bazy danych Northwind na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="bd714-105">To create the Northwind data service, you must have installed the Northwind sample database on the local computer.</span></span> <span data-ttu-id="bd714-106">Aby pobrać tej przykładowej bazy danych, zobacz stronę pobierania [przykładowych baz danych programu SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="bd714-106">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

 <span data-ttu-id="bd714-107">W tym temacie przedstawiono sposób tworzenia usługi danych przy użyciu dostawcy środowiska Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="bd714-107">This topic shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="bd714-108">Innych dostawców usług danych są dostępne.</span><span class="sxs-lookup"><span data-stu-id="bd714-108">Other data services providers are available.</span></span> <span data-ttu-id="bd714-109">Aby uzyskać więcej informacji, zobacz [dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="bd714-109">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>

 <span data-ttu-id="bd714-110">Po utworzeniu usługi, musisz jawnie określić dostęp do zasobów usługi danych.</span><span class="sxs-lookup"><span data-stu-id="bd714-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="bd714-111">Aby uzyskać więcej informacji, zobacz [jak: Zapewnianie dostępu do usługi danych](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="bd714-111">For more information, see [How to: Enable Access to the Data Service](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="bd714-112">Utwórz aplikację sieci web ASP.NET, która działa na serwerze IIS</span><span class="sxs-lookup"><span data-stu-id="bd714-112">Create the ASP.NET web application that runs on IIS</span></span>

1. <span data-ttu-id="bd714-113">W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="bd714-113">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

2. <span data-ttu-id="bd714-114">W **nowy projekt** okno dialogowe, wybierz opcję **zainstalowane** > [**Visual C#**  lub **języka Visual Basic**] > **sieci Web**  kategorii.</span><span class="sxs-lookup"><span data-stu-id="bd714-114">In the **New Project** dialog box, select the **Installed** > [**Visual C#** or **Visual Basic**] > **Web** category.</span></span>

3. <span data-ttu-id="bd714-115">Wybierz **aplikacji sieci Web ASP.NET** szablonu.</span><span class="sxs-lookup"><span data-stu-id="bd714-115">Select the **ASP.NET Web Application** template.</span></span>

1. <span data-ttu-id="bd714-116">Wprowadź `NorthwindService` jako nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="bd714-116">Enter `NorthwindService` as the name of the project.</span></span>

5. <span data-ttu-id="bd714-117">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="bd714-117">Click **OK**.</span></span>

6. <span data-ttu-id="bd714-118">Na **projektu** menu, wybierz opcję **właściwości NorthwindService**.</span><span class="sxs-lookup"><span data-stu-id="bd714-118">On the **Project** menu, select **NorthwindService Properties**.</span></span>

7. <span data-ttu-id="bd714-119">Wybierz **Web** , a następnie wybierz pozycję **użycia lokalnego serwera sieci Web usług IIS**.</span><span class="sxs-lookup"><span data-stu-id="bd714-119">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>

8. <span data-ttu-id="bd714-120">Kliknij przycisk **Utwórz katalog wirtualny** a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="bd714-120">Click **Create Virtual Directory** and then click **OK**.</span></span>

9. <span data-ttu-id="bd714-121">W wierszu polecenia z uprawnieniami administratora wykonaj jedną z następujących poleceń (w zależności od systemu operacyjnego):</span><span class="sxs-lookup"><span data-stu-id="bd714-121">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    -   <span data-ttu-id="bd714-122">systemy 32-bitowe:</span><span class="sxs-lookup"><span data-stu-id="bd714-122">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    -   <span data-ttu-id="bd714-123">systemy 64-bitowe:</span><span class="sxs-lookup"><span data-stu-id="bd714-123">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     <span data-ttu-id="bd714-124">Dzięki temu czy Windows Communication Foundation (WCF) jest zarejestrowana na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bd714-124">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>

10. <span data-ttu-id="bd714-125">W wierszu polecenia z uprawnieniami administratora wykonaj jedną z następujących poleceń (w zależności od systemu operacyjnego):</span><span class="sxs-lookup"><span data-stu-id="bd714-125">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    -   <span data-ttu-id="bd714-126">systemy 32-bitowe:</span><span class="sxs-lookup"><span data-stu-id="bd714-126">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    -   <span data-ttu-id="bd714-127">systemy 64-bitowe:</span><span class="sxs-lookup"><span data-stu-id="bd714-127">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     <span data-ttu-id="bd714-128">To sprawia, że się upewnić, że usługi IIS działa poprawnie po zainstalowaniu programu WCF na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bd714-128">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="bd714-129">Może być również ponowne uruchomienie usług IIS.</span><span class="sxs-lookup"><span data-stu-id="bd714-129">You might have to also restart IIS.</span></span>

11. <span data-ttu-id="bd714-130">Po uruchomieniu aplikacji ASP.NET w usługach IIS7, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bd714-130">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>

    1. <span data-ttu-id="bd714-131">Otwórz Menedżera usług IIS i przejdź do aplikacji PhotoService w ramach **domyślna witryna sieci Web**.</span><span class="sxs-lookup"><span data-stu-id="bd714-131">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>

    2. <span data-ttu-id="bd714-132">W **widoku funkcji**, kliknij dwukrotnie **uwierzytelniania**.</span><span class="sxs-lookup"><span data-stu-id="bd714-132">In **Features View**, double-click **Authentication**.</span></span>

    3. <span data-ttu-id="bd714-133">Na **uwierzytelniania** wybierz opcję **uwierzytelnianie anonimowe**.</span><span class="sxs-lookup"><span data-stu-id="bd714-133">On the **Authentication** page, select **Anonymous Authentication**.</span></span>

    4. <span data-ttu-id="bd714-134">W **akcje** okienku kliknij **Edytuj** można ustawić zabezpieczeń, jednostki, w którym użytkownicy anonimowi będą łączyć się z witryny.</span><span class="sxs-lookup"><span data-stu-id="bd714-134">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>

    5. <span data-ttu-id="bd714-135">W **edytowanie poświadczeń uwierzytelniania anonimowego** okno dialogowe, wybierz opcję **tożsamość puli aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="bd714-135">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="bd714-136">Gdy używasz konta Usługa sieciowa, udzielasz anonimowym użytkownikom wszystkich dostępu do sieci wewnętrznej powiązanej z tego konta.</span><span class="sxs-lookup"><span data-stu-id="bd714-136">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>

12. <span data-ttu-id="bd714-137">Za pomocą programu SQL Server Management Studio, narzędzia sqlcmd.exe lub edytora języka Transact-SQL w programie Visual Studio, wykonaj następujące polecenie języka Transact-SQL dla wystąpienia programu SQL Server, który zawiera bazę danych Northwind, dołączone:</span><span class="sxs-lookup"><span data-stu-id="bd714-137">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    <span data-ttu-id="bd714-138">Spowoduje to utworzenie nazwy logowania w wystąpieniu programu SQL Server dla konta Windows używane do uruchamiania usług IIS.</span><span class="sxs-lookup"><span data-stu-id="bd714-138">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="bd714-139">Dzięki temu usługi IIS, aby nawiązać połączenie z wystąpieniem programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bd714-139">This enables IIS to connect to the SQL Server instance.</span></span>

13. <span data-ttu-id="bd714-140">Z bazy danych Northwind, dołączony wykonaj następujące polecenia języka Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="bd714-140">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>

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

    <span data-ttu-id="bd714-141">Spowoduje to przydzielenie uprawnień do nowego identyfikatora użytkownika, który umożliwia usługom IIS do odczytu i zapisu danych w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="bd714-141">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="bd714-142">Zdefiniowanie modelu danych</span><span class="sxs-lookup"><span data-stu-id="bd714-142">Define the data model</span></span>

1. <span data-ttu-id="bd714-143">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="bd714-143">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="bd714-144">W **Dodaj nowy element** okno dialogowe, wybierz opcję **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="bd714-144">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="bd714-145">Nazwa modelu danych, wpisz `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="bd714-145">For the name of the data model, type `Northwind.edmx`.</span></span>

4. <span data-ttu-id="bd714-146">W kreatorze modelu danych jednostki, wybierz **Generuj z bazy danych**, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="bd714-146">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="bd714-147">Połączenia z bazą danych modelu danych, wykonując jedną z następujących czynności, a następnie kliknij przycisk **dalej**:</span><span class="sxs-lookup"><span data-stu-id="bd714-147">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    -   <span data-ttu-id="bd714-148">Jeśli nie masz połączenia z bazą danych już skonfigurowane, kliknij przycisk **nowe połączenie** i Utwórz nowe połączenie.</span><span class="sxs-lookup"><span data-stu-id="bd714-148">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="bd714-149">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie połączeń bazy danych SQL Server](https://go.microsoft.com/fwlink/?LinkId=123631).</span><span class="sxs-lookup"><span data-stu-id="bd714-149">For more information, see [How to: Create Connections to SQL Server Databases](https://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="bd714-150">To wystąpienie programu SQL Server musi mieć bazie danych Northwind dołączone.</span><span class="sxs-lookup"><span data-stu-id="bd714-150">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="bd714-151">\- lub —</span><span class="sxs-lookup"><span data-stu-id="bd714-151">\- or -</span></span>

    -   <span data-ttu-id="bd714-152">Jeśli masz już skonfigurowane do łączenia z bazą danych Northwind połączenia z bazą danych, wybierz połączenie z listy połączeń.</span><span class="sxs-lookup"><span data-stu-id="bd714-152">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="bd714-153">Na ostatniej stronie kreatora zaznacz pola wyboru dla wszystkich tabel w bazie danych, a następnie usuń zaznaczenie pól wyboru dla widoków i procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="bd714-153">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="bd714-154">Kliknij przycisk **Zakończ** aby zamknąć kreatora.</span><span class="sxs-lookup"><span data-stu-id="bd714-154">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-data-service"></a><span data-ttu-id="bd714-155">Utworzenie usługi danych</span><span class="sxs-lookup"><span data-stu-id="bd714-155">Create the data service</span></span>

1. <span data-ttu-id="bd714-156">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="bd714-156">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="bd714-157">W **Dodaj nowy element** okno dialogowe, wybierz opcję **usługi danych WCF**.</span><span class="sxs-lookup"><span data-stu-id="bd714-157">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>

   ![Szablon elementu usługi danych WCF w programie Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="bd714-159">**Usługi danych WCF** szablon jest dostępny w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="bd714-159">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="bd714-160">Wprowadź nazwę usługi `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="bd714-160">For the name of the service, enter `Northwind`.</span></span>

     <span data-ttu-id="bd714-161">Program Visual Studio tworzy pliki znaczników i kodu XML dla nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="bd714-161">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="bd714-162">Domyślnie zostanie otwarte okno edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="bd714-162">By default, the code-editor window opens.</span></span> <span data-ttu-id="bd714-163">W **Eksploratora rozwiązań**, usługa ma nazwę, Northwind i rozszerzenia. svc.cs lub. svc.vb.</span><span class="sxs-lookup"><span data-stu-id="bd714-163">In **Solution Explorer**, the service has the name, Northwind, and the extension .svc.cs or .svc.vb.</span></span>

4. <span data-ttu-id="bd714-164">W kodzie dla usługi danych, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych z typem, który jest kontenerem jednostki w modelu danych, który w tym przypadku jest `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="bd714-164">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="bd714-165">Definicja klasy powinna wyglądać to następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bd714-165">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a><span data-ttu-id="bd714-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd714-166">See also</span></span>

- [<span data-ttu-id="bd714-167">Udostępnianie danych jako usługi</span><span class="sxs-lookup"><span data-stu-id="bd714-167">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
