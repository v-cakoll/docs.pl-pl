---
title: New — Operator (Visual Basic)
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
ms.openlocfilehash: 36cf71529b1f81c27881638d788117222c37171d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955881"
---
# <a name="new-operator-visual-basic"></a>New — Operator (Visual Basic)
Wprowadza klauzulę do utworzenia nowego wystąpienia obiektu, określa ograniczenie konstruktora dla parametru typu lub `Sub` identyfikuje procedurę jako konstruktora klasy. `New`  
  
## <a name="remarks"></a>Uwagi  
 W deklaracji lub przypisaniu `New` klauzula musi określać zdefiniowaną klasę, z której można utworzyć wystąpienie. Oznacza to, że klasa musi uwidaczniać jeden lub więcej konstruktorów, do których kod wywołujący może uzyskać dostęp.  
  
 Można użyć `New` klauzuli w instrukcji deklaracji lub instrukcji przypisania. Po uruchomieniu instrukcji wywołuje odpowiedni Konstruktor określonej klasy, przekazując wszystkie podane argumenty. Poniższy przykład ilustruje to przez utworzenie wystąpień `Customer` klasy, która ma dwa konstruktory, jeden, który nie przyjmuje parametrów i jeden, który pobiera parametr ciągu.  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 Ponieważ tablice są klasami `New` , można utworzyć nowe wystąpienie tablicy, jak pokazano w poniższych przykładach.  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) zgłasza <xref:System.OutOfMemoryException> błąd, jeśli nie ma wystarczającej ilości pamięci do utworzenia nowego wystąpienia.  
  
> [!NOTE]
> `New` Słowo kluczowe jest również używane na listach parametrów typu, aby określić, że dostarczony typ musi uwidaczniać dostępny Konstruktor bez parametrów. Aby uzyskać więcej informacji o parametrach typu i ograniczeniach, zobacz [list typów](../../../visual-basic/language-reference/statements/type-list.md).  
  
 Aby utworzyć procedurę konstruktora dla klasy, należy ustawić nazwę `Sub` procedury `New` dla słowa kluczowego. Aby uzyskać więcej informacji, [Zobacz okres istnienia obiektu: Jak obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
 Słowa kluczowego `New` można używać w następujących kontekstach:  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Z](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.OutOfMemoryException>
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Okres istnienia obiektu: Jak obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
