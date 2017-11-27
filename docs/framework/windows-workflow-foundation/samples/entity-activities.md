---
title: "Działania jednostki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c04f7413-7fb8-40c6-819e-dc92b145b62e
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cc1ddb69e69e603c4460ef6db1a60f4e2e650749
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="entity-activities"></a><span data-ttu-id="0a0cf-102">Działania jednostki</span><span class="sxs-lookup"><span data-stu-id="0a0cf-102">Entity Activities</span></span>
<span data-ttu-id="0a0cf-103">Ten przykład przedstawia sposób użycia programu ADO.NET Entity Framework z [!INCLUDE[wf2](../../../../includes/wf2-md.md)] uprościć dostęp do danych.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-103">This sample shows how to use the ADO.NET Entity Framework with [!INCLUDE[wf2](../../../../includes/wf2-md.md)] to simplify data access.</span></span>  
  
 <span data-ttu-id="0a0cf-104">ADO.NET Entity Framework umożliwia deweloperom pracy z danymi w postaci obiektów specyficznego dla domeny, właściwości i relacje, takich jak klienci, zamówienia, szczegółów zamówienia i relacji między tymi obiektami.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-104">The ADO.NET Entity Framework enables developers to work with data in the form of domain-specific objects, properties and relationships such as Customers, Orders, Order Details and the relationships between these entities.</span></span> <span data-ttu-id="0a0cf-105">ADO.NET Entity Framework robi to przez zapewnienie na poziomie abstrakcji, która umożliwia programowanie w odniesieniu do modelu koncepcyjnego aplikacji, zamiast programowanie bezpośrednio ze schematem relacyjnego magazynu.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-105">The ADO.NET Entity Framework does this by providing a level of abstraction that enables programming against a conceptual application model instead of programming directly against a relational storage schema.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="0a0cf-106">Zobacz ADO.NET Entity Framework [ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549).</span><span class="sxs-lookup"><span data-stu-id="0a0cf-106"> the ADO.NET Entity Framework see [ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549).</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="0a0cf-107">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="0a0cf-107">Sample details</span></span>  
 <span data-ttu-id="0a0cf-108">W przykładzie użyto `Northwind` bazy danych i obejmuje skrypty umożliwiające tworzenie i usuwanie `Northwind` bazy danych (Setup.cmd i Cleanup.cmd).</span><span class="sxs-lookup"><span data-stu-id="0a0cf-108">This sample uses the `Northwind` database and includes scripts for creating and removing the `Northwind` database (Setup.cmd and Cleanup.cmd).</span></span> <span data-ttu-id="0a0cf-109">Projekty w tym przykładzie obejmują modelu danych jednostki na podstawie `Northwind` bazy danych.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-109">The projects in this sample include an Entity Data Model based on the `Northwind` database.</span></span> <span data-ttu-id="0a0cf-110">Można znaleźć modelu, otwierając `Northwind.edmx` pliku, który jest dołączony do projektu.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-110">You can find the model by opening the `Northwind.edmx` file that is included in the project.</span></span> <span data-ttu-id="0a0cf-111">To jest model, który określa kształt obiektów, które są dostępne przy użyciu programu ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-111">This is the model that defines the shape of the objects that can be accessed using the ADO.NET Entity Framework.</span></span>  
  
 <span data-ttu-id="0a0cf-112">Ten przykład obejmuje wykonywanie następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="0a0cf-112">The following activities are included in this sample:</span></span>  
  
-   <span data-ttu-id="0a0cf-113">`EntitySQLQuery`: `EntitySQLQuery` Działania umożliwia pobieranie obiektów z bazy danych, w zależności od ciągu zapytania SQL jednostki.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-113">`EntitySQLQuery`: The `EntitySQLQuery` activity allows you to retrieve objects from the database based on an Entity SQL query string.</span></span> <span data-ttu-id="0a0cf-114">Jednostka SQL jest językiem niezależne magazynu jest podobny do bazy danych SQL i umożliwia określenie zapytań na podstawie modelu koncepcyjnego i jednostkami, które są częścią modelu lub domeny.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-114">Entity SQL is a store independent language that is similar to SQL and it allows you to specify queries based on the conceptual model and the entities that are a part of the model or domain.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="0a0cf-115">Jednostki języka SQL, zobacz [języka SQL jednostki](http://go.microsoft.com/fwlink/?LinkId=165646).</span><span class="sxs-lookup"><span data-stu-id="0a0cf-115"> Entity SQL Language, see [Entity SQL Language](http://go.microsoft.com/fwlink/?LinkId=165646).</span></span>  
  
-   <span data-ttu-id="0a0cf-116">`EntityLinqQuery`: To działanie umożliwia pobieranie obiektów z bazy danych na podstawie zapytania LINQ lub predykatu.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-116">`EntityLinqQuery`: This activity allows you to retrieve objects from the database based on a LINQ query or predicate.</span></span>  
  
-   <span data-ttu-id="0a0cf-117">`EntityAdd`: `EntityAdd` Działania umożliwia dodanie jednostki lub kolekcji jednostek w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-117">`EntityAdd`: The `EntityAdd` activity allows you to add an entity or a collection of entities to the database.</span></span>  
  
-   <span data-ttu-id="0a0cf-118">`EntityDelete`: `EntityDelete` Działania umożliwia usunięcie jednostki lub kolekcji jednostek z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-118">`EntityDelete`: The `EntityDelete` activity allows you to delete an entity or a collection of entities from the database.</span></span>  
  
-   <span data-ttu-id="0a0cf-119">`ObjectContextScope`: Działania opisane powyżej można używać tylko w nadrzędnym `ObjectContextScope` wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-119">`ObjectContextScope`: The previously mentioned activities can only be used within a containing `ObjectContextScope` activity instance.</span></span> <span data-ttu-id="0a0cf-120">`ObjectContextScope` Działanie ustawia połączenie z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-120">The `ObjectContextScope` activity sets up the connection to the database.</span></span> <span data-ttu-id="0a0cf-121">Wymaga to ciąg połączenia (który jest przekazany lub pobrany przy użyciu ustawienia konfiguracji pliku).</span><span class="sxs-lookup"><span data-stu-id="0a0cf-121">It requires a connection string (that is either passed in or retrieved using a configuration file setting).</span></span> <span data-ttu-id="0a0cf-122">`ObjectContextScope` Działania można łatwo przeprowadzić grupy powiązanych operacji na jednostkach.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-122">The `ObjectContextScope` activity makes it easy to perform a group of related operations on entities.</span></span> <span data-ttu-id="0a0cf-123">Ponieważ ten zakres ma aktywne połączenie, jest zakres nie będą się powtarzać.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-123">Because this scope maintains an active connection, it is a No Persist scope.</span></span> <span data-ttu-id="0a0cf-124">Ponadto, kiedy `ObjectContextScope` wyjścia działania, wszystkie zmiany wprowadzone w obiektach pobrany przy użyciu jednostek działań w ramach tego zakresu automatycznie pobrać utrwalone w bazie danych, a żadne jawne lub kolejne działania są niezbędne do zapisywania obiektów z powrotem do Baza danych.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-124">In addition, when the `ObjectContextScope` activity exits, any changes that are made to objects retrieved using Entity Activities within that scope automatically get persisted back to the database, and no explicit or subsequent action is required to save objects back to the database.</span></span>  
  
## <a name="using-the-entity-activities"></a><span data-ttu-id="0a0cf-125">Przy użyciu działań jednostki</span><span class="sxs-lookup"><span data-stu-id="0a0cf-125">Using the entity activities</span></span>  
 <span data-ttu-id="0a0cf-126">Poniższe fragmenty kodu przedstawiają sposób działania jednostki przedstawionych w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-126">The following code snippets demonstrate how to use the entity activities presented in this sample.</span></span>  
  
### <a name="entitysql"></a><span data-ttu-id="0a0cf-127">EntitySql</span><span class="sxs-lookup"><span data-stu-id="0a0cf-127">EntitySql</span></span>  
 <span data-ttu-id="0a0cf-128">Poniższy fragment kodu przedstawia, jak wykonać zapytanie dotyczące wszystkich klientów w Londynie sortowane według nazwy i jak wykonać iterację na liście klientów.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-128">The code snippet below shows how to query all customers in London sorted by name and how to iterate through the list of customers.</span></span>  
  
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
  
### <a name="entitylinqquery"></a><span data-ttu-id="0a0cf-129">EntityLinqQuery</span><span class="sxs-lookup"><span data-stu-id="0a0cf-129">EntityLinqQuery</span></span>  
 <span data-ttu-id="0a0cf-130">Poniższy fragment kodu pokazano, jak wykonać zapytanie dotyczące wszystkich klientów w Londynie oraz jak wykonać iterację wynikowy listę klientów.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-130">The code snippet below shows how to query all customers in London and how to iterate through the resulting list of customers.</span></span>  
  
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
  
### <a name="entityadd"></a><span data-ttu-id="0a0cf-131">EntityAdd</span><span class="sxs-lookup"><span data-stu-id="0a0cf-131">EntityAdd</span></span>  
 <span data-ttu-id="0a0cf-132">Poniższy fragment kodu przedstawia sposób dodawania rekordu OrderDetail do istniejącego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-132">The code snippet below shows how to add an OrderDetail record to an existing Order.</span></span>  
  
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
  
### <a name="entitydelete"></a><span data-ttu-id="0a0cf-133">EntityDelete</span><span class="sxs-lookup"><span data-stu-id="0a0cf-133">EntityDelete</span></span>  
 <span data-ttu-id="0a0cf-134">Poniższy fragment kodu przedstawia sposób usuwanie istniejącego rekordu OrderDetail w kolejności (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="0a0cf-134">The code snippet below shows how to delete an existing OrderDetail record in an Order (if it exists).</span></span>  
  
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
  
## <a name="to-use-this-sample"></a><span data-ttu-id="0a0cf-135">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="0a0cf-135">To use this sample</span></span>  
 <span data-ttu-id="0a0cf-136">Należy utworzyć `Northwind` bazy danych w sieci lokalnej wystąpienie serwera SQL Express przed uruchomieniem tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-136">You must create the `Northwind` database in your local SQL server Express instance before running this sample.</span></span>  
  
#### <a name="to-set-up-the-northwind-database"></a><span data-ttu-id="0a0cf-137">Do konfigurowania bazy danych Northwind</span><span class="sxs-lookup"><span data-stu-id="0a0cf-137">To set up the Northwind database</span></span>  
  
1.  <span data-ttu-id="0a0cf-138">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-138">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="0a0cf-139">W nowym oknie wiersza polecenia przejdź do folderu EntityActivities\CS.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-139">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="0a0cf-140">Typ `setup.cmd` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-140">Type `setup.cmd` and press ENTER.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="0a0cf-141">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="0a0cf-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="0a0cf-142">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania EntityActivities.sln.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-142">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EntityActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="0a0cf-143">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-143">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="0a0cf-144">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-144">To run the solution, press CTRL+F5.</span></span>  
  
 <span data-ttu-id="0a0cf-145">Po uruchomieniu tego przykładu, można usunąć `Northwind` bazy danych.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-145">After running this sample, you may want to remove the `Northwind` database.</span></span>  
  
#### <a name="to-uninstall-the-northwind-database"></a><span data-ttu-id="0a0cf-146">Aby odinstalować bazy danych Northwind</span><span class="sxs-lookup"><span data-stu-id="0a0cf-146">To uninstall the Northwind database</span></span>  
  
1.  <span data-ttu-id="0a0cf-147">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-147">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="0a0cf-148">W nowym oknie wiersza polecenia przejdź do folderu EntityActivities\CS.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-148">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="0a0cf-149">Typ `cleanup.cmd` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-149">Type `cleanup.cmd` and press ENTER.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0a0cf-150">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0a0cf-151">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="0a0cf-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0a0cf-152">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0a0cf-153">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0a0cf-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`  
  
## <a name="see-also"></a><span data-ttu-id="0a0cf-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a0cf-154">See Also</span></span>
