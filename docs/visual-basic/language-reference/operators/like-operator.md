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
ms.openlocfilehash: a9c672a397510c69c9ee67358689feff80d8831a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605423"
---
# <a name="like-operator-visual-basic"></a>Like — Operator (Visual Basic)
Porównuje ciąg do wzorca.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Wszelkie `Boolean` zmiennej. Wynik jest `Boolean` wartość wskazującą, czy `string` spełnia `pattern`.  
  
 `string`  
 Wymagana. Wszelkie `String` wyrażenia.  
  
 `pattern`  
 Wymagana. Wszelkie `String` wyrażeń zgodnych z konwencjami dopasowywanie do wzorca opisanego w "Uwagi".  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość w `string` spełnia wzorzec zawarte w `pattern`, `result` jest `True`. Jeśli ciąg nie spełnia wzorzec, `result` jest `False`. Jeśli oba `string` i `pattern` są puste ciągi, wynikiem jest `True`.  
  
## <a name="comparison-method"></a>Porównanie — metoda  
 Zachowanie `Like` zależy od operatora [instrukcji porównanie opcji](../../../visual-basic/language-reference/statements/option-compare-statement.md). Domyślną metodę porównywania ciągów dla każdego pliku źródłowego jest `Option Compare Binary`.  
  
## <a name="pattern-options"></a>Opcje wzorca  
 Dopasowanie wzorca wbudowanych zapewnia elastyczne narzędzia do porównywania ciągów znaków. Dopasowywanie do wzorca funkcje umożliwiają dopasowanie każdego znaku w `string` przed określony znak symbolu wieloznacznego, listę znaku albo zakresu znaków. W poniższej tabeli przedstawiono znaków dozwolonych w `pattern` i są zgodne.  
  
|Znaków `pattern`|Dopasowania w `string`|  
|-----------------------------|-------------------------|  
|`?`|Dowolny pojedynczy znak|  
|`*`|Zero lub więcej znaków|  
|`#`|Dowolna cyfra (0 – 9)|  
|`[charlist]`|Dowolny pojedynczy znak `charlist`|  
|`[!charlist]`|Dowolny pojedynczy znak nie `charlist`|  
  
## <a name="character-lists"></a>Znak list  
 Grupy co najmniej jeden znak (`charlist`) w nawiasach (`[ ]`) może służyć do dopasowuje dowolny pojedynczy znak w `string` i może zawierać kod prawie każdego znaku, w tym cyfr.  
  
 Wykrzyknika (`!`) na początku `charlist` oznacza, że zgodność ma miejsce, jeśli dowolny znak z wyjątkiem znaków `charlist` znajduje się w `string`. W przypadku poza nawiasy wykrzyknika wykrzyknikami.  
  
## <a name="special-characters"></a>Znaki specjalne  
 Aby dopasować lewego nawiasu znaki specjalne (`[`), znak zapytania (`?`), znak (`#`) i gwiazdki (`*`), ujmij ją w nawiasach kwadratowych. Prawy nawias (`]`) nie można używać wewnątrz grupy bezpośrednio, ale może być używana poza grupą jako znak indywidualnych.  
  
 Sekwencja znaków `[]` jest traktowana jako ciąg o zerowej długości (`""`). Nie można go jednak częścią listy znaków w nawiasach. Jeśli chcesz sprawdzić, czy pozycja w `string` zawiera jeden grupy znaków lub nie znak na pozycji wszystkich, można użyć `Like` dwa razy. Na przykład zobacz [porady: dopasowywanie ciągu do wzorca](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Zakres znaków  
 Za pomocą łącznika (`–`) do oddzielania dolną i górną granicą zakresu, `charlist` można określić zakres znaków. Na przykład `[A–Z]` wynikiem dopasowania, jeśli odpowiedni znak umieść w `string` zawiera dowolny znak z zakresu `A`—`Z`, i `[!H–L]` wynikiem dopasowania, jeśli pozycja odpowiedni znak zawiera dowolny znak spoza zakresu `H`—`L`.  
  
 Podczas określania zakresu znaków muszą występować w kolejności rosnącej, czyli z najniższą najwyższe. W związku z tym `[A–Z]` jest prawidłowy wzorzec, ale `[Z–A]` nie jest.  
  
### <a name="multiple-character-ranges"></a>Zakresów wielu znaków  
 Aby określić wiele zakresów dla tej samej pozycji znaku, umieść je w nawiasach tego samego bez ograniczników. Na przykład `[A–CX–Z]` wynikiem dopasowania, jeśli odpowiedni znak umieść w `string` zawiera dowolny znak, albo z zakresu `A`—`C` lub zakres `X`—`Z`.  
  
### <a name="usage-of-the-hyphen"></a>Użycie łącznik  
 Łącznik (`–`) mogą być wyświetlane na początku (po wykrzyknik, jeśli istnieje) lub na końcu `charlist` bezpośrednio. W dowolnym miejscu łącznik określa zakres znaków rozdzielone znaki po obu stronach łącznik.  
  
## <a name="collating-sequence"></a>Kolejność sortowania  
 Znaczenie określony zakres jest zależna od znak kolejności w czasie wykonywania na podstawie `Option``Compare` i ustawień regionalnych systemu kod działa na. Z `Option``Compare``Binary`, zakres `[A–E]` odpowiada `A`, `B`, `C`, `D`, i `E`. Z `Option``Compare``Text`, `[A–E]` odpowiada `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, i `e`. Zakres nie pasuje `Ê` lub `ê` ponieważ znaki akcentowane collate po formami znaki w porządku sortowania.  
  
## <a name="digraph-characters"></a>Dwuznaku znaków  
 W przypadku niektórych języków istnieją znaki alfabetyczne, które reprezentują odrębne znaki. Na przykład użyć znaku w różnych językach `æ` reprezentujących znaki `a` i `e` gdy pojawią się one ze sobą. `Like` Operator rozpoznaje znak pojedynczego dwuznaku i dwa znaki są równoważne.  
  
 Gdy w języku korzystającym znak dwuznaku jest określona w ustawieniach regionalnych systemu, wystąpienie dwuznaku jednego znaku w albo `pattern` lub `string` odpowiada równoważne sekwencji dwóch znaków w innym ciągu. Podobnie, znaku dwuznaku w `pattern` w nawiasach (przez siebie, na liście lub w zakresie) jest zgodna równoważne sekwencję dwóch znaków w `string`.  
  
## <a name="overloading"></a>Przeciążenie  
 `Like` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Like` operator należy porównywać ciągi do różnych wzorców. Wyniki są kierowane do `Boolean` zmiennej wskazującą, czy każdy ciąg spełnia wzorzec.  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [Operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Option Compare, instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Instrukcje: dopasowywanie ciągu do wzorca](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
