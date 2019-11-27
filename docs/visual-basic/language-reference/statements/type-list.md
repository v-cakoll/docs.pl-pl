---
title: Lista typów
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: 3f2aaa65293ed2bcc6c8eeb4bd77e49907d93425
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352772"
---
# <a name="type-list-visual-basic"></a>Lista typów (Visual Basic)

Określa *parametry typu* dla *ogólnego* elementu programistycznego. Wiele parametrów jest oddzielonych przecinkami. Poniżej przedstawiono składnię dla jednego parametru typu.

## <a name="syntax"></a>Składnia

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a>Części

|Termin|Definicja|
|---|---|
|`genericmodifier`|Opcjonalna. Może być używany tylko w interfejsach ogólnych i delegatach. Można zadeklarować typ współvariant przy użyciu słowa kluczowego [out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) lub kontrawariantne za pomocą słowa kluczowego [in](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) . Zobacz [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).|
|`typename`|Wymagana. Nazwa parametru typu. Jest to symbol zastępczy, który ma zostać zastąpiony przez zdefiniowany typ dostarczony przez odpowiedni argument typu.|
|`constraintlist`|Opcjonalna. Lista wymagań, które ograniczają typ danych, które można dostarczyć dla `typename`. W przypadku wielu ograniczeń należy ująć je w nawiasy klamrowe (`{ }`) i oddzielić je przecinkami. Należy wprowadzić listę ograniczeń za pomocą słowa kluczowego [as](../../../visual-basic/language-reference/statements/as-clause.md) . `As` można używać tylko raz, na początku listy.|

## <a name="remarks"></a>Uwagi

Każdy ogólny element programistyczny musi przyjmować co najmniej jeden parametr typu. Parametr typu jest symbolem zastępczym określonego typu ( *skonstruowany element*), który jest określany przez kod klienta podczas tworzenia wystąpienia typu ogólnego. Istnieje możliwość zdefiniowania klasy ogólnej, struktury, interfejsu, procedury lub delegata.

Aby uzyskać więcej informacji na temat definiowania typu ogólnego, zobacz [typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md). Aby uzyskać więcej informacji na temat nazw parametrów typu, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

## <a name="rules"></a>Reguły

- **Nawiasów.** W przypadku podania listy parametrów typu należy ująć ją w nawiasy i należy wprowadzić listę za [pomocą słowa](../../../visual-basic/language-reference/statements/of-clause.md) kluczowego. `Of` można używać tylko raz, na początku listy.

- **Powiązanych.** Lista *ograniczeń* dla parametru typu może zawierać następujące elementy w dowolnej kombinacji:

  - Dowolna liczba interfejsów. Dostarczony typ musi implementować każdy interfejs na tej liście.

  - Co najwyżej jedna Klasa. Dostarczony typ musi dziedziczyć po tej klasie.

  - Słowo kluczowe `New`. Dostarczony typ musi ujawniać Konstruktor bez parametrów, który ma dostęp do typu ogólnego. Jest to przydatne w przypadku ograniczenia parametru typu przez jeden lub więcej interfejsów. Typ, który implementuje interfejsy, niekoniecznie uwidacznia Konstruktor i w zależności od poziomu dostępu konstruktora, kod wewnątrz typu generycznego może nie być w stanie uzyskać do niego dostępu.

  - Słowo kluczowe `Class` lub słowo kluczowe `Structure`. Słowo kluczowe `Class` ogranicza parametr typu ogólnego, aby wymagało, aby każdy argument typu, który został przesłany do niego, był typem referencyjnym, na przykład ciągiem, tablicą lub delegatem lub obiektem utworzonym na podstawie klasy. Słowo kluczowe `Structure` ogranicza parametr typu ogólnego, aby wymagało, aby dowolny argument typu przekazał do niego typ wartości, na przykład strukturę, Wyliczenie lub typ danych podstawowych. W tym samym `constraintlist`nie można uwzględnić jednocześnie `Class` i `Structure`.

  Dostarczony typ musi spełniać każde wymaganie zawarte w `constraintlist`.

  Ograniczenia dotyczące każdego parametru typu są niezależne od ograniczeń dla innych parametrów typu.

## <a name="behavior"></a>Zachowanie

- **Podstawienie czasu kompilacji.** Podczas tworzenia typu konstruowanego z generycznego elementu programistycznego, należy podać zdefiniowany typ dla każdego parametru typu. Kompilator Visual Basic zastępuje dostarczony typ dla każdego wystąpienia `typename` w elemencie ogólnym.

- **Brak ograniczeń.** Jeśli nie określisz żadnych ograniczeń dla parametru typu, kod jest ograniczony do operacji i elementów członkowskich obsługiwanych przez [Typ danych obiektu](../../../visual-basic/language-reference/data-types/object-data-type.md) dla tego parametru typu.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia definicję szkieletu klasy ogólnego słownika, w tym funkcję szkieletu, aby dodać nowy wpis do słownika.

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a>Przykład

Ponieważ `dictionary` jest ogólny, kod, który używa go, może utworzyć wiele obiektów z niego, z których każdy ma te same funkcje, ale działa na innym typie danych. Poniższy przykład pokazuje wiersz kodu, który tworzy obiekt `dictionary` z wpisami `String` i kluczami `Integer`.

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano równoważną definicję szkieletu wygenerowaną w poprzednim przykładzie.

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a>Zobacz także

- [Z](../../../visual-basic/language-reference/statements/of-clause.md)
- [Operator New](../../../visual-basic/language-reference/operators/new-operator.md)
- [Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Object, typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Instrukcje: używanie klasy ogólnej](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Podczas](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Określoną](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
