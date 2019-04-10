---
title: 'Instrukcje: Aktualizowanie wierszy w bazie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: e40866c5160d6850b39133050d09026f5ffd6cc5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344182"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="e4b5d-102">Instrukcje: Aktualizowanie wierszy w bazie danych</span><span class="sxs-lookup"><span data-stu-id="e4b5d-102">How to: Update Rows in the Database</span></span>
<span data-ttu-id="e4b5d-103">Możesz zaktualizować wierszy w bazie danych, zmieniając wartości elementów członkowskich obiektów skojarzonych z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekcji, a następnie przesyłanie zmian do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e4b5d-103">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e4b5d-104">tłumaczy zmiany w środowisku SQL odpowiednie `UPDATE` poleceń.</span><span class="sxs-lookup"><span data-stu-id="e4b5d-104">translates your changes into the appropriate SQL `UPDATE` commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4b5d-105">Można zastąpić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`, `Update`, i `Delete` bazy danych operacji.</span><span class="sxs-lookup"><span data-stu-id="e4b5d-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="e4b5d-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacje usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="e4b5d-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="e4b5d-107">Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Tworzenie procedur składowanych w tym samym celu.</span><span class="sxs-lookup"><span data-stu-id="e4b5d-107">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="e4b5d-108">W następujących krokach założono, że prawidłowy <xref:System.Data.Linq.DataContext> połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="e4b5d-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="e4b5d-109">Aby uzyskać więcej informacji, zobacz [jak: Łączenie z bazą danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="e4b5d-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="e4b5d-110">Aby zaktualizować wiersz w bazie danych</span><span class="sxs-lookup"><span data-stu-id="e4b5d-110">To update a row in the database</span></span>  
  
1. <span data-ttu-id="e4b5d-111">Odpytywanie bazy danych dla wiersza do zaktualizowania.</span><span class="sxs-lookup"><span data-stu-id="e4b5d-111">Query the database for the row to be updated.</span></span>  
  
2. <span data-ttu-id="e4b5d-112">Żądane zmiany wartości elementów członkowskich w wynikowym [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiektu.</span><span class="sxs-lookup"><span data-stu-id="e4b5d-112">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>  
  
3. <span data-ttu-id="e4b5d-113">Przesyłanie zmian do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e4b5d-113">Submit the changes to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4b5d-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4b5d-114">Example</span></span>  
 <span data-ttu-id="e4b5d-115">Poniższy przykład zapytania bazy danych dla zamówienia #11000, a następnie zmienia wartości `ShipName` i `ShipVia` w wynikowym `Order` obiektu.</span><span class="sxs-lookup"><span data-stu-id="e4b5d-115">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="e4b5d-116">Na koniec zmiany tych wartości elementów członkowskich są przesyłane do bazy danych zgodnie ze zmianami w `ShipName` i `ShipVia` kolumn.</span><span class="sxs-lookup"><span data-stu-id="e4b5d-116">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e4b5d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4b5d-117">See also</span></span>

- [<span data-ttu-id="e4b5d-118">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="e4b5d-118">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="e4b5d-119">Instrukcje: Przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="e4b5d-119">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="e4b5d-120">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="e4b5d-120">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
