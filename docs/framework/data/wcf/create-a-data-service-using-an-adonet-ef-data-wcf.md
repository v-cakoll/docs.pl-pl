---
title: "Porady: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d69a3cf60b60806085a9bb7ae292cc88ba99871e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="a0232-102">Porady: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework (usługi danych WCF)</span><span class="sxs-lookup"><span data-stu-id="a0232-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="a0232-103">udostępnia dane jednostki jako usługa danych.</span><span class="sxs-lookup"><span data-stu-id="a0232-103"> exposes entity data as a data service.</span></span> <span data-ttu-id="a0232-104">Dane te jednostki są udostępniane przez [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] po relacyjnej bazy danych w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="a0232-104">This entity data is provided by the [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] when the data source is a relational database.</span></span> <span data-ttu-id="a0232-105">W tym temacie przedstawiono sposób tworzenia [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]— na podstawie modelu danych w [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] sieci Web aplikacji, która jest oparta na istniejącej bazy danych i umożliwia utworzenie nowej usługi danych tego modelu danych.</span><span class="sxs-lookup"><span data-stu-id="a0232-105">This topic shows you how to create an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-based data model in a [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web application that is based on an existing database and use this data model to create a new data service.</span></span>  
  
 <span data-ttu-id="a0232-106">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Udostępnia narzędzie wiersza polecenia, które mogą generować [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] modelu poza [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="a0232-106">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] also provides a command line tool that can generate an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] model outside of a [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] project.</span></span> <span data-ttu-id="a0232-107">Aby uzyskać więcej informacji, zobacz [porady: EdmGen.exe używany do generowania modelu i mapowania plików](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="a0232-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
### <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="a0232-108">Aby dodać model narzędzia Entity Framework, która jest oparta na istniejącej bazy danych do istniejącej aplikacji sieci Web</span><span class="sxs-lookup"><span data-stu-id="a0232-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>  
  
1.  <span data-ttu-id="a0232-109">Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="a0232-109">On the **Project** menu, click **Add new item**.</span></span>  
  
2.  <span data-ttu-id="a0232-110">W **szablony** okienku, kliknij przycisk **danych** kategorii, a następnie wybierz **modelu danych jednostki ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="a0232-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="a0232-111">Wpisz nazwę modelu, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="a0232-111">Type the model name and then click **Add**.</span></span>  
  
     <span data-ttu-id="a0232-112">Na pierwszej stronie [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] zostanie wyświetlony Kreator.</span><span class="sxs-lookup"><span data-stu-id="a0232-112">The first page of the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard is displayed.</span></span>  
  
4.  <span data-ttu-id="a0232-113">W **wybierz zawartość modelu** okno dialogowe, wybierz opcję **generowania z bazy danych**.</span><span class="sxs-lookup"><span data-stu-id="a0232-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="a0232-114">Następnie kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="a0232-114">Then click **Next**.</span></span>  
  
5.  <span data-ttu-id="a0232-115">Kliknij przycisk **nowe połączenie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a0232-115">Click the **New Connection** button.</span></span>  
  
6.  <span data-ttu-id="a0232-116">W **właściwości połączenia** okno dialogowe, wpisz nazwę serwera, wybierz metodę uwierzytelniania, wpisz nazwę bazy danych i kliknięcie **OK**.</span><span class="sxs-lookup"><span data-stu-id="a0232-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a0232-117">**Wybierz połączenie danych**okno dialogowe s został zaktualizowany o ustawienia połączenia bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a0232-117">The **Choose Your Data Connection**s dialog box is updated with your database connection settings.</span></span>  
  
7.  <span data-ttu-id="a0232-118">Upewnij się, że **jednostki Zapisz ustawienia połączenia w pliku App.Config jako:** jest zaznaczone pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="a0232-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="a0232-119">Następnie kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="a0232-119">Then click **Next**.</span></span>  
  
8.  <span data-ttu-id="a0232-120">W **wybierz obiekty bazy danych użytkownika** okno dialogowe, wybierz wszystkie bazy danych obiektów planuje udostępnić w usłudze danych.</span><span class="sxs-lookup"><span data-stu-id="a0232-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0232-121">Liczba obiektów uwzględnionych w modelu danych nie są automatycznie widoczne przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="a0232-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="a0232-122">One musi być jawnie wystawiony przez samą usługę.</span><span class="sxs-lookup"><span data-stu-id="a0232-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="a0232-123">Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="a0232-123">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
9. <span data-ttu-id="a0232-124">Kliknij przycisk **Zakończ** aby zakończyć pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="a0232-124">Click **Finish** to complete the wizard.</span></span>  
  
     <span data-ttu-id="a0232-125">Spowoduje to utworzenie domyślny model danych, na podstawie określonej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a0232-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="a0232-126">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Umożliwia w celu dostosowania modelu danych.</span><span class="sxs-lookup"><span data-stu-id="a0232-126">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] enables to customize the data model.</span></span> <span data-ttu-id="a0232-127">Aby uzyskać więcej informacji, zobacz [zadania](http://msdn.microsoft.com/en-us/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).</span><span class="sxs-lookup"><span data-stu-id="a0232-127">For more information, see [Tasks](http://msdn.microsoft.com/en-us/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).</span></span>  
  
### <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="a0232-128">Aby utworzyć usługę danych przy użyciu nowego modelu danych</span><span class="sxs-lookup"><span data-stu-id="a0232-128">To create the data service by using the new data model</span></span>  
  
1.  <span data-ttu-id="a0232-129">W [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], otwórz plik edmx, który reprezentuje modelu danych.</span><span class="sxs-lookup"><span data-stu-id="a0232-129">In [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], open the .edmx file that represents the data model.</span></span>  
  
2.  <span data-ttu-id="a0232-130">W **przeglądarki modelu**, kliknij prawym przyciskiem myszy model, kliknij przycisk **właściwości**, a następnie zanotuj nazwę kontenera jednostek.</span><span class="sxs-lookup"><span data-stu-id="a0232-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>  
  
3.  <span data-ttu-id="a0232-131">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę Twojej [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, a następnie kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="a0232-131">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item**.</span></span>  
  
4.  <span data-ttu-id="a0232-132">W **Dodaj nowy element** okno dialogowe, wybierz opcję **usługi danych WCF**.</span><span class="sxs-lookup"><span data-stu-id="a0232-132">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
5.  <span data-ttu-id="a0232-133">Podaj nazwę usługi, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="a0232-133">Supply a name for the service, and then click **OK**.</span></span>  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]<span data-ttu-id="a0232-134">tworzy pliki znaczników i kodu XML dla nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="a0232-134"> creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="a0232-135">Domyślnie zostanie otwarte okno edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="a0232-135">By default, the code-editor window opens.</span></span>  
  
6.  <span data-ttu-id="a0232-136">W kodzie dla usługi data, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych z typem, który dziedziczy z <xref:System.Data.Objects.ObjectContext> klasy i który jest kontenera jednostek w modelu danych, który został zapisany w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="a0232-136">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>  
  
7.  <span data-ttu-id="a0232-137">W kodzie dla usługi data Włącz autoryzowanym klientom dostęp zestawów jednostek usługa ujawnia danych.</span><span class="sxs-lookup"><span data-stu-id="a0232-137">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="a0232-138">Aby uzyskać więcej informacji, zobacz [Tworzenie usługi danych](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="a0232-138">For more information, see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
8.  <span data-ttu-id="a0232-139">Aby przetestować usługę Northwind.svc danych za pomocą przeglądarki sieci Web, postępuj zgodnie z instrukcjami w temacie [uzyskiwania dostępu do usługi z przeglądarką sieci Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="a0232-139">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0232-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0232-140">See Also</span></span>  
 [<span data-ttu-id="a0232-141">Definiowanie usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="a0232-141">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [<span data-ttu-id="a0232-142">Dostawców usług danych</span><span class="sxs-lookup"><span data-stu-id="a0232-142">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="a0232-143">Porady: Tworzenie usługi danych przy użyciu dostawcy odbicia</span><span class="sxs-lookup"><span data-stu-id="a0232-143">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [<span data-ttu-id="a0232-144">Porady: Tworzenie usługi danych do źródła danych SQL za pomocą LINQ</span><span class="sxs-lookup"><span data-stu-id="a0232-144">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
