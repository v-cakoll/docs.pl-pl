---
title: Static (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: f1031fe005a2fc264b50116b8ea3311dc7065dbc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647641"
---
# <a name="static-visual-basic"></a><span data-ttu-id="0000f-102">Static (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0000f-102">Static (Visual Basic)</span></span>
<span data-ttu-id="0000f-103">Określa co najmniej jeden zadeklarowany zmienne lokalne są nadal istnieć i zachowywać swoje ostatnie wartości po zakończeniu procedury, w którym są one zgłoszone.</span><span class="sxs-lookup"><span data-stu-id="0000f-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0000f-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0000f-104">Remarks</span></span>  
 <span data-ttu-id="0000f-105">Normalnie zmienna lokalna w procedurach przestanie istnieć tak szybko, jak zatrzymuje procedury.</span><span class="sxs-lookup"><span data-stu-id="0000f-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="0000f-106">Zmienna statyczna nadal istnieje i zachowuje swoją wartość najbardziej aktualne.</span><span class="sxs-lookup"><span data-stu-id="0000f-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="0000f-107">Przy następnym kod wywołuje procedurę, zmienna nie są ponownie inicjowane i nadal utrzymuje najpóźniejszą wartość przypisana do niego.</span><span class="sxs-lookup"><span data-stu-id="0000f-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="0000f-108">Zmienna statyczna w dalszym ciągu dla okresu istnienia klasę lub moduł, który jest zdefiniowany w istnieje.</span><span class="sxs-lookup"><span data-stu-id="0000f-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="0000f-109">reguły</span><span class="sxs-lookup"><span data-stu-id="0000f-109">Rules</span></span>  
  
- <span data-ttu-id="0000f-110">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="0000f-110">**Declaration Context.**</span></span> <span data-ttu-id="0000f-111">Możesz użyć `Static` tylko w zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="0000f-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="0000f-112">Oznacza to, że kontekst deklaracji `Static` zmienna musi być procedurą lub blokiem w procedurze, a nie może być plikiem źródłowym, przestrzeń nazw, klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="0000f-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="0000f-113">Nie można użyć `Static` wewnątrz procedury struktury.</span><span class="sxs-lookup"><span data-stu-id="0000f-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
- <span data-ttu-id="0000f-114">Typy danych `Static` nie można wywnioskować zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="0000f-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="0000f-115">Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="0000f-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
- <span data-ttu-id="0000f-116">**Modyfikatory połączone.**</span><span class="sxs-lookup"><span data-stu-id="0000f-116">**Combined Modifiers.**</span></span> <span data-ttu-id="0000f-117">Nie można określić `Static` wraz z `ReadOnly`, `Shadows`, lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="0000f-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="0000f-118">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="0000f-118">Behavior</span></span>  
 <span data-ttu-id="0000f-119">Kiedy Deklarujesz zmienną statyczną w `Shared` procedura, tylko jedna kopia zmienna statyczna jest dostępna dla całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0000f-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="0000f-120">Należy wywołać `Shared` nazwę procedury przy użyciu klasy, nie zmienną, która wskazuje na wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="0000f-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="0000f-121">Kiedy Deklarujesz zmienną statyczną w procedurze, która nie jest `Shared`tylko jedną kopię zmiennej jest dostępna dla każdego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="0000f-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="0000f-122">Wywołujesz procedurę nieudostępnione, używając zmiennej, który wskazuje na konkretne wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="0000f-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0000f-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="0000f-123">Example</span></span>  
 <span data-ttu-id="0000f-124">W poniższym przykładzie pokazano użycie `Static`.</span><span class="sxs-lookup"><span data-stu-id="0000f-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 <span data-ttu-id="0000f-125">`Static` Zmiennej `totalSales` jest inicjowana wartością 0 tylko jeden raz.</span><span class="sxs-lookup"><span data-stu-id="0000f-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="0000f-126">Za każdym razem, należy wprowadzić `updateSales`, `totalSales` środki, nieopłacone najbardziej aktualną wartość, która została obliczona dla niego.</span><span class="sxs-lookup"><span data-stu-id="0000f-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="0000f-127">`Static` Modyfikatora można używać w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="0000f-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="0000f-128">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0000f-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="0000f-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0000f-129">See also</span></span>

- [<span data-ttu-id="0000f-130">Shadows</span><span class="sxs-lookup"><span data-stu-id="0000f-130">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="0000f-131">Shared</span><span class="sxs-lookup"><span data-stu-id="0000f-131">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="0000f-132">Okres istnienia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0000f-132">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="0000f-133">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="0000f-133">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="0000f-134">Struktury</span><span class="sxs-lookup"><span data-stu-id="0000f-134">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="0000f-135">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="0000f-135">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="0000f-136">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="0000f-136">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
