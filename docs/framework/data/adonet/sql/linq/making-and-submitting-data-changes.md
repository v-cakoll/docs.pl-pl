---
title: Tworzenie i przesyłanie zmian danych
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: 18468c9a2018a28e85d87155d98b0853854013fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792962"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="19953-102">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="19953-102">Making and Submitting Data Changes</span></span>

<span data-ttu-id="19953-103">W tematach w tej sekcji opisano, jak wprowadzać i przesyłać zmiany do bazy danych oraz jak obsługiwać optymistyczne konflikty współbieżności.</span><span class="sxs-lookup"><span data-stu-id="19953-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>

> [!NOTE]
> <span data-ttu-id="19953-104">Można przesłonić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`dla `Update`, i `Delete` operacji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="19953-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="19953-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="19953-105">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="19953-106">Deweloperzy korzystający z programu Visual Studio mogą opracowywać procedury składowane w tym samym celu przy użyciu Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="19953-106">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="19953-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="19953-107">In This Section</span></span>

<span data-ttu-id="19953-108">[Instrukcje: Wstawianie wierszy do bazy danych](how-to-insert-rows-into-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="19953-108">[How to: Insert Rows Into the Database](how-to-insert-rows-into-the-database.md) </span></span>\
<span data-ttu-id="19953-109">Opisuje sposób wstawiania wierszy w bazie danych przez dodanie obiektów do modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="19953-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>

<span data-ttu-id="19953-110">[Instrukcje: Aktualizowanie wierszy w bazie danych](how-to-update-rows-in-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="19953-110">[How to: Update Rows in the Database](how-to-update-rows-in-the-database.md) </span></span>\
<span data-ttu-id="19953-111">Opisuje sposób aktualizacji wierszy w bazie danych przez aktualizowanie obiektów w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="19953-111">Describes how to update rows in the database by updating objects in the object model.</span></span>

<span data-ttu-id="19953-112">[Instrukcje: Usuwanie wierszy z bazy danych](how-to-delete-rows-from-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="19953-112">[How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md) </span></span>\
<span data-ttu-id="19953-113">Opisuje sposób usuwania wierszy w bazie danych przez usunięcie obiektów w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="19953-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>

<span data-ttu-id="19953-114">[Instrukcje: Prześlij zmiany do bazy danych](how-to-submit-changes-to-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="19953-114">[How to: Submit Changes to the Database](how-to-submit-changes-to-the-database.md) </span></span>\
<span data-ttu-id="19953-115">Opisuje, w jaki sposób wysyłać zmiany modelu obiektów do bazy danych programu.</span><span class="sxs-lookup"><span data-stu-id="19953-115">Describes how to send object-model changes to the database.</span></span>

<span data-ttu-id="19953-116">[Instrukcje: Przeprzesyłanie danych w nawiasach przy użyciu transakcji](how-to-bracket-data-submissions-by-using-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="19953-116">[How to: Bracket Data Submissions by Using Transactions](how-to-bracket-data-submissions-by-using-transactions.md) </span></span>\
<span data-ttu-id="19953-117">Opisuje sposób dołączania operacji w transakcji.</span><span class="sxs-lookup"><span data-stu-id="19953-117">Describes how to include operations in a transaction.</span></span>

<span data-ttu-id="19953-118">[Instrukcje: Dynamiczne tworzenie bazy danych](how-to-dynamically-create-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="19953-118">[How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md) </span></span>\
<span data-ttu-id="19953-119">Opisuje sposób dynamicznego generowania baz danych oraz typowe scenariusze tego podejścia.</span><span class="sxs-lookup"><span data-stu-id="19953-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>

<span data-ttu-id="19953-120">[Instrukcje: Zarządzanie konfliktami zmian](how-to-manage-change-conflicts.md) </span><span class="sxs-lookup"><span data-stu-id="19953-120">[How to: Manage Change Conflicts](how-to-manage-change-conflicts.md) </span></span>\
<span data-ttu-id="19953-121">Opisuje techniki rozwiązywania optymistycznych problemów współbieżności.</span><span class="sxs-lookup"><span data-stu-id="19953-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
