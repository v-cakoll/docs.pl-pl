---
title: 'Instrukcje: Wstawianie wierszy do bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 8186b90a666a7b75ce626cccb7cc28af38de7c5b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781862"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="9831e-102">Instrukcje: Wstawianie wierszy do bazy danych</span><span class="sxs-lookup"><span data-stu-id="9831e-102">How to: Insert Rows Into the Database</span></span>

<span data-ttu-id="9831e-103">Wiersze są wstawiane do bazy danych przez dodanie obiektów do skojarzonej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekcji, a następnie przesłanie zmian do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9831e-103">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9831e-104">tłumaczy zmiany na odpowiednie polecenia SQL `INSERT` .</span><span class="sxs-lookup"><span data-stu-id="9831e-104">translates your changes into the appropriate SQL `INSERT` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="9831e-105">Można przesłonić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`dla `Update`, i `Delete` operacji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9831e-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="9831e-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9831e-106">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="9831e-107">Deweloperzy korzystający z programu Visual Studio mogą opracowywać procedury składowane w tym samym celu przy użyciu Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="9831e-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="9831e-108">W poniższych krokach przyjęto założenie, że prawidłowy <xref:System.Data.Linq.DataContext> nawiąże połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="9831e-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="9831e-109">Aby uzyskać więcej informacji, zobacz [jak: Nawiąż połączenie z](how-to-connect-to-a-database.md)bazą danych.</span><span class="sxs-lookup"><span data-stu-id="9831e-109">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="9831e-110">Aby wstawić wiersz do bazy danych</span><span class="sxs-lookup"><span data-stu-id="9831e-110">To insert a row into the database</span></span>

1. <span data-ttu-id="9831e-111">Utwórz nowy obiekt, który zawiera dane kolumn do przesłania.</span><span class="sxs-lookup"><span data-stu-id="9831e-111">Create a new object that includes the column data to be submitted.</span></span>

2. <span data-ttu-id="9831e-112">Dodaj nowy obiekt do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` kolekcji skojarzonej z tabelą docelową w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="9831e-112">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>

3. <span data-ttu-id="9831e-113">Prześlij zmianę do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9831e-113">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="9831e-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="9831e-114">Example</span></span>

<span data-ttu-id="9831e-115">Poniższy przykład kodu tworzy nowy obiekt typu `Order` i wypełnia go odpowiednimi wartościami.</span><span class="sxs-lookup"><span data-stu-id="9831e-115">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="9831e-116">Następnie dodaje nowy obiekt do `Order` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9831e-116">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="9831e-117">Na koniec przesyła zmiany do bazy danych jako nowy wiersz w `Orders` tabeli.</span><span class="sxs-lookup"><span data-stu-id="9831e-117">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="9831e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9831e-118">See also</span></span>

- [<span data-ttu-id="9831e-119">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="9831e-119">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="9831e-120">Metody DataContext (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="9831e-120">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="9831e-121">Instrukcje: Przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (Object Relational Designer)</span><span class="sxs-lookup"><span data-stu-id="9831e-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="9831e-122">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="9831e-122">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
