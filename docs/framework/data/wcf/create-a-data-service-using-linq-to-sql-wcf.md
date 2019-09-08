---
title: 'Instrukcje: Tworzenie usługi danych przy użyciu LINQ to SQL źródła danych (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: 7a1075b680ec3310e1bd8d712579872333c6ebed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791050"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="f6226-102">Instrukcje: Tworzenie usługi danych przy użyciu LINQ to SQL źródła danych (Usługi danych programu WCF)</span><span class="sxs-lookup"><span data-stu-id="f6226-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>

<span data-ttu-id="f6226-103">Usługi danych programu WCF udostępnia dane jednostki jako usługę danych.</span><span class="sxs-lookup"><span data-stu-id="f6226-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="f6226-104">Dostawca odbicia umożliwia zdefiniowanie modelu danych, który jest oparty na dowolnej klasie, która ujawnia elementy członkowskie, które <xref:System.Linq.IQueryable%601> zwracają implementację.</span><span class="sxs-lookup"><span data-stu-id="f6226-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="f6226-105">Aby móc wprowadzać aktualizacje danych w źródle danych, te klasy muszą również implementować <xref:System.Data.Services.IUpdatable> interfejs.</span><span class="sxs-lookup"><span data-stu-id="f6226-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="f6226-106">Aby uzyskać więcej informacji, zobacz [Data Services Providers](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="f6226-106">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="f6226-107">W tym temacie przedstawiono sposób tworzenia klas LINQ to SQL, które uzyskują dostęp do przykładowej bazy danych Northwind przy użyciu dostawcy odbicia, a także sposobu tworzenia usługi danych opartej na tych klasach danych.</span><span class="sxs-lookup"><span data-stu-id="f6226-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>

## <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="f6226-108">Aby dodać klasy LINQ to SQL do projektu</span><span class="sxs-lookup"><span data-stu-id="f6226-108">To add LINQ to SQL classes to a project</span></span>

1. <span data-ttu-id="f6226-109">W Visual Basic lub C# aplikacji, w menu **projekt** kliknij polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="f6226-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="f6226-110">Kliknij szablon **LINQ to SQL klas** .</span><span class="sxs-lookup"><span data-stu-id="f6226-110">Click the **LINQ to SQL Classes** template.</span></span>

3. <span data-ttu-id="f6226-111">Zmień nazwę na **Northwind. dbml**.</span><span class="sxs-lookup"><span data-stu-id="f6226-111">Change the name to **Northwind.dbml**.</span></span>

4. <span data-ttu-id="f6226-112">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="f6226-112">Click **Add**.</span></span>

     <span data-ttu-id="f6226-113">Plik Northwind. dbml jest dodawany do projektu, a Object Relational Designer (Projektant O/R) zostanie otwarty.</span><span class="sxs-lookup"><span data-stu-id="f6226-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>

5. <span data-ttu-id="f6226-114">W obszarze **serwer**/**Eksplorator bazy danych**w obszarze Northwind rozwiń pozycję **tabele** i przeciągnij `Customers` tabelę na Object Relational Designer (Projektant O/R).</span><span class="sxs-lookup"><span data-stu-id="f6226-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>

     <span data-ttu-id="f6226-115">Klasa `Customer` jednostki jest tworzona i pojawia się na powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="f6226-115">A `Customer` entity class is created and appears on the design surface.</span></span>

6. <span data-ttu-id="f6226-116">Powtórz krok 6 dla `Orders`tabel, `Order_Details`i. `Products`</span><span class="sxs-lookup"><span data-stu-id="f6226-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>

7. <span data-ttu-id="f6226-117">Kliknij prawym przyciskiem myszy nowy plik. dbml, który reprezentuje klasy LINQ to SQL i kliknij polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="f6226-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>

     <span data-ttu-id="f6226-118">Spowoduje to utworzenie nowej strony powiązanej z kodem o nazwie Northwind.cs, która zawiera definicję klasy częściowej dla klasy, która <xref:System.Data.Linq.DataContext> dziedziczy z klasy, która w tym `NorthwindDataContext`przypadku jest.</span><span class="sxs-lookup"><span data-stu-id="f6226-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>

8. <span data-ttu-id="f6226-119">Zastąp zawartość pliku kodu Northwind.cs następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="f6226-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="f6226-120">Ten kod implementuje dostawcę odbicia przez rozszerzenie <xref:System.Data.Linq.DataContext> klas danych i wygenerowanych przez LINQ to SQL:</span><span class="sxs-lookup"><span data-stu-id="f6226-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="f6226-121">Aby utworzyć usługę danych przy użyciu modelu danych opartego na LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f6226-121">To create a data service by using a LINQ to SQL-based data model</span></span>

1. <span data-ttu-id="f6226-122">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="f6226-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="f6226-123">W oknie dialogowym **Dodaj nowy element** wybierz szablon **usługi danych programu WCF** z kategorii **Sieć Web** .</span><span class="sxs-lookup"><span data-stu-id="f6226-123">In the **Add New Item** dialog box, select the **WCF Data Service** template from the **Web** category.</span></span>

   ![Szablon elementu usługi danych programu WCF w programie Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="f6226-125">Szablon **usługi danych programu WCF** jest dostępny w programie visual Studio 2015, ale nie w programie visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="f6226-125">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="f6226-126">Podaj nazwę usługi, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="f6226-126">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="f6226-127">Program Visual Studio tworzy znaczniki XML i pliki kodu dla nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="f6226-127">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="f6226-128">Domyślnie zostanie otwarte okno edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="f6226-128">By default, the code-editor window opens.</span></span>

4. <span data-ttu-id="f6226-129">W kodzie usługi danych Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych z typem, który jest kontenerem jednostek modelu danych, w tym `NorthwindDataContext`przypadku.</span><span class="sxs-lookup"><span data-stu-id="f6226-129">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>

5. <span data-ttu-id="f6226-130">W kodzie usługi danych Zastąp symbol zastępczy w `InitializeService` funkcji następującymi elementami:</span><span class="sxs-lookup"><span data-stu-id="f6226-130">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     <span data-ttu-id="f6226-131">Dzięki temu autoryzowani klienci mogą uzyskać dostęp do zasobów dla trzech określonych zestawów jednostek.</span><span class="sxs-lookup"><span data-stu-id="f6226-131">This enables authorized clients to access resources for the three specified entity sets.</span></span>

6. <span data-ttu-id="f6226-132">Aby przetestować usługę danych Northwind. svc przy użyciu przeglądarki sieci Web, postępuj zgodnie z instrukcjami podanymi w temacie [Uzyskiwanie dostępu do usługi z przeglądarki sieci Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="f6226-132">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f6226-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6226-133">See also</span></span>

- [<span data-ttu-id="f6226-134">Instrukcje: Tworzenie usługi danych przy użyciu źródła danych ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="f6226-134">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [<span data-ttu-id="f6226-135">Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia</span><span class="sxs-lookup"><span data-stu-id="f6226-135">How to: Create a Data Service Using the Reflection Provider</span></span>](create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="f6226-136">Dostawcy usług danych</span><span class="sxs-lookup"><span data-stu-id="f6226-136">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
