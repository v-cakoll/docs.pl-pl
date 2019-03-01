---
title: 'Instrukcje: Utwórz Dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 458421da70aca6728f3f03945c28b4c988e44ad7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978543"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="5c684-102">Instrukcje: Utwórz Dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c684-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="5c684-103">Gdy używasz inicjatora kolekcji, aby utworzyć kolekcję, kompilator Visual Basic, wyszukuje `Add` metody typu kolekcji, dla której parametry `Add` metoda pasują do typów wartości na liście inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5c684-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="5c684-104">To `Add` metoda jest używana do wypełniania kolekcji z wartościami z inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5c684-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="5c684-105">Jeśli brak zgodności `Add` metoda istnieje i nie można zmodyfikować kod dla kolekcji, można dodać metodę rozszerzenia o nazwie `Add` która przyjmuje parametry, które są wymagane przez inicjator kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5c684-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="5c684-106">Jest to zazwyczaj, co należy zrobić, gdy używasz inicjatory kolekcji dla kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5c684-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c684-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c684-107">Example</span></span>  
 <span data-ttu-id="5c684-108">Poniższy przykład pokazuje, jak dodać metody rozszerzenia do ogólnego <xref:System.Collections.Generic.List%601> wpisz, aby inicjatora kolekcji można dodawać obiekty określonego typu `Employee`.</span><span class="sxs-lookup"><span data-stu-id="5c684-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="5c684-109">Metoda rozszerzenia umożliwia przy użyciu składni inicjatora kolekcji skrócona.</span><span class="sxs-lookup"><span data-stu-id="5c684-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5c684-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c684-110">See also</span></span>
- [<span data-ttu-id="5c684-111">Inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="5c684-111">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="5c684-112">Instrukcje: Tworzenie kolekcji wykorzystywanej przez inicjator kolekcji</span><span class="sxs-lookup"><span data-stu-id="5c684-112">How to: Create a Collection Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
