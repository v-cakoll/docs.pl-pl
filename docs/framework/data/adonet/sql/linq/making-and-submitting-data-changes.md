---
title: Tworzenie i przesyłanie zmian danych
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: c9d319727a750fbd3e2a186c28e79b20200c6bd0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360796"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="9b274-102">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="9b274-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="9b274-103">Tematy w tej sekcji opisano sposób tworzenia i przesłania zmian w bazie danych i sposobu obsługi konfliktów optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="9b274-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b274-104">Można zastąpić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`, `Update`, i `Delete` bazy danych operacji.</span><span class="sxs-lookup"><span data-stu-id="9b274-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="9b274-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacji usunięcia](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9b274-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="9b274-106">Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aby opracować procedury składowane do takiej obsługi.</span><span class="sxs-lookup"><span data-stu-id="9b274-106">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b274-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9b274-107">In This Section</span></span>  
 [<span data-ttu-id="9b274-108">Instrukcje: Wstawianie wierszy do bazy danych</span><span class="sxs-lookup"><span data-stu-id="9b274-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="9b274-109">Opisuje sposób wstawiania wierszy w bazie danych, przez dodawanie obiektów w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="9b274-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="9b274-110">Instrukcje: Aktualizowanie wierszy w bazie danych</span><span class="sxs-lookup"><span data-stu-id="9b274-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="9b274-111">Opisuje sposób aktualizacji wierszy w bazie danych, aktualizując obiektów w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="9b274-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="9b274-112">Instrukcje: Usuwanie wierszy z bazy danych</span><span class="sxs-lookup"><span data-stu-id="9b274-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="9b274-113">Opisuje sposób usuwania wierszy w bazie danych przez usunięcie obiektów w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="9b274-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="9b274-114">Instrukcje: Przesyłanie zmian do bazy danych</span><span class="sxs-lookup"><span data-stu-id="9b274-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="9b274-115">Opisuje sposób wysyłania zmiany modelu obiektów w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="9b274-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="9b274-116">Instrukcje: Przesyłanie danych nawiasów za pomocą transakcji</span><span class="sxs-lookup"><span data-stu-id="9b274-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="9b274-117">Opisuje sposób obejmują operacje w ramach transakcji.</span><span class="sxs-lookup"><span data-stu-id="9b274-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="9b274-118">Instrukcje: Dynamiczne tworzenie bazy danych</span><span class="sxs-lookup"><span data-stu-id="9b274-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="9b274-119">Opisuje sposób generowania dynamicznie baz danych i typowe scenariusze dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="9b274-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="9b274-120">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="9b274-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="9b274-121">Opisuje metody adresowania problemów optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="9b274-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
