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
ms.openlocfilehash: 4279d90c74c80403146448a8ba5a6051ec9d12f6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401562"
---
# <a name="like-operator-visual-basic"></a>Like — Operator (Visual Basic)
Porównuje ciąg ze wzorcem.  

> [!IMPORTANT]
> `Like`Operator nie jest obecnie obsługiwany w projektach .NET Core i .NET Standard.

## <a name="syntax"></a>Składnia  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Dowolna `Boolean` zmienna. Wynik jest `Boolean` wartością wskazującą, czy jest to element `string` spełniający kryteria `pattern` .  
  
 `string`  
 Wymagany. Dowolne `String` wyrażenie.  
  
 `pattern`  
 Wymagany. Każde `String` wyrażenie zgodne z konwencjami dopasowania wzorca opisanymi w "uwagi".  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość w jest równa `string` wzorzec zawarte w `pattern` , `result` to `True` . Jeśli ciąg nie spełnia wzorca, `result` jest `False` . Jeśli oba `string` i `pattern` są pustymi ciągami, wynik jest `True` .  
  
## <a name="comparison-method"></a>Metoda porównania  
 Zachowanie `Like` operatora zależy od [opcji Compare instrukcji](../statements/option-compare-statement.md). Domyślną metodą porównywania ciągów dla każdego pliku źródłowego jest `Option Compare Binary` .  
  
## <a name="pattern-options"></a>Opcje wzorca  
 Wbudowane dopasowania wzorców zapewniają uniwersalne narzędzie do porównywania ciągów. Funkcje dopasowania wzorców umożliwiają dopasowanie każdego znaku w `string` odniesieniu do określonego znaku, symbolu wieloznacznego, listy znaków lub zakresu znaków. W poniższej tabeli przedstawiono znaki dozwolone w `pattern` i ich zgodność.  
  
|Znaki w`pattern`|Pasuje do`string`|  
|-----------------------------|-------------------------|  
|`?`|Dowolny pojedynczy znak|  
|`*`|Zero lub więcej znaków|  
|`#`|Dowolna pojedyncza cyfra (0 – 9)|  
|`[charlist]`|Dowolny pojedynczy znak w`charlist`|  
|`[!charlist]`|Dowolny pojedynczy znak, który nie znajduje się w`charlist`|  
  
## <a name="character-lists"></a>Listy znaków  
 Grupa zawierająca jeden lub więcej znaków ( `charlist` ) ujęta w nawiasy kwadratowe ( `[ ]` ) może być używana do dopasowania dowolnego pojedynczego znaku w `string` i może zawierać prawie dowolny kod znaku, w tym cyfry.  
  
 Wykrzyknik ( `!` ) na początku `charlist` oznacza, że jest to dopasowanie, jeśli którykolwiek znak z wyjątkiem znaków w `charlist` jest znaleziony w `string` . Gdy używany jest nawiasy klamrowe, wykrzyknik dopasowuje się do samego siebie.  
  
## <a name="special-characters"></a>Znaki specjalne  
 Aby dopasować znaki specjalne do lewego nawiasu ( `[` ), znaku zapytania ( `?` ), znaku numeru ( `#` ) i gwiazdki ( `*` ), umieść je w nawiasach. Nie można użyć prawego nawiasu ( `]` ) w grupie, aby dopasować się do siebie, ale może być używany poza grupą jako pojedynczy znak.  
  
 Sekwencja znaków `[]` jest traktowana jako ciąg o zerowej długości ( `""` ). Jednak nie może być częścią listy znaków ujętej w nawiasy klamrowe. Jeśli chcesz sprawdzić, czy pozycja w polu `string` zawiera jedną z grup znaków lub nie ma żadnego znaku, możesz użyć `Like` dwa razy. Aby zapoznać się z przykładem, zobacz [jak: dopasowywanie ciągu do wzorca](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Zakresy znaków  
 Używając łącznika ( `–` ), aby oddzielić dolną i górną granicę zakresu, `charlist` można określić zakres znaków. Na przykład `[A–Z]` wynikiem jest dopasowanie, jeśli odpowiadająca pozycja znaku w `string` zawiera dowolny znak z zakresu `A` – `Z` , a `[!H–L]` wynikiem jest dopasowanie, Jeśli odpowiednia pozycja znaku zawiera dowolny znak poza zakresem `H` — `L` .  
  
 Po określeniu zakresu znaków muszą one znajdować się w rosnącej kolejności sortowania, czyli od najniższego do najwyższego. W tym celu, `[A–Z]` jest prawidłowym wzorcem, ale `[Z–A]` nie jest.  
  
### <a name="multiple-character-ranges"></a>Wiele zakresów znaków  
 Aby określić wiele zakresów dla tej samej pozycji znaku, umieść je w tych samych nawiasach bez ograniczników. Na przykład `[A–CX–Z]` wynikiem jest dopasowanie, Jeśli odpowiednia pozycja znaku w `string` zawiera dowolny znak z zakresu `A` `C` lub zakresu `X` — `Z` .  
  
### <a name="usage-of-the-hyphen"></a>Użycie łącznika  
 Łącznik ( `–` ) może pojawić się na początku (po wykrzykniku, jeśli istnieje) lub na końcu, `charlist` Aby dopasować sam siebie. W każdej innej lokalizacji łącznik identyfikuje zakres znaków, które są rozdzielane znakami po obu stronach łącznika.  
  
## <a name="collating-sequence"></a>Kolejność sortowania  
 Znaczenie określonego zakresu zależy od kolejności znaków w czasie wykonywania, zgodnie z ustawieniami `Option Compare` regionalnymi systemu, w którym jest uruchomiony kod. Z `Option Compare Binary` , zakres `[A–E]` dopasowuje `A` , `B` , `C` , `D` , i `E` . With `Option Compare Text` , dopasowuje,,,,,,,, `[A–E]` `A` ,, `a` `À` `à` `B` `b` `C` `c` `D` `d` `E` i `e` . Zakres nie pasuje `Ê` lub `ê` ponieważ znaki akcentowane są sortowane po nieakcentowane znaki w kolejności sortowania.  
  
## <a name="digraph-characters"></a>Znaki odgrafu  
 W niektórych językach istnieją znaki alfabetyczne, które reprezentują dwa oddzielne znaki. Na przykład kilka języków używa znaku, `æ` aby reprezentować znaki `a` i `e` kiedy pojawiają się razem. `Like`Operator rozpoznaje, że pojedynczy znak dwugrafu i dwa poszczególne znaki są równoważne.  
  
 Gdy język, który używa znaku oddzielenia, jest określony w ustawieniach regionalnych systemu, wystąpienie pojedynczego znaku w `pattern` lub `string` pasuje do równoważnej dwuznakowej sekwencji w innym ciągu. Analogicznie, znak podgrafu `pattern` umieszczony w nawiasach (na liście lub w zakresie) jest zgodny z równoważną dwuznakową sekwencją w `string` .  
  
## <a name="overloading"></a>Przeciążenie  
 `Like`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa `Like` operatora do porównywania ciągów z różnymi wzorcami. Wyniki są wprowadzane do `Boolean` zmiennej wskazującej, czy każdy ciąg spełnia wzorzec.  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [Operatory porównania](comparison-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Option Compare — Instrukcja](../statements/option-compare-statement.md)
- [Operatory i wyrażenia](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Instrukcje: dopasowywanie ciągu do wzorca](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
