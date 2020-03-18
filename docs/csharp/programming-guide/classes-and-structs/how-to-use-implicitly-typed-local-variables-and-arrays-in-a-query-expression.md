---
title: Jak używać niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania — Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: f4ff71fc4dc1a0b2affa1f032ab1d3d6bb04d297
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705564"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Jak używać niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania (Przewodnik programowania C#)
Można użyć niejawnie wpisane zmienne lokalne, gdy chcesz kompilator, aby określić typ zmiennej lokalnej. Należy użyć niejawnie wpisane zmienne lokalne do przechowywania typów anonimowych, które są często używane w wyrażeniach kwerendy. Poniższe przykłady ilustrują zarówno opcjonalne, jak i wymagane użycie niejawnie wpisanych zmiennych lokalnych w kwerendach.  
  
 Niejawnie wpisane zmienne lokalne są deklarowane przy użyciu słowa kluczowego kontekstowego [var.](../../language-reference/keywords/var.md) Aby uzyskać więcej informacji, zobacz [Niejawnie wpisane zmienne lokalne](./implicitly-typed-local-variables.md) i [tablice niejawnie wpisane](../arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono typowy `var` scenariusz, w którym słowo kluczowe jest wymagane: wyrażenie kwerendy, która tworzy sekwencję typów anonimowych. W tym scenariuszu zarówno zmiennej kwerendy, `foreach` jak i zmiennej iteracji w instrukcji muszą być niejawnie wpisane przy użyciu, `var` ponieważ nie masz dostępu do nazwy typu dla typu anonimowego. Aby uzyskać więcej informacji na temat typów anonimowych, zobacz [Typy anonimowe](./anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#32)]  
  
## <a name="example"></a>Przykład  
 W poniższym `var` przykładzie użyto słowa kluczowego w sytuacji `var` podobnej, ale w której użycie jest opcjonalne. Ponieważ `student.LastName` jest ciągiem, wykonanie kwerendy zwraca sekwencję ciągów. W związku z `queryID` tym typ `System.Collections.Generic.IEnumerable<string>` można `var`zadeklarować jako zamiast . Słowo `var` kluczowe jest używane dla wygody. W tym przykładzie zmienna iteracji w `foreach` instrukcji jest jawnie wpisany jako ciąg, `var`ale zamiast tego może być zadeklarowany przy użyciu . Ponieważ typ zmiennej iteracji nie jest typem `var` anonimowym, użycie jest opcją, a nie wymaganiem. Należy `var` pamiętać, sam nie jest typem, ale instrukcja do kompilatora, aby wywnioskować i przypisać typ.  
  
 [!code-csharp[csProgGuideLINQ#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#33)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Metody rozszerzeń](./extension-methods.md)
- [LINQ (zapytanie zintegrowane z językiem)](../../linq/index.md)
- [Var](../../language-reference/keywords/var.md)
- [LINQ w C#](../../linq/index.md)
