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
ms.openlocfilehash: 630b0c48def77449f426b287a26f95af7cfb930e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837735"
---
# <a name="new-operator-visual-basic"></a>New — Operator (Visual Basic)
Wprowadza `New` klauzulę, aby utworzyć nowe wystąpienie obiektu określa ograniczenie konstruktora dla parametru typu lub identyfikuje `Sub` procedury jak konstruktora klasy.  
  
## <a name="remarks"></a>Uwagi  
 W deklaracji lub instrukcji przypisania `New` klauzula musi określać zdefiniowana klasa, z którego można utworzyć wystąpienia. Oznacza to, że klasa musi ujawniać jeden lub więcej konstruktorów, które mogą uzyskiwać dostęp do kodu wywołującego.  
  
 Możesz użyć `New` klauzuli w instrukcji deklaracji lub instrukcji przypisania. Po uruchomieniu instrukcja wywołuje odpowiedniego konstruktora określonej klasy, przekazując dowolne argumenty, które zostały wprowadzone. Poniższy przykład przedstawia to przez utworzenie wystąpienia `Customer` klasy, która ma dwa konstruktory: jedną, która nie przyjmuje żadnych parametrów, a ta, która przyjmuje jako parametr ciągu.  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 Ponieważ tablice są klasami, `New` można utworzyć nowego wystąpienia tablicy, jak pokazano w poniższych przykładach.  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) zgłasza <xref:System.OutOfMemoryException> błąd, jeśli ma za mało pamięci do utworzenia nowego wystąpienia.  
  
> [!NOTE]
>  `New` Słowo kluczowe jest również używane w liście parametrów typu do określenia, czy podany typ należy ujawnić dostępny konstruktora bez parametrów. Aby uzyskać więcej informacji na temat parametrów typu i ograniczeń, zobacz [lista typów](../../../visual-basic/language-reference/statements/type-list.md).  
  
 Aby utworzyć procedurę konstruktora dla klasy, ustaw nazwę `Sub` procedury, aby `New` — słowo kluczowe. Aby uzyskać więcej informacji, zobacz [okres istnienia obiektów: Jak obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
 Słowa kluczowego `New` można używać w następujących kontekstach:  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [z](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.OutOfMemoryException>
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Okres istnienia obiektów: Jak obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
