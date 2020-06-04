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
ms.openlocfilehash: 7e22ad6e32ec13f081391e1d47a80df8b1e65063
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412991"
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
|`genericmodifier`|Opcjonalny. Może być używany tylko w interfejsach ogólnych i delegatach. Można zadeklarować typ współvariant przy użyciu słowa kluczowego [out](../modifiers/out-generic-modifier.md) lub kontrawariantne za pomocą słowa kluczowego [in](../modifiers/in-generic-modifier.md) . Zobacz [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).|
|`typename`|Wymagany. Nazwa parametru typu. Jest to symbol zastępczy, który ma zostać zastąpiony przez zdefiniowany typ dostarczony przez odpowiedni argument typu.|
|`constraintlist`|Opcjonalny. Lista wymagań, które ograniczają typ danych, które mogą być dostarczone `typename` . Jeśli masz wiele ograniczeń, umieść je w nawiasach klamrowych ( `{ }` ) i rozdziel je przecinkami. Należy wprowadzić listę ograniczeń za pomocą słowa kluczowego [as](as-clause.md) . Używasz `As` tylko raz, na początku listy.|

## <a name="remarks"></a>Uwagi

Każdy ogólny element programistyczny musi przyjmować co najmniej jeden parametr typu. Parametr typu jest symbolem zastępczym określonego typu ( *skonstruowany element*), który jest określany przez kod klienta podczas tworzenia wystąpienia typu ogólnego. Istnieje możliwość zdefiniowania klasy ogólnej, struktury, interfejsu, procedury lub delegata.

Aby uzyskać więcej informacji na temat definiowania typu ogólnego, zobacz [typy ogólne w Visual Basic](../../programming-guide/language-features/data-types/generic-types.md). Aby uzyskać więcej informacji na temat nazw parametrów typu, zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).

## <a name="rules"></a>Reguły

- **Nawiasów.** W przypadku podania listy parametrów typu należy ująć ją w nawiasy i należy wprowadzić listę za [pomocą słowa](of-clause.md) kluczowego. Używasz `Of` tylko raz, na początku listy.

- **Powiązanych.** Lista *ograniczeń* dla parametru typu może zawierać następujące elementy w dowolnej kombinacji:

  - Dowolna liczba interfejsów. Dostarczony typ musi implementować każdy interfejs na tej liście.

  - Co najwyżej jedna Klasa. Dostarczony typ musi dziedziczyć po tej klasie.

  - `New`Słowo kluczowe. Dostarczony typ musi ujawniać Konstruktor bez parametrów, który ma dostęp do typu ogólnego. Jest to przydatne w przypadku ograniczenia parametru typu przez jeden lub więcej interfejsów. Typ, który implementuje interfejsy, niekoniecznie uwidacznia Konstruktor i w zależności od poziomu dostępu konstruktora, kod wewnątrz typu generycznego może nie być w stanie uzyskać do niego dostępu.

  - `Class`Słowo kluczowe lub `Structure` słowo kluczowe. `Class`Słowo kluczowe ogranicza parametr typu ogólnego, aby wymagało, aby dowolny argument typu, który został przesłany do niego, jest typem referencyjnym, na przykład String, array lub Delegate lub obiektem utworzonym na podstawie klasy. `Structure`Słowo kluczowe ogranicza parametr typu ogólnego, aby wymagało, aby dowolny argument typu przekazał do niego typ wartości, na przykład strukturę, Wyliczenie lub typ danych podstawowych. Nie można uwzględnić jednocześnie `Class` i `Structure` w tym samym elemencie `constraintlist` .

  Dostarczony typ musi spełniać każde wymaganie zawarte w `constraintlist` .

  Ograniczenia dotyczące każdego parametru typu są niezależne od ograniczeń dla innych parametrów typu.

## <a name="behavior"></a>Zachowanie

- **Podstawienie czasu kompilacji.** Podczas tworzenia typu konstruowanego z generycznego elementu programistycznego, należy podać zdefiniowany typ dla każdego parametru typu. Kompilator Visual Basic zastępuje typ dostarczony dla każdego wystąpienia `typename` elementu generycznego.

- **Brak ograniczeń.** Jeśli nie określisz żadnych ograniczeń dla parametru typu, kod jest ograniczony do operacji i elementów członkowskich obsługiwanych przez [Typ danych obiektu](../data-types/object-data-type.md) dla tego parametru typu.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia definicję szkieletu klasy ogólnego słownika, w tym funkcję szkieletu, aby dodać nowy wpis do słownika.

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a>Przykład

Ponieważ `dictionary` jest ogólny, kod, który używa go, może utworzyć wiele obiektów z niego, z których każdy ma te same funkcje, ale działa na innym typie danych. Poniższy przykład pokazuje wiersz kodu, który tworzy `dictionary` obiekt z `String` wpisami i `Integer` kluczami.

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano równoważną definicję szkieletu wygenerowaną w poprzednim przykładzie.

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a>Zobacz też

- [Z](of-clause.md)
- [Operator new](../operators/new-operator.md)
- [Poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Object — typ danych](../data-types/object-data-type.md)
- [Function, instrukcja](function-statement.md)
- [Structure — Instrukcja](structure-statement.md)
- [Sub, instrukcja](sub-statement.md)
- [Instrukcje: Używanie klasy ogólnej](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md)
- [W](../modifiers/in-generic-modifier.md)
- [Określoną](../modifiers/out-generic-modifier.md)
