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
# <a name="entity-activities"></a>Działania jednostki
Ten przykład przedstawia sposób użycia programu ADO.NET Entity Framework z [!INCLUDE[wf2](../../../../includes/wf2-md.md)] uprościć dostęp do danych.  
  
 ADO.NET Entity Framework umożliwia deweloperom pracy z danymi w postaci obiektów specyficznego dla domeny, właściwości i relacje, takich jak klienci, zamówienia, szczegółów zamówienia i relacji między tymi obiektami. ADO.NET Entity Framework robi to przez zapewnienie na poziomie abstrakcji, która umożliwia programowanie w odniesieniu do modelu koncepcyjnego aplikacji, zamiast programowanie bezpośrednio ze schematem relacyjnego magazynu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Zobacz ADO.NET Entity Framework [ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549).  
  
## <a name="sample-details"></a>Szczegóły próbki  
 W przykładzie użyto `Northwind` bazy danych i obejmuje skrypty umożliwiające tworzenie i usuwanie `Northwind` bazy danych (Setup.cmd i Cleanup.cmd). Projekty w tym przykładzie obejmują modelu danych jednostki na podstawie `Northwind` bazy danych. Można znaleźć modelu, otwierając `Northwind.edmx` pliku, który jest dołączony do projektu. To jest model, który określa kształt obiektów, które są dostępne przy użyciu programu ADO.NET Entity Framework.  
  
 Ten przykład obejmuje wykonywanie następujących czynności:  
  
-   `EntitySQLQuery`: `EntitySQLQuery` Działania umożliwia pobieranie obiektów z bazy danych, w zależności od ciągu zapytania SQL jednostki. Jednostka SQL jest językiem niezależne magazynu jest podobny do bazy danych SQL i umożliwia określenie zapytań na podstawie modelu koncepcyjnego i jednostkami, które są częścią modelu lub domeny. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Jednostki języka SQL, zobacz [języka SQL jednostki](http://go.microsoft.com/fwlink/?LinkId=165646).  
  
-   `EntityLinqQuery`: To działanie umożliwia pobieranie obiektów z bazy danych na podstawie zapytania LINQ lub predykatu.  
  
-   `EntityAdd`: `EntityAdd` Działania umożliwia dodanie jednostki lub kolekcji jednostek w bazie danych.  
  
-   `EntityDelete`: `EntityDelete` Działania umożliwia usunięcie jednostki lub kolekcji jednostek z bazy danych.  
  
-   `ObjectContextScope`: Działania opisane powyżej można używać tylko w nadrzędnym `ObjectContextScope` wystąpienia działania. `ObjectContextScope` Działanie ustawia połączenie z bazą danych. Wymaga to ciąg połączenia (który jest przekazany lub pobrany przy użyciu ustawienia konfiguracji pliku). `ObjectContextScope` Działania można łatwo przeprowadzić grupy powiązanych operacji na jednostkach. Ponieważ ten zakres ma aktywne połączenie, jest zakres nie będą się powtarzać. Ponadto, kiedy `ObjectContextScope` wyjścia działania, wszystkie zmiany wprowadzone w obiektach pobrany przy użyciu jednostek działań w ramach tego zakresu automatycznie pobrać utrwalone w bazie danych, a żadne jawne lub kolejne działania są niezbędne do zapisywania obiektów z powrotem do Baza danych.  
  
## <a name="using-the-entity-activities"></a>Przy użyciu działań jednostki  
 Poniższe fragmenty kodu przedstawiają sposób działania jednostki przedstawionych w tym przykładzie.  
  
### <a name="entitysql"></a>EntitySql  
 Poniższy fragment kodu przedstawia, jak wykonać zapytanie dotyczące wszystkich klientów w Londynie sortowane według nazwy i jak wykonać iterację na liście klientów.  
  
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
 Poniższy fragment kodu pokazano, jak wykonać zapytanie dotyczące wszystkich klientów w Londynie oraz jak wykonać iterację wynikowy listę klientów.  
  
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
 Poniższy fragment kodu przedstawia sposób dodawania rekordu OrderDetail do istniejącego zamówienia.  
  
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
 Poniższy fragment kodu przedstawia sposób usuwanie istniejącego rekordu OrderDetail w kolejności (jeśli istnieje).  
  
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
 Należy utworzyć `Northwind` bazy danych w sieci lokalnej wystąpienie serwera SQL Express przed uruchomieniem tego przykładu.  
  
#### <a name="to-set-up-the-northwind-database"></a>Do konfigurowania bazy danych Northwind  
  
1.  Otwórz wiersz polecenia.  
  
2.  W nowym oknie wiersza polecenia przejdź do folderu EntityActivities\CS.  
  
3.  Typ `setup.cmd` i naciśnij klawisz ENTER.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania EntityActivities.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
 Po uruchomieniu tego przykładu, można usunąć `Northwind` bazy danych.  
  
#### <a name="to-uninstall-the-northwind-database"></a>Aby odinstalować bazy danych Northwind  
  
1.  Otwórz wiersz polecenia.  
  
2.  W nowym oknie wiersza polecenia przejdź do folderu EntityActivities\CS.  
  
3.  Typ `cleanup.cmd` i naciśnij klawisz ENTER.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`  
  
## <a name="see-also"></a>Zobacz też
