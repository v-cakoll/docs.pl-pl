---
title: Parametry ogólne używane jako typy parametrów opcjonalnych muszą być ograniczone przez klasę
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 273ea592e73be5d76a4ffef077e691014a108347
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402930"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="73dd8-102">Parametry ogólne używane jako typy parametrów opcjonalnych muszą być ograniczone przez klasę</span><span class="sxs-lookup"><span data-stu-id="73dd8-102">Generic parameters used as optional parameter types must be class constrained</span></span>
<span data-ttu-id="73dd8-103">Procedura jest zadeklarowana z opcjonalnym parametrem, który używa parametru typu, który nie jest ograniczony do typu referencyjnego.</span><span class="sxs-lookup"><span data-stu-id="73dd8-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>  
  
 <span data-ttu-id="73dd8-104">Należy zawsze podać wartość domyślną dla każdego opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="73dd8-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="73dd8-105">Jeśli parametr jest typu referencyjnego, wartość opcjonalna musi być `Nothing` , która jest prawidłową wartością dla dowolnego typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="73dd8-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="73dd8-106">Jeśli jednak parametr ma typ wartości, ten typ musi być typem danych podstawowych wstępnie zdefiniowanym przez Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="73dd8-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="73dd8-107">Wynika to z faktu, że złożony typ wartości, taki jak struktura zdefiniowana przez użytkownika, nie ma prawidłowej wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="73dd8-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>  
  
 <span data-ttu-id="73dd8-108">W przypadku użycia parametru typu dla parametru opcjonalnego należy zagwarantować, że jest typem referencyjnym, aby uniknąć możliwości typu wartości bez prawidłowej wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="73dd8-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="73dd8-109">Oznacza to, że należy ograniczyć parametr typu za pomocą `Class` słowa kluczowego lub nazwy konkretnej klasy.</span><span class="sxs-lookup"><span data-stu-id="73dd8-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>  
  
 <span data-ttu-id="73dd8-110">**Identyfikator błędu:** BC32124</span><span class="sxs-lookup"><span data-stu-id="73dd8-110">**Error ID:** BC32124</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="73dd8-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="73dd8-111">To correct this error</span></span>  
  
- <span data-ttu-id="73dd8-112">Ogranicz parametr typu, aby akceptował tylko typ referencyjny, lub nie używaj go dla parametru opcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="73dd8-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73dd8-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73dd8-113">See also</span></span>

- [<span data-ttu-id="73dd8-114">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="73dd8-114">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="73dd8-115">Lista typów</span><span class="sxs-lookup"><span data-stu-id="73dd8-115">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="73dd8-116">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="73dd8-116">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="73dd8-117">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="73dd8-117">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="73dd8-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="73dd8-118">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="73dd8-119">Nothing</span><span class="sxs-lookup"><span data-stu-id="73dd8-119">Nothing</span></span>](../nothing.md)
