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
ms.openlocfilehash: c5b26bd1d3ebae5136718833c124e3c6e575e9b7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44198169"
---
# <a name="like-operator-visual-basic"></a>Like — Operator (Visual Basic)
Porównuje ciąg do wzorca.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagane. Wszelkie `Boolean` zmiennej. Wynik jest `Boolean` wartość wskazującą czy `string` spełnia `pattern`.  
  
 `string`  
 Wymagane. Wszelkie `String` wyrażenia.  
  
 `pattern`  
 Wymagane. Wszelkie `String` wyrażeń zgodnych z konwencjami dopasowania do wzorca opisanego w "Uwagi".  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość w `string` spełnia wzorzec zawarte w `pattern`, `result` jest `True`. Jeśli ciąg nie spełnia wzorzec, `result` jest `False`. Jeśli oba `string` i `pattern` są puste ciągi, wynik jest `True`.  
  
## <a name="comparison-method"></a>Metody porównania  
 Zachowanie `Like` zależy od operatora [instrukcji porównanie opcji](../../../visual-basic/language-reference/statements/option-compare-statement.md). Domyślną metodę porównywania ciągów dla każdego pliku źródłowego jest `Option Compare Binary`.  
  
## <a name="pattern-options"></a>Opcje wzorzec  
 Dopasowanie wzorca wbudowanych zapewnia wszechstronne narzędzie do porównywania ciągów znaków. Dopasowanie wzorca funkcje umożliwiają pasuje do każdego znaku w `string` względem określonego znaku, symbolu wieloznacznego, lista znak lub zakres znaków. W poniższej tabeli przedstawiono znaki są dozwolone w `pattern` i są zgodne.  
  
|Znaków `pattern`|Dopasowania w `string`|  
|-----------------------------|-------------------------|  
|`?`|Dowolny pojedynczy znak|  
|`*`|Zero lub więcej znaków|  
|`#`|Dowolna cyfra (0 – 9)|  
|`[charlist]`|Dowolny pojedynczy znak `charlist`|  
|`[!charlist]`|Dowolny pojedynczy znak, nie w `charlist`|  
  
## <a name="character-lists"></a>Znak list  
 Grupy z jednego lub więcej znaków (`charlist`) w nawiasach (`[ ]`) może służyć do Dopasuj jeden dowolny znak w `string` i może zawierać niemal dowolnego kodu znaku, w tym cyfr.  
  
 Znak wykrzyknika (`!`) na początku `charlist` oznacza, że dopasowanie jest wykonywane, gdy dowolny znak z wyjątkiem znaków `charlist` znajduje się w `string`. W przypadku użycia poza nawiasem kwadratowym, wykrzyknik wykrzyknikami.  
  
## <a name="special-characters"></a>Znaki specjalne  
 Aby dopasować lewy nawias znaków specjalnych (`[`), znaku zapytania (`?`), krzyżyk (`#`), a gwiazdka (`*`), Otaczaj ich nawiasami kwadratowymi. Prawy nawias kwadratowy (`]`) nie można użyć w obrębie grupy do dopasowania, ale mogą być używane na zewnątrz grupy jako pojedynczy znak.  
  
 Sekwencja znaków `[]` jest traktowana jako ciąg o zerowej długości (`""`). Jednak nie może być częścią listy znaków, ujęte w nawiasy kwadratowe. Jeśli chcesz sprawdzić, czy pozycja w `string` zawiera jeden grupy znaków lub żaden znak w ogóle, można użyć `Like` dwa razy. Aby uzyskać przykład, zobacz [porady: dopasowywanie ciągu do wzorca](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Zakres znaków  
 Za pomocą łącznika (`–`) do oddzielenia dolną i górną granicą zakresu, `charlist` można określić zakres znaków. Na przykład `[A–Z]` skutkuje dopasowania, jeśli znak odpowiedniej pozycji w `string` zawierającej dowolny znak w zakresie `A`—`Z`, i `[!H–L]` skutkuje dopasowania, jeśli pozycji odpowiedniego znaku zawierającej dowolny znak spoza zakresu `H`—`L`.  
  
 Po określeniu zakresu znaków, musi znajdować się w kolejności rosnącej, oznacza to, z od najmniejszych do największych. W związku z tym `[A–Z]` jest prawidłowy wzorzec, ale `[Z–A]` nie jest.  
  
### <a name="multiple-character-ranges"></a>Wiele zakresów znaków  
 Aby określić wiele zakresów dla tej samej pozycji znaku, umieść je w ramach tej samej nawiasów bez ograniczników. Na przykład `[A–CX–Z]` skutkuje dopasowania, jeśli znak odpowiedniej pozycji w `string` zawierającej dowolny znak w zakresie albo `A`—`C` lub zakres `X`—`Z`.  
  
### <a name="usage-of-the-hyphen"></a>Użycie łącznika  
 Znak minusa (`–`) może znajdować się na początku (po wykrzyknik, jeśli istnieje) lub na końcu `charlist` do dopasowania. W dowolnym miejscu łącznik określa zakres znaków rozdzielone znaki po obu stronach łącznik.  
  
## <a name="collating-sequence"></a>Kolejność sortowania  
 Znaczenie określony zakres jest zależna od znaków, kolejności w czasie wykonywania, zgodnie z ustaleniami `Option Compare` i ustawień regionalnych systemu kod działa na. Za pomocą `Option Compare Binary`, zakres `[A–E]` odpowiada `A`, `B`, `C`, `D`, i `E`. Za pomocą `Option Compare Text`, `[A–E]` odpowiada `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, i `e`. Zakres nie jest zgodny `Ê` lub `ê` ponieważ znaki akcentowane sortowane po nieakcentowane znaki w porządku sortowania.  
  
## <a name="digraph-characters"></a>Dwuznak znaków  
 W przypadku niektórych języków istnieją, które reprezentują dwa oddzielne znaki alfabetu. Na przykład użyć znaku w kilku językach `æ` do reprezentowania znaków `a` i `e` kiedy pojawiają się razem. `Like` Operator rozpoznaje dwuznak pojedynczy znak i dwóch pojedynczych znaków są równoważne.  
  
 Gdy języka, który używa znaku dwuznak jest określony w ustawieniach regionalnych systemu, wystąpienia tego znaku pojedynczego dwuznak albo `pattern` lub `string` pasuje do równoważne sekwencji dwuznakowy w innym ciągu. Podobnie, znak dwuznak w `pattern` ujęte w nawiasy kwadratowe (samodzielnie, na liście lub w zakresie) dopasowuje równoważne sekwencję dwóch znaków w `string`.  
  
## <a name="overloading"></a>Przeciążenie  
 `Like` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Like` operatora porównania ciągów do różnych wzorców. Wyniki są przekazywane do `Boolean` wskazującą, czy każdy ciąg spełnia wzorzec zmiennej.  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [Operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Option Compare, instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Instrukcje: dopasowywanie ciągu do wzorca](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
