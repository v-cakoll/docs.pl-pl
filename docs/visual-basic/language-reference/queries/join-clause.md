---
title: Join, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: f73dc31bbbb9014a8a1a315de406c53fa58d1c65
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359777"
---
# <a name="join-clause-visual-basic"></a>Join — Klauzula (Visual Basic)

Łączy dwie kolekcje w jedną kolekcję. Operacja join jest oparta na zgodnych kluczach i używa `Equals` operatora.

## <a name="syntax"></a>Składnia

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a>Części

`element`Wymagane. Zmienna kontroli dla połączonej kolekcji.

`collection`  
Wymagany. Kolekcja do połączenia z kolekcją zidentyfikowaną po lewej stronie `Join` operatora. `Join`Klauzula może być zagnieżdżona w innej `Join` klauzuli lub w `Group Join` klauzuli.

`joinClause`  
Opcjonalny. Co najmniej jednej `Join` z dodatkowych klauzul, aby dodatkowo uściślić zapytanie.

`groupJoinClause`  
Opcjonalny. Co najmniej jednej `Group Join` z dodatkowych klauzul, aby dodatkowo uściślić zapytanie.

`key1` `Equals` `key2`  
Wymagany. Identyfikuje klucze dla kolekcji, które są sprzężone. Należy użyć operatora, `Equals` Aby porównać klucze z kolekcji, które są sprzężone. Możesz połączyć warunki sprzężenia przy użyciu `And` operatora, aby zidentyfikować wiele kluczy. `key1`musi znajdować się w kolekcji po lewej stronie `Join` operatora. `key2`musi znajdować się w kolekcji po prawej stronie `Join` operatora.

Klucze używane w warunku sprzężenia mogą być wyrażeniami, które zawierają więcej niż jeden element z kolekcji. Jednak każde wyrażenie klucza może zawierać tylko elementy z odpowiedniej kolekcji.

## <a name="remarks"></a>Uwagi

`Join`Klauzula łączy dwie kolekcje na podstawie pasujących wartości klucza z kolekcji, które są sprzężone. Kolekcja wyników może zawierać dowolną kombinację wartości z kolekcji identyfikowanej po lewej stronie `Join` operatora i kolekcji identyfikowanej w `Join` klauzuli. Zapytanie zwróci tylko wyniki, dla których spełniony jest warunek określony przez `Equals` operatora. Jest to odpowiednik `INNER JOIN` w programie SQL Server.

Można użyć wielu `Join` klauzul w zapytaniu, aby dołączyć dwie lub więcej kolekcji do jednej kolekcji.

Można wykonać niejawne sprzężenie w celu łączenia kolekcji bez `Join` klauzuli. W tym celu należy uwzględnić `In` w klauzuli wiele klauzul `From` i określić `Where` klauzulę, która identyfikuje klucze, które mają być używane dla sprzężenia.

Możesz użyć klauzuli, `Group Join` Aby połączyć kolekcje w pojedynczej kolekcji hierarchicznej. Jest to podobne do `LEFT OUTER JOIN` języka SQL.

## <a name="example"></a>Przykład

Poniższy przykład kodu wykonuje niejawne sprzężenie w celu połączenia listy klientów z ich zamówieniami.

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a>Przykład

Poniższy przykład kodu łączy dwie kolekcje przy użyciu `Join` klauzuli.

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

Ten przykład generuje dane wyjściowe podobne do następujących:

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a>Przykład

Poniższy przykład kodu łączy dwie kolekcje przy użyciu `Join` klauzuli z dwiema kolumnami klucza.

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

Przykład generuje dane wyjściowe podobne do następujących:

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do LINQ w Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](index.md)
- [SELECT — klauzula](select-clause.md)
- [Klauzula from](from-clause.md)
- [Group Join. klauzula](group-join-clause.md)
- [Klauzula WHERE](where-clause.md)
