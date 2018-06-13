---
title: 'Porady: Tworzenie usługi danych za pomocą LINQ do SQL źródła danych (usługi danych WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: 5769ff5296d096df41b59104ad0581f0e816c648
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362250"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="5b45d-102">Porady: Tworzenie usługi danych za pomocą LINQ do SQL źródła danych (usługi danych WCF)</span><span class="sxs-lookup"><span data-stu-id="5b45d-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="5b45d-103"> udostępnia dane jednostki jako usługa danych.</span><span class="sxs-lookup"><span data-stu-id="5b45d-103"> exposes entity data as a data service.</span></span> <span data-ttu-id="5b45d-104">Dostawca odbicia umożliwia zdefiniowanie modelu danych, która jest oparta na dowolnej klasy, która udostępnia elementy Członkowskie zwracające <xref:System.Linq.IQueryable%601> implementacji.</span><span class="sxs-lookup"><span data-stu-id="5b45d-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="5b45d-105">Aby można było dokonać aktualizacji danych w źródle danych, również musi implementować następujące klasy <xref:System.Data.Services.IUpdatable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5b45d-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="5b45d-106">Aby uzyskać więcej informacji, zobacz [dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="5b45d-106">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="5b45d-107">W tym temacie przedstawiono sposób tworzenia LINQ w klasach SQL, które uzyskują dostęp do przykładowej bazy danych Northwind przy użyciu dostawcy odbicia, a także sposób utworzyć usługę danych, która jest oparta na tych klas danych.</span><span class="sxs-lookup"><span data-stu-id="5b45d-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>  
  
### <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="5b45d-108">Aby dodać LINQ w klasach SQL do projektu</span><span class="sxs-lookup"><span data-stu-id="5b45d-108">To add LINQ to SQL classes to a project</span></span>  
  
1.  <span data-ttu-id="5b45d-109">Z poziomu aplikacji Visual Basic lub C# na **projektu** menu, kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="5b45d-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="5b45d-110">Kliknij przycisk **klasy LINQ do SQL** szablonu.</span><span class="sxs-lookup"><span data-stu-id="5b45d-110">Click the **LINQ to SQL Classes** template.</span></span>  
  
3.  <span data-ttu-id="5b45d-111">Zmień nazwę, aby **Northwind.dbml**.</span><span class="sxs-lookup"><span data-stu-id="5b45d-111">Change the name to **Northwind.dbml**.</span></span>  
  
4.  <span data-ttu-id="5b45d-112">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="5b45d-112">Click **Add**.</span></span>  
  
     <span data-ttu-id="5b45d-113">Plik Northwind.dbml zostanie dodany do projektu i otwiera Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych).</span><span class="sxs-lookup"><span data-stu-id="5b45d-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>  
  
5.  <span data-ttu-id="5b45d-114">W **serwera**/**Eksploratora bazy danych**, w obszarze Northwind, rozwiń węzeł **tabel** i przeciągnij `Customers` tabeli w Projektancie obiektów relacyjnych (obiektów relacyjnych Projektant).</span><span class="sxs-lookup"><span data-stu-id="5b45d-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>  
  
     <span data-ttu-id="5b45d-115">A `Customer` klasy jednostka jest tworzony i wyświetlany na powierzchni projektu.</span><span class="sxs-lookup"><span data-stu-id="5b45d-115">A `Customer` entity class is created and appears on the design surface.</span></span>  
  
6.  <span data-ttu-id="5b45d-116">Powtórz kroki od 6 do `Orders`, `Order_Details`, i `Products` tabel.</span><span class="sxs-lookup"><span data-stu-id="5b45d-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>  
  
7.  <span data-ttu-id="5b45d-117">Kliknij prawym przyciskiem myszy nowy plik .dbml, który reprezentuje LINQ do SQL klas i kliknij przycisk **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="5b45d-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>  
  
     <span data-ttu-id="5b45d-118">Spowoduje to utworzenie nowej strony związane z kodem o nazwie Northwind.cs, który zawiera definicję klasy częściowej klasy, która dziedziczy po <xref:System.Data.Linq.DataContext> klasy, która jest w tym przypadku `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="5b45d-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>  
  
8.  <span data-ttu-id="5b45d-119">Zastąp zawartość pliku kodu Northwind.cs następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="5b45d-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="5b45d-120">Ten kod implementuje dostawcę odbicia rozszerzając <xref:System.Data.Linq.DataContext> i klas danych wygenerowanych przez składnik LINQ to SQL:</span><span class="sxs-lookup"><span data-stu-id="5b45d-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>  
  
     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]  
  
### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="5b45d-121">Aby utworzyć usługę danych za pomocą LINQ do SQL na podstawie danych modelu</span><span class="sxs-lookup"><span data-stu-id="5b45d-121">To create a data service by using a LINQ to SQL-based data model</span></span>  
  
1.  <span data-ttu-id="5b45d-122">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="5b45d-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="5b45d-123">W **Dodaj nowy element** okno dialogowe, wybierz opcję **usługi danych WCF**.</span><span class="sxs-lookup"><span data-stu-id="5b45d-123">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
3.  <span data-ttu-id="5b45d-124">Podaj nazwę usługi, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="5b45d-124">Supply a name for the service, and then click **OK**.</span></span>  
  
     <span data-ttu-id="5b45d-125">Program Visual Studio tworzy pliki znaczników i kodu XML dla nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="5b45d-125">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="5b45d-126">Domyślnie zostanie otwarte okno edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="5b45d-126">By default, the code-editor window opens.</span></span>  
  
4.  <span data-ttu-id="5b45d-127">W kodzie dla usługi data, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych o typie kontenera jednostek w modelu danych, który w tym przypadku jest `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="5b45d-127">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>  
  
5.  <span data-ttu-id="5b45d-128">W kodzie dla usługi data, Zastąp kod symbol zastępczy w `InitializeService` funkcji z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5b45d-128">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]  
  
     <span data-ttu-id="5b45d-129">Dzięki temu autoryzowanym klientom dostęp do zasobów dla trzech zestawów określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="5b45d-129">This enables authorized clients to access resources for the three specified entity sets.</span></span>  
  
6.  <span data-ttu-id="5b45d-130">Aby przetestować usługę Northwind.svc danych za pomocą przeglądarki sieci Web, postępuj zgodnie z instrukcjami w temacie [uzyskiwania dostępu do usługi z przeglądarką sieci Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="5b45d-130">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b45d-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b45d-131">See Also</span></span>  
 [<span data-ttu-id="5b45d-132">Instrukcje: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="5b45d-132">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)  
 [<span data-ttu-id="5b45d-133">Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia</span><span class="sxs-lookup"><span data-stu-id="5b45d-133">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [<span data-ttu-id="5b45d-134">Dostawcy usług danych</span><span class="sxs-lookup"><span data-stu-id="5b45d-134">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
