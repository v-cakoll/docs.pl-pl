---
title: Działania jednostki
ms.date: 03/30/2017
ms.assetid: c04f7413-7fb8-40c6-819e-dc92b145b62e
ms.openlocfilehash: 03bd0e42c70f1226558d492bcb3b2cfa5c7010f2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861156"
---
# <a name="entity-activities"></a><span data-ttu-id="e3e97-102">Działania jednostki</span><span class="sxs-lookup"><span data-stu-id="e3e97-102">Entity Activities</span></span>
<span data-ttu-id="e3e97-103">W tym przykładzie pokazano, jak za pomocą ADO.NET Entity Framework Windows Workflow Foundation Aby uprościć dostęp do danych.</span><span class="sxs-lookup"><span data-stu-id="e3e97-103">This sample shows how to use the ADO.NET Entity Framework with Windows Workflow Foundation to simplify data access.</span></span>  
  
 <span data-ttu-id="e3e97-104">ADO.NET Entity Framework umożliwia deweloperom pracę z danymi w postaci obiektów specyficznych dla domeny, właściwości i relacje, takich jak klientów i zamówień, szczegółów zamówienia relacji między tymi jednostkami.</span><span class="sxs-lookup"><span data-stu-id="e3e97-104">The ADO.NET Entity Framework enables developers to work with data in the form of domain-specific objects, properties and relationships such as Customers, Orders, Order Details and the relationships between these entities.</span></span> <span data-ttu-id="e3e97-105">ADO.NET Entity Framework robi to dzięki zapewnieniu poziomu abstrakcji, która umożliwia programowanie w oparciu o model koncepcyjny aplikacji zamiast programowania bezpośrednio w odniesieniu do schematu magazyn relacyjny.</span><span class="sxs-lookup"><span data-stu-id="e3e97-105">The ADO.NET Entity Framework does this by providing a level of abstraction that enables programming against a conceptual application model instead of programming directly against a relational storage schema.</span></span> <span data-ttu-id="e3e97-106">Aby uzyskać więcej informacji na temat ADO.NET Entity Framework, zobacz [ADO.NET Entity Framework](https://go.microsoft.com/fwlink/?LinkId=165549).</span><span class="sxs-lookup"><span data-stu-id="e3e97-106">For more information about the ADO.NET Entity Framework see [ADO.NET Entity Framework](https://go.microsoft.com/fwlink/?LinkId=165549).</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="e3e97-107">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="e3e97-107">Sample details</span></span>  
 <span data-ttu-id="e3e97-108">W tym przykładzie użyto `Northwind` bazy danych i obejmuje skrypty do tworzenia i usuwania `Northwind` bazy danych (plik Setup.cmd i Cleanup.cmd).</span><span class="sxs-lookup"><span data-stu-id="e3e97-108">This sample uses the `Northwind` database and includes scripts for creating and removing the `Northwind` database (Setup.cmd and Cleanup.cmd).</span></span> <span data-ttu-id="e3e97-109">Projekty, w tym przykładzie zawierają oparte na modelu danych jednostki `Northwind` bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e3e97-109">The projects in this sample include an Entity Data Model based on the `Northwind` database.</span></span> <span data-ttu-id="e3e97-110">Model można znaleźć, otwierając `Northwind.edmx` pliku, który znajduje się w projekcie.</span><span class="sxs-lookup"><span data-stu-id="e3e97-110">You can find the model by opening the `Northwind.edmx` file that is included in the project.</span></span> <span data-ttu-id="e3e97-111">Jest to model, który definiuje kształt obiektów, które mogą być udostępniane za pomocą ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="e3e97-111">This is the model that defines the shape of the objects that can be accessed using the ADO.NET Entity Framework.</span></span>  
  
 <span data-ttu-id="e3e97-112">W tym przykładzie znajdują się następujące działania:</span><span class="sxs-lookup"><span data-stu-id="e3e97-112">The following activities are included in this sample:</span></span>  
  
-   <span data-ttu-id="e3e97-113">`EntitySQLQuery``EntitySQLQuery` Działanie umożliwia pobieranie obiektów z bazy danych na podstawie ciągu zapytania SQL jednostki.</span><span class="sxs-lookup"><span data-stu-id="e3e97-113">`EntitySQLQuery`: The `EntitySQLQuery` activity allows you to retrieve objects from the database based on an Entity SQL query string.</span></span> <span data-ttu-id="e3e97-114">Jednostka SQL jest język niezależnie od magazynu, który jest podobny do bazy danych SQL i umożliwia określenie zapytania oparte na modelu koncepcyjnego i jednostek, które są częścią modelu lub domeny.</span><span class="sxs-lookup"><span data-stu-id="e3e97-114">Entity SQL is a store independent language that is similar to SQL and it allows you to specify queries based on the conceptual model and the entities that are a part of the model or domain.</span></span> <span data-ttu-id="e3e97-115">Aby uzyskać więcej informacji na temat jednostki języka SQL, zobacz [jednostki języka SQL](https://go.microsoft.com/fwlink/?LinkId=165646).</span><span class="sxs-lookup"><span data-stu-id="e3e97-115">For more information about Entity SQL Language, see [Entity SQL Language](https://go.microsoft.com/fwlink/?LinkId=165646).</span></span>  
  
-   <span data-ttu-id="e3e97-116">`EntityLinqQuery`: To działanie umożliwia pobieranie obiektów z bazy danych na podstawie zapytania LINQ lub predykat.</span><span class="sxs-lookup"><span data-stu-id="e3e97-116">`EntityLinqQuery`: This activity allows you to retrieve objects from the database based on a LINQ query or predicate.</span></span>  
  
-   <span data-ttu-id="e3e97-117">`EntityAdd``EntityAdd` Działań pozwala na dodawanie jednostki lub kolekcję jednostek w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="e3e97-117">`EntityAdd`: The `EntityAdd` activity allows you to add an entity or a collection of entities to the database.</span></span>  
  
-   <span data-ttu-id="e3e97-118">`EntityDelete``EntityDelete` Działanie umożliwia usunięcie z bazy danych jednostki lub kolekcję jednostek.</span><span class="sxs-lookup"><span data-stu-id="e3e97-118">`EntityDelete`: The `EntityDelete` activity allows you to delete an entity or a collection of entities from the database.</span></span>  
  
-   <span data-ttu-id="e3e97-119">`ObjectContextScope`: Działania opisanych powyżej można używać tylko w nadrzędnym `ObjectContextScope` wystąpienie działania.</span><span class="sxs-lookup"><span data-stu-id="e3e97-119">`ObjectContextScope`: The previously mentioned activities can only be used within a containing `ObjectContextScope` activity instance.</span></span> <span data-ttu-id="e3e97-120">`ObjectContextScope` Działanie ustawia połączenie z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="e3e97-120">The `ObjectContextScope` activity sets up the connection to the database.</span></span> <span data-ttu-id="e3e97-121">Wymaga parametrów połączenia (albo zostały przekazane lub pobrany przy użyciu ustawienia pliku konfiguracyjnego).</span><span class="sxs-lookup"><span data-stu-id="e3e97-121">It requires a connection string (that is either passed in or retrieved using a configuration file setting).</span></span> <span data-ttu-id="e3e97-122">`ObjectContextScope` Działania można łatwo wykonywać grupą powiązanych operacji na jednostkach.</span><span class="sxs-lookup"><span data-stu-id="e3e97-122">The `ObjectContextScope` activity makes it easy to perform a group of related operations on entities.</span></span> <span data-ttu-id="e3e97-123">Ponieważ ten zakres przechowuje aktywnego połączenia, jest utrwalić bez zakresu.</span><span class="sxs-lookup"><span data-stu-id="e3e97-123">Because this scope maintains an active connection, it is a No Persist scope.</span></span> <span data-ttu-id="e3e97-124">Ponadto, jeśli `ObjectContextScope` wyjścia działania, wszelkie zmiany wprowadzone do obiektów pobrany przy użyciu działań jednostek w tym zakresie automatycznie pobrać utrwalane w bazie danych, a nie jawne lub kolejnych czynności do zapisywania obiektów z powrotem do Baza danych.</span><span class="sxs-lookup"><span data-stu-id="e3e97-124">In addition, when the `ObjectContextScope` activity exits, any changes that are made to objects retrieved using Entity Activities within that scope automatically get persisted back to the database, and no explicit or subsequent action is required to save objects back to the database.</span></span>  
  
## <a name="using-the-entity-activities"></a><span data-ttu-id="e3e97-125">Za pomocą działania jednostki</span><span class="sxs-lookup"><span data-stu-id="e3e97-125">Using the entity activities</span></span>  
 <span data-ttu-id="e3e97-126">Poniższe fragmenty kodu przedstawiają sposób działania jednostki znajdujące się w tym przykładzie są używane.</span><span class="sxs-lookup"><span data-stu-id="e3e97-126">The following code snippets demonstrate how to use the entity activities presented in this sample.</span></span>  
  
### <a name="entitysql"></a><span data-ttu-id="e3e97-127">EntitySql</span><span class="sxs-lookup"><span data-stu-id="e3e97-127">EntitySql</span></span>  
 <span data-ttu-id="e3e97-128">Poniższy fragment kodu przedstawia, jak wykonywać zapytania dla wszystkich klientów w Londynie sortowane według nazwy i jak do iteracji przez listę klientów.</span><span class="sxs-lookup"><span data-stu-id="e3e97-128">The code snippet below shows how to query all customers in London sorted by name and how to iterate through the list of customers.</span></span>  
  
```  
Variable<IEnumerable<Customer>> londonCustomers = new Variable<IEnumerable<Customer>>();  
DelegateInArgument<Customer> iterationVariable = new DelegateInArgument<Customer>();  
  
// create and return the workflow  
return new ObjectContextScope  
{  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Variables = { londonCustomers },  
    Body = new Sequence  
        {  
            Activities =   
                {               
                    new WriteLine { Text = "Executing query" },                            
                    // query for all customers that are in london   
                    new EntitySqlQuery<Customer>  
                    {  
                        EntitySql =  @"SELECT VALUE Customer   
                                        FROM NorthwindEntities.Customers AS Customer   
                                        WHERE Customer.City = 'London'   
                                        ORDER BY Customer.ContactName",  
                        Result = londonCustomers  
                    },  
  
                    // iterate through the list of customers and display them   
                    new ForEach<Customer>  
                    {                                      
                        Values = londonCustomers,  
                        Body = new ActivityAction<Customer>  
                        {  
                            Argument = iterationVariable,  
                            Handler = new WriteLine   
                            {   
                                  Text = new InArgument<String>(e =>    
                                              iterationVariable.Get(e).ContactName)   
                            }  
                        }  
                    }  
                }  
        }                 
};     
```  
  
### <a name="entitylinqquery"></a><span data-ttu-id="e3e97-129">EntityLinqQuery</span><span class="sxs-lookup"><span data-stu-id="e3e97-129">EntityLinqQuery</span></span>  
 <span data-ttu-id="e3e97-130">Poniższy fragment kodu przedstawia, jak wykonywać zapytania dla wszystkich klientów w Londynie i iterowania przez uzyskaną listę klientów.</span><span class="sxs-lookup"><span data-stu-id="e3e97-130">The code snippet below shows how to query all customers in London and how to iterate through the resulting list of customers.</span></span>  
  
```  
Variable<IEnumerable<Customer>> londonCustomers = new Variable<IEnumerable<Customer>>() { Name = "LondonCustomers" };  
DelegateInArgument<Customer> iterationVariable = new DelegateInArgument<Customer>() { Name = "iterationVariable" };  
  
return new ObjectContextScope  
{  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Variables = { londonCustomers },  
    Body = new Sequence  
    {  
        Activities =   
        {               
            // return all the customers that match with the provided Linq predicate  
            new EntityLinqQuery<Customer>  
            {   
                Predicate = new LambdaValue<Func<Customer, bool>>(  
                          ctx => new Func<Customer, bool>(c => c.City.Equals("London"))),                              
                Result = londonCustomers  
            },  
  
            // iterate through the list of customers and display in the console  
            new ForEach<Customer>  
            {                                      
                Values = londonCustomers,  
                Body = new ActivityAction<Customer>  
                {  
                    Argument = iterationVariable,  
                    Handler = new WriteLine   
                    {   
                        Text = new InArgument<String>(e =>   
                                      iterationVariable.Get(e).ContactName)   
                    }  
                }  
            }  
        }  
    }  
};  
```  
  
### <a name="entityadd"></a><span data-ttu-id="e3e97-131">EntityAdd</span><span class="sxs-lookup"><span data-stu-id="e3e97-131">EntityAdd</span></span>  
 <span data-ttu-id="e3e97-132">Poniższy fragment kodu przedstawia sposób dodawania rekord OrderDetail do istniejącego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="e3e97-132">The code snippet below shows how to add an OrderDetail record to an existing Order.</span></span>  
  
```  
Variable<IEnumerable<Order>> orders = new Variable<IEnumerable<Order>>();  
Variable<IEnumerable<OrderDetail>> orderDetails = new Variable<IEnumerable<OrderDetail>>();  
Variable<Order> order = new Variable<Order>();  
Variable<OrderDetail> orderDetail = new Variable<OrderDetail>();              
  
return new ObjectContextScope  
{  
    Variables = { order, orders, orderDetail, orderDetails },  
    ContainerName = "NorthwindEntities",  
    ConnectionString = new InArgument<string>(connStr),                  
    Body = new Sequence  
    {                      
        Activities =   
        {                            
           // get the order where we want to add the detail  
           new EntitySqlQuery<Order>  
           {  
               EntitySql =    
                    @"SELECT VALUE [Order]  
                      FROM NorthwindEntities.Orders as [Order]  
                      WHERE Order.OrderID == 10249",  
               Result = orders  
           },  
  
           // store the order in a variable  
           new Assign<Order>   
           {  
               To = new OutArgument<Order>(order),  
               Value = new InArgument<Order>(c => orders.Get(c).First<Order>())  
           },  
  
           // add the detail to the order  
           new EntityAdd<OrderDetail>  
           {  
               Entity = new InArgument<OrderDetail>(c =>   
                                         new OrderDetail {   
                                                  OrderID=10249, ProductID=11,   
                                                  Quantity=1, UnitPrice = 15,   
                                                  Discount = 0, Order = order.Get(c) })  
           }  
        }  
    }  
};  
```  
  
### <a name="entitydelete"></a><span data-ttu-id="e3e97-133">EntityDelete</span><span class="sxs-lookup"><span data-stu-id="e3e97-133">EntityDelete</span></span>  
 <span data-ttu-id="e3e97-134">Poniższy fragment kodu przedstawia sposób usuwania istniejącego rekordu OrderDetail w kolejności (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="e3e97-134">The code snippet below shows how to delete an existing OrderDetail record in an Order (if it exists).</span></span>  
  
```  
Variable<IEnumerable<OrderDetail>> orderDetails = new Variable<IEnumerable<OrderDetail>>();              
  
return new ObjectContextScope  
{  
    Variables = { orderDetails },  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Body = new Sequence  
    {  
        Activities =   
        {               
            // find the entitiy to be deleted (order detail for product 11 in order 10249)  
            new EntitySqlQuery<OrderDetail>  
            {  
                EntitySql = @"SELECT VALUE OrderDetail  
                                FROM NorthwindEntities.OrderDetails as OrderDetail  
                               WHERE OrderDetail.OrderID == 10249   
                                 AND OrderDetail.ProductID == 11",  
                Result = orderDetails  
            },  
  
            // if the order detail is found, delete it, otherwise, display a message  
            new If  
            {  
                Condition = new InArgument<bool>(c=>orderDetails.Get(c).Count() > 0),  
                Then = new Sequence  
                {   
                    Activities =   
                    {                                      
                        new EntityDelete<OrderDetail>  
                        {  
                            Entity = new InArgument<OrderDetail>(c =>   
                                              orderDetails.Get(c).First<OrderDetail>())  
                        },  
                    }  
                },                              
                Else = new WriteLine { Text = "Order Detail for Deleting not found" }                              
            }                                                  
        }  
    }  
};  
```  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="e3e97-135">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="e3e97-135">To use this sample</span></span>  
 <span data-ttu-id="e3e97-136">Należy utworzyć `Northwind` bazy danych w lokalnym wystąpieniem serwera SQL Express przed uruchomieniem tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="e3e97-136">You must create the `Northwind` database in your local SQL server Express instance before running this sample.</span></span>  
  
#### <a name="to-set-up-the-northwind-database"></a><span data-ttu-id="e3e97-137">Aby skonfigurować bazę danych Northwind</span><span class="sxs-lookup"><span data-stu-id="e3e97-137">To set up the Northwind database</span></span>  
  
1.  <span data-ttu-id="e3e97-138">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="e3e97-138">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="e3e97-139">W nowym oknie wiersza polecenia przejdź do folderu EntityActivities\CS.</span><span class="sxs-lookup"><span data-stu-id="e3e97-139">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="e3e97-140">Typ `setup.cmd` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="e3e97-140">Type `setup.cmd` and press ENTER.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="e3e97-141">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="e3e97-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="e3e97-142">Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania EntityActivities.sln.</span><span class="sxs-lookup"><span data-stu-id="e3e97-142">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EntityActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="e3e97-143">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="e3e97-143">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e3e97-144">Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="e3e97-144">To run the solution, press CTRL+F5.</span></span>  
  
 <span data-ttu-id="e3e97-145">Po uruchomieniu tego przykładu, możesz usunąć `Northwind` bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e3e97-145">After running this sample, you may want to remove the `Northwind` database.</span></span>  
  
#### <a name="to-uninstall-the-northwind-database"></a><span data-ttu-id="e3e97-146">Aby odinstalować bazy danych Northwind</span><span class="sxs-lookup"><span data-stu-id="e3e97-146">To uninstall the Northwind database</span></span>  
  
1.  <span data-ttu-id="e3e97-147">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="e3e97-147">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="e3e97-148">W nowym oknie wiersza polecenia przejdź do folderu EntityActivities\CS.</span><span class="sxs-lookup"><span data-stu-id="e3e97-148">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="e3e97-149">Typ `cleanup.cmd` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="e3e97-149">Type `cleanup.cmd` and press ENTER.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e3e97-150">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e3e97-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e3e97-151">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e3e97-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e3e97-152">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="e3e97-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e3e97-153">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e3e97-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`