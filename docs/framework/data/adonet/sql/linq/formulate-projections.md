---
title: Sformułować projekcje
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: f554007bd8c9e69f6a8dc475c122d3fbdfc43a4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364951"
---
# <a name="formulate-projections"></a><span data-ttu-id="a1817-102">Sformułować projekcje</span><span class="sxs-lookup"><span data-stu-id="a1817-102">Formulate Projections</span></span>
<span data-ttu-id="a1817-103">W poniższych przykładach pokazano sposób `select` instrukcji w języku C# i `Select` instrukcji w języku Visual Basic można łączyć z innymi funkcjami do formularza projekcje zapytania.</span><span class="sxs-lookup"><span data-stu-id="a1817-103">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1817-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1817-104">Example</span></span>  
 <span data-ttu-id="a1817-105">W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` klauzuli w języku C#) do zwrócenia sekwencji kontaktu nazw `Customers`.</span><span class="sxs-lookup"><span data-stu-id="a1817-105">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="a1817-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1817-106">Example</span></span>  
 <span data-ttu-id="a1817-107">W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` klauzuli w języku C#) i *typy anonimowe* zwraca sekwencję nazwy kontaktów i numerów telefonu `Customers`.</span><span class="sxs-lookup"><span data-stu-id="a1817-107">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="a1817-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1817-108">Example</span></span>  
 <span data-ttu-id="a1817-109">W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` klauzuli w języku C#) i *typy anonimowe* zwraca sekwencję nazwy i numery telefonów dla pracowników.</span><span class="sxs-lookup"><span data-stu-id="a1817-109">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="a1817-110">`FirstName` i `LastName` pola są łączone w jedno pole (`Name`) i `HomePhone` pole jest zmieniana na `Phone` w wynikowej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a1817-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="a1817-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1817-111">Example</span></span>  
 <span data-ttu-id="a1817-112">W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` klauzuli w języku C#) i *typy anonimowe* do zwrócenia sekwencji wszystkich `ProductID`s i obliczonej wartości o nazwie `HalfPrice`.</span><span class="sxs-lookup"><span data-stu-id="a1817-112">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="a1817-113">Ta wartość jest równa `UnitPrice` podzielona przez 2.</span><span class="sxs-lookup"><span data-stu-id="a1817-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="a1817-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1817-114">Example</span></span>  
 <span data-ttu-id="a1817-115">W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` klauzuli w języku C#) i *instrukcji warunkowej* do zwrócenia sekwencji dostępności produktu i nazwa produktu.</span><span class="sxs-lookup"><span data-stu-id="a1817-115">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="a1817-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1817-116">Example</span></span>  
 <span data-ttu-id="a1817-117">W poniższym przykładzie użyto języka Visual Basic `Select` klauzuli (`select` klauzuli w języku C#) i *znany typ* (nazwy), aby znaleźć sekwencję imiona i nazwiska pracowników.</span><span class="sxs-lookup"><span data-stu-id="a1817-117">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="a1817-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1817-118">Example</span></span>  
 <span data-ttu-id="a1817-119">W poniższym przykładzie użyto `Select` i `Where` w języku Visual Basic (`select` i `where` w języku C#) do zwrócenia *filtrowane sekwencji* nazw kontaktu dla klientów w Londynie.</span><span class="sxs-lookup"><span data-stu-id="a1817-119">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="a1817-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1817-120">Example</span></span>  
 <span data-ttu-id="a1817-121">W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` klauzuli w języku C#) i *typy anonimowe* do zwrócenia *w kształcie podzestawu* danych dotyczących klientów.</span><span class="sxs-lookup"><span data-stu-id="a1817-121">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="a1817-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1817-122">Example</span></span>  
 <span data-ttu-id="a1817-123">W poniższym przykładzie użyto zapytania zagnieżdżone, aby zostać zwrócone następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="a1817-123">The following example uses nested queries to return the following results:</span></span>  
  
-   <span data-ttu-id="a1817-124">Sekwencja wszystkich zleceń i odpowiednie `OrderID`s.</span><span class="sxs-lookup"><span data-stu-id="a1817-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
-   <span data-ttu-id="a1817-125">Podsekwencji elementów w kolejności, dla którego jest rabat.</span><span class="sxs-lookup"><span data-stu-id="a1817-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
-   <span data-ttu-id="a1817-126">Ilość pieniędzy zapisany, jeśli nie dołączono kosztu wysyłki.</span><span class="sxs-lookup"><span data-stu-id="a1817-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="a1817-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1817-127">See Also</span></span>  
 [<span data-ttu-id="a1817-128">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="a1817-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
