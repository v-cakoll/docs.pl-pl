---
title: gdzie klauzula - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 33616e4eacb484b9c6eda3862cd86fdd1e6df165
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173487"
---
# <a name="where-clause-c-reference"></a>Klauzula where (odwołanie w C#)

Klauzula `where` jest używana w wyrażeniu kwerendy, aby określić, które elementy ze źródła danych zostaną zwrócone w wyrażeniu kwerendy. Stosuje warunek logiczny *(predykat)* do każdego elementu źródłowego (odwołuje się do zmiennej zakresu) i zwraca te, dla których określony warunek jest spełniony. Wyrażenie pojedynczej kwerendy `where` może zawierać wiele klauzul, a pojedyncza klauzula może zawierać wiele podwyrażeń predykatu.

## <a name="example"></a>Przykład

W poniższym przykładzie `where` klauzula odfiltrowuje wszystkie liczby z wyjątkiem tych, które są mniejsze niż pięć. Jeśli usuniesz klauzulę, `where` wszystkie numery ze źródła danych zostaną zwrócone. Wyrażenie `num < 5` jest predykatem, który jest stosowany do każdego elementu.

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a>Przykład

W ramach `where` jednej klauzuli można określić tyle predykatów, ile jest to konieczne przy użyciu [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) i [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operatorów. W poniższym przykładzie kwerenda określa dwa predykaty, aby wybrać tylko liczby parzyste, które są mniejsze niż pięć.

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a>Przykład

Klauzula `where` może zawierać jedną lub więcej metod, które zwracają wartości logiczne. W poniższym przykładzie `where` klauzula używa metody, aby określić, czy bieżąca wartość zmiennej zakresu jest parzysta czy nieparzysta.

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a>Uwagi

Klauzula `where` jest mechanizmfiltrowania. Może być umieszczony prawie w dowolnym miejscu w wyrażeniu zapytania, z wyjątkiem nie może być pierwszą lub ostatnią klauzulą. Klauzula `where` może pojawić się przed lub po klauzuli [grupy](group-clause.md) w zależności od tego, czy trzeba filtrować elementy źródłowe przed lub po ich zgrupowaniu.

Jeśli określony predykat nie jest prawidłowy dla elementów w źródle danych, wystąpi błąd w czasie kompilacji. Jest to jedna z zalet silnego sprawdzania typu zapewnianego przez LINQ.

W czasie kompilacji `where` słowo kluczowe jest konwertowane na wywołanie do standardowego <xref:System.Linq.Enumerable.Where%2A> operatora kwerendy metody.

## <a name="see-also"></a>Zobacz też

- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [z klauzuli](from-clause.md)
- [klauzula wyboru](select-clause.md)
- [Filtrowanie danych](../../programming-guide/concepts/linq/filtering-data.md)
- [LINQ w C#](../../linq/index.md)
- [Language Integrated Query (LINQ)](../../programming-guide/concepts/linq/index.md)
