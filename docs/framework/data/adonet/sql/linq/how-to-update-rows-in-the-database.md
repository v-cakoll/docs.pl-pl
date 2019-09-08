---
title: 'Instrukcje: Aktualizowanie wierszy w bazie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: c2055e1dd988352b50a439531ab5533f34a4965e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793136"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="70fb5-102">Instrukcje: Aktualizowanie wierszy w bazie danych</span><span class="sxs-lookup"><span data-stu-id="70fb5-102">How to: Update Rows in the Database</span></span>

<span data-ttu-id="70fb5-103">Wiersze w bazie danych można aktualizować, modyfikując wartości elementów członkowskich obiektów skojarzonych z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekcją, a następnie przesyłając zmiany do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="70fb5-103">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="70fb5-104">tłumaczy zmiany na odpowiednie polecenia SQL `UPDATE` .</span><span class="sxs-lookup"><span data-stu-id="70fb5-104">translates your changes into the appropriate SQL `UPDATE` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="70fb5-105">Można przesłonić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`dla `Update`, i `Delete` operacji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="70fb5-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="70fb5-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="70fb5-106">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="70fb5-107">Deweloperzy korzystający z programu Visual Studio mogą opracowywać procedury składowane w tym samym celu przy użyciu Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="70fb5-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="70fb5-108">W poniższych krokach przyjęto założenie, że prawidłowy <xref:System.Data.Linq.DataContext> nawiąże połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="70fb5-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="70fb5-109">Aby uzyskać więcej informacji, zobacz [jak: Nawiąż połączenie z](how-to-connect-to-a-database.md)bazą danych.</span><span class="sxs-lookup"><span data-stu-id="70fb5-109">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="70fb5-110">Aby zaktualizować wiersz w bazie danych</span><span class="sxs-lookup"><span data-stu-id="70fb5-110">To update a row in the database</span></span>

1. <span data-ttu-id="70fb5-111">Wykonaj zapytanie względem bazy danych, aby wiersz został zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="70fb5-111">Query the database for the row to be updated.</span></span>

2. <span data-ttu-id="70fb5-112">Wprowadź żądane zmiany wartości elementów członkowskich w obiekcie wynikiem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="70fb5-112">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>

3. <span data-ttu-id="70fb5-113">Prześlij zmiany do bazy danych programu.</span><span class="sxs-lookup"><span data-stu-id="70fb5-113">Submit the changes to the database.</span></span>

## <a name="example"></a><span data-ttu-id="70fb5-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="70fb5-114">Example</span></span>

<span data-ttu-id="70fb5-115">Poniższy przykład wykonuje zapytanie do bazy danych w kolejności #11000, a następnie zmienia wartości `ShipName` i `ShipVia` w obiekcie wyniku `Order` .</span><span class="sxs-lookup"><span data-stu-id="70fb5-115">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="70fb5-116">Na koniec zmiany tych wartości elementów członkowskich są przesyłane do bazy danych jako zmiany w `ShipName` kolumnach i. `ShipVia`</span><span class="sxs-lookup"><span data-stu-id="70fb5-116">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="70fb5-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70fb5-117">See also</span></span>

- [<span data-ttu-id="70fb5-118">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="70fb5-118">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="70fb5-119">Instrukcje: Przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (Object Relational Designer)</span><span class="sxs-lookup"><span data-stu-id="70fb5-119">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="70fb5-120">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="70fb5-120">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
