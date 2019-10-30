---
title: Nawigowanie w elementach DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: 73523297454be37716acedad13498954ef9a89a0
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040348"
---
# <a name="navigating-datarelations"></a><span data-ttu-id="4fc36-102">Nawigowanie w elementach DataRelation</span><span class="sxs-lookup"><span data-stu-id="4fc36-102">Navigating DataRelations</span></span>
<span data-ttu-id="4fc36-103">Jedną z podstawowych funkcji <xref:System.Data.DataRelation> jest umożliwienie nawigowania z jednego <xref:System.Data.DataTable> do innego w <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="4fc36-103">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="4fc36-104">Dzięki temu można pobrać wszystkie powiązane obiekty <xref:System.Data.DataRow> w jednej **DataTable** , gdy podaje jeden element **DataRow** z powiązanej **tabeli DataTable**.</span><span class="sxs-lookup"><span data-stu-id="4fc36-104">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="4fc36-105">Na przykład po ustaleniu **relacji** między tabelą klientów a tabelą zamówień można pobrać wszystkie wiersze zamówienia dla danego wiersza klienta przy użyciu **GetChildRows**.</span><span class="sxs-lookup"><span data-stu-id="4fc36-105">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="4fc36-106">Poniższy przykład kodu tworzy **relację** między tabelą **Customers** i tabelą **Orders** **zestawu danych** i zwraca wszystkie zamówienia dla każdego klienta.</span><span class="sxs-lookup"><span data-stu-id="4fc36-106">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="4fc36-107">Następny przykład jest oparty na powyższym przykładzie, łącznie z czterema tabelami i nawigowaniem w tych relacjach.</span><span class="sxs-lookup"><span data-stu-id="4fc36-107">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="4fc36-108">Tak jak w poprzednim przykładzie, **CustomerID** powiąże tabelę **Customers** z tabelą **Orders** .</span><span class="sxs-lookup"><span data-stu-id="4fc36-108">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="4fc36-109">Dla każdego klienta w tabeli **Customers** są określane wszystkie wiersze podrzędne w tabeli **Orders** , aby można było zwrócić liczbę zamówień określonych przez określonego klienta i ich wartości **IDZamówienia** .</span><span class="sxs-lookup"><span data-stu-id="4fc36-109">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="4fc36-110">Rozwinięty przykład zwraca również wartości z tabel **OrderDetails** i **Products** .</span><span class="sxs-lookup"><span data-stu-id="4fc36-110">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="4fc36-111">Tabela **Orders** jest powiązana z tabelą **OrderDetails** przy użyciu funkcji **IDZamówienia** , aby określić, jakie produkty i ilości zostały uporządkowane według kolejności.</span><span class="sxs-lookup"><span data-stu-id="4fc36-111">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="4fc36-112">Ponieważ tabela **OrderDetails** zawiera tylko identyfikator **ProductID** uporządkowanego produktu, **OrderDetails** jest związana z **produktami** przy użyciu klasy **ProductID** w celu zwrócenia **ProductName**.</span><span class="sxs-lookup"><span data-stu-id="4fc36-112">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="4fc36-113">W tej relacji tabela **Products** jest elementem nadrzędnym, a tabela **Order Details** jest elementem podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="4fc36-113">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="4fc36-114">W związku z tym podczas iterowania za pomocą tabeli **OrderDetails** zostaje wywołana funkcja **GetParentRow** w celu pobrania pokrewnej wartości **ProductName** .</span><span class="sxs-lookup"><span data-stu-id="4fc36-114">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="4fc36-115">Należy zauważyć, że po utworzeniu **relacji** dla tabel **Customers** i **Orders** nie określono żadnej wartości dla flagi **xmlconstraint** (wartość domyślna to **true**).</span><span class="sxs-lookup"><span data-stu-id="4fc36-115">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="4fc36-116">Przyjęto założenie, że wszystkie wiersze w tabeli **Orders** mają wartość **CustomerID** , która istnieje w tabeli nadrzędnych **klientów** .</span><span class="sxs-lookup"><span data-stu-id="4fc36-116">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="4fc36-117">Jeśli element **CustomerID** istnieje w tabeli **Orders** , która nie istnieje w tabeli **Customers** , <xref:System.Data.ForeignKeyConstraint> powoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4fc36-117">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="4fc36-118">Gdy kolumna podrzędna może zawierać wartości, których kolumna nadrzędna nie zawiera, ustaw dla flagi " **isconstraint** **" wartość false** podczas dodawania **relacji**między elementami.</span><span class="sxs-lookup"><span data-stu-id="4fc36-118">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="4fc36-119">W przykładzie flaga **"** **isconstraint** " ma wartość false dla **relacji** między tabelą **Orders** i tabelą **OrderDetails** .</span><span class="sxs-lookup"><span data-stu-id="4fc36-119">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="4fc36-120">Dzięki temu aplikacja zwróci wszystkie rekordy z tabeli **OrderDetails** i tylko podzestaw rekordów z tabeli **Orders** bez generowania wyjątku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4fc36-120">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="4fc36-121">Rozwinięty przykład generuje dane wyjściowe w następującym formacie.</span><span class="sxs-lookup"><span data-stu-id="4fc36-121">The expanded sample generates output in the following format.</span></span>  
  
```output  
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
  
 <span data-ttu-id="4fc36-122">Poniższy przykład kodu jest rozwiniętą próbką, gdy zwracane są wartości z tabeli **OrderDetails** i **Products** , z tylko podzbiorem rekordów w tabeli **Orders** .</span><span class="sxs-lookup"><span data-stu-id="4fc36-122">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4fc36-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4fc36-123">See also</span></span>

- [<span data-ttu-id="4fc36-124">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="4fc36-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="4fc36-125">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4fc36-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
