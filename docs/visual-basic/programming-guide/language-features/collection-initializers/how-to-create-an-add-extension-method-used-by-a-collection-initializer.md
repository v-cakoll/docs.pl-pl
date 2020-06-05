---
title: 'Porady: tworzenie i dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 4dbe6146b70181864a6717146071f9b93a1f583e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414572"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="e9915-102">Porady: tworzenie i dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9915-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="e9915-103">W przypadku tworzenia kolekcji za pomocą inicjatora kolekcji, kompilator Visual Basic wyszukuje `Add` metodę typu kolekcji, dla którego parametry `Add` metody pasują do typów wartości w inicjatorze kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e9915-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="e9915-104">Ta `Add` Metoda służy do wypełniania kolekcji wartościami z inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e9915-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="e9915-105">Jeśli żadna zgodna `Add` Metoda nie istnieje i nie można zmodyfikować kodu dla kolekcji, można dodać metodę rozszerzenia o nazwie `Add` , która pobiera parametry wymagane przez inicjator kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e9915-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="e9915-106">Zazwyczaj jest to konieczne, gdy do kolekcji ogólnych są używane Inicjatory kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e9915-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9915-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9915-107">Example</span></span>  
 <span data-ttu-id="e9915-108">Poniższy przykład pokazuje, jak dodać metodę rozszerzenia do typu ogólnego, <xref:System.Collections.Generic.List%601> Aby inicjator kolekcji mógł służyć do dodawania obiektów typu `Employee` .</span><span class="sxs-lookup"><span data-stu-id="e9915-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="e9915-109">Metoda rozszerzenia umożliwia użycie skróconej składni inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e9915-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e9915-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9915-110">See also</span></span>

- [<span data-ttu-id="e9915-111">Inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="e9915-111">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="e9915-112">Instrukcje: tworzenie kolekcji używanej przez inicjator kolekcji</span><span class="sxs-lookup"><span data-stu-id="e9915-112">How to: Create a Collection Used by a Collection Initializer</span></span>](how-to-create-a-collection-used-by-a-collection-initializer.md)
