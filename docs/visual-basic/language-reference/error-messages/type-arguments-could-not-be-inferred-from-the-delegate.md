---
title: Nie można wywnioskować argumentów typu na podstawie obiektu delegowanego
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 3e2902da7fe9d8fa2194db681df098f0148cbbaf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584259"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="2e7db-102">Nie można wywnioskować argumentów typu na podstawie obiektu delegowanego</span><span class="sxs-lookup"><span data-stu-id="2e7db-102">Type arguments could not be inferred from the delegate</span></span>
<span data-ttu-id="2e7db-103">Używa instrukcji przypisania `AddressOf` na przypisanie adresu ogólnej procedury, aby obiekt delegowany, ale nie dostarcza żadnych argumentów typu rodzajowego procedury.</span><span class="sxs-lookup"><span data-stu-id="2e7db-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="2e7db-104">Zwykle po wywołaniu typu ogólnego, podaj argument typu dla każdego parametru typu, który definiuje typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="2e7db-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="2e7db-105">Jeśli nie podasz żadnych argumentów typu, kompilator spróbuje wnioskowanie typów, które mają być przekazane do parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="2e7db-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="2e7db-106">Jeśli kontekst nie zawiera wystarczających informacji, aby kompilator mógł wnioskowanie typów, zostanie wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="2e7db-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="2e7db-107">**Identyfikator błędu:** BC36564</span><span class="sxs-lookup"><span data-stu-id="2e7db-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2e7db-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="2e7db-108">To correct this error</span></span>  
  
- <span data-ttu-id="2e7db-109">Określ argumenty tupu ogólnego procedury w `AddressOf` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2e7db-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e7db-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e7db-110">See also</span></span>

- [<span data-ttu-id="2e7db-111">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e7db-111">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="2e7db-112">AddressOf, operator</span><span class="sxs-lookup"><span data-stu-id="2e7db-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="2e7db-113">Procedury ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e7db-113">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="2e7db-114">Lista typów</span><span class="sxs-lookup"><span data-stu-id="2e7db-114">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="2e7db-115">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="2e7db-115">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
