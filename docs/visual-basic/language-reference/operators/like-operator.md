---
title: Like — Operator
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
ms.openlocfilehash: 5db9488bbec716156a3ab464042c0853241a82b1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350944"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="25624-102">Like — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25624-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="25624-103">Porównuje ciąg ze wzorcem.</span><span class="sxs-lookup"><span data-stu-id="25624-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="25624-104">Operator `Like` nie jest obecnie obsługiwany w projektach .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="25624-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="25624-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="25624-105">Syntax</span></span>  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="25624-106">Części</span><span class="sxs-lookup"><span data-stu-id="25624-106">Parts</span></span>  
 `result`  
 <span data-ttu-id="25624-107">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="25624-107">Required.</span></span> <span data-ttu-id="25624-108">Dowolna zmienna `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="25624-108">Any `Boolean` variable.</span></span> <span data-ttu-id="25624-109">Wynik jest `Boolean` wartość wskazującą, czy `string` spełnia `pattern`.</span><span class="sxs-lookup"><span data-stu-id="25624-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="25624-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="25624-110">Required.</span></span> <span data-ttu-id="25624-111">Dowolne wyrażenie `String`.</span><span class="sxs-lookup"><span data-stu-id="25624-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="25624-112">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="25624-112">Required.</span></span> <span data-ttu-id="25624-113">Każde wyrażenie `String` zgodne z konwencjami dopasowania wzorca opisanymi w "uwagi".</span><span class="sxs-lookup"><span data-stu-id="25624-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25624-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25624-114">Remarks</span></span>  
 <span data-ttu-id="25624-115">Jeśli wartość w `string` spełnia wzorzec zawarty w `pattern`, `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="25624-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="25624-116">Jeśli ciąg nie spełnia wzorca, `result` jest `False`.</span><span class="sxs-lookup"><span data-stu-id="25624-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="25624-117">Jeśli oba `string` i `pattern` są pustymi ciągami, wynik jest `True`.</span><span class="sxs-lookup"><span data-stu-id="25624-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="25624-118">Metoda porównania</span><span class="sxs-lookup"><span data-stu-id="25624-118">Comparison Method</span></span>  
 <span data-ttu-id="25624-119">Zachowanie operatora `Like` zależy od [opcji Compare instrukcji](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="25624-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="25624-120">Domyślną metodą porównywania ciągów dla każdego pliku źródłowego jest `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="25624-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="25624-121">Opcje wzorca</span><span class="sxs-lookup"><span data-stu-id="25624-121">Pattern Options</span></span>  
 <span data-ttu-id="25624-122">Wbudowane dopasowania wzorców zapewniają uniwersalne narzędzie do porównywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="25624-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="25624-123">Funkcje dopasowania wzorców umożliwiają dopasowanie każdego znaku w `string` względem określonego znaku, symbolu wieloznacznego, listy znaków lub zakresu znaków.</span><span class="sxs-lookup"><span data-stu-id="25624-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="25624-124">W poniższej tabeli przedstawiono znaki dozwolone w `pattern` i ich zgodność.</span><span class="sxs-lookup"><span data-stu-id="25624-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="25624-125">Znaki w `pattern`</span><span class="sxs-lookup"><span data-stu-id="25624-125">Characters in `pattern`</span></span>|<span data-ttu-id="25624-126">Dopasowania w `string`</span><span class="sxs-lookup"><span data-stu-id="25624-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="25624-127">Dowolny pojedynczy znak</span><span class="sxs-lookup"><span data-stu-id="25624-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="25624-128">Zero lub więcej znaków</span><span class="sxs-lookup"><span data-stu-id="25624-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="25624-129">Dowolna pojedyncza cyfra (0 – 9)</span><span class="sxs-lookup"><span data-stu-id="25624-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="25624-130">Dowolny pojedynczy znak w `charlist`</span><span class="sxs-lookup"><span data-stu-id="25624-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="25624-131">Dowolny pojedynczy znak, który nie znajduje się w `charlist`</span><span class="sxs-lookup"><span data-stu-id="25624-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="25624-132">Listy znaków</span><span class="sxs-lookup"><span data-stu-id="25624-132">Character Lists</span></span>  
 <span data-ttu-id="25624-133">Grupa zawierająca co najmniej jeden znak (`charlist`) ujęta w nawiasy kwadratowe (`[ ]`) może być używana do dopasowania dowolnego pojedynczego znaku w `string` i może zawierać prawie dowolny kod znaków, w tym cyfry.</span><span class="sxs-lookup"><span data-stu-id="25624-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="25624-134">Wykrzyknik (`!`) na początku `charlist` oznacza, że jest to dopasowanie, jeśli dowolny znak z wyjątkiem znaków w `charlist` zostanie znaleziony w `string`.</span><span class="sxs-lookup"><span data-stu-id="25624-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="25624-135">Gdy używany jest nawiasy klamrowe, wykrzyknik dopasowuje się do samego siebie.</span><span class="sxs-lookup"><span data-stu-id="25624-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="25624-136">Znaki specjalne</span><span class="sxs-lookup"><span data-stu-id="25624-136">Special Characters</span></span>  
 <span data-ttu-id="25624-137">Aby dopasować znaki specjalne do lewego nawiasu (`[`), znaku zapytania (`?`), znaku numeru (`#`) i gwiazdki (`*`), umieść je w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="25624-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="25624-138">Nie można użyć prawego nawiasu (`]`) w grupie, aby dopasować się do siebie, ale można go użyć poza grupą jako pojedynczym znakiem.</span><span class="sxs-lookup"><span data-stu-id="25624-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="25624-139">`[]` sekwencji znaków jest traktowany jako ciąg o zerowej długości (`""`).</span><span class="sxs-lookup"><span data-stu-id="25624-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="25624-140">Jednak nie może być częścią listy znaków ujętej w nawiasy klamrowe.</span><span class="sxs-lookup"><span data-stu-id="25624-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="25624-141">Jeśli chcesz sprawdzić, czy pozycja w `string` zawiera jedną z grup znaków lub nie ma żadnego znaku, możesz użyć `Like` dwa razy.</span><span class="sxs-lookup"><span data-stu-id="25624-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="25624-142">Aby zapoznać się z przykładem, zobacz [jak: dopasowywanie ciągu do wzorca](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="25624-142">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="25624-143">Zakresy znaków</span><span class="sxs-lookup"><span data-stu-id="25624-143">Character Ranges</span></span>  
 <span data-ttu-id="25624-144">Używając łącznika (`–`), aby oddzielić dolną i górną granicę zakresu, `charlist` może określić zakres znaków.</span><span class="sxs-lookup"><span data-stu-id="25624-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="25624-145">Na przykład `[A–Z]` powoduje dopasowanie, Jeśli odpowiednia pozycja znaku w `string` zawiera dowolny znak w `A`zakres,`Z`i `[!H–L]` powoduje dopasowanie, Jeśli odpowiednia pozycja znaku zawiera dowolny znak spoza zakresu `H`–`L`.</span><span class="sxs-lookup"><span data-stu-id="25624-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="25624-146">Po określeniu zakresu znaków muszą one znajdować się w rosnącej kolejności sortowania, czyli od najniższego do najwyższego.</span><span class="sxs-lookup"><span data-stu-id="25624-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="25624-147">W tym celu `[A–Z]` jest prawidłowym wzorcem, ale `[Z–A]` nie jest.</span><span class="sxs-lookup"><span data-stu-id="25624-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="25624-148">Wiele zakresów znaków</span><span class="sxs-lookup"><span data-stu-id="25624-148">Multiple Character Ranges</span></span>  
 <span data-ttu-id="25624-149">Aby określić wiele zakresów dla tej samej pozycji znaku, umieść je w tych samych nawiasach bez ograniczników.</span><span class="sxs-lookup"><span data-stu-id="25624-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="25624-150">Na przykład `[A–CX–Z]` powoduje dopasowanie, Jeśli odpowiednia pozycja znaku w `string` zawiera dowolny znak w zakresie `A``C` lub zakres `X`—`Z`.</span><span class="sxs-lookup"><span data-stu-id="25624-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="25624-151">Użycie łącznika</span><span class="sxs-lookup"><span data-stu-id="25624-151">Usage of the Hyphen</span></span>  
 <span data-ttu-id="25624-152">Łącznik (`–`) może pojawić się na początku (po wykrzykniku, jeśli istnieje) lub na końcu `charlist`, aby dopasować sam siebie.</span><span class="sxs-lookup"><span data-stu-id="25624-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="25624-153">W każdej innej lokalizacji łącznik identyfikuje zakres znaków, które są rozdzielane znakami po obu stronach łącznika.</span><span class="sxs-lookup"><span data-stu-id="25624-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="25624-154">Kolejność sortowania</span><span class="sxs-lookup"><span data-stu-id="25624-154">Collating Sequence</span></span>  
 <span data-ttu-id="25624-155">Znaczenie określonego zakresu zależy od kolejności znaków w czasie wykonywania określony przez `Option Compare` i ustawienia regionalne systemu, w którym uruchomiono kod.</span><span class="sxs-lookup"><span data-stu-id="25624-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="25624-156">W przypadku `Option Compare Binary`zakres `[A–E]` pasuje do `A`, `B`, `C`, `D`i `E`.</span><span class="sxs-lookup"><span data-stu-id="25624-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="25624-157">W `Option Compare Text``[A–E]` dopasowuje `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`i `e`.</span><span class="sxs-lookup"><span data-stu-id="25624-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="25624-158">Zakres nie pasuje do `Ê` lub `ê`, ponieważ znaki akcentowane są sortowane po nieakcentowane znaki w kolejności sortowania.</span><span class="sxs-lookup"><span data-stu-id="25624-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="25624-159">Znaki odgrafu</span><span class="sxs-lookup"><span data-stu-id="25624-159">Digraph Characters</span></span>  
 <span data-ttu-id="25624-160">W niektórych językach istnieją znaki alfabetyczne, które reprezentują dwa oddzielne znaki.</span><span class="sxs-lookup"><span data-stu-id="25624-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="25624-161">Na przykład kilka języków używa znaku `æ`, aby reprezentować znaki `a` i `e` pojawiają się razem.</span><span class="sxs-lookup"><span data-stu-id="25624-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="25624-162">Operator `Like` rozpoznaje, że pojedynczy znak dwugrafu i dwa poszczególne znaki są równoważne.</span><span class="sxs-lookup"><span data-stu-id="25624-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="25624-163">Gdy język, który używa znaku oddzielenia jest określony w ustawieniach ustawień regionalnych systemu, wystąpienie pojedynczego znaku w obu `pattern` lub `string` dopasowuje odpowiednik dwuznakowej sekwencji w innym ciągu.</span><span class="sxs-lookup"><span data-stu-id="25624-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="25624-164">Analogicznie, znak podgrafu w `pattern` w nawiasach (samo, na liście lub w zakresie) jest zgodny z równoważną dwuznakową sekwencją w `string`.</span><span class="sxs-lookup"><span data-stu-id="25624-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="25624-165">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="25624-165">Overloading</span></span>  
 <span data-ttu-id="25624-166">Operator `Like` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="25624-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="25624-167">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="25624-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="25624-168">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="25624-168">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="25624-169">Przykład</span><span class="sxs-lookup"><span data-stu-id="25624-169">Example</span></span>  
 <span data-ttu-id="25624-170">W tym przykładzie używa operatora `Like` do porównywania ciągów z różnymi wzorcami.</span><span class="sxs-lookup"><span data-stu-id="25624-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="25624-171">Wyniki przechodzą do zmiennej `Boolean`, wskazując, czy każdy ciąg spełnia wzorzec.</span><span class="sxs-lookup"><span data-stu-id="25624-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="25624-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25624-172">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="25624-173">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="25624-173">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="25624-174">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25624-174">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="25624-175">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="25624-175">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="25624-176">Option Compare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="25624-176">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="25624-177">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="25624-177">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="25624-178">Instrukcje: dopasowywanie ciągu do wzorca</span><span class="sxs-lookup"><span data-stu-id="25624-178">How to: Match a String against a Pattern</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
