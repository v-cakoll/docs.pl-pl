---
title: "Tworzenie i przesyłanie zmian danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb52916e8e0948725a2eeb15cf78410077c7dca1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="3ca56-102">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="3ca56-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="3ca56-103">Tematy w tej sekcji opisano sposób tworzenia i przesłania zmian w bazie danych i sposobu obsługi konfliktów optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="3ca56-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ca56-104">Można zastąpić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`, `Update`, i `Delete` bazy danych operacji.</span><span class="sxs-lookup"><span data-stu-id="3ca56-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="3ca56-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacji usunięcia](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="3ca56-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="3ca56-106">Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] można użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aby opracować procedury składowane do takiej obsługi.</span><span class="sxs-lookup"><span data-stu-id="3ca56-106">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3ca56-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3ca56-107">In This Section</span></span>  
 [<span data-ttu-id="3ca56-108">Porady: wstawianie wierszy w bazie danych</span><span class="sxs-lookup"><span data-stu-id="3ca56-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="3ca56-109">Opisuje sposób wstawiania wierszy w bazie danych, przez dodawanie obiektów w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="3ca56-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="3ca56-110">Porady: aktualizowanie wierszy w bazie danych</span><span class="sxs-lookup"><span data-stu-id="3ca56-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="3ca56-111">Opisuje sposób aktualizacji wierszy w bazie danych, aktualizując obiektów w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="3ca56-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="3ca56-112">Porady: usuwanie wierszy z bazy danych</span><span class="sxs-lookup"><span data-stu-id="3ca56-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="3ca56-113">Opisuje sposób usuwania wierszy w bazie danych przez usunięcie obiektów w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="3ca56-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="3ca56-114">Porady: przesyłanie zmian w bazie danych</span><span class="sxs-lookup"><span data-stu-id="3ca56-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="3ca56-115">Opisuje sposób wysyłania zmiany modelu obiektów w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="3ca56-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="3ca56-116">Porady: nawiasów przesyłania danych za pomocą transakcji</span><span class="sxs-lookup"><span data-stu-id="3ca56-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="3ca56-117">Opisuje sposób obejmują operacje w ramach transakcji.</span><span class="sxs-lookup"><span data-stu-id="3ca56-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="3ca56-118">Porady: dynamiczne tworzenie bazy danych</span><span class="sxs-lookup"><span data-stu-id="3ca56-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="3ca56-119">Opisuje sposób generowania dynamicznie baz danych i typowe scenariusze dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="3ca56-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="3ca56-120">Porady: Zarządzanie konfliktów zmian</span><span class="sxs-lookup"><span data-stu-id="3ca56-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="3ca56-121">Opisuje metody adresowania problemów optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="3ca56-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
