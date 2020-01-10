---
title: Wybierz klauzulę C# -odwołanie
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: b4d25f80e4cdb08fbc28fa4db3cb1c790b1145e6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713095"
---
# <a name="select-clause-c-reference"></a>select — Klauzula (odwołanie w C#)

W wyrażeniu zapytania klauzula `select` określa typ wartości, które zostaną utworzone podczas wykonywania zapytania. Wynik jest oparty na ocenie wszystkich poprzednich klauzul i w dowolnych wyrażeniach w samej klauzuli `select`. Wyrażenie zapytania musi kończyć się klauzulą `select` lub klauzulą [Group](group-clause.md) .

W poniższym przykładzie pokazano prostą klauzulę `select` w wyrażeniu zapytania.

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

Typ sekwencji utworzonej przez klauzulę `select` określa typ zmiennej zapytania `queryHighScores`. W najprostszym przypadku klauzula `select` określa tylko zmienną zakresu. Powoduje to, że zwracana sekwencja zawiera elementy tego samego typu co źródło danych. Aby uzyskać więcej informacji, zobacz temat [relacje typu w operacjach zapytań LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). Jednak klauzula `select` zapewnia również zaawansowany mechanizm przekształcania (lub *projekcji*) danych źródłowych na nowe typy. Aby uzyskać więcej informacji, zobacz [Przekształcanie danych zaC#pomocą LINQ ()](../../programming-guide/concepts/linq/data-transformations-with-linq.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano wszystkie różne formy, które mogą wykonać `select` klauzulę. W każdym zapytaniu Zwróć uwagę na relacje między klauzulą `select` i typem *zmiennej zapytania* (`studentQuery1`, `studentQuery2`itd.).

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

Jak pokazano w `studentQuery8` w poprzednim przykładzie, czasami można chcieć, aby elementy zwracanej sekwencji zawierały tylko podzestaw właściwości elementów źródłowych. Przez pozostawienie zwróconej sekwencji jak najmniejszej ilości, można zmniejszyć wymagania dotyczące pamięci i zwiększyć szybkość wykonywania zapytania. Można to zrobić przez utworzenie typu anonimowego w klauzuli `select` i użycie inicjatora obiektów w celu zainicjowania go z odpowiednimi właściwościami z elementu źródłowego. Aby uzyskać przykład, jak to zrobić, zobacz [Inicjatory obiektów i kolekcji](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="remarks"></a>Uwagi

W czasie kompilacji klauzula `select` jest tłumaczona na wywołanie metody do standardowego operatora zapytania <xref:System.Linq.Enumerable.Select%2A>.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [from, klauzula](from-clause.md)
- [częściowe (Metoda) (C# odwołanie)](partial-method.md)
- [Typy anonimowe](../../programming-guide/classes-and-structs/anonymous-types.md)
- [LINQ w C#](../../linq/index.md)
- [Wprowadzenie do korzystania z LINQ w C#](/dotnet/csharp/programming-guide/concepts/linq/)
