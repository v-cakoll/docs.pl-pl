---
title: 'Instrukcje: Tworzenie usługi danych przy użyciu LINQ do SQL źródła danych (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: 7447a9f2ab0b2a9cca396ee947a0eb5fe2cc8715
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608576"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="7825d-102">Instrukcje: Tworzenie usługi danych przy użyciu LINQ do SQL źródła danych (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="7825d-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>

<span data-ttu-id="7825d-103">Usługi danych WCF przedstawia dane jednostki w postaci usługi danych.</span><span class="sxs-lookup"><span data-stu-id="7825d-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="7825d-104">Dostawca odbicia pozwala na zdefiniowanie modelu danych, który opiera się na każdej klasy, która udostępnia elementy Członkowskie zwracające <xref:System.Linq.IQueryable%601> implementacji.</span><span class="sxs-lookup"><span data-stu-id="7825d-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="7825d-105">Aby można było zaktualizować dane w źródle danych, w ramach tych zajęć musi implementować też <xref:System.Data.Services.IUpdatable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7825d-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="7825d-106">Aby uzyskać więcej informacji, zobacz [dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7825d-106">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="7825d-107">W tym temacie dowiesz się, jak utworzyć LINQ do klas SQL, uzyskujących dostęp do przykładowej bazy danych Northwind za pomocą dostawcy odbicia, a także jak utworzyć usługę danych, która opiera się na tych klas danych.</span><span class="sxs-lookup"><span data-stu-id="7825d-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>

## <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="7825d-108">Aby dodać LINQ do klas SQL do projektu</span><span class="sxs-lookup"><span data-stu-id="7825d-108">To add LINQ to SQL classes to a project</span></span>

1. <span data-ttu-id="7825d-109">Z aplikacji Visual Basic lub C# na **projektu** menu, kliknij przycisk **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="7825d-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="7825d-110">Kliknij przycisk **klasy LINQ do SQL** szablonu.</span><span class="sxs-lookup"><span data-stu-id="7825d-110">Click the **LINQ to SQL Classes** template.</span></span>

3. <span data-ttu-id="7825d-111">Zmień nazwę na **Northwind.dbml**.</span><span class="sxs-lookup"><span data-stu-id="7825d-111">Change the name to **Northwind.dbml**.</span></span>

4. <span data-ttu-id="7825d-112">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="7825d-112">Click **Add**.</span></span>

     <span data-ttu-id="7825d-113">Plik Northwind.dbml zostanie dodany do projektu, i otwiera Object Relational Designer (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="7825d-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>

5. <span data-ttu-id="7825d-114">W **serwera**/**Eksplorator bazy danych**, w obszarze Northwind, rozwiń węzeł **tabel** i przeciągnij `Customers` tabeli do Object Relational Designer (O/R Projektant).</span><span class="sxs-lookup"><span data-stu-id="7825d-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>

     <span data-ttu-id="7825d-115">A `Customer` Klasa jednostki jest utworzony i wyświetlony na powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="7825d-115">A `Customer` entity class is created and appears on the design surface.</span></span>

6. <span data-ttu-id="7825d-116">Powtórz krok 6 dla `Orders`, `Order_Details`, i `Products` tabel.</span><span class="sxs-lookup"><span data-stu-id="7825d-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>

7. <span data-ttu-id="7825d-117">Kliknij prawym przyciskiem myszy nowy plik dbml, który reprezentuje LINQ do klas SQL i kliknij przycisk **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="7825d-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>

     <span data-ttu-id="7825d-118">Spowoduje to utworzenie nowej strony związanym z kodem o nazwie Northwind.cs, który zawiera definicję klasy częściowej klasy dziedziczącej z klasy <xref:System.Data.Linq.DataContext> klasy, która jest w tym przypadku `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="7825d-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>

8. <span data-ttu-id="7825d-119">Zastąp zawartość pliku z kodem Northwind.cs następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="7825d-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="7825d-120">Ten kod implementuje dostawcy odbicia, rozszerzając <xref:System.Data.Linq.DataContext> i klas danych generowanych przez LINQ to SQL:</span><span class="sxs-lookup"><span data-stu-id="7825d-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="7825d-121">Aby utworzyć usługę danych za pomocą LINQ do modelu danych programu SQL</span><span class="sxs-lookup"><span data-stu-id="7825d-121">To create a data service by using a LINQ to SQL-based data model</span></span>

1. <span data-ttu-id="7825d-122">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="7825d-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="7825d-123">W **Dodaj nowy element** okno dialogowe, wybierz opcję **usługi danych WCF** szablonu z **Web** kategorii.</span><span class="sxs-lookup"><span data-stu-id="7825d-123">In the **Add New Item** dialog box, select the **WCF Data Service** template from the **Web** category.</span></span>

   ![Szablon elementu usługi danych WCF w programie Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="7825d-125">**Usługi danych WCF** szablon jest dostępny w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="7825d-125">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="7825d-126">Podaj nazwę usługi, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="7825d-126">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="7825d-127">Program Visual Studio tworzy pliki znaczników i kodu XML dla nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="7825d-127">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="7825d-128">Domyślnie zostanie otwarte okno edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="7825d-128">By default, the code-editor window opens.</span></span>

4. <span data-ttu-id="7825d-129">W kodzie dla usługi danych, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych z typem, który jest kontenerem jednostki w modelu danych, który w tym przypadku jest `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="7825d-129">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>

5. <span data-ttu-id="7825d-130">W kodzie dla usługi danych, Zastąp kod symbolu zastępczego `InitializeService` funkcji następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="7825d-130">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]

     <span data-ttu-id="7825d-131">Dzięki temu autoryzowanych klientów dostępu do zasobów dla trzech zestawów określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="7825d-131">This enables authorized clients to access resources for the three specified entity sets.</span></span>

6. <span data-ttu-id="7825d-132">Aby przetestować usługę danych Northwind.svc przy użyciu przeglądarki sieci Web, postępuj zgodnie z instrukcjami w temacie [uzyskiwania dostępu do usługi z przeglądarki sieci Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="7825d-132">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7825d-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7825d-133">See also</span></span>

- [<span data-ttu-id="7825d-134">Instrukcje: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="7825d-134">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [<span data-ttu-id="7825d-135">Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia</span><span class="sxs-lookup"><span data-stu-id="7825d-135">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="7825d-136">Dostawcy usług danych</span><span class="sxs-lookup"><span data-stu-id="7825d-136">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)