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
ms.openlocfilehash: aceda6cfd33a53388a5afb046359c4dcfddfd1f8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602020"
---
# <a name="where-clause-c-reference"></a>Klauzula where (odwołanie w C#)

`where` Klauzula jest używana w wyrażeniu zapytania, aby określić, które elementy ze źródła danych będą zwracane w wyrażeniu zapytania. Stosuje warunek logiczny (*predykat*) do każdego elementu źródłowego (do którego odwołuje się zmienna zakresu) i zwraca te, dla których określony warunek ma wartość true. Pojedyncze wyrażenie zapytania może zawierać wiele `where` klauzul, a pojedyncza klauzula może zawierać wiele podwyrażeń predykatu.

## <a name="example"></a>Przykład

W poniższym przykładzie `where` klauzula filtruje wszystkie liczby z wyjątkiem tych, które są mniejsze niż pięć. Usunięcie `where` klauzuli spowoduje zwrócenie wszystkich liczb ze źródła danych. Wyrażenie `num < 5` jest predykatem, który jest stosowany do każdego elementu.

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a>Przykład

W obrębie jednej `where` klauzuli można określić dowolną liczbę predykatów, [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) używając operatorów i [ &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) . W poniższym przykładzie zapytanie określa dwa predykaty w celu wybrania tylko liczb parzystych mniejszych niż pięć.

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a>Przykład

`where` Klauzula może zawierać jedną lub więcej metod, które zwracają wartości logiczne. W poniższym przykładzie `where` klauzula używa metody, aby określić, czy bieżąca wartość zmiennej zakresu jest parzysta czy nieparzysta.

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a>Uwagi

`where` Klauzula jest mechanizmem filtrowania. Można ją umieścić niemal w dowolnym miejscu w wyrażeniu zapytania, z wyjątkiem sytuacji, w której nie może być pierwszą lub ostatnią klauzulą. Klauzula może pojawić się przed lub po klauzuli Group w zależności od tego, czy konieczne jest Filtrowanie elementów źródłowych przed lub po zgrupowaniu. [](group-clause.md) `where`

Jeśli określony predykat jest nieprawidłowy dla elementów w źródle danych, zostanie zwrócony błąd czasu kompilacji. Jest to jedna korzyść dla ścisłego sprawdzania typu zapewnianego przez [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].

W czasie `where` kompilacji słowo kluczowe jest konwertowane na wywołanie <xref:System.Linq.Enumerable.Where%2A> metody standardowego operatora zapytań.

## <a name="see-also"></a>Zobacz także

- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [from, klauzula](from-clause.md)
- [select, klauzula](select-clause.md)
- [Filtrowanie danych](../../programming-guide/concepts/linq/filtering-data.md)
- [Wyrażenia zapytania LINQ](../../programming-guide/linq-query-expressions/index.md)
- [Wprowadzenie do korzystania z LINQ w C#](../../programming-guide/concepts/linq/getting-started-with-linq.md)
