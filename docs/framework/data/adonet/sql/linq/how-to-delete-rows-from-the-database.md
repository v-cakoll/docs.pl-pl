---
title: 'Porady: usuwanie wierszy z bazy danych'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: f84531be8bc8ae57db895959513fdc7dd4a8d154
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-delete-rows-from-the-database"></a><span data-ttu-id="a7846-102">Porady: usuwanie wierszy z bazy danych</span><span class="sxs-lookup"><span data-stu-id="a7846-102">How to: Delete Rows From the Database</span></span>
<span data-ttu-id="a7846-103">Można usunąć wierszy w bazie danych przez usunięcie odpowiadającego [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiektów z kolekcji ich związanych z tabeli.</span><span class="sxs-lookup"><span data-stu-id="a7846-103">You can delete rows in a database by removing the corresponding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objects from their table-related collection.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a7846-104"> tłumaczy zmiany, aby odpowiednie SQL `DELETE` poleceń.</span><span class="sxs-lookup"><span data-stu-id="a7846-104"> translates your changes to the appropriate SQL `DELETE` commands.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a7846-105"> nie obsługuje ani nie rozpoznaje operacjami usuwania kaskadowego.</span><span class="sxs-lookup"><span data-stu-id="a7846-105"> does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="a7846-106">Jeśli chcesz usunąć wiersza w tabeli, która ma ograniczenia na nim, należy wykonać jedną z następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="a7846-106">If you want to delete a row in a table that has constraints against it, you must complete either of the following tasks:</span></span>  
  
-   <span data-ttu-id="a7846-107">Ustaw `ON DELETE CASCADE` reguły w ograniczenie klucza obcego w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a7846-107">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>  
  
-   <span data-ttu-id="a7846-108">Najpierw usuń obiekty podrzędne, które zapobiec usunięciu obiektu nadrzędnego przy użyciu własnego kodu.</span><span class="sxs-lookup"><span data-stu-id="a7846-108">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>  
  
 <span data-ttu-id="a7846-109">W przeciwnym razie jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a7846-109">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="a7846-110">Zobacz drugi przykład kodu w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a7846-110">See the second code example later in this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7846-111">Można zastąpić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`, `Update`, i `Delete` bazy danych operacji.</span><span class="sxs-lookup"><span data-stu-id="a7846-111">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="a7846-112">Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacji usunięcia](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a7846-112">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="a7846-113">Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aby opracować procedury składowane do takiej obsługi.</span><span class="sxs-lookup"><span data-stu-id="a7846-113">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="a7846-114">W następujących krokach założono, że jest prawidłowym <xref:System.Data.Linq.DataContext> połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="a7846-114">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="a7846-115">Aby uzyskać więcej informacji, zobacz [porady: połączenie z bazą danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="a7846-115">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-delete-a-row-in-the-database"></a><span data-ttu-id="a7846-116">Aby usunąć wiersz w bazie danych</span><span class="sxs-lookup"><span data-stu-id="a7846-116">To delete a row in the database</span></span>  
  
1.  <span data-ttu-id="a7846-117">Wyślij zapytanie do bazy danych dla wiersza, który ma zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="a7846-117">Query the database for the row to be deleted.</span></span>  
  
2.  <span data-ttu-id="a7846-118">Wywołanie <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a7846-118">Call the <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> method.</span></span>  
  
3.  <span data-ttu-id="a7846-119">Przedstawia zmiany w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a7846-119">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7846-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7846-120">Example</span></span>  
 <span data-ttu-id="a7846-121">W tym przykładzie pierwsze kodu wysyła zapytanie do bazy danych dla szczegółów zamówienia, które należą do 11000 # kolejności, oznacza tych informacji do usunięcia i przesyła te zmiany w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a7846-121">This first code example queries the database for order details that belong to Order #11000, marks these order details for deletion, and submits these changes to the database.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="a7846-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7846-122">Example</span></span>  
 <span data-ttu-id="a7846-123">W drugim przykładzie celem jest usunięcie zamówienia (#10250).</span><span class="sxs-lookup"><span data-stu-id="a7846-123">In this second example, the objective is to remove an order (#10250).</span></span> <span data-ttu-id="a7846-124">Kod najpierw sprawdza, czy `OrderDetails` tabeli, aby sprawdzić, czy kolejność, która ma zostać usunięta ma elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a7846-124">The code first examines the `OrderDetails` table to see whether the order to be removed has children there.</span></span> <span data-ttu-id="a7846-125">Jeśli kolejność ma elementy podrzędne, pierwszy z nich elementów podrzędnych, a następnie kolejność są oznaczone do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="a7846-125">If the order has children, first the children and then the order are marked for removal.</span></span> <span data-ttu-id="a7846-126"><xref:System.Data.Linq.DataContext> Umieszcza rzeczywiste usuwa w odpowiedniej kolejności, aby polecenia usuwania wysłanych do bazy danych przestrzegania ograniczeń bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a7846-126">The <xref:System.Data.Linq.DataContext> puts the actual deletes in correct order so that delete commands sent to the database abide by the database constraints.</span></span>  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a7846-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7846-127">See Also</span></span>  
 [<span data-ttu-id="a7846-128">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="a7846-128">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="a7846-129">Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)</span><span class="sxs-lookup"><span data-stu-id="a7846-129">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [<span data-ttu-id="a7846-130">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="a7846-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
