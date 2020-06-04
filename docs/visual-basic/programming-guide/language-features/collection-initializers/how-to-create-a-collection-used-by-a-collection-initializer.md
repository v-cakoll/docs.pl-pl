---
title: 'Porady: tworzenie kolekcji wykorzystywanej przez inicjator kolekcji'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 7cba290b92f41125a93d1ed022e4db5ef62da789
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414559"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="e4b4f-102">Porady: tworzenie kolekcji wykorzystywanej przez inicjator kolekcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4b4f-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="e4b4f-103">W przypadku tworzenia kolekcji za pomocą inicjatora kolekcji, kompilator Visual Basic wyszukuje `Add` metodę typu kolekcji, dla którego parametry `Add` metody pasują do typów wartości w inicjatorze kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e4b4f-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="e4b4f-104">Ta `Add` Metoda służy do wypełniania kolekcji wartościami z inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e4b4f-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4b4f-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4b4f-105">Example</span></span>  
 <span data-ttu-id="e4b4f-106">Poniższy przykład pokazuje `OrderCollection` kolekcję zawierającą metodę publiczną `Add` , która może być używana przez inicjator kolekcji do dodawania obiektów typu `Order` .</span><span class="sxs-lookup"><span data-stu-id="e4b4f-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="e4b4f-107">`Add`Metoda umożliwia użycie skróconej składni inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e4b4f-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e4b4f-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4b4f-108">See also</span></span>

- [<span data-ttu-id="e4b4f-109">Inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="e4b4f-109">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="e4b4f-110">Instrukcje: tworzenie i dodawanie metody rozszerzenia używanej przez inicjator kolekcji</span><span class="sxs-lookup"><span data-stu-id="e4b4f-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
