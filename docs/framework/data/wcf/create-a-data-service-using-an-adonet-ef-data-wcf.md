---
title: 'Porady: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 72439596ec6dc6c42024ed38116ba0026922154c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394111"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="29e53-102">Porady: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="29e53-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>

<span data-ttu-id="29e53-103">Usługi danych WCF przedstawia dane jednostki w postaci usługi danych.</span><span class="sxs-lookup"><span data-stu-id="29e53-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="29e53-104">Dane te jednostki są udostępniane przez [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] po relacyjnej bazy danych w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="29e53-104">This entity data is provided by the [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] when the data source is a relational database.</span></span> <span data-ttu-id="29e53-105">W tym temacie przedstawiono sposób tworzenia [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]— na podstawie modelu danych w aplikacji internetowego programu Visual Studio, która opiera się na istniejącą bazę danych i Utwórz nową usługę danych przy użyciu tego modelu danych.</span><span class="sxs-lookup"><span data-stu-id="29e53-105">This topic shows you how to create an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-based data model in a Visual Studio Web application that is based on an existing database and use this data model to create a new data service.</span></span>

<span data-ttu-id="29e53-106">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Także narzędzia wiersza polecenia, które mogą generować [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] modelu spoza projektu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="29e53-106">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] also provides a command line tool that can generate an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] model outside of a Visual Studio project.</span></span> <span data-ttu-id="29e53-107">Aby uzyskać więcej informacji, zobacz [porady: użycie EdmGen.exe do generowania modelu i mapowania plików](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="29e53-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="29e53-108">Aby dodać modelu Entity Framework, która opiera się na istniejącą bazę danych do istniejącej aplikacji sieci Web</span><span class="sxs-lookup"><span data-stu-id="29e53-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>

1. <span data-ttu-id="29e53-109">Na **projektu** menu, kliknij przycisk **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="29e53-109">On the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="29e53-110">W **szablony** okienku kliknij **danych** kategorii, a następnie wybierz **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="29e53-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="29e53-111">Wprowadź nazwę modelu, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="29e53-111">Enter the model name and then click **Add**.</span></span>

     <span data-ttu-id="29e53-112">Na pierwszej stronie [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] zostanie wyświetlony Kreator.</span><span class="sxs-lookup"><span data-stu-id="29e53-112">The first page of the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard is displayed.</span></span>

4. <span data-ttu-id="29e53-113">W **wybierz zawartość modelu** okno dialogowe, wybierz opcję **Generuj z bazy danych**.</span><span class="sxs-lookup"><span data-stu-id="29e53-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="29e53-114">Następnie kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="29e53-114">Then click **Next**.</span></span>

5. <span data-ttu-id="29e53-115">Kliknij przycisk **nowe połączenie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="29e53-115">Click the **New Connection** button.</span></span>

6. <span data-ttu-id="29e53-116">W **właściwości połączenia** okno dialogowe, wpisz nazwę serwera, wybierz metodę uwierzytelniania, wpisz nazwę bazy danych, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="29e53-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>

     <span data-ttu-id="29e53-117">**Wybierz połączenie danych**s, okno dialogowe zostanie zaktualizowana przy użyciu ustawienia połączenia bazy danych.</span><span class="sxs-lookup"><span data-stu-id="29e53-117">The **Choose Your Data Connection**s dialog box is updated with your database connection settings.</span></span>

7. <span data-ttu-id="29e53-118">Upewnij się, że **zapisywanie ustawień połączenia w pliku App.Config jako jednostki:** zaznaczono pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="29e53-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="29e53-119">Następnie kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="29e53-119">Then click **Next**.</span></span>

8. <span data-ttu-id="29e53-120">W **wybierz obiekty bazy danych** okno dialogowe, zaznacz wszystkie bazy danych obiekty czy planowane jest udostępnianie w usłudze danych.</span><span class="sxs-lookup"><span data-stu-id="29e53-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="29e53-121">Obiektów uwzględnionych w modelu danych nie są automatycznie widoczne przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="29e53-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="29e53-122">One muszą być wyraźnie widoczne za samą usługę.</span><span class="sxs-lookup"><span data-stu-id="29e53-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="29e53-123">Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="29e53-123">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>

9. <span data-ttu-id="29e53-124">Kliknij przycisk **Zakończ** aby zakończyć działanie kreatora.</span><span class="sxs-lookup"><span data-stu-id="29e53-124">Click **Finish** to complete the wizard.</span></span>

     <span data-ttu-id="29e53-125">Spowoduje to utworzenie domyślny model danych, na podstawie określonej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="29e53-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="29e53-126">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Umożliwia dostosowywanie modelu danych.</span><span class="sxs-lookup"><span data-stu-id="29e53-126">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] enables to customize the data model.</span></span> <span data-ttu-id="29e53-127">Aby uzyskać więcej informacji, zobacz [zadania](https://msdn.microsoft.com/library/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).</span><span class="sxs-lookup"><span data-stu-id="29e53-127">For more information, see [Tasks](https://msdn.microsoft.com/library/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).</span></span>

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="29e53-128">Aby utworzyć usługę danych przy użyciu nowego modelu danych</span><span class="sxs-lookup"><span data-stu-id="29e53-128">To create the data service by using the new data model</span></span>

1. <span data-ttu-id="29e53-129">W programie Visual Studio Otwórz plik edmx, reprezentujące model danych.</span><span class="sxs-lookup"><span data-stu-id="29e53-129">In Visual Studio, open the .edmx file that represents the data model.</span></span>

2. <span data-ttu-id="29e53-130">W **przeglądarka modeli**, kliknij prawym przyciskiem myszy model, kliknij przycisk **właściwości**, a następnie zanotuj nazwę kontenera jednostek.</span><span class="sxs-lookup"><span data-stu-id="29e53-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>

3. <span data-ttu-id="29e53-131">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę swojej [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, a następnie kliknij przycisk **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="29e53-131">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add** > **New Item**.</span></span>

4. <span data-ttu-id="29e53-132">W **Dodaj nowy element** okno dialogowe, wybierz opcję **usługi danych WCF** szablonu w **Web** kategorii.</span><span class="sxs-lookup"><span data-stu-id="29e53-132">In the **Add New Item** dialog box, select the **WCF Data Service** template in the **Web** category.</span></span>

   ![Szablon elementu usługi danych WCF w programie Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="29e53-134">**Usługi danych WCF** szablon jest dostępny w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="29e53-134">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

5. <span data-ttu-id="29e53-135">Podaj nazwę usługi, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="29e53-135">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="29e53-136">Program Visual Studio tworzy pliki znaczników i kodu XML dla nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="29e53-136">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="29e53-137">Domyślnie zostanie otwarte okno edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="29e53-137">By default, the code-editor window opens.</span></span>

6. <span data-ttu-id="29e53-138">W kodzie dla usługi danych, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych o typie, który dziedziczy z <xref:System.Data.Objects.ObjectContext> klasy i oznacza to kontener jednostek w modelu danych, która została zanotowanym w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="29e53-138">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>

7. <span data-ttu-id="29e53-139">W kodzie dla usługi danych należy włączyć autoryzowanym klientom dostęp zestawy jednostek usługi ujawnia w danych.</span><span class="sxs-lookup"><span data-stu-id="29e53-139">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="29e53-140">Aby uzyskać więcej informacji, zobacz [Tworzenie usługi danych](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="29e53-140">For more information, see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>

8. <span data-ttu-id="29e53-141">Aby przetestować usługę danych Northwind.svc przy użyciu przeglądarki sieci Web, postępuj zgodnie z instrukcjami w temacie [uzyskiwania dostępu do usługi z przeglądarki sieci Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="29e53-141">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="29e53-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29e53-142">See Also</span></span>

- [<span data-ttu-id="29e53-143">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="29e53-143">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [<span data-ttu-id="29e53-144">Dostawcy usług danych</span><span class="sxs-lookup"><span data-stu-id="29e53-144">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="29e53-145">Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia</span><span class="sxs-lookup"><span data-stu-id="29e53-145">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="29e53-146">Instrukcje: Tworzenie usługi danych przy użyciu źródła danych LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="29e53-146">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)