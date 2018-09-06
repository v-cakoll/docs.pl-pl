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
# <a name="entity-activities"></a>Działania jednostki
W tym przykładzie pokazano, jak za pomocą ADO.NET Entity Framework Windows Workflow Foundation Aby uprościć dostęp do danych.  
  
 ADO.NET Entity Framework umożliwia deweloperom pracę z danymi w postaci obiektów specyficznych dla domeny, właściwości i relacje, takich jak klientów i zamówień, szczegółów zamówienia relacji między tymi jednostkami. ADO.NET Entity Framework robi to dzięki zapewnieniu poziomu abstrakcji, która umożliwia programowanie w oparciu o model koncepcyjny aplikacji zamiast programowania bezpośrednio w odniesieniu do schematu magazyn relacyjny. Aby uzyskać więcej informacji na temat ADO.NET Entity Framework, zobacz [ADO.NET Entity Framework](https://go.microsoft.com/fwlink/?LinkId=165549).  
  
## <a name="sample-details"></a>Przykład szczegółów  
 W tym przykładzie użyto `Northwind` bazy danych i obejmuje skrypty do tworzenia i usuwania `Northwind` bazy danych (plik Setup.cmd i Cleanup.cmd). Projekty, w tym przykładzie zawierają oparte na modelu danych jednostki `Northwind` bazy danych. Model można znaleźć, otwierając `Northwind.edmx` pliku, który znajduje się w projekcie. Jest to model, który definiuje kształt obiektów, które mogą być udostępniane za pomocą ADO.NET Entity Framework.  
  
 W tym przykładzie znajdują się następujące działania:  
  
-   `EntitySQLQuery``EntitySQLQuery` Działanie umożliwia pobieranie obiektów z bazy danych na podstawie ciągu zapytania SQL jednostki. Jednostka SQL jest język niezależnie od magazynu, który jest podobny do bazy danych SQL i umożliwia określenie zapytania oparte na modelu koncepcyjnego i jednostek, które są częścią modelu lub domeny. Aby uzyskać więcej informacji na temat jednostki języka SQL, zobacz [jednostki języka SQL](https://go.microsoft.com/fwlink/?LinkId=165646).  
  
-   `EntityLinqQuery`: To działanie umożliwia pobieranie obiektów z bazy danych na podstawie zapytania LINQ lub predykat.  
  
-   `EntityAdd``EntityAdd` Działań pozwala na dodawanie jednostki lub kolekcję jednostek w bazie danych.  
  
-   `EntityDelete``EntityDelete` Działanie umożliwia usunięcie z bazy danych jednostki lub kolekcję jednostek.  
  
-   `ObjectContextScope`: Działania opisanych powyżej można używać tylko w nadrzędnym `ObjectContextScope` wystąpienie działania. `ObjectContextScope` Działanie ustawia połączenie z bazą danych. Wymaga parametrów połączenia (albo zostały przekazane lub pobrany przy użyciu ustawienia pliku konfiguracyjnego). `ObjectContextScope` Działania można łatwo wykonywać grupą powiązanych operacji na jednostkach. Ponieważ ten zakres przechowuje aktywnego połączenia, jest utrwalić bez zakresu. Ponadto, jeśli `ObjectContextScope` wyjścia działania, wszelkie zmiany wprowadzone do obiektów pobrany przy użyciu działań jednostek w tym zakresie automatycznie pobrać utrwalane w bazie danych, a nie jawne lub kolejnych czynności do zapisywania obiektów z powrotem do Baza danych.  
  
## <a name="using-the-entity-activities"></a>Za pomocą działania jednostki  
 Poniższe fragmenty kodu przedstawiają sposób działania jednostki znajdujące się w tym przykładzie są używane.  
  
### <a name="entitysql"></a>EntitySql  
 Poniższy fragment kodu przedstawia, jak wykonywać zapytania dla wszystkich klientów w Londynie sortowane według nazwy i jak do iteracji przez listę klientów.  
  
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
  
### <a name="entitylinqquery"></a>EntityLinqQuery  
 Poniższy fragment kodu przedstawia, jak wykonywać zapytania dla wszystkich klientów w Londynie i iterowania przez uzyskaną listę klientów.  
  
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
  
### <a name="entityadd"></a>EntityAdd  
 Poniższy fragment kodu przedstawia sposób dodawania rekord OrderDetail do istniejącego zamówienia.  
  
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
  
### <a name="entitydelete"></a>EntityDelete  
 Poniższy fragment kodu przedstawia sposób usuwania istniejącego rekordu OrderDetail w kolejności (jeśli istnieje).  
  
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
  
## <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
 Należy utworzyć `Northwind` bazy danych w lokalnym wystąpieniem serwera SQL Express przed uruchomieniem tego przykładu.  
  
#### <a name="to-set-up-the-northwind-database"></a>Aby skonfigurować bazę danych Northwind  
  
1.  Otwórz wiersz polecenia.  
  
2.  W nowym oknie wiersza polecenia przejdź do folderu EntityActivities\CS.  
  
3.  Typ `setup.cmd` i naciśnij klawisz ENTER.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania EntityActivities.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
 Po uruchomieniu tego przykładu, możesz usunąć `Northwind` bazy danych.  
  
#### <a name="to-uninstall-the-northwind-database"></a>Aby odinstalować bazy danych Northwind  
  
1.  Otwórz wiersz polecenia.  
  
2.  W nowym oknie wiersza polecenia przejdź do folderu EntityActivities\CS.  
  
3.  Typ `cleanup.cmd` i naciśnij klawisz ENTER.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`