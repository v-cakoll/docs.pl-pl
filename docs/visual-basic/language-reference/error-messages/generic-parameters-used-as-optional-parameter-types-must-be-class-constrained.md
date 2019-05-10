---
title: Parametry ogólne używane jako typy parametrów opcjonalnych muszą być ograniczone przez klasę
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 11cf4f8d9457ebff385a601786dc97334f274324
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662060"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="faaa8-102">Parametry ogólne używane jako typy parametrów opcjonalnych muszą być ograniczone przez klasę</span><span class="sxs-lookup"><span data-stu-id="faaa8-102">Generic parameters used as optional parameter types must be class constrained</span></span>
<span data-ttu-id="faaa8-103">Procedura jest zadeklarowana z opcjonalnym parametrem, który korzysta z parametrem typu, który nie jest ograniczony do być typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="faaa8-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>  
  
 <span data-ttu-id="faaa8-104">Zawsze należy podać wartość domyślną dla każdego opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="faaa8-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="faaa8-105">Jeśli parametr jest typem referencyjnym, opcjonalna wartość musi być `Nothing`, która jest prawidłową wartością dla dowolnego typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="faaa8-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="faaa8-106">Jednakże jeśli parametr jest typem wartości, tego typu musi być typu danych podstawowych wstępnie zdefiniowane przez program Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="faaa8-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="faaa8-107">Jest to spowodowane typu złożonych wartości, takie jak struktury zdefiniowany przez użytkownika, nie ma prawidłowe wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="faaa8-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>  
  
 <span data-ttu-id="faaa8-108">Gdy używasz parametru typu dla opcjonalnego parametru musi zagwarantować, jest typu odwołania, aby uniknąć możliwości typu wartości bez wartości prawidłowy domyślny.</span><span class="sxs-lookup"><span data-stu-id="faaa8-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="faaa8-109">Oznacza to, że parametr typu należy ograniczyć przy użyciu `Class` — słowo kluczowe lub o nazwie określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="faaa8-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>  
  
 <span data-ttu-id="faaa8-110">**Identyfikator błędu:** BC32124</span><span class="sxs-lookup"><span data-stu-id="faaa8-110">**Error ID:** BC32124</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="faaa8-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="faaa8-111">To correct this error</span></span>  
  
- <span data-ttu-id="faaa8-112">Ograniczenia parametru typu do akceptowania tylko typem referencyjnym lub nie jest używana dla parametru opcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="faaa8-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faaa8-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="faaa8-113">See also</span></span>

- [<span data-ttu-id="faaa8-114">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="faaa8-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="faaa8-115">Lista typów</span><span class="sxs-lookup"><span data-stu-id="faaa8-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="faaa8-116">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="faaa8-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="faaa8-117">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="faaa8-117">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="faaa8-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="faaa8-118">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="faaa8-119">Nothing</span><span class="sxs-lookup"><span data-stu-id="faaa8-119">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
