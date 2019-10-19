---
title: Join — Klauzula (Visual Basic)
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
ms.openlocfilehash: b5211d0ed3f618013dc9fe764a6d7b2db8177c26
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582293"
---
# <a name="join-clause-visual-basic"></a>Join — Klauzula (Visual Basic)

Łączy dwie kolekcje w jedną kolekcję. Operacja join jest oparta na zgodnych kluczach i używa operatora `Equals`.

## <a name="syntax"></a>Składnia

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a>Części

Wymagane `element`. Zmienna kontroli dla połączonej kolekcji.

`collection`  
Wymagany. Kolekcja do połączenia z kolekcją zidentyfikowaną po lewej stronie operatora `Join`. Klauzula `Join` może być zagnieżdżona w innej klauzuli `Join` lub w klauzuli `Group Join`.

`joinClause`  
Opcjonalny. Co najmniej jednej z dodatkowych klauzul `Join` w celu dodatkowego uściślenia zapytania.

`groupJoinClause`  
Opcjonalny. Co najmniej jednej z dodatkowych klauzul `Group Join` w celu dodatkowego uściślenia zapytania.

`key1` `Equals` `key2`  
Wymagany. Identyfikuje klucze dla kolekcji, które są sprzężone. Należy użyć operatora `Equals`, aby porównać klucze z kolekcji, które są sprzężone. Możesz połączyć warunki sprzężenia przy użyciu operatora `And`, aby zidentyfikować wiele kluczy. `key1` musi znajdować się w kolekcji po lewej stronie operatora `Join`. `key2` musi pochodzić z kolekcji po prawej stronie operatora `Join`.

Klucze używane w warunku sprzężenia mogą być wyrażeniami, które zawierają więcej niż jeden element z kolekcji. Jednak każde wyrażenie klucza może zawierać tylko elementy z odpowiedniej kolekcji.

## <a name="remarks"></a>Uwagi

Klauzula `Join` łączy dwie kolekcje na podstawie pasujących wartości klucza z kolekcji, które są sprzężone. Kolekcja wyników może zawierać dowolną kombinację wartości z kolekcji identyfikowanej po lewej stronie operatora `Join` i kolekcji identyfikowanej w klauzuli `Join`. Zapytanie zwróci tylko wyniki, dla których spełniony jest warunek określony przez operator `Equals`. Jest to odpowiednik `INNER JOIN` w SQL.

W zapytaniu można użyć wielu klauzul `Join` w celu dołączenia dwóch lub większej liczby kolekcji do pojedynczej kolekcji.

Można wykonać niejawne sprzężenie w celu łączenia kolekcji bez klauzuli `Join`. W tym celu należy uwzględnić wiele klauzul `In` w klauzuli `From` i określić klauzulę `Where`, która identyfikuje klucze, które mają być używane dla sprzężenia.

Można użyć klauzuli `Group Join`, aby połączyć kolekcje w jedną hierarchiczną kolekcję. Jest to podobne do `LEFT OUTER JOIN` w SQL.

## <a name="example"></a>Przykład

Poniższy przykład kodu wykonuje niejawne sprzężenie w celu połączenia listy klientów z ich zamówieniami.

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a>Przykład

Poniższy przykład kodu łączy dwie kolekcje przy użyciu klauzuli `Join`.

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

Ten przykład generuje dane wyjściowe podobne do następujących:

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a>Przykład

Poniższy przykład kodu łączy dwie kolekcje przy użyciu klauzuli `Join` z dwiema kolumnami klucza.

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

Przykład generuje dane wyjściowe podobne do następujących:

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Group Join, klauzula](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
