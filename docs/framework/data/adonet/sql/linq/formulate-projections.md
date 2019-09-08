---
title: Formułowanie projekcji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: 0dfd5d951750de2ab918c51dd9f4f2deeb8a6318
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793817"
---
# <a name="formulate-projections"></a><span data-ttu-id="c24b9-102">Formułowanie projekcji</span><span class="sxs-lookup"><span data-stu-id="c24b9-102">Formulate Projections</span></span>
<span data-ttu-id="c24b9-103">W poniższych przykładach pokazano, `select` jak instrukcje C# w `Select` instrukcji in i w Visual Basic mogą być łączone z innymi funkcjami w celu tworzenia zapytań dotyczących projekcji.</span><span class="sxs-lookup"><span data-stu-id="c24b9-103">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c24b9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c24b9-104">Example</span></span>  
 <span data-ttu-id="c24b9-105">W poniższym przykładzie zastosowano `Select` klauzulę w Visual Basic`select` (klauzula C#in) do zwrócenia sekwencji nazw kontaktów dla `Customers`.</span><span class="sxs-lookup"><span data-stu-id="c24b9-105">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="c24b9-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c24b9-106">Example</span></span>  
 <span data-ttu-id="c24b9-107">W poniższym przykładzie zastosowano `Select` klauzulę w Visual Basic`select` (klauzula C#in) i *Typy anonimowe* , aby zwrócić sekwencję nazw kontaktów i numerów `Customers`telefonów dla programu.</span><span class="sxs-lookup"><span data-stu-id="c24b9-107">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="c24b9-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="c24b9-108">Example</span></span>  
 <span data-ttu-id="c24b9-109">W poniższym przykładzie zastosowano `Select` klauzulę w Visual Basic`select` (klauzula C#in) i *Typy anonimowe* , aby zwrócić sekwencję nazw i numerów telefonów dla pracowników.</span><span class="sxs-lookup"><span data-stu-id="c24b9-109">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="c24b9-110">`Phone` `HomePhone` `Name`Pola i sąpołączone`LastName` w jedno pole (), a nazwa pola jest zmieniana na w `FirstName` wyniku sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c24b9-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="c24b9-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c24b9-111">Example</span></span>  
 <span data-ttu-id="c24b9-112">W poniższym przykładzie zastosowano `Select` klauzulę w Visual Basic`select` (klauzula C#in) i *Typy anonimowe* , aby zwrócić sekwencję wszystkich `ProductID`i wartości obliczeniowej o nazwie. `HalfPrice`</span><span class="sxs-lookup"><span data-stu-id="c24b9-112">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="c24b9-113">Ta wartość jest ustawiana na `UnitPrice` podzieloną przez 2.</span><span class="sxs-lookup"><span data-stu-id="c24b9-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="c24b9-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="c24b9-114">Example</span></span>  
 <span data-ttu-id="c24b9-115">W `Select` poniższym przykładzie jest używana klauzula w Visual Basic (`select` klauzula in C#) i *Instrukcja warunkowa* zwracająca sekwencję nazwy produktu i dostępności produktu.</span><span class="sxs-lookup"><span data-stu-id="c24b9-115">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="c24b9-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="c24b9-116">Example</span></span>  
 <span data-ttu-id="c24b9-117">W poniższym przykładzie jest używana klauzula `Select` Visual Basic (`select` klauzula in C#) i *znany typ* (nazwa) do zwrócenia sekwencji nazw pracowników.</span><span class="sxs-lookup"><span data-stu-id="c24b9-117">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="c24b9-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="c24b9-118">Example</span></span>  
 <span data-ttu-id="c24b9-119">`Select` Poniższy przykład używa i `Where` w Visual Basic (`select` i `where` C#) do zwracania *filtrowanej sekwencji* nazw kontaktów dla klientów w Londynie.</span><span class="sxs-lookup"><span data-stu-id="c24b9-119">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="c24b9-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="c24b9-120">Example</span></span>  
 <span data-ttu-id="c24b9-121">W poniższym przykładzie zastosowano `Select` klauzulę w Visual Basic`select` (klauzula C#in) i *Typy anonimowe* , aby zwrócić *podzbiór* danych dotyczących klientów.</span><span class="sxs-lookup"><span data-stu-id="c24b9-121">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="c24b9-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="c24b9-122">Example</span></span>  
 <span data-ttu-id="c24b9-123">Poniższy przykład używa zagnieżdżonych zapytań, aby zwrócić następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c24b9-123">The following example uses nested queries to return the following results:</span></span>  
  
- <span data-ttu-id="c24b9-124">Sekwencja wszystkich zamówień i odpowiadających im `OrderID`elementów typu.</span><span class="sxs-lookup"><span data-stu-id="c24b9-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
- <span data-ttu-id="c24b9-125">Podsekwencja elementów w kolejności, w której występuje rabat.</span><span class="sxs-lookup"><span data-stu-id="c24b9-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
- <span data-ttu-id="c24b9-126">Ilość pieniędzy zapisana, jeśli koszt wysyłki nie jest uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="c24b9-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="c24b9-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c24b9-127">See also</span></span>

- [<span data-ttu-id="c24b9-128">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="c24b9-128">Query Examples</span></span>](query-examples.md)
