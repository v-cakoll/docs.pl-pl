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
ms.openlocfilehash: b1551583079c66d1bf5f6963a42d5d24e518fff3
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "44778438"
---
# <a name="join-clause-visual-basic"></a>Join — Klauzula (Visual Basic)
Łączy dwie kolekcje w jedną kolekcję. Operacja łączenia jest oparta na zgodności kluczy i używa `Equals` operatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a>Części  
 `element`  
 Wymagane. Zmienna sterująca dla kolekcji jest dołączony.  
  
 `collection`  
 Wymagane. Kolekcja do łączenia z tą kolekcją identyfikowane w lewej części `Join` operatora. A `Join` klauzuli może być zagnieżdżona w innej `Join` klauzuli lub `Group Join` klauzuli.  
  
 `joinClause`  
 Opcjonalna. Jeden lub więcej dodatkowych `Join` klauzul, aby jeszcze bardziej zawęzić zapytanie.  
  
 `groupJoinClause`  
 Opcjonalna. Jeden lub więcej dodatkowych `Group Join` klauzul, aby jeszcze bardziej zawęzić zapytanie.  
  
 `key1` `Equals` `key2`  
 Wymagane. Określa klucze dla kolekcji jest dołączony. Należy użyć `Equals` operatora do porównywania kluczy z kolekcji jest dołączony. Warunki sprzężenia można połączyć za pomocą `And` operatora, aby zidentyfikować wielu kluczy. `key1` musi mieć długość od kolekcji w lewej części `Join` operatora. `key2` musi mieć długość od kolekcji na prawej krawędzi `Join` operatora.  
  
 Klucze używane w warunek sprzężenia, może być wyrażeń, które zawierają więcej niż jeden element z kolekcji. Jednak każde wyrażenie kluczy może zawierać tylko elementy z jego odpowiednich kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 `Join` Klauzuli łączy dwie kolekcje, w oparciu o dopasowanie wartości kluczy z kolekcji jest dołączony. Wynikowy Kolekcja może zawierać dowolną kombinację wartości z kolekcji identyfikowane w lewej części `Join` operatora i kolekcji w `Join` klauzuli. Kwerenda będzie zwracać tylko wyniki, dla których warunek określony przez `Equals` operator jest spełniony. Jest to równoważne `INNER JOIN` w języku SQL.  
  
 Możesz użyć wielu `Join` klauzul zapytania do dołączenia do co najmniej dwóch kolekcje w jedną kolekcję.  
  
 Można wykonać sprzężenie niejawne połączyć kolekcji bez `Join` klauzuli. Aby to zrobić, należy dołączyć wiele `In` klauzul swoje `From` klauzuli i określ `Where` klauzulę identyfikującą klucze, które chcesz użyć w celu utworzenia sprzężenia.  
  
 Możesz użyć `Group Join` klauzuli połączyć kolekcje w jedną hierarchiczną kolekcję. Formuła ta przypomina `LEFT OUTER JOIN` w języku SQL.  
  
## <a name="example"></a>Przykład  
 Poniższy kod wykonuje sprzężenie niejawne połączyć listę klientów z jego zamówienia.  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod łączy dwie kolekcje przy użyciu `Join` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 Ten przykład generuje dane wyjściowe podobne do następujących:  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a>Przykład  
 Poniższy kod łączy dwie kolekcje przy użyciu `Join` klauzulę zawierającą dwie kolumny klucza.  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 Przykład generuje dane wyjściowe podobne do następujących:  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/index.md)  
 [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
