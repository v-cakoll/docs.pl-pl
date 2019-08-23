---
title: Co można zrobić za pomocą funkcji LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: 21ed620ab5b7a78fc4f396cc474e7c62b70f1ddd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946621"
---
# <a name="what-you-can-do-with-linq-to-sql"></a><span data-ttu-id="84448-102">Co można zrobić za pomocą funkcji LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="84448-102">What You Can Do With LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="84448-103">Program obsługuje wszystkie kluczowe możliwości, które należy oczekiwać jako deweloper SQL.</span><span class="sxs-lookup"><span data-stu-id="84448-103">supports all the key capabilities you would expect as a SQL developer.</span></span> <span data-ttu-id="84448-104">Możesz wysyłać zapytania o informacje oraz wstawiać, aktualizować i usuwać informacje z tabel.</span><span class="sxs-lookup"><span data-stu-id="84448-104">You can query for information, and insert, update, and delete information from tables.</span></span>  
  
## <a name="selecting"></a><span data-ttu-id="84448-105">Zaznaczenie</span><span class="sxs-lookup"><span data-stu-id="84448-105">Selecting</span></span>  
 <span data-ttu-id="84448-106">Wybór (*projekcja*) jest realizowany przez zapisanie [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytania w własnym języku programowania, a następnie wykonanie zapytania w celu pobrania wyników.</span><span class="sxs-lookup"><span data-stu-id="84448-106">Selecting (*projection*) is achieved by just writing a [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] query in your own programming language, and then executing that query to retrieve the results.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="84448-107">samo tłumaczy wszystkie niezbędne operacje na niezbędne operacje SQL, które znasz.</span><span class="sxs-lookup"><span data-stu-id="84448-107">itself translates all the necessary operations into the necessary SQL operations that you are familiar with.</span></span> <span data-ttu-id="84448-108">Aby uzyskać więcej informacji, zobacz [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="84448-108">For more information, see [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="84448-109">W poniższym przykładzie nazwy firmowe klientów z Londynie są pobierane i wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="84448-109">In the following example, the company names of customers from London are retrieved and displayed in the console window.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a><span data-ttu-id="84448-110">Wstawieniu</span><span class="sxs-lookup"><span data-stu-id="84448-110">Inserting</span></span>  
 <span data-ttu-id="84448-111">Aby wykonać instrukcję SQL `Insert`, wystarczy dodać obiekty do modelu obiektów, który został utworzony, i wywołać <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext>polecenie.</span><span class="sxs-lookup"><span data-stu-id="84448-111">To execute a SQL `Insert`, just add objects to the object model you have created, and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="84448-112">W poniższym przykładzie nowy klient i informacje o kliencie są dodawane do `Customers` tabeli przy użyciu. <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A></span><span class="sxs-lookup"><span data-stu-id="84448-112">In the following example, a new customer and information about the customer is added to the `Customers` table by using <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a><span data-ttu-id="84448-113">Aktualizowanie</span><span class="sxs-lookup"><span data-stu-id="84448-113">Updating</span></span>  
 <span data-ttu-id="84448-114">Aby `Update` wejść do bazy danych, najpierw Pobierz element i edytuj go bezpośrednio w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="84448-114">To `Update` a database entry, first retrieve the item and edit it directly in the object model.</span></span> <span data-ttu-id="84448-115">Po zmodyfikowaniu obiektu Wywołaj <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> polecenie, aby zaktualizować bazę danych.</span><span class="sxs-lookup"><span data-stu-id="84448-115">After you have modified the object, call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to update the database.</span></span>  
  
 <span data-ttu-id="84448-116">W poniższym przykładzie są pobierane wszyscy klienci z usługi Londyn.</span><span class="sxs-lookup"><span data-stu-id="84448-116">In the following example, all customers who are from London are retrieved.</span></span> <span data-ttu-id="84448-117">Nazwa miasta zostanie zmieniona z "Londyn" na "Londyn-metro".</span><span class="sxs-lookup"><span data-stu-id="84448-117">Then the name of the city is changed from "London" to "London - Metro".</span></span> <span data-ttu-id="84448-118">Na koniec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana w celu wysłania zmian do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="84448-118">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to send the changes to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a><span data-ttu-id="84448-119">Usunąć</span><span class="sxs-lookup"><span data-stu-id="84448-119">Deleting</span></span>  
 <span data-ttu-id="84448-120">Do `Delete` elementu, Usuń element z kolekcji, do której należy, a następnie Wywołaj metodę <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> , aby zatwierdzić zmianę.</span><span class="sxs-lookup"><span data-stu-id="84448-120">To `Delete` an item, remove the item from the collection to which it belongs, and then call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to commit the change.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="84448-121">nie rozpoznaje operacji kaskadowego usuwania.</span><span class="sxs-lookup"><span data-stu-id="84448-121">does not recognize cascade-delete operations.</span></span> <span data-ttu-id="84448-122">Jeśli chcesz usunąć wiersz z tabeli zawierającej ograniczenia, zobacz [How to: Usuń wiersze z bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span><span class="sxs-lookup"><span data-stu-id="84448-122">If you want to delete a row in a table that has constraints against it, see [How to: Delete Rows From the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="84448-123">W poniższym przykładzie klient, który ma `CustomerID` zostać pobrany z bazy danych programu. `98128`</span><span class="sxs-lookup"><span data-stu-id="84448-123">In the following example, the customer who has `CustomerID` of `98128` is retrieved from the database.</span></span> <span data-ttu-id="84448-124">Następnie po potwierdzeniu, że wiersz klienta został pobrany, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> jest wywoływana, aby usunąć ten obiekt z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="84448-124">Then, after confirming that the customer row was retrieved, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> is called to remove that object from the collection.</span></span> <span data-ttu-id="84448-125">Na koniec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana, aby przesłać dalej operację usuwania do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="84448-125">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to forward the deletion to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="84448-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84448-126">See also</span></span>

- [<span data-ttu-id="84448-127">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="84448-127">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [<span data-ttu-id="84448-128">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="84448-128">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="84448-129">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="84448-129">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
