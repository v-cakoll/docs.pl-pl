---
title: 'Porady: użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: c2bc990f9dda4b91928c176cf7f10bfb349ba343
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Porady: użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania (Przewodnik programowania w języku C#)
Niejawnie wpisane zmienne lokalne służy zawsze, gdy kompilator można określić typu zmienną lokalną. Niejawnie wpisane zmienne lokalne musi używać do przechowywania typy anonimowe, które są często używane w wyrażeniach zapytań. Poniższe przykłady przedstawiają zarówno opcjonalne i wymagane zastosowań niejawnie wpisane zmienne lokalne w zapytaniach.  
  
 Niejawnie wpisane zmienne lokalne są zadeklarowane za pomocą [var](../../../csharp/language-reference/keywords/var.md) kontekstowe słowo kluczowe. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) i [niejawnie wpisane tablice](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono typowy scenariusz, w którym `var` słowa kluczowego: wyrażenie zapytania, które tworzy sekwencję typy anonimowe. W tym scenariuszu zarówno do zmiennej zapytania i zmiennej iteracji w `foreach` instrukcji musi być niejawnie wpisanych przy użyciu `var` , ponieważ nie masz dostępu do nazwy typu dla typu anonimowego. Aby uzyskać więcej informacji na temat typów anonimowych, zobacz [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_1.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `var` — słowo kluczowe w sytuacji, która jest podobna, ale w którym korzystanie z `var` jest opcjonalne. Ponieważ `student.LastName` jest ciągiem, wykonanie zapytanie zwraca sekwencję ciągów. W związku z tym typem `queryID` może być zadeklarowana jako `System.Collections.Generic.IEnumerable<string>` zamiast `var`. Słowo kluczowe `var` służy do zapewnienia wygody. W tym przykładzie zmiennej iteracji w `foreach` instrukcji jest jawnie wpisana jako ciąg znaków, ale zamiast tego może być zadeklarowany za pomocą `var`. Ponieważ typ zmiennej iteracji nie jest typu anonimowego, użycie `var` jest opcją nie wymagane. Należy pamiętać, że `var` sam nie jest typem, ale instrukcję do kompilatora wnioskować i przypisać typu.  
  
 [!code-csharp[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Metody rozszerzeń](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [LINQ (zapytania o języku zintegrowanym)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [var](../../../csharp/language-reference/keywords/var.md)  
 [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
