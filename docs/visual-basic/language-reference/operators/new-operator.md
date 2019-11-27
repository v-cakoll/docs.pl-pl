---
title: Nowy operator
ms.date: 07/20/2015
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
ms.openlocfilehash: 27b5b4516ef729045036c36fedc24b6c576a4f61
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348318"
---
# <a name="new-operator-visual-basic"></a>New — Operator (Visual Basic)

Wprowadza klauzulę `New`, aby utworzyć nowe wystąpienie obiektu, określa ograniczenie konstruktora dla parametru typu lub identyfikuje procedurę `Sub` jako konstruktora klasy.

## <a name="remarks"></a>Uwagi

W deklaracji lub przypisaniu klauzula `New` musi określać zdefiniowaną klasę, z której można utworzyć wystąpienie. Oznacza to, że klasa musi uwidaczniać jeden lub więcej konstruktorów, do których kod wywołujący może uzyskać dostęp.

Można użyć klauzuli `New` w instrukcji deklaracji lub instrukcji przypisania. Po uruchomieniu instrukcji wywołuje odpowiedni Konstruktor określonej klasy, przekazując wszystkie podane argumenty. Poniższy przykład ilustruje to przez utworzenie wystąpień klasy `Customer`, która ma dwa konstruktory, jeden, który nie przyjmuje parametrów i jeden z nich przyjmuje parametr String:

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

Ponieważ tablice są klasami, `New` może utworzyć nowe wystąpienie tablicy, jak pokazano w następującym przykładzie:

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

Środowisko uruchomieniowe języka wspólnego (CLR) zgłasza błąd <xref:System.OutOfMemoryException>, jeśli nie ma wystarczającej ilości pamięci do utworzenia nowego wystąpienia.

> [!NOTE]
> Słowo kluczowe `New` jest również używane na listach parametrów typu, aby określić, że dostarczony typ musi uwidaczniać dostępny Konstruktor bez parametrów. Aby uzyskać więcej informacji o parametrach typu i ograniczeniach, zobacz [list typów](../statements/type-list.md).

Aby utworzyć procedurę konstruktora dla klasy, należy ustawić nazwę procedury `Sub` na słowo kluczowe `New`. Aby uzyskać więcej informacji, zobacz [okres istnienia obiektu: sposób tworzenia i zniszczenia obiektów](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

Słowa kluczowego `New` można użyć w tych kontekstach:

- [Dim, instrukcja](../statements/dim-statement.md)
- [Z](../statements/of-clause.md)
- [Sub, instrukcja](../statements/sub-statement.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.OutOfMemoryException>
- [Słowa kluczowe](../keywords/index.md)
- [Lista typów](../statements/type-list.md)
- [Typy ogólne w Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
