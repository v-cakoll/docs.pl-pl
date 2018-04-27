---
title: 'Porady: aktualizowanie wierszy w bazie danych'
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
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 4ca47fb5a522ebcab68544a538064aa5cc3d60d7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="064d0-102">Porady: aktualizowanie wierszy w bazie danych</span><span class="sxs-lookup"><span data-stu-id="064d0-102">How to: Update Rows in the Database</span></span>
<span data-ttu-id="064d0-103">Można zaktualizować wierszy w bazie danych przez zmodyfikowanie wartości elementu członkowskiego obiektów skojarzonych z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekcji, a następnie przesyłanie zmian w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="064d0-103">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="064d0-104"> tłumaczy zmiany odpowiednie SQL `UPDATE` poleceń.</span><span class="sxs-lookup"><span data-stu-id="064d0-104"> translates your changes into the appropriate SQL `UPDATE` commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="064d0-105">Można zastąpić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`, `Update`, i `Delete` bazy danych operacji.</span><span class="sxs-lookup"><span data-stu-id="064d0-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="064d0-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacji usunięcia](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="064d0-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="064d0-107">Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aby opracować procedury składowane do takiej obsługi.</span><span class="sxs-lookup"><span data-stu-id="064d0-107">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="064d0-108">W następujących krokach założono, że jest prawidłowym <xref:System.Data.Linq.DataContext> połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="064d0-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="064d0-109">Aby uzyskać więcej informacji, zobacz [porady: połączenie z bazą danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="064d0-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="064d0-110">Aby zaktualizować wierszy w bazie danych</span><span class="sxs-lookup"><span data-stu-id="064d0-110">To update a row in the database</span></span>  
  
1.  <span data-ttu-id="064d0-111">Wyślij zapytanie do bazy danych dla wiersza do zaktualizowania.</span><span class="sxs-lookup"><span data-stu-id="064d0-111">Query the database for the row to be updated.</span></span>  
  
2.  <span data-ttu-id="064d0-112">Żądane zmiany wartości elementu członkowskiego w wynikowym [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiektu.</span><span class="sxs-lookup"><span data-stu-id="064d0-112">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>  
  
3.  <span data-ttu-id="064d0-113">Przesyłanie zmian w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="064d0-113">Submit the changes to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="064d0-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="064d0-114">Example</span></span>  
 <span data-ttu-id="064d0-115">Poniższy przykład kwerendę bazy danych dla zlecenia #11000, a następnie zmienia wartości `ShipName` i `ShipVia` w wynikowym `Order` obiektu.</span><span class="sxs-lookup"><span data-stu-id="064d0-115">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="064d0-116">Na koniec zmiany tych wartości elementów członkowskich są przesyłane do bazy danych do zmian `ShipName` i `ShipVia` kolumn.</span><span class="sxs-lookup"><span data-stu-id="064d0-116">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="064d0-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="064d0-117">See Also</span></span>  
 [<span data-ttu-id="064d0-118">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="064d0-118">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="064d0-119">Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)</span><span class="sxs-lookup"><span data-stu-id="064d0-119">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [<span data-ttu-id="064d0-120">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="064d0-120">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
