---
title: 'Instrukcje: Tworzenie kolekcji wykorzystywanej przez inicjator kolekcji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 75c280b57df03bde173c740123cccda278536dc1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053629"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="8b41f-102">Instrukcje: Tworzenie kolekcji wykorzystywanej przez inicjator kolekcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b41f-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="8b41f-103">Gdy używasz inicjatora kolekcji, aby utworzyć kolekcję, kompilator Visual Basic, wyszukuje `Add` metody typu kolekcji, dla której parametry `Add` metoda pasują do typów wartości na liście inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8b41f-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="8b41f-104">To `Add` metoda jest używana do wypełniania kolekcji z wartościami z inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8b41f-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b41f-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="8b41f-105">Example</span></span>  
 <span data-ttu-id="8b41f-106">W poniższym przykładzie przedstawiono `OrderCollection` kolekcji, która zawiera publiczny `Add` metodę, która inicjator kolekcji służy do dodawania obiektów typu `Order`.</span><span class="sxs-lookup"><span data-stu-id="8b41f-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="8b41f-107">`Add` Metoda pozwala przy użyciu składni inicjatora kolekcji skrócona.</span><span class="sxs-lookup"><span data-stu-id="8b41f-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8b41f-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b41f-108">See also</span></span>

- [<span data-ttu-id="8b41f-109">Inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="8b41f-109">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="8b41f-110">Instrukcje: Utwórz Dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji</span><span class="sxs-lookup"><span data-stu-id="8b41f-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
