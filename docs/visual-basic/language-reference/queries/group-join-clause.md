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
ms.openlocfilehash: 7916e51293c06016b2581b7109df3f0a599404ca
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359839"
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
|`type`|Opcjonalny. Typ `element` . Jeśli nie `type` jest określony, typ `element` jest wnioskowany z `collection` .|  
|`collection`|Wymagany. Kolekcja, która ma zostać połączona z kolekcją znajdującą się po lewej stronie `Group Join` operatora. `Group Join`Klauzula może być zagnieżdżona w `Join` klauzuli lub w innej `Group Join` klauzuli.|  
|`key1` `Equals` `key2`|Wymagany. Identyfikuje klucze dla kolekcji, które są sprzężone. Należy użyć operatora, `Equals` Aby porównać klucze z kolekcji, które są sprzężone. Możesz połączyć warunki sprzężenia przy użyciu `And` operatora, aby zidentyfikować wiele kluczy. `key1`Parametr musi znajdować się w kolekcji po lewej stronie `Join` operatora. `key2`Parametr musi znajdować się w kolekcji po prawej stronie `Join` operatora.<br /><br /> Klucze używane w warunku sprzężenia mogą być wyrażeniami, które zawierają więcej niż jeden element z kolekcji. Jednak każde wyrażenie klucza może zawierać tylko elementy z odpowiedniej kolekcji.|  
|`expressionList`|Wymagany. Co najmniej jedno wyrażenie określające sposób agregowania grup elementów z kolekcji. Aby zidentyfikować nazwę elementu członkowskiego pogrupowanych wyników, użyj `Group` słowa kluczowego ( `<alias> = Group` ). Można również dołączyć funkcje agregujące, które mają zostać zastosowane do grupy.|  
  
## <a name="remarks"></a>Uwagi  
 `Group Join`Klauzula łączy dwie kolekcje na podstawie pasujących wartości klucza z kolekcji, które są sprzężone. Kolekcja wyników może zawierać element członkowski, który odwołuje się do kolekcji elementów z drugiej kolekcji, która pasuje do wartości klucza z pierwszej kolekcji. Można również określić funkcje agregujące, które mają być stosowane do zgrupowanych elementów z drugiej kolekcji. Aby uzyskać informacje o funkcjach agregujących, zobacz [klauzula Aggregate](aggregate-clause.md).  
  
 Rozważmy na przykład kolekcję menedżerów i kolekcję pracowników. Elementy z obu kolekcji mają właściwość ManagerID, która identyfikuje pracowników, którzy raportują do określonego Menedżera. Wyniki operacji JOIN zawierają wyniki dla każdego menedżera i pracownika o pasującej wartości ManagerID. Wyniki `Group Join` operacji będą zawierać pełną listę menedżerów. Każdy wynik menedżera będzie miał element członkowski, który odwołuje się do listy pracowników, którzy byli zgodni z określonym menedżerem.  
  
 Kolekcja będąca wynikiem `Group Join` operacji może zawierać dowolną kombinację wartości z kolekcji identyfikowanej w `From` klauzuli i wyrażeń określonych w `Into` klauzuli `Group Join` klauzuli. Aby uzyskać więcej informacji na temat prawidłowych wyrażeń dla `Into` klauzuli, zobacz [Aggregate Group](aggregate-clause.md).  
  
 `Group Join`Operacja zwróci wszystkie wyniki z kolekcji identyfikowanej po lewej stronie `Group Join` operatora. Ta wartość jest prawdziwa nawet wtedy, gdy nie ma żadnych dopasowań w kolekcji. Jest to podobne do `LEFT OUTER JOIN` języka SQL.  
  
 Możesz użyć klauzuli, `Join` Aby połączyć kolekcje w jedną kolekcję. Jest to odpowiednik `INNER JOIN` w programie SQL Server.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu łączy dwie kolekcje przy użyciu `Group Join` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do LINQ w Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](index.md)
- [SELECT — klauzula](select-clause.md)
- [Klauzula from](from-clause.md)
- [Klauzula join](join-clause.md)
- [Klauzula WHERE](where-clause.md)
- [Group By, klauzula](group-by-clause.md)
