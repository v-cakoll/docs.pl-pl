---
title: Like — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: 38e56b8c0ec6bab89052ee42a2cd9c24053c658e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835703"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="5fb2d-102">Like — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fb2d-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="5fb2d-103">Porównuje ciąg do wzorca.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="5fb2d-104">`Like` Operator nie jest obecnie obsługiwane w projektach .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="5fb2d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5fb2d-105">Syntax</span></span>  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="5fb2d-106">Części</span><span class="sxs-lookup"><span data-stu-id="5fb2d-106">Parts</span></span>  
 `result`  
 <span data-ttu-id="5fb2d-107">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-107">Required.</span></span> <span data-ttu-id="5fb2d-108">Wszelkie `Boolean` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-108">Any `Boolean` variable.</span></span> <span data-ttu-id="5fb2d-109">Wynik jest `Boolean` wartość wskazującą czy `string` spełnia `pattern`.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="5fb2d-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-110">Required.</span></span> <span data-ttu-id="5fb2d-111">Wszelkie `String` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="5fb2d-112">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-112">Required.</span></span> <span data-ttu-id="5fb2d-113">Wszelkie `String` wyrażeń zgodnych z konwencjami dopasowania do wzorca opisanego w "Uwagi".</span><span class="sxs-lookup"><span data-stu-id="5fb2d-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fb2d-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5fb2d-114">Remarks</span></span>  
 <span data-ttu-id="5fb2d-115">Jeśli wartość w `string` spełnia wzorzec zawarte w `pattern`, `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="5fb2d-116">Jeśli ciąg nie spełnia wzorzec, `result` jest `False`.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="5fb2d-117">Jeśli oba `string` i `pattern` są puste ciągi, wynik jest `True`.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="5fb2d-118">Metody porównania</span><span class="sxs-lookup"><span data-stu-id="5fb2d-118">Comparison Method</span></span>  
 <span data-ttu-id="5fb2d-119">Zachowanie `Like` zależy od operatora [instrukcji porównanie opcji](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5fb2d-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="5fb2d-120">Domyślną metodę porównywania ciągów dla każdego pliku źródłowego jest `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="5fb2d-121">Opcje wzorzec</span><span class="sxs-lookup"><span data-stu-id="5fb2d-121">Pattern Options</span></span>  
 <span data-ttu-id="5fb2d-122">Dopasowanie wzorca wbudowanych zapewnia wszechstronne narzędzie do porównywania ciągów znaków.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="5fb2d-123">Dopasowanie wzorca funkcje umożliwiają pasuje do każdego znaku w `string` względem określonego znaku, symbolu wieloznacznego, lista znak lub zakres znaków.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="5fb2d-124">W poniższej tabeli przedstawiono znaki są dozwolone w `pattern` i są zgodne.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="5fb2d-125">Znaków `pattern`</span><span class="sxs-lookup"><span data-stu-id="5fb2d-125">Characters in `pattern`</span></span>|<span data-ttu-id="5fb2d-126">Dopasowania w `string`</span><span class="sxs-lookup"><span data-stu-id="5fb2d-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="5fb2d-127">Dowolny pojedynczy znak</span><span class="sxs-lookup"><span data-stu-id="5fb2d-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="5fb2d-128">Zero lub więcej znaków</span><span class="sxs-lookup"><span data-stu-id="5fb2d-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="5fb2d-129">Dowolna cyfra (0 – 9)</span><span class="sxs-lookup"><span data-stu-id="5fb2d-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="5fb2d-130">Dowolny pojedynczy znak `charlist`</span><span class="sxs-lookup"><span data-stu-id="5fb2d-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="5fb2d-131">Dowolny pojedynczy znak, nie w `charlist`</span><span class="sxs-lookup"><span data-stu-id="5fb2d-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="5fb2d-132">Znak list</span><span class="sxs-lookup"><span data-stu-id="5fb2d-132">Character Lists</span></span>  
 <span data-ttu-id="5fb2d-133">Grupy z jednego lub więcej znaków (`charlist`) w nawiasach (`[ ]`) może służyć do Dopasuj jeden dowolny znak w `string` i może zawierać niemal dowolnego kodu znaku, w tym cyfr.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="5fb2d-134">Znak wykrzyknika (`!`) na początku `charlist` oznacza, że dopasowanie jest wykonywane, gdy dowolny znak z wyjątkiem znaków `charlist` znajduje się w `string`.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="5fb2d-135">W przypadku użycia poza nawiasem kwadratowym, wykrzyknik wykrzyknikami.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="5fb2d-136">Znaki specjalne</span><span class="sxs-lookup"><span data-stu-id="5fb2d-136">Special Characters</span></span>  
 <span data-ttu-id="5fb2d-137">Aby dopasować lewy nawias znaków specjalnych (`[`), znaku zapytania (`?`), krzyżyk (`#`), a gwiazdka (`*`), Otaczaj ich nawiasami kwadratowymi.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="5fb2d-138">Prawy nawias kwadratowy (`]`) nie można użyć w obrębie grupy do dopasowania, ale mogą być używane na zewnątrz grupy jako pojedynczy znak.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="5fb2d-139">Sekwencja znaków `[]` jest traktowana jako ciąg o zerowej długości (`""`).</span><span class="sxs-lookup"><span data-stu-id="5fb2d-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="5fb2d-140">Jednak nie może być częścią listy znaków, ujęte w nawiasy kwadratowe.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="5fb2d-141">Jeśli chcesz sprawdzić, czy pozycja w `string` zawiera jeden grupy znaków lub żaden znak w ogóle, można użyć `Like` dwa razy.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="5fb2d-142">Aby uzyskać przykład, zobacz [jak: Dopasowanie ciągu do wzorca](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="5fb2d-142">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="5fb2d-143">Zakres znaków</span><span class="sxs-lookup"><span data-stu-id="5fb2d-143">Character Ranges</span></span>  
 <span data-ttu-id="5fb2d-144">Za pomocą łącznika (`–`) do oddzielenia dolną i górną granicą zakresu, `charlist` można określić zakres znaków.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="5fb2d-145">Na przykład `[A–Z]` skutkuje dopasowania, jeśli znak odpowiedniej pozycji w `string` zawierającej dowolny znak w zakresie `A`—`Z`, i `[!H–L]` skutkuje dopasowania, jeśli pozycji odpowiedniego znaku zawierającej dowolny znak spoza zakresu `H`—`L`.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="5fb2d-146">Po określeniu zakresu znaków, musi znajdować się w kolejności rosnącej, oznacza to, z od najmniejszych do największych.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="5fb2d-147">W związku z tym `[A–Z]` jest prawidłowy wzorzec, ale `[Z–A]` nie jest.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="5fb2d-148">Multiple Character Ranges</span><span class="sxs-lookup"><span data-stu-id="5fb2d-148">Multiple Character Ranges</span></span>  
 <span data-ttu-id="5fb2d-149">Aby określić wiele zakresów dla tej samej pozycji znaku, umieść je w ramach tej samej nawiasów bez ograniczników.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="5fb2d-150">Na przykład `[A–CX–Z]` skutkuje dopasowania, jeśli znak odpowiedniej pozycji w `string` zawierającej dowolny znak w zakresie albo `A`—`C` lub zakres `X`—`Z`.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="5fb2d-151">Użycie łącznika</span><span class="sxs-lookup"><span data-stu-id="5fb2d-151">Usage of the Hyphen</span></span>  
 <span data-ttu-id="5fb2d-152">Znak minusa (`–`) może znajdować się na początku (po wykrzyknik, jeśli istnieje) lub na końcu `charlist` do dopasowania.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="5fb2d-153">W dowolnym miejscu łącznik określa zakres znaków rozdzielone znaki po obu stronach łącznik.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="5fb2d-154">Kolejność sortowania</span><span class="sxs-lookup"><span data-stu-id="5fb2d-154">Collating Sequence</span></span>  
 <span data-ttu-id="5fb2d-155">Znaczenie określony zakres jest zależna od znaków, kolejności w czasie wykonywania, zgodnie z ustaleniami `Option Compare` i ustawień regionalnych systemu kod działa na.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="5fb2d-156">Za pomocą `Option Compare Binary`, zakres `[A–E]` odpowiada `A`, `B`, `C`, `D`, i `E`.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="5fb2d-157">Za pomocą `Option Compare Text`, `[A–E]` odpowiada `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, i `e`.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="5fb2d-158">Zakres nie jest zgodny `Ê` lub `ê` ponieważ znaki akcentowane sortowane po nieakcentowane znaki w porządku sortowania.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="5fb2d-159">Dwuznak znaków</span><span class="sxs-lookup"><span data-stu-id="5fb2d-159">Digraph Characters</span></span>  
 <span data-ttu-id="5fb2d-160">W przypadku niektórych języków istnieją, które reprezentują dwa oddzielne znaki alfabetu.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="5fb2d-161">Na przykład użyć znaku w kilku językach `æ` do reprezentowania znaków `a` i `e` kiedy pojawiają się razem.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="5fb2d-162">`Like` Operator rozpoznaje dwuznak pojedynczy znak i dwóch pojedynczych znaków są równoważne.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="5fb2d-163">Gdy języka, który używa znaku dwuznak jest określony w ustawieniach regionalnych systemu, wystąpienia tego znaku pojedynczego dwuznak albo `pattern` lub `string` pasuje do równoważne sekwencji dwuznakowy w innym ciągu.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="5fb2d-164">Podobnie, znak dwuznak w `pattern` ujęte w nawiasy kwadratowe (samodzielnie, na liście lub w zakresie) dopasowuje równoważne sekwencję dwóch znaków w `string`.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="5fb2d-165">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="5fb2d-165">Overloading</span></span>  
 <span data-ttu-id="5fb2d-166">`Like` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5fb2d-167">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="5fb2d-168">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5fb2d-168">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fb2d-169">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fb2d-169">Example</span></span>  
 <span data-ttu-id="5fb2d-170">W tym przykładzie użyto `Like` operatora porównania ciągów do różnych wzorców.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="5fb2d-171">Wyniki są przekazywane do `Boolean` wskazującą, czy każdy ciąg spełnia wzorzec zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5fb2d-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="5fb2d-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fb2d-172">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="5fb2d-173">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="5fb2d-173">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="5fb2d-174">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fb2d-174">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="5fb2d-175">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="5fb2d-175">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="5fb2d-176">Option Compare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5fb2d-176">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="5fb2d-177">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="5fb2d-177">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="5fb2d-178">Instrukcje: Dopasowanie ciągu do wzorca</span><span class="sxs-lookup"><span data-stu-id="5fb2d-178">How to: Match a String against a Pattern</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
