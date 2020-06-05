---
title: Nie można wywnioskować argumentów typu na podstawie obiektu delegowanego
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: f29e92c8245e33c0418d9a387070b03f645c331e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362751"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="131c6-102">Nie można wywnioskować argumentów typu na podstawie obiektu delegowanego</span><span class="sxs-lookup"><span data-stu-id="131c6-102">Type arguments could not be inferred from the delegate</span></span>
<span data-ttu-id="131c6-103">Instrukcja przypisania używa `AddressOf` do przypisywania adresu procedury ogólnej do delegata, ale nie dostarcza żadnych argumentów typu do procedury ogólnej.</span><span class="sxs-lookup"><span data-stu-id="131c6-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="131c6-104">Zwykle podczas wywoływania typu ogólnego należy podać argument typu dla każdego parametru typu, który definiuje typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="131c6-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="131c6-105">Jeśli nie podasz żadnych argumentów typu, kompilator próbuje wywnioskować typy do przekazania do parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="131c6-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="131c6-106">Jeśli kontekst nie zapewnia wystarczającej ilości informacji do wywnioskowania typów przez kompilator, generowany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="131c6-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="131c6-107">**Identyfikator błędu:** BC36564</span><span class="sxs-lookup"><span data-stu-id="131c6-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="131c6-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="131c6-108">To correct this error</span></span>  
  
- <span data-ttu-id="131c6-109">Określ argumenty typu dla procedury ogólnej w `AddressOf` wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="131c6-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131c6-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="131c6-110">See also</span></span>

- [<span data-ttu-id="131c6-111">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="131c6-111">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="131c6-112">AddressOf, operator</span><span class="sxs-lookup"><span data-stu-id="131c6-112">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="131c6-113">Procedury ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="131c6-113">Generic Procedures in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="131c6-114">Lista typów</span><span class="sxs-lookup"><span data-stu-id="131c6-114">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="131c6-115">Metody rozszerzające</span><span class="sxs-lookup"><span data-stu-id="131c6-115">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
