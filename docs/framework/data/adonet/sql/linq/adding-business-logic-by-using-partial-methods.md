---
title: Dodawanie logiki biznesowej przy użyciu metod częściowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: e3f82c260a2cab85270a9f33a87eb9a9f04b72c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964141"
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="16013-102">Dodawanie logiki biznesowej przy użyciu metod częściowych</span><span class="sxs-lookup"><span data-stu-id="16013-102">Adding Business Logic By Using Partial Methods</span></span>
<span data-ttu-id="16013-103">Możesz dostosować Visual Basic i C# wygenerowany kod w swoich [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektach przy użyciu *metod częściowych*.</span><span class="sxs-lookup"><span data-stu-id="16013-103">You can customize Visual Basic and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="16013-104">Kod, który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje definiuje podpisy jako jedną część metody częściowej.</span><span class="sxs-lookup"><span data-stu-id="16013-104">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="16013-105">Jeśli chcesz zaimplementować metodę, możesz dodać własną metodę częściową.</span><span class="sxs-lookup"><span data-stu-id="16013-105">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="16013-106">Jeśli nie dodasz własnej implementacji, kompilator odrzuca podpis metod częściowych i wywołuje metody domyślne w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="16013-106">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16013-107">Jeśli używasz programu Visual Studio, możesz użyć Object Relational Designer, aby dodać walidację i inne dostosowania do klas jednostek.</span><span class="sxs-lookup"><span data-stu-id="16013-107">If you are using Visual Studio, you can use the Object Relational Designer to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="16013-108">Na przykład domyślne mapowanie `Customer` klasy w przykładowej bazie danych Northwind zawiera następującą metodę częściową:</span><span class="sxs-lookup"><span data-stu-id="16013-108">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="16013-109">Możesz zaimplementować własną metodę, dodając kod, taki jak poniżej, do własnej klasy częściowej `Customer` :</span><span class="sxs-lookup"><span data-stu-id="16013-109">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="16013-110">Takie podejście jest zwykle używane w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] programie, aby przesłonić `Update`domyślne `Delete`metody dla `Insert`,, i do walidacji właściwości podczas zdarzeń cyklu życia obiektu.</span><span class="sxs-lookup"><span data-stu-id="16013-110">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="16013-111">Aby uzyskać więcej informacji, zobacz [częściowe metody](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) lub [częściowe (Metoda)C# (odwołanie)](../../../../../csharp/language-reference/keywords/partial-method.md) (C#).</span><span class="sxs-lookup"><span data-stu-id="16013-111">For more information, see [Partial Methods](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) or [partial (Method) (C# Reference)](../../../../../csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="16013-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="16013-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="16013-113">Opis</span><span class="sxs-lookup"><span data-stu-id="16013-113">Description</span></span>  
 <span data-ttu-id="16013-114">Poniższy przykład pokazuje `ExampleClass` pierwszy, ponieważ może być zdefiniowany przez narzędzie generujące kod, takie jak SQLMetal, a następnie jak można zaimplementować tylko jedną z dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="16013-114">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="16013-115">Kod</span><span class="sxs-lookup"><span data-stu-id="16013-115">Code</span></span>  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="16013-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="16013-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="16013-117">Opis</span><span class="sxs-lookup"><span data-stu-id="16013-117">Description</span></span>  
 <span data-ttu-id="16013-118">Poniższy przykład używa relacji między `Shipper` i `Order` jednostką.</span><span class="sxs-lookup"><span data-stu-id="16013-118">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="16013-119">Zwróć uwagę między metodami częściowymi `InsertShipper` i. `DeleteShipper`</span><span class="sxs-lookup"><span data-stu-id="16013-119">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="16013-120">Te metody zastępują domyślne metody częściowe dostarczone przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapowanie.</span><span class="sxs-lookup"><span data-stu-id="16013-120">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="16013-121">Kod</span><span class="sxs-lookup"><span data-stu-id="16013-121">Code</span></span>  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="16013-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16013-122">See also</span></span>

- [<span data-ttu-id="16013-123">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="16013-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="16013-124">Dostosowywanie operacji wstawiania, aktualizowania i usuwania</span><span class="sxs-lookup"><span data-stu-id="16013-124">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
