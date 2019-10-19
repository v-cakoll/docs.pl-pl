---
title: Lista parametrów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 0dded7fd68256b9b9de8ebe4b48073eb40696c12
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582179"
---
# <a name="parameter-list-visual-basic"></a>Lista parametrów (Visual Basic)

Określa parametry, których oczekuje procedura, gdy jest wywoływana. Wiele parametrów jest oddzielonych przecinkami. Poniżej znajduje się składnia jednego parametru.

## <a name="syntax"></a>Składnia

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a>Części

`attributelist`  
Opcjonalny. Lista atrybutów, które są stosowane do tego parametru. Należy ująć [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ostre ("`<`" i "`>`").

`Optional`  
Opcjonalny. Określa, że ten parametr nie jest wymagany, gdy procedura jest wywoływana.

`ByVal`  
Opcjonalny. Określa, że procedura nie może zastąpić ani ponownie przypisać elementu zmiennej odpowiadającego mu argumentu w kodzie wywołującym.

`ByRef`  
Opcjonalny. Określa, że procedura może zmodyfikować bazowy element zmiennej w kodzie wywołującym tak samo jak kod wywołujący może.

`ParamArray`  
Opcjonalny. Określa, że ostatnim parametrem na liście parametrów jest opcjonalna Tablica elementów określonego typu danych. Dzięki temu kod wywołujący przekazuje dowolną liczbę argumentów do procedury.

`parametername`  
Wymagany. Nazwa zmiennej lokalnej reprezentującej parametr.

`parametertype`  
Wymagane, jeśli `Option Strict` jest `On`. Typ danych zmiennej lokalnej reprezentującej parametr.

`defaultvalue`  
Wymagane dla `Optional` parametrów. Każde stałe lub stałe wyrażenie, którego wynikiem jest typ danych parametru. Jeśli typ jest `Object` lub Klasa, interfejs, tablica lub struktura, wartość domyślna może być `Nothing`a.

## <a name="remarks"></a>Uwagi

Parametry są ujęte w nawiasy i oddzielane przecinkami. Parametr można zadeklarować przy użyciu dowolnego typu danych. Jeśli nie określisz `parametertype`, wartość domyślna to `Object`.

Gdy wywoływany kod wywołuje procedurę, przekazuje *argument* do każdego wymaganego parametru. Aby uzyskać więcej informacji, zobacz [różnice między parametrami i argumentami](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).

Argument wywoływany przez kod przekazywany do każdego parametru jest wskaźnikiem do podstawowego elementu w kodzie wywołującym. Jeśli ten element jest *niezmienny* (stała, literał, Wyliczenie lub wyrażenie), nie można go zmienić. Jeśli jest to element *zmiennej* (zadeklarowana zmienna, pole, właściwość, element tablicy lub element struktury), kod wywołujący może go zmienić. Aby uzyskać więcej informacji, zobacz [różnice między argumentami modyfikowalnymi i niemodyfikowalnymi](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).

Jeśli element zmiennej jest przenoszona `ByRef`, procedura może je również zmienić. Aby uzyskać więcej informacji, zobacz [różnice między przekazywaniem argumentu według wartości i przez odwołanie](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).

## <a name="rules"></a>Przepisy

- **Nawiasów.** W przypadku określenia listy parametrów należy ująć ją w nawiasy. Jeśli nie ma żadnych parametrów, można nadal używać nawiasów otaczających pustą listę. Poprawia to czytelność kodu przez wyjaśnienie, że element jest procedurą.

- **Parametry opcjonalne.** Jeśli używasz modyfikatora `Optional` dla parametru, wszystkie kolejne parametry na liście muszą być również opcjonalne i być deklarowane przy użyciu modyfikatora `Optional`.

     Każda deklaracja opcjonalnego parametru musi podawać klauzulę `defaultvalue`.

     Aby uzyskać więcej informacji, zobacz [Parametry opcjonalne](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).

- **Tablice parametrów.** Należy określić `ByVal` dla parametru `ParamArray`.

     Na tej samej liście parametrów nie można używać jednocześnie `Optional` i `ParamArray`.

     Aby uzyskać więcej informacji, zobacz [tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).

- **Mechanizm przekazywania.** Domyślny mechanizm dla każdego argumentu jest `ByVal`, co oznacza, że procedura nie może zmienić bazowego elementu zmiennej. Jeśli jednak element jest typem referencyjnym, procedura może zmodyfikować zawartość lub elementy członkowskie obiektu bazowego, nawet jeśli nie można zastąpić ani ponownie przypisać samego obiektu.

- **Nazwy parametrów.** Jeśli typ danych parametru jest tablicą, obserwuj `parametername` od razu przez nawiasy. Aby uzyskać więcej informacji na temat nazw parametrów, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje procedurę `Function`, która definiuje dwa parametry.

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Przegląd atrybutów](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
