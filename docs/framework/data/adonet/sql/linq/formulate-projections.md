---
title: "Sformułować projekcje"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8afd48c6ce7c6313e82a7b74c2271f52833d1f5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="formulate-projections"></a><span data-ttu-id="07206-102">Sformułować projekcje</span><span class="sxs-lookup"><span data-stu-id="07206-102">Formulate Projections</span></span>
<span data-ttu-id="07206-103">W poniższych przykładach pokazano sposób `select` instrukcji w języku C# i `Select` instrukcji w [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] można łączyć z innymi funkcjami do formularza projekcje zapytania.</span><span class="sxs-lookup"><span data-stu-id="07206-103">The following examples show how the `select` statement in C# and `Select` statement in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07206-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="07206-104">Example</span></span>  
 <span data-ttu-id="07206-105">W poniższym przykładzie użyto `Select` w klauzuli [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzuli w języku C#) do zwrócenia sekwencji kontaktu nazw `Customers`.</span><span class="sxs-lookup"><span data-stu-id="07206-105">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="07206-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="07206-106">Example</span></span>  
 <span data-ttu-id="07206-107">W poniższym przykładzie użyto `Select` w klauzuli [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzuli w języku C#) i *typy anonimowe* zwraca sekwencję nazwy kontaktów i numerów telefonu `Customers`.</span><span class="sxs-lookup"><span data-stu-id="07206-107">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="07206-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="07206-108">Example</span></span>  
 <span data-ttu-id="07206-109">W poniższym przykładzie użyto `Select` w klauzuli [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzuli w języku C#) i *typy anonimowe* zwraca sekwencję nazwy i numery telefonów dla pracowników.</span><span class="sxs-lookup"><span data-stu-id="07206-109">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="07206-110">`FirstName` i `LastName` pola są łączone w jedno pole (`Name`) i `HomePhone` pole jest zmieniana na `Phone` w wynikowej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="07206-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="07206-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="07206-111">Example</span></span>  
 <span data-ttu-id="07206-112">W poniższym przykładzie użyto `Select` w klauzuli [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzuli w języku C#) i *typy anonimowe* do zwrócenia sekwencji wszystkich `ProductID`s i obliczonej wartości o nazwie `HalfPrice`.</span><span class="sxs-lookup"><span data-stu-id="07206-112">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="07206-113">Ta wartość jest równa `UnitPrice` podzielona przez 2.</span><span class="sxs-lookup"><span data-stu-id="07206-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="07206-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="07206-114">Example</span></span>  
 <span data-ttu-id="07206-115">W poniższym przykładzie użyto `Select` w klauzuli [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzuli w języku C#) i *instrukcji warunkowej* do zwrócenia sekwencji dostępności produktu i nazwa produktu.</span><span class="sxs-lookup"><span data-stu-id="07206-115">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="07206-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="07206-116">Example</span></span>  
 <span data-ttu-id="07206-117">W poniższym przykładzie użyto [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `Select` klauzuli (`select` klauzuli w języku C#) i *znany typ* (nazwy), aby znaleźć sekwencję imiona i nazwiska pracowników.</span><span class="sxs-lookup"><span data-stu-id="07206-117">The following example uses a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="07206-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="07206-118">Example</span></span>  
 <span data-ttu-id="07206-119">W poniższym przykładzie użyto `Select` i `Where` w [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` i `where` w języku C#) do zwrócenia *filtrowane sekwencji* nazw kontaktu dla klientów w Londynie.</span><span class="sxs-lookup"><span data-stu-id="07206-119">The following example uses `Select` and `Where` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="07206-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="07206-120">Example</span></span>  
 <span data-ttu-id="07206-121">W poniższym przykładzie użyto `Select` w klauzuli [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzuli w języku C#) i *typy anonimowe* do zwrócenia *w kształcie podzestawu* danych dotyczących klientów.</span><span class="sxs-lookup"><span data-stu-id="07206-121">The following example uses a `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="07206-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="07206-122">Example</span></span>  
 <span data-ttu-id="07206-123">W poniższym przykładzie użyto zapytania zagnieżdżone, aby zostać zwrócone następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="07206-123">The following example uses nested queries to return the following results:</span></span>  
  
-   <span data-ttu-id="07206-124">Sekwencja wszystkich zleceń i odpowiednie `OrderID`s.</span><span class="sxs-lookup"><span data-stu-id="07206-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
-   <span data-ttu-id="07206-125">Podsekwencji elementów w kolejności, dla którego jest rabat.</span><span class="sxs-lookup"><span data-stu-id="07206-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
-   <span data-ttu-id="07206-126">Ilość pieniędzy zapisany, jeśli nie dołączono kosztu wysyłki.</span><span class="sxs-lookup"><span data-stu-id="07206-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="07206-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07206-127">See Also</span></span>  
 [<span data-ttu-id="07206-128">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="07206-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
