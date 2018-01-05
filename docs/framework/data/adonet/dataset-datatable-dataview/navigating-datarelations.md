---
title: Nawigowanie po DataRelations
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d7d1dc98bdb235c6501ee503494d3c2bdc3a1820
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="navigating-datarelations"></a><span data-ttu-id="3e7fc-102">Nawigowanie po DataRelations</span><span class="sxs-lookup"><span data-stu-id="3e7fc-102">Navigating DataRelations</span></span>
<span data-ttu-id="3e7fc-103">Jeden z podstawowych funkcji <xref:System.Data.DataRelation> jest umożliwienie nawigacji z jednego <xref:System.Data.DataTable> do drugiej w ramach <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-103">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="3e7fc-104">Dzięki temu można pobrać wszystkich odnośnych <xref:System.Data.DataRow> obiektów w jednym **DataTable** , gdy jeden **DataRow** z powiązanego **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-104">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="3e7fc-105">Na przykład po ustanowieniu **DataRelation** między spisu klientów i tabela zamówienia, możesz pobrać wszystkie wiersze kolejności dla wiersza określonego klienta przy użyciu **GetChildRows**.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-105">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="3e7fc-106">Poniższy przykład kodu tworzy **DataRelation** między **klientów** tabeli i **zamówień** spis **DataSet** i zwraca wszystkie zamówienia dla każdego klienta.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-106">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="3e7fc-107">Kolejnym przykładzie opiera się na poprzednim przykładzie związanych ze sobą czterech tabel i nawigowanie po relacjach tych.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-107">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="3e7fc-108">Tak jak w poprzednim przykładzie **CustomerID** odnosi się **klientów** do tabeli **zamówień** tabeli.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-108">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="3e7fc-109">Dla każdego klienta w **klientów** tabeli wierszy podrzędnych w **zamówień** tabeli są określone, aby można było zwrócenie liczby zamówień ma konkretnego klienta i ich **OrderID** wartości.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-109">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="3e7fc-110">Przykład rozwinięte również zwraca wartości z **SzczegółyZamówienia** i **produktów** tabel.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-110">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="3e7fc-111">**Zamówień** tabela jest powiązana z **SzczegółyZamówienia** tabeli, używając **OrderID** ustalenie, dla każdego klienta kolejności, jakie produktów i ilości zostały uporządkowane.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-111">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="3e7fc-112">Ponieważ **SzczegółyZamówienia** tabela zawiera tylko **ProductID** uporządkowanej produktu **SzczegółyZamówienia** jest powiązany z **produktów** przy użyciu **ProductID** celu powrotu **ProductName**.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-112">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="3e7fc-113">W tej relacji **produktów** tabeli jest nadrzędny i **szczegółów zamówienia** tabeli jest elementem podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-113">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="3e7fc-114">W wyniku iteracja **SzczegółyZamówienia** tabeli **element GetParentRow** jest wywoływana w celu pobrania pokrewny **ProductName** wartość.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-114">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="3e7fc-115">Zwróć uwagę, że w przypadku **DataRelation** jest tworzona dla **klientów** i **zamówień** tabel, nie określono wartości dla **createConstraints**flagi (wartość domyślna to **true**).</span><span class="sxs-lookup"><span data-stu-id="3e7fc-115">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="3e7fc-116">Przy założeniu, że wszystkie wiersze w **zamówień** tabela ma **CustomerID** wartość, która istnieje w obiekcie nadrzędnym **klientów** tabeli.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-116">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="3e7fc-117">Jeśli **CustomerID** istnieje w **zamówień** tabeli, która nie istnieje w **klientów** tabeli <xref:System.Data.ForeignKeyConstraint> powoduje zgłoszenie wyjątku zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-117">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="3e7fc-118">Jeśli kolumna podrzędnych może zawierać wartości, które nie zawiera kolumny nadrzędnej, należy skonfigurować **createConstraints** flaga **false** podczas dodawania **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-118">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="3e7fc-119">W tym przykładzie **createConstraints** flaga jest ustawiona na **false** dla **DataRelation** między **zamówień** tabeli i  **SzczegółyZamówień** tabeli.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-119">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="3e7fc-120">Umożliwia to aplikacji zwrócić wszystkie rekordy z **SzczegółyZamówienia** tabeli i tylko podzestaw rekordów z **zamówień** tabeli bez generowania wyjątku czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-120">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="3e7fc-121">Przykładowe rozwinięte generuje dane wyjściowe w następującym formacie.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-121">The expanded sample generates output in the following format.</span></span>  
  
```  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 <span data-ttu-id="3e7fc-122">Poniższy przykładowy kod jest przykładem rozszerzonej gdzie wartości z **SzczegółyZamówienia** i **produktów** tabele są zwracane z tylko podzestaw rekordów **zamówień**tabeli są zwracane.</span><span class="sxs-lookup"><span data-stu-id="3e7fc-122">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3e7fc-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e7fc-123">See Also</span></span>  
 [<span data-ttu-id="3e7fc-124">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="3e7fc-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="3e7fc-125">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="3e7fc-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
