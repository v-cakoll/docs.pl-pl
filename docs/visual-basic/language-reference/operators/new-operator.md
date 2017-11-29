---
title: "New — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74f0352379e861ad135ea23d31ea07d638f9e6c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-visual-basic"></a>New — Operator (Visual Basic)
Wprowadza `New` klauzuli do utworzenia nowego wystąpienia obiektu, określa ograniczenie konstruktora dla parametru typu lub identyfikuje `Sub` procedury jako konstruktora klasy.  
  
## <a name="remarks"></a>Uwagi  
 W deklaracji lub instrukcji przypisania `New` klauzula musi określać zdefiniowanej klasy, z którego można utworzyć wystąpienia. Oznacza to, że klasa musi ujawniać konstruktorów co najmniej jeden kod wywołujący może uzyskać dostęp.  
  
 Można użyć `New` klauzuli w instrukcji deklaracji lub instrukcji przypisania. Po uruchomieniu instrukcji, wymaga odpowiedniego konstruktora określonej klasy, przekazując żadnych argumentów, które podano. W poniższym przykładzie pokazano to przez utworzenie wystąpienia `Customer` klasy, która ma dwa konstruktory, który nie przyjmuje żadnych parametrów i jedną, która przyjmuje parametr typu string.  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 Ponieważ tablic są klasy, `New` można utworzyć nowego wystąpienia tablicy, jak pokazano w poniższych przykładach.  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) zgłasza <xref:System.OutOfMemoryException> błędu, jeśli jest za mało pamięci do utworzenia nowego wystąpienia.  
  
> [!NOTE]
>  `New` — Słowo kluczowe umożliwia również w liście parametrów typu określ, czy dostarczony typ musi ujawniać dostępny konstruktor bez parametrów. Aby uzyskać więcej informacji na temat parametrów typu i ograniczeń, zobacz [lista typów](../../../visual-basic/language-reference/statements/type-list.md).  
  
 Aby utworzyć procedury konstruktora dla klasy, ustaw nazwę `Sub` procedura `New` — słowo kluczowe. Aby uzyskać więcej informacji, zobacz [okres istnienia obiektów: sposób obiekty są utworzone i Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
 `New` — Słowo kluczowe może być używana w tych sytuacjach:  
  
 [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Z](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.OutOfMemoryException>  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)  
 [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Okres istnienia obiektów: Sposób obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
