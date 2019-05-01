---
title: Group Join — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
ms.openlocfilehash: 3da4ca2db299a65b2c0f1fa259bbaabe4f53aa33
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945317"
---
# <a name="group-join-clause-visual-basic"></a>Group Join — Klauzula (Visual Basic)
Łączy dwie kolekcje w jedną hierarchiczną kolekcję. Operacja łączenia jest oparta na zgodności kluczy.  
  
## <a name="syntax"></a>Składnia  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`element`|Wymagana. Zmienna sterująca dla kolekcji jest dołączony.|  
|`type`|Opcjonalna. Typ `element`. Jeśli nie `type` jest określona, typ `element` wynika z `collection`.|  
|`collection`|Wymagana. Kolekcja do łączenia z tą kolekcją, która znajduje się w lewej części `Group Join` operatora. A `Group Join` klauzuli może być zagnieżdżona w `Join` klauzuli lub w innym `Group Join` klauzuli.|  
|`key1` `Equals` `key2`|Wymagana. Określa klucze dla kolekcji jest dołączony. Należy użyć `Equals` operatora do porównywania kluczy z kolekcji jest dołączony. Warunki sprzężenia można połączyć za pomocą `And` operatora, aby zidentyfikować wielu kluczy. `key1` Parametr musi być z kolekcji w lewej części `Join` operatora. `key2` Parametr musi mieć długość od kolekcji na prawej krawędzi `Join` operatora.<br /><br /> Klucze używane w warunek sprzężenia, może być wyrażeń, które zawierają więcej niż jeden element z kolekcji. Jednak każde wyrażenie kluczy może zawierać tylko elementy z jego odpowiednich kolekcji.|  
|`expressionList`|Wymagana. Co najmniej jednego wyrażenia, które określają, jak są agregowane grup elementów z kolekcji. Aby zidentyfikować nazwę elementu członkowskiego pogrupowane wyniki, należy użyć `Group` — słowo kluczowe (`<alias> = Group`). Może również zawierać funkcje agregujące do zastosowania w grupie.|  
  
## <a name="remarks"></a>Uwagi  
 `Group Join` Klauzuli łączy dwie kolekcje, w oparciu o dopasowanie wartości kluczy z kolekcji jest dołączony. Wynikowy Kolekcja może zawierać elementu członkowskiego, która odwołuje się druga kolekcja, które odpowiadają wartości klucza w pierwszej kolekcji kolekcję elementów. Można również określić funkcje agregujące do zastosowania do zgrupowanych elementów z drugiej kolekcji. Aby uzyskać informacji na temat funkcji agregujących, zobacz [Aggregate — klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Należy wziąć pod uwagę, na przykład zbiór menedżerów i kolekcji pracowników. Elementy z obu kolekcji mają właściwość ManagerID, która identyfikuje pracowników, którzy raportują do określonego menedżera. Wyniki z operacji sprzężenia zawiera wyniki dla każdego menedżera i pracownika o pasującej wartości ManagerID. Wyniki z `Group Join` operacji zawiera pełną listę menedżerów. Wynik każdego menedżera musi elementu członkowskiego, do którego odwołuje się listę pracowników, które były dopasowania dla konkretnego menedżera.  
  
 Kolekcja wynikające z `Group Join` operacji może zawierać dowolną kombinację wartości z kolekcji w `From` klauzula i wyrażenia określone w `Into` klauzuli `Group Join` klauzuli. Aby uzyskać więcej informacji dotyczących prawidłowych wyrażeń dla `Into` klauzuli, zobacz [Aggregate — klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 A `Group Join` operacji zostaną zwrócone wszystkie wyniki z kolekcji identyfikowane w lewej części `Group Join` operatora. Ta zasada obowiązuje, nawet jeśli nie ma żadnych dopasowań w kolekcji jest dołączony. Formuła ta przypomina `LEFT OUTER JOIN` w języku SQL.  
  
 Możesz użyć `Join` klauzuli połączyć kolekcje w jedną kolekcję. Jest to równoważne `INNER JOIN` w języku SQL.  
  
## <a name="example"></a>Przykład  
 Poniższy kod łączy dwie kolekcje przy użyciu `Group Join` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Join, klauzula](../../../visual-basic/language-reference/queries/join-clause.md)
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
- [Klauzula Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
