---
title: Nawigowanie w elementach DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: f4dfccad23bf5d15f5cbd0a33e76a136417e13ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204162"
---
# <a name="navigating-datarelations"></a><span data-ttu-id="70099-102">Nawigowanie w elementach DataRelation</span><span class="sxs-lookup"><span data-stu-id="70099-102">Navigating DataRelations</span></span>
<span data-ttu-id="70099-103">Jedną z podstawowych funkcji <xref:System.Data.DataRelation> jest umożliwienie nawigacji z jednego <xref:System.Data.DataTable> do drugiej w ramach <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="70099-103">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="70099-104">Dzięki temu można pobrać wszystkie powiązane <xref:System.Data.DataRow> obiekty w jednym **DataTable** , gdy jeden **DataRow** z powiązanych **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="70099-104">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="70099-105">Na przykład po ustanowieniu **DataRelation** między spisu klientów i tabelę zamówień, mogą pobierać wszystkie wiersze zamówienia dla wiersza określonego klienta za pomocą **GetChildRows**.</span><span class="sxs-lookup"><span data-stu-id="70099-105">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="70099-106">Poniższy przykład kodu tworzy **DataRelation** między **klientów** tabeli i **zamówienia** tabeli **DataSet** i zwraca wszystkie zamówienia dla każdego klienta.</span><span class="sxs-lookup"><span data-stu-id="70099-106">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="70099-107">Następny przykład opiera się na poprzednim przykładzie związanych ze sobą cztery tabele i nawigowanie po relacjach tych.</span><span class="sxs-lookup"><span data-stu-id="70099-107">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="70099-108">Co w poprzednim przykładzie **CustomerID** odnosi się **klientów** do tabeli **zamówienia** tabeli.</span><span class="sxs-lookup"><span data-stu-id="70099-108">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="70099-109">Dla każdego klienta w **klientów** tabeli wiersze podrzędne w **zamówienia** tabeli są określone, aby zwrócić liczbę zamówień ma określonego klienta i ich **OrderID** wartości.</span><span class="sxs-lookup"><span data-stu-id="70099-109">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="70099-110">Rozwinięty przykład zwraca również wartość wartości z **OrderDetails** i **produktów** tabel.</span><span class="sxs-lookup"><span data-stu-id="70099-110">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="70099-111">**Zamówienia** tabela jest powiązana z **OrderDetails** tabeli, używając **OrderID** Aby ustalić, dla każdego zamówienia klienta, jakich produktów i ilości zostały uporządkowane.</span><span class="sxs-lookup"><span data-stu-id="70099-111">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="70099-112">Ponieważ **OrderDetails** tabeli zawiera tylko **ProductID** produktu uporządkowane **OrderDetails** jest powiązany z **produktów** za pomocą **ProductID** celu zwrócenie **ProductName**.</span><span class="sxs-lookup"><span data-stu-id="70099-112">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="70099-113">W tej relacji **produktów** tabeli jest elementem nadrzędnym i **Orderdetails** tabeli jest elementem podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="70099-113">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="70099-114">W rezultacie podczas iteracji przez **OrderDetails** tabeli **GetParentRow** jest wywoływana w celu pobrania powiązane **ProductName** wartość.</span><span class="sxs-lookup"><span data-stu-id="70099-114">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="70099-115">Należy zauważyć, że w przypadku **DataRelation** jest tworzona dla **klientów** i **zamówienia** tabele, nie określono wartości dla **createConstraints**flagi (wartość domyślna to **true**).</span><span class="sxs-lookup"><span data-stu-id="70099-115">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="70099-116">To zakłada się, że wszystkie wiersze w **zamówienia** tabela ma **CustomerID** wartość, która istnieje w obiekcie nadrzędnym **klientów** tabeli.</span><span class="sxs-lookup"><span data-stu-id="70099-116">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="70099-117">Jeśli **CustomerID** istnieje w **zamówienia** tabelę, która nie istnieje w **klientów** tabeli <xref:System.Data.ForeignKeyConstraint> powoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="70099-117">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="70099-118">Kolumna podrzędny może zawierać wartości, które nie zawiera kolumny nadrzędnej, ustawić **createConstraints** flaga **false** podczas dodawania **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="70099-118">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="70099-119">W tym przykładzie **createConstraints** flaga jest ustawiona na **false** dla **DataRelation** między **zamówienia** tabeli i  **OrderDetails** tabeli.</span><span class="sxs-lookup"><span data-stu-id="70099-119">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="70099-120">Umożliwia to aplikacji zwrócić wszystkie rekordy z **OrderDetails** tabeli i tylko podzestaw rekordów z **zamówienia** tabeli bez generowania wyjątku czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="70099-120">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="70099-121">Rozwinięty przykładowe generuje dane wyjściowe w następującym formacie.</span><span class="sxs-lookup"><span data-stu-id="70099-121">The expanded sample generates output in the following format.</span></span>  
  
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
  
 <span data-ttu-id="70099-122">Poniższy przykład kodu jest rozwinięty przykładowe gdzie wartości z **OrderDetails** i **produktów** tabele są zwracane, za pomocą tylko podzestaw rekordów w **zamówienia**tabeli są zwracane.</span><span class="sxs-lookup"><span data-stu-id="70099-122">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="70099-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70099-123">See also</span></span>

- [<span data-ttu-id="70099-124">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="70099-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="70099-125">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="70099-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
