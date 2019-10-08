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
ms.openlocfilehash: 184077f2689eb64e4373d407913eefcc03b795c2
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005720"
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
|`element`|Wymagany. Zmienna kontroli dla połączonej kolekcji.|  
|`type`|Opcjonalny. Typ `element`. Jeśli nie określono `type`, typ `element` jest wnioskowany z `collection`.|  
|`collection`|Wymagany. Kolekcja, która ma zostać połączona z kolekcją znajdującą się po lewej stronie operatora `Group Join`. Klauzula `Group Join` może być zagnieżdżona w klauzuli `Join` lub w innej klauzuli `Group Join`.|  
|`key1` `Equals` `key2`|Wymagany. Identyfikuje klucze dla kolekcji, które są sprzężone. Należy użyć operatora `Equals`, aby porównać klucze z kolekcji, które są sprzężone. Możesz połączyć warunki sprzężenia przy użyciu operatora `And`, aby zidentyfikować wiele kluczy. Parametr `key1` musi znajdować się w kolekcji po lewej stronie operatora `Join`. Parametr `key2` musi znajdować się w kolekcji po prawej stronie operatora `Join`.<br /><br /> Klucze używane w warunku sprzężenia mogą być wyrażeniami, które zawierają więcej niż jeden element z kolekcji. Jednak każde wyrażenie klucza może zawierać tylko elementy z odpowiedniej kolekcji.|  
|`expressionList`|Wymagany. Co najmniej jedno wyrażenie określające sposób agregowania grup elementów z kolekcji. Aby zidentyfikować nazwę elementu członkowskiego pogrupowanych wyników, użyj słowa kluczowego `Group` (`<alias> = Group`). Można również dołączyć funkcje agregujące, które mają zostać zastosowane do grupy.|  
  
## <a name="remarks"></a>Uwagi  
 Klauzula `Group Join` łączy dwie kolekcje na podstawie pasujących wartości klucza z kolekcji, które są sprzężone. Kolekcja wyników może zawierać element członkowski, który odwołuje się do kolekcji elementów z drugiej kolekcji, która pasuje do wartości klucza z pierwszej kolekcji. Można również określić funkcje agregujące, które mają być stosowane do zgrupowanych elementów z drugiej kolekcji. Aby uzyskać informacje o funkcjach agregujących, zobacz [klauzula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Rozważmy na przykład kolekcję menedżerów i kolekcję pracowników. Elementy z obu kolekcji mają właściwość ManagerID, która identyfikuje pracowników, którzy raportują do określonego Menedżera. Wyniki operacji JOIN zawierają wyniki dla każdego menedżera i pracownika o pasującej wartości ManagerID. Wyniki operacji `Group Join` będą zawierać pełną listę menedżerów. Każdy wynik menedżera będzie miał element członkowski, który odwołuje się do listy pracowników, którzy byli zgodni z określonym menedżerem.  
  
 Kolekcja będąca wynikiem operacji `Group Join` może zawierać dowolną kombinację wartości z kolekcji identyfikowanej w klauzuli `From` i wyrażeń zidentyfikowanych w klauzuli `Into` klauzuli `Group Join`. Aby uzyskać więcej informacji na temat prawidłowych wyrażeń dla klauzuli `Into`, zobacz [Aggregate — klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Operacja `Group Join` zwróci wszystkie wyniki z kolekcji identyfikowanej po lewej stronie operatora `Group Join`. Ta wartość jest prawdziwa nawet wtedy, gdy nie ma żadnych dopasowań w kolekcji. Jest to podobne do `LEFT OUTER JOIN` w SQL.  
  
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
