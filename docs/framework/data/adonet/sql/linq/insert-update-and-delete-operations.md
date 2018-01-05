---
title: "Wstawiania, aktualizowania i usuwania działań"
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
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: bc279fa541ed14244ea093dcd3ea52c37a4698f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="insert-update-and-delete-operations"></a><span data-ttu-id="91fb4-102">Wstawiania, aktualizowania i usuwania działań</span><span class="sxs-lookup"><span data-stu-id="91fb4-102">Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="91fb4-103">Należy wykonać `Insert`, `Update`, i `Delete` operacje w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przez dodawanie, zmienianie i usuwanie obiektów w modelu obiektu.</span><span class="sxs-lookup"><span data-stu-id="91fb4-103">You perform `Insert`, `Update`, and `Delete` operations in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] by adding, changing, and removing objects in your object model.</span></span> <span data-ttu-id="91fb4-104">Domyślnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy akcje użytkownika do bazy danych SQL i przesyła zmiany do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="91fb4-104">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your actions to SQL and submits the changes to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="91fb4-105">zapewnia elastyczność maksymalną manipulowanie i przechowywanie zmiany wprowadzone do obiektów.</span><span class="sxs-lookup"><span data-stu-id="91fb4-105"> offers maximum flexibility in manipulating and persisting changes that you made to your objects.</span></span> <span data-ttu-id="91fb4-106">Jak jednostki dostępnych obiektów (niezależnie, pobierając je za pomocą kwerendy lub tworząc je ponownie), można je zmienić w typowych obiektów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91fb4-106">As soon as entity objects are available (either by retrieving them through a query or by constructing them anew), you can change them as typical objects in your application.</span></span> <span data-ttu-id="91fb4-107">Oznacza to można zmienić ich wartości, należy dodać je do kolekcji i można go usunąć z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="91fb4-107">That is, you can change their values, you can add them to your collections, and you can remove them from your collections.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="91fb4-108">Śledzi zmiany i jest gotowy do przesyłania ich do bazy danych podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="91fb4-108"> tracks your changes and is ready to transmit them back to the database when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="91fb4-109">nie obsługuje ani nie rozpoznaje operacjami usuwania kaskadowego.</span><span class="sxs-lookup"><span data-stu-id="91fb4-109"> does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="91fb4-110">Jeśli chcesz usunąć wiersza w tabeli, która ma ograniczenia na nim, należy albo zestaw `ON DELETE CASCADE` reguły w ograniczenie klucza obcego w bazie danych lub użyj własny kod, aby najpierw usunąć obiekty podrzędne, które zapobiec usunięciu obiektu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="91fb4-110">If you want to delete a row in a table that has constraints against it, you must either set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database, or use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span> <span data-ttu-id="91fb4-111">W przeciwnym razie jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="91fb4-111">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="91fb4-112">Aby uzyskać więcej informacji, zobacz [porady: usuwanie wierszy z bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span><span class="sxs-lookup"><span data-stu-id="91fb4-112">For more information, see [How to: Delete Rows From the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="91fb4-113">Następujące fragmentów użyj `Customer` i `Order` klasy z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="91fb4-113">The following excerpts use the `Customer` and `Order` classes from the Northwind sample database.</span></span> <span data-ttu-id="91fb4-114">Definicje klas nie są wyświetlane do skrócenia.</span><span class="sxs-lookup"><span data-stu-id="91fb4-114">Class definitions are not shown for brevity.</span></span>  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 <span data-ttu-id="91fb4-115">Podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatycznie generuje i wykonuje polecenia SQL, które muszą mieć do przesłania zmian w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="91fb4-115">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatically generates and executes the SQL commands that it must have to transmit your changes back to the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91fb4-116">Aby zmienić to zachowanie, należy za pomocą własnych niestandardowej logiki, zwykle na procedurę przechowywaną.</span><span class="sxs-lookup"><span data-stu-id="91fb4-116">You can override this behavior by using your own custom logic, typically by way of a stored procedure.</span></span> <span data-ttu-id="91fb4-117">Aby uzyskać więcej informacji, zobacz [obowiązki deweloperów w zastępowanie domyślne zachowanie](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="91fb4-117">For more information, see [Responsibilities of the Developer In Overriding Default Behavior](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).</span></span>  
>   
>  <span data-ttu-id="91fb4-118">Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] można użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aby opracować procedury składowane w tym celu.</span><span class="sxs-lookup"><span data-stu-id="91fb4-118">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for this purpose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91fb4-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91fb4-119">See Also</span></span>  
 [<span data-ttu-id="91fb4-120">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="91fb4-120">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="91fb4-121">Dostosowywanie operacji wstawiania, aktualizowania i usuwania</span><span class="sxs-lookup"><span data-stu-id="91fb4-121">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
