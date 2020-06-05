---
title: Lista parametrów
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
ms.openlocfilehash: 706fc2414806db5608cce410bf4156839ec2d83e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404320"
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
Opcjonalny. Lista atrybutów, które są stosowane do tego parametru. Należy ująć [listę atrybutów](attribute-list.md) w nawiasy kątowe (" `<` " i " `>` ").

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
Wymagane, jeśli `Option Strict` jest `On` . Typ danych zmiennej lokalnej reprezentującej parametr.

`defaultvalue`  
Wymagany dla `Optional` parametrów. Każde stałe lub stałe wyrażenie, którego wynikiem jest typ danych parametru. Jeśli typem jest `Object` lub Klasa, interfejs, tablica lub struktura, wartość domyślna to `Nothing` .

## <a name="remarks"></a>Uwagi

Parametry są ujęte w nawiasy i oddzielane przecinkami. Parametr można zadeklarować przy użyciu dowolnego typu danych. Jeśli nie określisz `parametertype` wartości, wartość domyślna to `Object` .

Gdy wywoływany kod wywołuje procedurę, przekazuje *argument* do każdego wymaganego parametru. Aby uzyskać więcej informacji, zobacz [różnice między parametrami i argumentami](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).

Argument wywoływany przez kod przekazywany do każdego parametru jest wskaźnikiem do podstawowego elementu w kodzie wywołującym. Jeśli ten element jest *niezmienny* (stała, literał, Wyliczenie lub wyrażenie), nie można go zmienić. Jeśli jest to element *zmiennej* (zadeklarowana zmienna, pole, właściwość, element tablicy lub element struktury), kod wywołujący może go zmienić. Aby uzyskać więcej informacji, zobacz [różnice między argumentami modyfikowalnymi i niemodyfikowalnymi](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).

W przypadku przekazania elementu zmiennej `ByRef` procedura może również je zmienić. Aby uzyskać więcej informacji, zobacz [różnice między przekazywaniem argumentu według wartości i przez odwołanie](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).

## <a name="rules"></a>Reguły

- **Nawiasów.** W przypadku określenia listy parametrów należy ująć ją w nawiasy. Jeśli nie ma żadnych parametrów, można nadal używać nawiasów otaczających pustą listę. Poprawia to czytelność kodu przez wyjaśnienie, że element jest procedurą.

- **Parametry opcjonalne.** Jeśli używasz `Optional` modyfikatora w parametrze, wszystkie kolejne parametry na liście muszą być również opcjonalne i być zadeklarowane za pomocą `Optional` modyfikatora.

     Każda deklaracja opcjonalnego parametru musi dostarczyć `defaultvalue` klauzulę.

     Aby uzyskać więcej informacji, zobacz [Parametry opcjonalne](../../programming-guide/language-features/procedures/optional-parameters.md).

- **Tablice parametrów.** Należy określić `ByVal` dla `ParamArray` parametru.

     Nie można używać obu `Optional` i `ParamArray` na tej samej liście parametrów.

     Aby uzyskać więcej informacji, zobacz [tablice parametrów](../../programming-guide/language-features/procedures/parameter-arrays.md).

- **Mechanizm przekazywania.** Domyślny mechanizm dla każdego argumentu to `ByVal` , co oznacza, że procedura nie może zmienić bazowego elementu zmiennej. Jeśli jednak element jest typem referencyjnym, procedura może zmodyfikować zawartość lub elementy członkowskie obiektu bazowego, nawet jeśli nie można zastąpić ani ponownie przypisać samego obiektu.

- **Nazwy parametrów.** Jeśli typ danych parametru jest tablicą, obserwuj `parametername` bezpośrednio w nawiasach. Aby uzyskać więcej informacji na temat nazw parametrów, zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje `Function` procedurę, która definiuje dwa parametry.

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Function, instrukcja](function-statement.md)
- [Sub, instrukcja](sub-statement.md)
- [Declare — Instrukcja](declare-statement.md)
- [Structure — Instrukcja](structure-statement.md)
- [Option Strict — Instrukcja](option-strict-statement.md)
- [Przegląd atrybutów](../../programming-guide/concepts/attributes/index.md)
- [Instrukcje: Przerywanie i łączenie instrukcji w kodzie](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
