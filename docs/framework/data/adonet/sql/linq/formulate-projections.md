---
title: Formułowanie projekcji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: e1f7a7da1ab2ce0ad7d7908ecd1f896d229b8e1a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223306"
---
# <a name="formulate-projections"></a><span data-ttu-id="10fff-102">Formułowanie projekcji</span><span class="sxs-lookup"><span data-stu-id="10fff-102">Formulate Projections</span></span>
<span data-ttu-id="10fff-103">W poniższych przykładach pokazano sposób, w jaki `select` instrukcji w C# i `Select` instrukcji w języku Visual Basic można łączyć z innymi funkcjami do formularza projekcje zapytania.</span><span class="sxs-lookup"><span data-stu-id="10fff-103">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10fff-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="10fff-104">Example</span></span>  
 <span data-ttu-id="10fff-105">W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` w klauzuli C#) do zwrócenia sekwencji skontaktuj się z nazwy `Customers`.</span><span class="sxs-lookup"><span data-stu-id="10fff-105">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="10fff-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="10fff-106">Example</span></span>  
 <span data-ttu-id="10fff-107">W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` w klauzuli C#) i *typy anonimowe* do zwrócenia sekwencji skontaktuj się z nazwy i numery telefonu `Customers`.</span><span class="sxs-lookup"><span data-stu-id="10fff-107">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="10fff-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="10fff-108">Example</span></span>  
 <span data-ttu-id="10fff-109">W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` w klauzuli C#) i *typy anonimowe* do zwrócenia sekwencji nazwy i numery telefonów dla pracowników.</span><span class="sxs-lookup"><span data-stu-id="10fff-109">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="10fff-110">`FirstName` i `LastName` pola są połączone w jedno pole (`Name`), a `HomePhone` pola została zmieniona na `Phone` w wynikowej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="10fff-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="10fff-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="10fff-111">Example</span></span>  
 <span data-ttu-id="10fff-112">W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` w klauzuli C#) i *typy anonimowe* celu zwrócenia sekwencji wszystkich `ProductID`s i obliczonej wartości o nazwie `HalfPrice`.</span><span class="sxs-lookup"><span data-stu-id="10fff-112">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="10fff-113">Ta wartość jest równa `UnitPrice` podzielonej przez 2.</span><span class="sxs-lookup"><span data-stu-id="10fff-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="10fff-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="10fff-114">Example</span></span>  
 <span data-ttu-id="10fff-115">W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` w klauzuli C#) i *instrukcji warunkowej* celu zwrócenia sekwencji nazwę produktu i dostępność produktu.</span><span class="sxs-lookup"><span data-stu-id="10fff-115">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="10fff-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="10fff-116">Example</span></span>  
 <span data-ttu-id="10fff-117">W poniższym przykładzie użyto języka Visual Basic `Select` — klauzula (`select` w klauzuli C#) i *znany typ* (nazwa) w celu zwrócenia sekwencji nazw pracowników.</span><span class="sxs-lookup"><span data-stu-id="10fff-117">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="10fff-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="10fff-118">Example</span></span>  
 <span data-ttu-id="10fff-119">W poniższym przykładzie użyto `Select` i `Where` w języku Visual Basic (`select` i `where` w C#) do zwrócenia *filtrowane sekwencji* nazw kontaktu dla klientów w Londynie.</span><span class="sxs-lookup"><span data-stu-id="10fff-119">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="10fff-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="10fff-120">Example</span></span>  
 <span data-ttu-id="10fff-121">W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` w klauzuli C#) i *typy anonimowe* do zwrócenia *ukształtowane podzbioru* danych dotyczących klientów.</span><span class="sxs-lookup"><span data-stu-id="10fff-121">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="10fff-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="10fff-122">Example</span></span>  
 <span data-ttu-id="10fff-123">W poniższym przykładzie użyto zapytań zagnieżdżonej, aby zostały zwrócone następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="10fff-123">The following example uses nested queries to return the following results:</span></span>  
  
-   <span data-ttu-id="10fff-124">Sekwencja wszystkich zamówień i odpowiadające im `OrderID`s.</span><span class="sxs-lookup"><span data-stu-id="10fff-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
-   <span data-ttu-id="10fff-125">Podsekwencji elementy w kolejności, dla którego jest rabat.</span><span class="sxs-lookup"><span data-stu-id="10fff-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
-   <span data-ttu-id="10fff-126">Ilość pieniądze zapisane, jeżeli nie dołączono kosztu wysyłki.</span><span class="sxs-lookup"><span data-stu-id="10fff-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="10fff-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10fff-127">See also</span></span>

- [<span data-ttu-id="10fff-128">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="10fff-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
