---
title: Tworzenie i przesyłanie zmian danych
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: dd0a8288ca924cb17bdacdeeb94f81c3d27d3e4e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915774"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="7dc8c-102">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="7dc8c-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="7dc8c-103">W tematach w tej sekcji opisano, jak wprowadzać i przesyłać zmiany do bazy danych oraz jak obsługiwać optymistyczne konflikty współbieżności.</span><span class="sxs-lookup"><span data-stu-id="7dc8c-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7dc8c-104">Można przesłonić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`dla `Update`, i `Delete` operacji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7dc8c-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="7dc8c-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="7dc8c-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="7dc8c-106">Deweloperzy korzystający z programu Visual Studio mogą opracowywać procedury składowane w tym samym celu przy użyciu Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="7dc8c-106">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7dc8c-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7dc8c-107">In This Section</span></span>  
 [<span data-ttu-id="7dc8c-108">Instrukcje: Wstawianie wierszy do bazy danych</span><span class="sxs-lookup"><span data-stu-id="7dc8c-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="7dc8c-109">Opisuje sposób wstawiania wierszy w bazie danych przez dodanie obiektów do modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="7dc8c-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="7dc8c-110">Instrukcje: Aktualizowanie wierszy w bazie danych</span><span class="sxs-lookup"><span data-stu-id="7dc8c-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="7dc8c-111">Opisuje sposób aktualizacji wierszy w bazie danych przez aktualizowanie obiektów w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="7dc8c-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="7dc8c-112">Instrukcje: Usuwanie wierszy z bazy danych</span><span class="sxs-lookup"><span data-stu-id="7dc8c-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="7dc8c-113">Opisuje sposób usuwania wierszy w bazie danych przez usunięcie obiektów w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="7dc8c-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="7dc8c-114">Instrukcje: Prześlij zmiany do bazy danych</span><span class="sxs-lookup"><span data-stu-id="7dc8c-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="7dc8c-115">Opisuje, w jaki sposób wysyłać zmiany modelu obiektów do bazy danych programu.</span><span class="sxs-lookup"><span data-stu-id="7dc8c-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="7dc8c-116">Instrukcje: Przeprzesyłanie danych w nawiasach przy użyciu transakcji</span><span class="sxs-lookup"><span data-stu-id="7dc8c-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="7dc8c-117">Opisuje sposób dołączania operacji w transakcji.</span><span class="sxs-lookup"><span data-stu-id="7dc8c-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="7dc8c-118">Instrukcje: Dynamiczne tworzenie bazy danych</span><span class="sxs-lookup"><span data-stu-id="7dc8c-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="7dc8c-119">Opisuje sposób dynamicznego generowania baz danych oraz typowe scenariusze tego podejścia.</span><span class="sxs-lookup"><span data-stu-id="7dc8c-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="7dc8c-120">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="7dc8c-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="7dc8c-121">Opisuje techniki rozwiązywania optymistycznych problemów współbieżności.</span><span class="sxs-lookup"><span data-stu-id="7dc8c-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
