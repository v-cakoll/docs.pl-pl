---
title: Dodawanie logiki biznesowej przy użyciu metod częściowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: ed440f3315fc25e82b648f21410acb7a2c2a08f9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743669"
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="89f2f-102">Dodawanie logiki biznesowej przy użyciu metod częściowych</span><span class="sxs-lookup"><span data-stu-id="89f2f-102">Adding Business Logic By Using Partial Methods</span></span>
<span data-ttu-id="89f2f-103">Można dostosować Visual Basic i C# wygenerowany kod w swojej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektów za pomocą *metod częściowych*.</span><span class="sxs-lookup"><span data-stu-id="89f2f-103">You can customize Visual Basic and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="89f2f-104">Kod, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje definiuje podpisów w ramach jednej metody częściowej.</span><span class="sxs-lookup"><span data-stu-id="89f2f-104">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="89f2f-105">Jeśli chcesz wdrożyć metodę, można dodać własne metody częściowej.</span><span class="sxs-lookup"><span data-stu-id="89f2f-105">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="89f2f-106">Jeśli nie dodasz Twojej własnej implementacji, kompilator odrzuca podpis metod częściowych i wywołania metody domyślną, w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="89f2f-106">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89f2f-107">Jeśli używasz programu Visual Studio można użyć Object Relational Designer, aby dodać sprawdzanie poprawności i innych dostosowań do klas jednostek.</span><span class="sxs-lookup"><span data-stu-id="89f2f-107">If you are using Visual Studio, you can use the Object Relational Designer to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="89f2f-108">Na przykład do domyślnego mapowania dla `Customer` klasy w bazie danych Northwind obejmuje następujące metody częściowej:</span><span class="sxs-lookup"><span data-stu-id="89f2f-108">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="89f2f-109">Można zaimplementować własną metodę, dodając następujący kod do własnych częściowego `Customer` klasy:</span><span class="sxs-lookup"><span data-stu-id="89f2f-109">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="89f2f-110">To podejście jest zwykle używana w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przesłonić domyślne metody `Insert`, `Update`, `Delete`, a do sprawdzania poprawności właściwości podczas zdarzenia cyklu życia obiektów.</span><span class="sxs-lookup"><span data-stu-id="89f2f-110">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="89f2f-111">Aby uzyskać więcej informacji, zobacz [metod częściowych](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) lub [partial (metoda) (C# odwołania)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).</span><span class="sxs-lookup"><span data-stu-id="89f2f-111">For more information, see [Partial Methods](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) or [partial (Method) (C# Reference)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="89f2f-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="89f2f-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="89f2f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="89f2f-113">Description</span></span>  
 <span data-ttu-id="89f2f-114">W poniższym przykładzie przedstawiono `ExampleClass` najpierw może być zdefiniowana przez narzędzie generowania kodu, takich jak program SQLMetal, a następnie implementacji tylko w jednej z dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="89f2f-114">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="89f2f-115">Kod</span><span class="sxs-lookup"><span data-stu-id="89f2f-115">Code</span></span>  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="89f2f-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="89f2f-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="89f2f-117">Opis</span><span class="sxs-lookup"><span data-stu-id="89f2f-117">Description</span></span>  
 <span data-ttu-id="89f2f-118">W poniższym przykładzie użyto relacji między `Shipper` i `Order` jednostek.</span><span class="sxs-lookup"><span data-stu-id="89f2f-118">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="89f2f-119">Należy zauważyć jedną z metod metod częściowych `InsertShipper` i `DeleteShipper`.</span><span class="sxs-lookup"><span data-stu-id="89f2f-119">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="89f2f-120">Te metody Przesłaniaj metody częściowej domyślne, dostarczone przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapowania.</span><span class="sxs-lookup"><span data-stu-id="89f2f-120">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="89f2f-121">Kod</span><span class="sxs-lookup"><span data-stu-id="89f2f-121">Code</span></span>  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="89f2f-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89f2f-122">See also</span></span>

- [<span data-ttu-id="89f2f-123">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="89f2f-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="89f2f-124">Dostosowywanie operacji wstawiania, aktualizowania i usuwania</span><span class="sxs-lookup"><span data-stu-id="89f2f-124">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
