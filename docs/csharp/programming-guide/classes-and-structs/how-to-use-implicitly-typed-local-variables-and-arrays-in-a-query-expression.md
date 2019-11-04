---
title: 'Instrukcje: użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: 3cb47f9e80e1fc067a8bac860aa06f3e1860d33d
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419318"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Porady: użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu kwerendy (Przewodnik programowania w języku C#)
Możesz użyć niejawnie wpisanych zmiennych lokalnych, ilekroć kompilator ma określić typ zmiennej lokalnej. Należy użyć niejawnie wpisanych zmiennych lokalnych do przechowywania typów anonimowych, które są często używane w wyrażeniach zapytań. Poniższe przykłady ilustrują opcjonalne i wymagane zastosowania niejawnie wpisanych zmiennych lokalnych w zapytaniach.  
  
 Niejawnie wpisane zmienne lokalne są deklarowane przy użyciu słowa kluczowego [var](../../language-reference/keywords/var.md) . Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](./implicitly-typed-local-variables.md) i [niejawnie wpisane tablice](../arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono typowy scenariusz, w którym jest wymagane `var` słowo kluczowe: wyrażenie zapytania, które tworzy sekwencję typów anonimowych. W tym scenariuszu zarówno zmienna zapytania, jak i Zmienna iteracji w instrukcji `foreach` muszą być wpisane niejawnie przy użyciu `var`, ponieważ nie masz dostępu do nazwy typu dla typu anonimowego. Aby uzyskać więcej informacji na temat typów anonimowych, zobacz [Typy anonimowe](./anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#32)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto słowa kluczowego `var` w podobnej sytuacji, ale w której użycie `var` jest opcjonalne. Ponieważ `student.LastName` jest ciągiem, wykonywanie zapytania zwraca sekwencję ciągów. W związku z tym typ `queryID` może być zadeklarowany jako `System.Collections.Generic.IEnumerable<string>` zamiast `var`. `var` słów kluczowych jest używana w celu wygody. W przykładzie zmienna iteracji w instrukcji `foreach` jest jawnie wpisana jako ciąg, ale zamiast tego można ją zadeklarować przy użyciu `var`. Ponieważ typ zmiennej iteracji nie jest typem anonimowym, użycie `var` jest opcją, a nie wymaganiem. Pamiętaj, `var` sam nie jest typem, ale instrukcją kompilatora do wnioskowania i przypisania typu.  
  
 [!code-csharp[csProgGuideLINQ#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#33)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Metody rozszerzeń](./extension-methods.md)
- [LINQ (zapytanie zintegrowane z językiem)](../../linq/index.md)
- [var](../../language-reference/keywords/var.md)
- [LINQ w C#](../../linq/index.md)
