---
title: 'Instrukcje: Tworzenie usługi danych przy użyciu źródła danych ADO.NET Entity Framework (Usługi danych programu WCF)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 8c597738d656b32e7b4c75246027b726f425c6ef
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053015"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="ac67d-102">Instrukcje: Tworzenie usługi danych przy użyciu źródła danych ADO.NET Entity Framework (Usługi danych programu WCF)</span><span class="sxs-lookup"><span data-stu-id="ac67d-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>

<span data-ttu-id="ac67d-103">Usługi danych programu WCF udostępnia dane jednostki jako usługę danych.</span><span class="sxs-lookup"><span data-stu-id="ac67d-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="ac67d-104">Te dane jednostki są udostępniane przez platformę ADO. webentity Framework, gdy źródłem danych jest relacyjna baza danych.</span><span class="sxs-lookup"><span data-stu-id="ac67d-104">This entity data is provided by the ADO.NETEntity Framework when the data source is a relational database.</span></span> <span data-ttu-id="ac67d-105">W tym temacie pokazano, jak utworzyć model danych oparty na Entity Framework w aplikacji sieci Web programu Visual Studio, która jest oparta na istniejącej bazie danych, i korzystać z tego modelu danych w celu utworzenia nowej usługi danych.</span><span class="sxs-lookup"><span data-stu-id="ac67d-105">This topic shows you how to create an Entity Framework-based data model in a Visual Studio Web application that is based on an existing database and use this data model to create a new data service.</span></span>

<span data-ttu-id="ac67d-106">Entity Framework udostępnia również narzędzie wiersza polecenia, które może generować model Entity Framework poza projektem programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ac67d-106">The Entity Framework also provides a command line tool that can generate an Entity Framework model outside of a Visual Studio project.</span></span> <span data-ttu-id="ac67d-107">Aby uzyskać więcej informacji, zobacz [jak: Użyj programu EdmGen. exe, aby wygenerować model i pliki](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)mapowania.</span><span class="sxs-lookup"><span data-stu-id="ac67d-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="ac67d-108">Aby dodać model Entity Framework, który jest oparty na istniejącej bazie danych w istniejącej aplikacji sieci Web</span><span class="sxs-lookup"><span data-stu-id="ac67d-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>

1. <span data-ttu-id="ac67d-109">W menu **projekt** kliknij polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="ac67d-109">On the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="ac67d-110">W okienku **Szablony** kliknij kategorię **dane** , a następnie wybierz pozycję **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="ac67d-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="ac67d-111">Wprowadź nazwę modelu, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="ac67d-111">Enter the model name and then click **Add**.</span></span>

     <span data-ttu-id="ac67d-112">Zostanie wyświetlona pierwsza strona kreatora Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="ac67d-112">The first page of the Entity Data Model Wizard is displayed.</span></span>

4. <span data-ttu-id="ac67d-113">W oknie dialogowym **Wybierz zawartość modelu** wybierz pozycję **Generuj z bazy danych**.</span><span class="sxs-lookup"><span data-stu-id="ac67d-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="ac67d-114">Następnie kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="ac67d-114">Then click **Next**.</span></span>

5. <span data-ttu-id="ac67d-115">Kliknij przycisk **nowe połączenie** .</span><span class="sxs-lookup"><span data-stu-id="ac67d-115">Click the **New Connection** button.</span></span>

6. <span data-ttu-id="ac67d-116">W oknie dialogowym **Właściwości połączenia** wpisz nazwę serwera, wybierz metodę uwierzytelniania, wpisz nazwę bazy danych, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ac67d-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>

     <span data-ttu-id="ac67d-117">Okno dialogowe **Wybieranie połączenia danych** zostanie zaktualizowane przy użyciu ustawień połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="ac67d-117">The **Choose Your Data Connection** dialog box is updated with your database connection settings.</span></span>

7. <span data-ttu-id="ac67d-118">Upewnij się, że pole wyboru **Zapisz ustawienia połączenia jednostek w pliku App. config as:** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="ac67d-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="ac67d-119">Następnie kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="ac67d-119">Then click **Next**.</span></span>

8. <span data-ttu-id="ac67d-120">W oknie dialogowym **Wybierz obiekty bazy danych** wybierz wszystkie obiekty bazy danych, które planujesz uwidocznić w usłudze danych.</span><span class="sxs-lookup"><span data-stu-id="ac67d-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ac67d-121">Obiekty zawarte w modelu danych nie są automatycznie uwidaczniane przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="ac67d-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="ac67d-122">Muszą być jawnie udostępniane przez samą usługę.</span><span class="sxs-lookup"><span data-stu-id="ac67d-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="ac67d-123">Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="ac67d-123">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>

9. <span data-ttu-id="ac67d-124">Kliknij przycisk **Zakończ** , aby zakończyć pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="ac67d-124">Click **Finish** to complete the wizard.</span></span>

     <span data-ttu-id="ac67d-125">Spowoduje to utworzenie domyślnego modelu danych opartego na określonej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="ac67d-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="ac67d-126">Entity Framework umożliwia dostosowanie modelu danych.</span><span class="sxs-lookup"><span data-stu-id="ac67d-126">The Entity Framework enables to customize the data model.</span></span> <span data-ttu-id="ac67d-127">Aby uzyskać więcej informacji, zobacz [Entity Data Model narzędzia zadań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ac67d-127">For more information, see [Entity Data Model Tools Tasks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).</span></span>

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="ac67d-128">Aby utworzyć usługę danych przy użyciu nowego modelu danych</span><span class="sxs-lookup"><span data-stu-id="ac67d-128">To create the data service by using the new data model</span></span>

1. <span data-ttu-id="ac67d-129">W programie Visual Studio Otwórz plik. edmx, który reprezentuje model danych.</span><span class="sxs-lookup"><span data-stu-id="ac67d-129">In Visual Studio, open the .edmx file that represents the data model.</span></span>

2. <span data-ttu-id="ac67d-130">W **przeglądarce modelu**kliknij prawym przyciskiem myszy Model, kliknij polecenie **Właściwości**, a następnie zanotuj nazwę kontenera jednostek.</span><span class="sxs-lookup"><span data-stu-id="ac67d-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>

3. <span data-ttu-id="ac67d-131">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="ac67d-131">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

4. <span data-ttu-id="ac67d-132">W oknie dialogowym **Dodaj nowy element** wybierz szablon **usługi danych programu WCF** w kategorii **Sieć Web** .</span><span class="sxs-lookup"><span data-stu-id="ac67d-132">In the **Add New Item** dialog box, select the **WCF Data Service** template in the **Web** category.</span></span>

   ![Szablon elementu usługi danych programu WCF w programie Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="ac67d-134">Szablon **usługi danych programu WCF** jest dostępny w programie visual Studio 2015, ale nie w programie visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ac67d-134">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

5. <span data-ttu-id="ac67d-135">Podaj nazwę usługi, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ac67d-135">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="ac67d-136">Program Visual Studio tworzy znaczniki XML i pliki kodu dla nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="ac67d-136">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="ac67d-137">Domyślnie zostanie otwarte okno edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="ac67d-137">By default, the code-editor window opens.</span></span>

6. <span data-ttu-id="ac67d-138">W kodzie usługi danych Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych z typem, który dziedziczy <xref:System.Data.Objects.ObjectContext> z klasy i jest kontenerem jednostek modelu danych, który został zanotowany w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="ac67d-138">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>

7. <span data-ttu-id="ac67d-139">W kodzie usługi danych Włącz autoryzowanych klientów, aby uzyskać dostęp do zestawów jednostek udostępnianych przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="ac67d-139">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="ac67d-140">Aby uzyskać więcej informacji, zobacz [Tworzenie usługi danych](creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="ac67d-140">For more information, see [Creating the Data Service](creating-the-data-service.md).</span></span>

8. <span data-ttu-id="ac67d-141">Aby przetestować usługę danych Northwind. svc przy użyciu przeglądarki sieci Web, postępuj zgodnie z instrukcjami podanymi w temacie [Uzyskiwanie dostępu do usługi z przeglądarki sieci Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="ac67d-141">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac67d-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac67d-142">See also</span></span>

- [<span data-ttu-id="ac67d-143">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="ac67d-143">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="ac67d-144">Dostawcy usług danych</span><span class="sxs-lookup"><span data-stu-id="ac67d-144">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="ac67d-145">Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia</span><span class="sxs-lookup"><span data-stu-id="ac67d-145">How to: Create a Data Service Using the Reflection Provider</span></span>](create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="ac67d-146">Instrukcje: Tworzenie usługi danych przy użyciu LINQ to SQL źródła danych</span><span class="sxs-lookup"><span data-stu-id="ac67d-146">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
