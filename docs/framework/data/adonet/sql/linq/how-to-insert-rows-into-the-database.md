---
title: 'Instrukcje: Wstawianie wierszy do bazy danych'
description: Dowiedz się, jak wstawiać wiersze do bazy danych, dodając LINQ to SQL obiektów do kolekcji powiązanej z tabelą. LINQ to SQL tłumaczy dodatki na polecenia SQL INSERT.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 39eee6edf59d2adb7de41efd88899050fbe69fd8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286355"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="c1184-104">Instrukcje: Wstawianie wierszy do bazy danych</span><span class="sxs-lookup"><span data-stu-id="c1184-104">How to: Insert Rows Into the Database</span></span>

<span data-ttu-id="c1184-105">Wiersze są wstawiane do bazy danych przez dodanie obiektów do skojarzonej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekcji, a następnie przesłanie zmian do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="c1184-105">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="c1184-106">tłumaczy zmiany na odpowiednie `INSERT` polecenia SQL.</span><span class="sxs-lookup"><span data-stu-id="c1184-106">translates your changes into the appropriate SQL `INSERT` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="c1184-107">Można przesłonić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody dla `Insert` , `Update` i `Delete` operacji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="c1184-107">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="c1184-108">Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="c1184-108">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="c1184-109">Deweloperzy korzystający z programu Visual Studio mogą opracowywać procedury składowane w tym samym celu przy użyciu Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="c1184-109">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="c1184-110">W poniższych krokach przyjęto założenie, że prawidłowy <xref:System.Data.Linq.DataContext> nawiąże połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="c1184-110">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="c1184-111">Aby uzyskać więcej informacji, zobacz [How to: Connect to a Database](how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="c1184-111">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="c1184-112">Aby wstawić wiersz do bazy danych</span><span class="sxs-lookup"><span data-stu-id="c1184-112">To insert a row into the database</span></span>

1. <span data-ttu-id="c1184-113">Utwórz nowy obiekt, który zawiera dane kolumn do przesłania.</span><span class="sxs-lookup"><span data-stu-id="c1184-113">Create a new object that includes the column data to be submitted.</span></span>

2. <span data-ttu-id="c1184-114">Dodaj nowy obiekt do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` kolekcji skojarzonej z tabelą docelową w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="c1184-114">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>

3. <span data-ttu-id="c1184-115">Prześlij zmianę do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="c1184-115">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="c1184-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1184-116">Example</span></span>

<span data-ttu-id="c1184-117">Poniższy przykład kodu tworzy nowy obiekt typu `Order` i wypełnia go odpowiednimi wartościami.</span><span class="sxs-lookup"><span data-stu-id="c1184-117">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="c1184-118">Następnie dodaje nowy obiekt do `Order` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c1184-118">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="c1184-119">Na koniec przesyła zmiany do bazy danych jako nowy wiersz w `Orders` tabeli.</span><span class="sxs-lookup"><span data-stu-id="c1184-119">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="c1184-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1184-120">See also</span></span>

- [<span data-ttu-id="c1184-121">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="c1184-121">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="c1184-122">Metody DataContext (Object Relational Designer)</span><span class="sxs-lookup"><span data-stu-id="c1184-122">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="c1184-123">Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="c1184-123">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="c1184-124">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="c1184-124">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
