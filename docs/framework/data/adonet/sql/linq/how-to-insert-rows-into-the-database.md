---
title: 'Porady: wstawianie wierszy w bazie danych'
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
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a96a0ab800076db16022f5b02c84d7a53ca99147
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="2a134-102">Porady: wstawianie wierszy w bazie danych</span><span class="sxs-lookup"><span data-stu-id="2a134-102">How to: Insert Rows Into the Database</span></span>
<span data-ttu-id="2a134-103">Wstawianie wierszy w bazie danych przez dodawanie obiektów do skojarzonego [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekcji, a następnie przesyłanie zmian w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="2a134-103">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="2a134-104">tłumaczy zmiany odpowiednie SQL `INSERT` poleceń.</span><span class="sxs-lookup"><span data-stu-id="2a134-104"> translates your changes into the appropriate SQL `INSERT` commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a134-105">Można zastąpić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`, `Update`, i `Delete` bazy danych operacji.</span><span class="sxs-lookup"><span data-stu-id="2a134-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="2a134-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacji usunięcia](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="2a134-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="2a134-107">Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] można użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aby opracować procedury składowane do takiej obsługi.</span><span class="sxs-lookup"><span data-stu-id="2a134-107">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="2a134-108">W następujących krokach założono, że jest prawidłowym <xref:System.Data.Linq.DataContext> połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="2a134-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="2a134-109">Aby uzyskać więcej informacji, zobacz [porady: połączenie z bazą danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="2a134-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="2a134-110">Aby wstawić wiersza do bazy danych</span><span class="sxs-lookup"><span data-stu-id="2a134-110">To insert a row into the database</span></span>  
  
1.  <span data-ttu-id="2a134-111">Utwórz nowy obiekt, który zawiera kolumny danych do przesłania.</span><span class="sxs-lookup"><span data-stu-id="2a134-111">Create a new object that includes the column data to be submitted.</span></span>  
  
2.  <span data-ttu-id="2a134-112">Dodaj nowy obiekt do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` kolekcji skojarzonych z tabeli docelowej w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="2a134-112">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>  
  
3.  <span data-ttu-id="2a134-113">Przedstawia zmiany w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="2a134-113">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a134-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a134-114">Example</span></span>  
 <span data-ttu-id="2a134-115">Poniższy przykład kodu tworzy nowy obiekt typu `Order` i wypełnia odpowiednie wartości.</span><span class="sxs-lookup"><span data-stu-id="2a134-115">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="2a134-116">Następnie dodaje nowy obiekt do `Order` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2a134-116">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="2a134-117">Na koniec przesyła zmiany do bazy danych jako nowy wiersz w `Orders` tabeli.</span><span class="sxs-lookup"><span data-stu-id="2a134-117">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2a134-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a134-118">See Also</span></span>  
 [<span data-ttu-id="2a134-119">Porady: Zarządzanie konfliktów zmian</span><span class="sxs-lookup"><span data-stu-id="2a134-119">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="2a134-120">Metody DataContext (Projektanta obiektów relacyjnych)</span><span class="sxs-lookup"><span data-stu-id="2a134-120">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="2a134-121">Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)</span><span class="sxs-lookup"><span data-stu-id="2a134-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [<span data-ttu-id="2a134-122">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="2a134-122">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
