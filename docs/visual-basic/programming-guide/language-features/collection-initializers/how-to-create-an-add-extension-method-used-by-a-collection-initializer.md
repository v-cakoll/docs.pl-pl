---
title: 'Instrukcje: Utwórz Dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 3a1db8ede8162b329d546c0e712ef1c2df7d7883
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661675"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="f72ee-102">Instrukcje: Utwórz Dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f72ee-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="f72ee-103">Gdy używasz inicjatora kolekcji, aby utworzyć kolekcję, kompilator Visual Basic, wyszukuje `Add` metody typu kolekcji, dla której parametry `Add` metoda pasują do typów wartości na liście inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f72ee-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="f72ee-104">To `Add` metoda jest używana do wypełniania kolekcji z wartościami z inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f72ee-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="f72ee-105">Jeśli brak zgodności `Add` metoda istnieje i nie można zmodyfikować kod dla kolekcji, można dodać metodę rozszerzenia o nazwie `Add` która przyjmuje parametry, które są wymagane przez inicjator kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f72ee-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="f72ee-106">Jest to zazwyczaj, co należy zrobić, gdy używasz inicjatory kolekcji dla kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f72ee-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f72ee-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="f72ee-107">Example</span></span>  
 <span data-ttu-id="f72ee-108">Poniższy przykład pokazuje, jak dodać metody rozszerzenia do ogólnego <xref:System.Collections.Generic.List%601> wpisz, aby inicjatora kolekcji można dodawać obiekty określonego typu `Employee`.</span><span class="sxs-lookup"><span data-stu-id="f72ee-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="f72ee-109">Metoda rozszerzenia umożliwia przy użyciu składni inicjatora kolekcji skrócona.</span><span class="sxs-lookup"><span data-stu-id="f72ee-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f72ee-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f72ee-110">See also</span></span>
- [<span data-ttu-id="f72ee-111">Inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="f72ee-111">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="f72ee-112">Instrukcje: Tworzenie kolekcji wykorzystywanej przez inicjator kolekcji</span><span class="sxs-lookup"><span data-stu-id="f72ee-112">How to: Create a Collection Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
