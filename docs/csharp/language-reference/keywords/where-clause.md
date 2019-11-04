---
title: klauzula WHERE- C# Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 15df6339cec9eabadf5aa4c184d7504c4e065032
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421933"
---
# <a name="where-clause-c-reference"></a>Klauzula where (odwołanie w C#)

Klauzula `where` jest używana w wyrażeniu zapytania, aby określić, które elementy ze źródła danych będą zwracane w wyrażeniu zapytania. Stosuje warunek logiczny (*predykat*) do każdego elementu źródłowego (do którego odwołuje się zmienna zakresu) i zwraca te, dla których określony warunek ma wartość true. Pojedyncze wyrażenie zapytania może zawierać wiele klauzul `where`, a pojedyncza klauzula może zawierać wiele podwyrażeń predykatu.

## <a name="example"></a>Przykład

W poniższym przykładzie klauzula `where` filtruje wszystkie liczby z wyjątkiem tych, które są mniejsze niż pięć. Jeśli usuniesz klauzulę `where`, zostaną zwrócone wszystkie liczby ze źródła danych. Wyrażenie `num < 5` jest predykatem stosowanym do każdego elementu.

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a>Przykład

W ramach jednej klauzuli `where` można określić dowolną liczbę predykatów, używając [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) i [ &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operatorów. W poniższym przykładzie zapytanie określa dwa predykaty w celu wybrania tylko liczb parzystych mniejszych niż pięć.

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a>Przykład

Klauzula `where` może zawierać jedną lub więcej metod, które zwracają wartości logiczne. W poniższym przykładzie klauzula `where` używa metody, aby określić, czy bieżąca wartość zmiennej zakresu jest parzysta czy nieparzysta.

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a>Uwagi

Klauzula `where` jest mechanizmem filtrowania. Można ją umieścić niemal w dowolnym miejscu w wyrażeniu zapytania, z wyjątkiem sytuacji, w której nie może być pierwszą lub ostatnią klauzulą. Klauzula `where` może pojawić się przed lub po klauzuli [Group](group-clause.md) w zależności od tego, czy należy filtrować elementy źródłowe przed lub po zgrupowaniu.

Jeśli określony predykat jest nieprawidłowy dla elementów w źródle danych, zostanie zwrócony błąd czasu kompilacji. Jest to jedna z zalet ścisłego sprawdzania typu zapewnianego przez [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].

W czasie kompilacji słowo kluczowe `where` jest konwertowane na wywołanie metody standardowego operatora zapytań <xref:System.Linq.Enumerable.Where%2A>.

## <a name="see-also"></a>Zobacz także

- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [from, klauzula](from-clause.md)
- [select, klauzula](select-clause.md)
- [Filtrowanie danych](../../programming-guide/concepts/linq/filtering-data.md)
- [LINQ w C#](../../linq/index.md)
- [Wprowadzenie do korzystania z LINQ w C#](/dotnet/csharp/programming-guide/concepts/linq/)
