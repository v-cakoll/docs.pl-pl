---
title: 'Instrukcje: Użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania C# — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: 5003e03b488a16d53e4e3d20a0b0b0e09630b46f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596709"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Instrukcje: Użyj niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytaniaC# (Przewodnik programowania)
Możesz użyć niejawnie wpisanych zmiennych lokalnych, ilekroć kompilator ma określić typ zmiennej lokalnej. Należy użyć niejawnie wpisanych zmiennych lokalnych do przechowywania typów anonimowych, które są często używane w wyrażeniach zapytań. Poniższe przykłady ilustrują opcjonalne i wymagane zastosowania niejawnie wpisanych zmiennych lokalnych w zapytaniach.  
  
 Niejawnie wpisane zmienne lokalne są deklarowane przy użyciu słowa kluczowego [var](../../language-reference/keywords/var.md) . Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](./implicitly-typed-local-variables.md) i niejawnie [wpisane tablice](../arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono typowy scenariusz, w którym `var` słowo kluczowe jest wymagane: wyrażenie zapytania, które tworzy sekwencję typów anonimowych. W tym scenariuszu zarówno zmienna zapytania, jak i Zmienna iteracji w `foreach` instrukcji muszą zostać wpisane niejawnie przy użyciu `var` , ponieważ nie masz dostępu do nazwy typu dla typu anonimowego. Aby uzyskać więcej informacji na temat typów anonimowych, zobacz [Typy anonimowe](./anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#32)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `var` słowa kluczowego w podobnej sytuacji, ale w którym `var` użycie jest opcjonalne. Ponieważ `student.LastName` jest ciągiem, wykonywanie zapytania zwraca sekwencję ciągów. W związku z tym typ `queryID` może być zadeklarowany `System.Collections.Generic.IEnumerable<string>` jako zamiast `var`. Słowo `var` kluczowe jest używane w celu wygody. W przykładzie zmienna iteracji w `foreach` instrukcji jest jawnie wpisana jako ciąg, ale zamiast tego może być zadeklarowana przy użyciu. `var` Ponieważ typ zmiennej iteracji nie jest typem anonimowym, użycie `var` jest opcją, a nie wymaganie. Pamiętaj, `var` że sam nie jest typem, ale instrukcją kompilatora do wnioskowania i przypisania typu.  
  
 [!code-csharp[csProgGuideLINQ#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#33)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Metody rozszerzeń](./extension-methods.md)
- [LINQ (zapytanie zintegrowane z językiem)](../../linq/index.md)
- [var](../../language-reference/keywords/var.md)
- [Wyrażenia zapytania LINQ](../linq-query-expressions/index.md)
