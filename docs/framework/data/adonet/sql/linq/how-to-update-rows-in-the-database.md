---
title: 'Instrukcje: Aktualizowanie wierszy w bazie danych'
description: Dowiedz się, jak aktualizować wiersze w bazie danych, modyfikując LINQ to SQL obiektów w kolekcji powiązanej z tabelą. LINQ to SQL tłumaczy Dodatki do poleceń aktualizacji SQL.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: f25efb91fb5a83fb1c7c109bd018c8210edaec8b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286342"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="0cf4a-104">Instrukcje: Aktualizowanie wierszy w bazie danych</span><span class="sxs-lookup"><span data-stu-id="0cf4a-104">How to: Update Rows in the Database</span></span>

<span data-ttu-id="0cf4a-105">Wiersze w bazie danych można aktualizować, modyfikując wartości elementów członkowskich obiektów skojarzonych z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekcją, a następnie przesyłając zmiany do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-105">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="0cf4a-106">tłumaczy zmiany na odpowiednie `UPDATE` polecenia SQL.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-106">translates your changes into the appropriate SQL `UPDATE` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="0cf4a-107">Można przesłonić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody dla `Insert` , `Update` i `Delete` operacji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-107">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="0cf4a-108">Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="0cf4a-108">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="0cf4a-109">Deweloperzy korzystający z programu Visual Studio mogą opracowywać procedury składowane w tym samym celu przy użyciu Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-109">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="0cf4a-110">W poniższych krokach przyjęto założenie, że prawidłowy <xref:System.Data.Linq.DataContext> nawiąże połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-110">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="0cf4a-111">Aby uzyskać więcej informacji, zobacz [How to: Connect to a Database](how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="0cf4a-111">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="0cf4a-112">Aby zaktualizować wiersz w bazie danych</span><span class="sxs-lookup"><span data-stu-id="0cf4a-112">To update a row in the database</span></span>

1. <span data-ttu-id="0cf4a-113">Wykonaj zapytanie względem bazy danych, aby wiersz został zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-113">Query the database for the row to be updated.</span></span>

2. <span data-ttu-id="0cf4a-114">Wprowadź żądane zmiany wartości elementów członkowskich w obiekcie wynikiem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0cf4a-114">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>

3. <span data-ttu-id="0cf4a-115">Prześlij zmiany do bazy danych programu.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-115">Submit the changes to the database.</span></span>

## <a name="example"></a><span data-ttu-id="0cf4a-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="0cf4a-116">Example</span></span>

<span data-ttu-id="0cf4a-117">Poniższy przykład wykonuje zapytanie do bazy danych w kolejności #11000, a następnie zmienia wartości `ShipName` i `ShipVia` w `Order` obiekcie wyniku.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-117">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="0cf4a-118">Na koniec zmiany tych wartości elementów członkowskich są przesyłane do bazy danych jako zmiany w `ShipName` `ShipVia` kolumnach i.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-118">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="0cf4a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0cf4a-119">See also</span></span>

- [<span data-ttu-id="0cf4a-120">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="0cf4a-120">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="0cf4a-121">Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="0cf4a-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="0cf4a-122">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="0cf4a-122">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
