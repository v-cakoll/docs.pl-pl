---
title: Parametry ogólne używane jako typy parametrów opcjonalnych muszą być ograniczone przez klasę
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 7e2b59f758ef236717a912694576b514e2ae8a60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="4c05b-102">Parametry ogólne używane jako typy parametrów opcjonalnych muszą być ograniczone przez klasę</span><span class="sxs-lookup"><span data-stu-id="4c05b-102">Generic parameters used as optional parameter types must be class constrained</span></span>
<span data-ttu-id="4c05b-103">Procedura jest zadeklarowana z opcjonalnym parametrem, który używa parametru typu, który nie jest ograniczona do typu referencyjnego.</span><span class="sxs-lookup"><span data-stu-id="4c05b-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>  
  
 <span data-ttu-id="4c05b-104">Należy zawsze podać wartość domyślną dla każdego parametru opcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="4c05b-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="4c05b-105">Jeśli parametr jest typu referencyjnego, opcjonalna wartość musi być `Nothing`, która jest prawidłową wartością dla dowolnego typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="4c05b-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="4c05b-106">Jednak jeśli parametr jest typu wartości, typu musi być typem danych podstawowych wstępnie zdefiniowane przez program Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4c05b-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="4c05b-107">Jest to spowodowane typu złożonego wartość, na przykład struktury zdefiniowane przez użytkownika, nie ma prawidłowe wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="4c05b-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>  
  
 <span data-ttu-id="4c05b-108">Gdy używasz parametru typu dla parametru opcjonalnego musi zagwarantowania, że będzie typu odwołania, aby uniknąć możliwości bez wartości prawidłowy domyślny typ wartości.</span><span class="sxs-lookup"><span data-stu-id="4c05b-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="4c05b-109">Oznacza to, że parametr typu należy ograniczyć za pomocą `Class` — słowo kluczowe lub o nazwie określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="4c05b-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>  
  
 <span data-ttu-id="4c05b-110">**Identyfikator błędu:** BC32124</span><span class="sxs-lookup"><span data-stu-id="4c05b-110">**Error ID:** BC32124</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4c05b-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="4c05b-111">To correct this error</span></span>  
  
-   <span data-ttu-id="4c05b-112">Ograniczenie parametru typu do akceptowania tylko typem referencyjnym lub nie jest używana dla parametru opcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="4c05b-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c05b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c05b-113">See Also</span></span>  
 [<span data-ttu-id="4c05b-114">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4c05b-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="4c05b-115">Lista typów</span><span class="sxs-lookup"><span data-stu-id="4c05b-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="4c05b-116">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4c05b-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="4c05b-117">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="4c05b-117">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [<span data-ttu-id="4c05b-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="4c05b-118">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="4c05b-119">Nothing</span><span class="sxs-lookup"><span data-stu-id="4c05b-119">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
