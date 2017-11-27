---
title: "Group Join — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c43b41336393b40684aee79f88c1e6999ebda674
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="group-join-clause-visual-basic"></a>Group Join — Klauzula (Visual Basic)
Łączy dwie kolekcje do jednej kolekcji hierarchicznej. Operacja łączenia jest oparta na zgodności kluczy.  
  
## <a name="syntax"></a>Składnia  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`element`|Wymagany. Zmienna sterująca dla kolekcji jest dołączony.|  
|`type`|Opcjonalny. Typ `element`. Jeśli nie `type` jest określony typ `element` jest wywnioskowany na podstawie `collection`.|  
|`collection`|Wymagany. Kolekcja do łączenia z tą kolekcją, która znajduje się w lewej części `Group Join` operatora. A `Group Join` klauzuli mogą być zagnieżdżane w `Join` klauzuli lub w innym `Group Join` klauzuli.|  
|`key1` `Equals` `key2`|Wymagany. Określa klucze w kolekcji jest dołączony. Należy użyć `Equals` operatora, aby porównać klucze z kolekcji jest dołączony. Warunki sprzężenia można połączyć za pomocą `And` operatora, aby zidentyfikować wielu kluczy. `key1` Parametr musi być z kolekcji po lewej stronie `Join` operatora. `key2` Parametr musi być z kolekcji w prawej części `Join` operatora.<br /><br /> Klucze używane w warunek sprzężenia można wyrażeń, które zawierają więcej niż jeden element z kolekcji. Każde wyrażenie klucza może jednak zawierać tylko elementy z jego odpowiednich kolekcji.|  
|`expressionList`|Wymagany. Co najmniej jednego wyrażenia, które identyfikują agregowaniem grup elementów z kolekcji. Aby zidentyfikować nazwę elementu członkowskiego grupowanych wyników, należy użyć `Group` — słowo kluczowe (`<alias> = Group`). Możesz również uwzględnić funkcje agregujące do zastosowania do grupy.|  
  
## <a name="remarks"></a>Uwagi  
 `Group Join` Klauzuli łączy dwie kolekcje oparte na zgodności kluczy wartości z kolekcji jest dołączony. Wynikowa Kolekcja może zawierać elementu członkowskiego, który odwołuje się do kolekcji elementów z druga kolekcja, która jest zgodna z wartością klucza z pierwszej kolekcji. Można również określić funkcje agregujące do zastosowania do zgrupowanych elementów z drugiej kolekcji. Aby uzyskać informacje o funkcjach agregujących, zobacz [Aggregate — klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Należy rozważyć, na przykład kolekcja menedżerów i kolekcji pracowników. Elementy z obu kolekcji mają właściwość ManagerID, która identyfikuje pracowników, którzy raportują do konkretnego menedżera. Wyniki z operacji sprzężenia zawiera wynik dla każdego manager i pracowników o pasującej wartości ManagerID. Wyniki z `Group Join` operacji zawiera pełną listę menedżerów. Każdy wynik Menedżera musi elementu członkowskiego, który odwołuje się do listy pracowników, które były zgodne dla określonego menedżera.  
  
 Kolekcja wynikające z `Group Join` operacja może zawierać dowolną kombinację wartości z kolekcji określonej w `From` klauzul i wyrażenia określone w `Into` klauzuli `Group Join` klauzuli. Aby uzyskać więcej informacji na temat prawidłowe wyrażenia dla `Into` klauzuli, zobacz [Aggregate — klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 A `Group Join` operacji zostaną zwrócone wszystkie wyniki z kolekcji zidentyfikowane po lewej stronie `Group Join` operatora. Dotyczy to nawet jeśli nie ma zgodnych wyników w kolekcji jest dołączony. Przypomina to `LEFT OUTER JOIN` w języku SQL.  
  
 Można użyć `Join` klauzuli połączyć kolekcji do jednej kolekcji. Jest to równoważne `INNER JOIN` w języku SQL.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu łączy dwie kolekcje przy użyciu `Group Join` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#14](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-join-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [SELECT — klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzula FROM](../../../visual-basic/language-reference/queries/from-clause.md)  
 [JOIN — klauzula](../../../visual-basic/language-reference/queries/join-clause.md)  
 [Gdy klauzula](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Group By — klauzula](../../../visual-basic/language-reference/queries/group-by-clause.md)
