---
title: "Join — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2bb25c9dac8994e7f975539c1d036f0f0d9d239e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="join-clause-visual-basic"></a>Join — Klauzula (Visual Basic)
Łączy dwie kolekcje do jednej kolekcji. Operacja łączenia jest oparta na zgodności kluczy i używa `Equals` operatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a>Części  
 `element`  
 Wymagany. Zmienna sterująca dla kolekcji jest dołączony.  
  
 `collection`  
 Wymagany. Kolekcja do łączenia z tą kolekcją zidentyfikowane po lewej stronie `Join` operatora. A `Join` klauzuli mogą być zagnieżdżone w innym `Join` klauzuli lub `Group Join` klauzuli.  
  
 `joinClause`  
 Opcjonalny. Jeden lub więcej dodatkowych `Join` klauzule dalsze uściślenie kwerendy.  
  
 `groupJoinClause`  
 Opcjonalny. Jeden lub więcej dodatkowych `Group Join` klauzule dalsze uściślenie kwerendy.  
  
 `key1` `Equals` `key2`  
 Wymagany. Określa klucze w kolekcji jest dołączony. Należy użyć `Equals` operatora, aby porównać klucze z kolekcji jest dołączony. Warunki sprzężenia można połączyć za pomocą `And` operatora, aby zidentyfikować wielu kluczy. `key1`musi pochodzić z kolekcji po lewej stronie `Join` operatora. `key2`musi pochodzić z kolekcji w prawej części `Join` operatora.  
  
 Klucze używane w warunek sprzężenia można wyrażeń, które zawierają więcej niż jeden element z kolekcji. Każde wyrażenie klucza może jednak zawierać tylko elementy z jego odpowiednich kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 `Join` Klauzuli łączy dwie kolekcje oparte na zgodności kluczy wartości z kolekcji jest dołączony. Wynikowa Kolekcja może zawierać dowolną kombinację wartości z kolekcji zidentyfikowane po lewej stronie `Join` operatora i kolekcji objęci `Join` klauzuli. Zwraca tylko wyniki, dla których warunek określony przez `Equals` operator jest spełniony. Jest to równoważne `INNER JOIN` w języku SQL.  
  
 Można użyć wielu `Join` klauzule zapytanie w celu dołączenia dwóch lub więcej kolekcji do jednej kolekcji.  
  
 Można wykonywać niejawne sprzężenia połączyć kolekcji bez `Join` klauzuli. Aby to zrobić, zawierają wiele `In` klauzul w Twojej `From` klauzuli i określ `Where` klauzulę identyfikującą kluczy, które ma być używany w celu utworzenia sprzężenia.  
  
 Można użyć `Group Join` klauzuli połączyć kolekcji do jednej kolekcji hierarchicznej. Przypomina to `LEFT OUTER JOIN` w języku SQL.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykonuje sprzężenie niejawne połączyć listę klientów z ich zleceń.  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu łączy dwie kolekcje przy użyciu `Join` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 W tym przykładzie utworzy dane wyjściowe podobne do następującego:  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu łączy dwie kolekcje przy użyciu `Join` klauzuli z dwiema kolumnami klucza.  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 Przykład utworzy dane wyjściowe podobne do następującego:  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [SELECT — klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzula FROM](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Group Join — klauzula](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Gdy klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
