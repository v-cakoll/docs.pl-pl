---
title: Tworzenie i przesyłanie zmian danych
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: 23dc45c990763e69b41608f6c3ec15a8db17bf23
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743010"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="038f2-102">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="038f2-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="038f2-103">Tematy w tej sekcji opisano sposób tworzenia i przesyłania zmian w bazie danych i sposób obsługi konfliktów optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="038f2-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="038f2-104">Można zastąpić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`, `Update`, i `Delete` bazy danych operacji.</span><span class="sxs-lookup"><span data-stu-id="038f2-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="038f2-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacje usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="038f2-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="038f2-106">Deweloperzy korzystający z programu Visual Studio umożliwia tworzenie procedur składowanych w tym samym celu Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="038f2-106">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="038f2-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="038f2-107">In This Section</span></span>  
 [<span data-ttu-id="038f2-108">Instrukcje: Wstawianie wierszy do bazy danych</span><span class="sxs-lookup"><span data-stu-id="038f2-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="038f2-109">W tym artykule opisano sposób wstawiania wierszy w bazie danych, dodając obiekty w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="038f2-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="038f2-110">Instrukcje: Aktualizowanie wierszy w bazie danych</span><span class="sxs-lookup"><span data-stu-id="038f2-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="038f2-111">Opisuje sposób aktualizacji wierszy w bazie danych, aktualizując obiekty w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="038f2-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="038f2-112">Instrukcje: Usuwanie wierszy z bazy danych</span><span class="sxs-lookup"><span data-stu-id="038f2-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="038f2-113">Opisuje sposób usuwania wierszy w bazie danych, usuwając obiekty w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="038f2-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="038f2-114">Instrukcje: Przesyłanie zmian do bazy danych</span><span class="sxs-lookup"><span data-stu-id="038f2-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="038f2-115">W tym artykule opisano sposób wysyłania model obiektu zmienia się z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="038f2-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="038f2-116">Instrukcje: Przesyłanie danych nawiasów za pomocą transakcji</span><span class="sxs-lookup"><span data-stu-id="038f2-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="038f2-117">Opisuje sposób obejmują operacje w ramach transakcji.</span><span class="sxs-lookup"><span data-stu-id="038f2-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="038f2-118">Instrukcje: Dynamiczne tworzenie bazy danych</span><span class="sxs-lookup"><span data-stu-id="038f2-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="038f2-119">W tym artykule opisano, jak dynamicznie generować baz danych i typowe scenariusze dotyczące tego podejścia.</span><span class="sxs-lookup"><span data-stu-id="038f2-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="038f2-120">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="038f2-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="038f2-121">Opisano techniki Rozwiązywanie problemów z optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="038f2-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
