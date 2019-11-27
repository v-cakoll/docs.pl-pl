---
title: Group Join. klauzula
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
ms.openlocfilehash: 0546c86322663ce6c56a89e63311d0f02f88cfe4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346845"
---
# <a name="group-join-clause-visual-basic"></a>Group Join — Klauzula (Visual Basic)
Łączy dwie kolekcje w jedną hierarchiczną kolekcję. Operacja join zależy od pasujących kluczy.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`element`|Wymagana. Zmienna kontroli dla połączonej kolekcji.|  
|`type`|Opcjonalna. Typ elementu `element`. Jeśli nie określono `type`, typ `element` zostanie wywnioskowany na podstawie `collection`.|  
|`collection`|Wymagana. Kolekcja, która ma zostać połączona z kolekcją znajdującą się po lewej stronie operatora `Group Join`. Klauzula `Group Join` może być zagnieżdżona w klauzuli `Join` lub w innej klauzuli `Group Join`.|  
|`key1` `Equals` `key2`|Wymagana. Identyfikuje klucze dla kolekcji, które są sprzężone. Należy użyć operatora `Equals`, aby porównać klucze z kolekcji, które są sprzężone. Możesz połączyć warunki sprzężenia przy użyciu operatora `And`, aby zidentyfikować wiele kluczy. Parametr `key1` musi znajdować się w kolekcji po lewej stronie operatora `Join`. Parametr `key2` musi znajdować się w kolekcji po prawej stronie operatora `Join`.<br /><br /> Klucze używane w warunku sprzężenia mogą być wyrażeniami, które zawierają więcej niż jeden element z kolekcji. Jednak każde wyrażenie klucza może zawierać tylko elementy z odpowiedniej kolekcji.|  
|`expressionList`|Wymagana. Co najmniej jedno wyrażenie określające sposób agregowania grup elementów z kolekcji. Aby zidentyfikować nazwę elementu członkowskiego pogrupowanych wyników, użyj słowa kluczowego `Group` (`<alias> = Group`). Można również dołączyć funkcje agregujące, które mają zostać zastosowane do grupy.|  
  
## <a name="remarks"></a>Uwagi  
 Klauzula `Group Join` łączy dwie kolekcje na podstawie pasujących wartości klucza z kolekcji, które są sprzężone. Kolekcja wyników może zawierać element członkowski, który odwołuje się do kolekcji elementów z drugiej kolekcji, która pasuje do wartości klucza z pierwszej kolekcji. Można również określić funkcje agregujące, które mają być stosowane do zgrupowanych elementów z drugiej kolekcji. Aby uzyskać informacje o funkcjach agregujących, zobacz [klauzula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Rozważmy na przykład kolekcję menedżerów i kolekcję pracowników. Elementy z obu kolekcji mają właściwość ManagerID, która identyfikuje pracowników, którzy raportują do określonego Menedżera. Wyniki operacji JOIN zawierają wyniki dla każdego menedżera i pracownika o pasującej wartości ManagerID. Wyniki operacji `Group Join` mogą zawierać pełną listę menedżerów. Każdy wynik menedżera będzie miał element członkowski, który odwołuje się do listy pracowników, którzy byli zgodni z określonym menedżerem.  
  
 Kolekcja będąca wynikiem operacji `Group Join` może zawierać dowolną kombinację wartości z kolekcji identyfikowanej w klauzuli `From` i wyrażeń określonych w klauzuli `Into` klauzuli `Group Join`. Aby uzyskać więcej informacji na temat prawidłowych wyrażeń dla klauzuli `Into`, zobacz [Aggregate Group](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Operacja `Group Join` zwróci wszystkie wyniki z kolekcji identyfikowanej po lewej stronie operatora `Group Join`. Ta wartość jest prawdziwa nawet wtedy, gdy nie ma żadnych dopasowań w kolekcji. Jest to takie samo jak `LEFT OUTER JOIN` w programie SQL Server.  
  
 Do łączenia kolekcji z jedną kolekcją można użyć klauzuli `Join`. Jest to odpowiednik `INNER JOIN` w SQL.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu łączy dwie kolekcje przy użyciu klauzuli `Group Join`.  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Join, klauzula](../../../visual-basic/language-reference/queries/join-clause.md)
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
- [Group By, klauzula](../../../visual-basic/language-reference/queries/group-by-clause.md)
