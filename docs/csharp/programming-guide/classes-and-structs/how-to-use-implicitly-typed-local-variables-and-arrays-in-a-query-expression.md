---
title: 'Porady: użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: dccf40508d4223bdef0b2fbbe5ce97f75ffb5773
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500989"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Porady: użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania (Przewodnik programowania w języku C#)
Niejawnie wpisane zmienne lokalne można użyć w każdym przypadku, gdy chcesz, aby kompilator, aby określić typ zmiennej lokalnej. Niejawnie wpisane zmienne lokalne musi być przechowywanie anonimowych typów, które są często używane w wyrażeniach zapytań. Poniższe przykłady ilustrują wymagane i opcjonalne zastosowań niejawnie wpisane zmienne lokalne w zapytaniach.  
  
 Niejawnie wpisane zmienne lokalne są zadeklarowane za pomocą [var](../../../csharp/language-reference/keywords/var.md) kontekstowego słowa kluczowego. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) i [niejawnie wpisane tablice](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typowy scenariusz, w którym `var` — słowo kluczowe jest wymagane: wyrażenie zapytania, który wytwarza sekwencję typów anonimowych. W tym scenariuszu, zmienna zapytania i Zmienna iteracji w `foreach` instrukcja musi być wpisana niejawnie przy użyciu `var` , ponieważ nie masz dostępu do nazwy typu dla typu anonimowego. Aby uzyskać więcej informacji na temat typów anonimowych, zobacz [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_1.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `var` — słowo kluczowe w sytuacji, która jest podobna, ale która użytkowania `var` jest opcjonalne. Ponieważ `student.LastName` jest ciągiem, wykonanie zwraca zapytanie sekwencji ciągów. W związku z tym, typ `queryID` może być zadeklarowana jako `System.Collections.Generic.IEnumerable<string>` zamiast `var`. Słowo kluczowe `var` służy do zapewnienia wygody. W tym przykładzie zmienna iteracji w `foreach` instrukcji jest jawnie wpisane jako ciąg znaków, ale zamiast tego może być zadeklarowana za pomocą `var`. Ponieważ typ zmiennej iteracji nie jest typu anonimowego użytkowania `var` jest opcją, nie wymagania. Należy pamiętać, że `var` sam nie jest typem, ale instrukcję kompilatora wywnioskować i przypisać typu.  
  
 [!code-csharp[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_2.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Metody rozszerzeń](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
- [LINQ (Language-Integrated Query)](../../../csharp/linq/index.md)  
- [var](../../../csharp/language-reference/keywords/var.md)  
- [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
