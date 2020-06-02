---
title: 'Instrukcje: Usuwanie wierszy z bazy danych'
description: Informacje o usuwaniu wierszy w bazie danych przez usunięcie LINQ to SQL obiektów z kolekcji powiązanej z tabelą. LINQ to SQL tłumaczy operacje usuwania na polecenia DELETE języka SQL.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: d08621e834961e1db9312cac36bd2e69133142b5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286394"
---
# <a name="how-to-delete-rows-from-the-database"></a><span data-ttu-id="cd115-104">Instrukcje: Usuwanie wierszy z bazy danych</span><span class="sxs-lookup"><span data-stu-id="cd115-104">How to: Delete Rows From the Database</span></span>

<span data-ttu-id="cd115-105">Można usunąć wiersze w bazie danych, usuwając odpowiednie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiekty z kolekcji powiązanej z tabelą.</span><span class="sxs-lookup"><span data-stu-id="cd115-105">You can delete rows in a database by removing the corresponding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objects from their table-related collection.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="cd115-106">tłumaczy zmiany w odpowiednie `DELETE` polecenia SQL.</span><span class="sxs-lookup"><span data-stu-id="cd115-106">translates your changes to the appropriate SQL `DELETE` commands.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="cd115-107">nie obsługuje ani nie rozpoznaje operacji kaskadowego usuwania.</span><span class="sxs-lookup"><span data-stu-id="cd115-107">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="cd115-108">Jeśli chcesz usunąć wiersz w tabeli zawierającej ograniczenia, musisz wykonać jedno z następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="cd115-108">If you want to delete a row in a table that has constraints against it, you must complete either of the following tasks:</span></span>

- <span data-ttu-id="cd115-109">Ustaw `ON DELETE CASCADE` regułę w ograniczeniu klucza obcego w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="cd115-109">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>

- <span data-ttu-id="cd115-110">Aby najpierw usunąć obiekty podrzędne, które uniemożliwiają usunięcie obiektu nadrzędnego, użyj własnego kodu.</span><span class="sxs-lookup"><span data-stu-id="cd115-110">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>

 <span data-ttu-id="cd115-111">W przeciwnym razie jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="cd115-111">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="cd115-112">Zobacz drugi przykład kodu w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cd115-112">See the second code example later in this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="cd115-113">Można przesłonić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody dla `Insert` , `Update` i `Delete` operacji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cd115-113">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="cd115-114">Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="cd115-114">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="cd115-115">Deweloperzy korzystający z programu Visual Studio mogą opracowywać procedury składowane w tym samym celu przy użyciu Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="cd115-115">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="cd115-116">W poniższych krokach przyjęto założenie, że prawidłowy <xref:System.Data.Linq.DataContext> nawiąże połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="cd115-116">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="cd115-117">Aby uzyskać więcej informacji, zobacz [How to: Connect to a Database](how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="cd115-117">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-delete-a-row-in-the-database"></a><span data-ttu-id="cd115-118">Aby usunąć wiersz w bazie danych</span><span class="sxs-lookup"><span data-stu-id="cd115-118">To delete a row in the database</span></span>

1. <span data-ttu-id="cd115-119">Wykonaj zapytanie względem bazy danych dla wiersza, który ma zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="cd115-119">Query the database for the row to be deleted.</span></span>

2. <span data-ttu-id="cd115-120">Wywołaj <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="cd115-120">Call the <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> method.</span></span>

3. <span data-ttu-id="cd115-121">Prześlij zmianę do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cd115-121">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="cd115-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd115-122">Example</span></span>

<span data-ttu-id="cd115-123">Ten pierwszy przykład kodu wysyła zapytanie do bazy danych w celu uzyskania szczegółów zamówienia, które należą do kolejności #11000, oznacza te szczegóły zamówienia do usunięcia i przesyła te zmiany do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cd115-123">This first code example queries the database for order details that belong to Order #11000, marks these order details for deletion, and submits these changes to the database.</span></span>

[!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
[!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="cd115-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd115-124">Example</span></span>

<span data-ttu-id="cd115-125">W tym drugim przykładzie celem jest usunięcie zamówienia (#10250).</span><span class="sxs-lookup"><span data-stu-id="cd115-125">In this second example, the objective is to remove an order (#10250).</span></span> <span data-ttu-id="cd115-126">Kod najpierw analizuje `OrderDetails` tabelę, aby sprawdzić, czy kolejność usuwania jest tam dostępna.</span><span class="sxs-lookup"><span data-stu-id="cd115-126">The code first examines the `OrderDetails` table to see whether the order to be removed has children there.</span></span> <span data-ttu-id="cd115-127">Jeśli zamówienie ma elementy podrzędne, najpierw elementy podrzędne, a następnie zamówienie jest oznaczone do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="cd115-127">If the order has children, first the children and then the order are marked for removal.</span></span> <span data-ttu-id="cd115-128"><xref:System.Data.Linq.DataContext>Umieszcza rzeczywiste usuwanie w prawidłowej kolejności, tak aby polecenia Delete wysyłane do bazy danych przestrzegać ograniczeń bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cd115-128">The <xref:System.Data.Linq.DataContext> puts the actual deletes in correct order so that delete commands sent to the database abide by the database constraints.</span></span>

[!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
[!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="cd115-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd115-129">See also</span></span>

- [<span data-ttu-id="cd115-130">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="cd115-130">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="cd115-131">Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="cd115-131">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="cd115-132">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="cd115-132">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
