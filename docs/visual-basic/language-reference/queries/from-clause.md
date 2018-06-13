---
title: From — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: 1f113444efae83de7d299db330593937c7800bb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604721"
---
# <a name="from-clause-visual-basic"></a>From — Klauzula (Visual Basic)
Określa co najmniej jednej zmiennej zakresu i kolekcji do zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`element`|Wymagana. A *zmiennej zakresu* używany do iterowania po elementach kolekcji. Zmienna zakresu jest używana do odwoływania się do każdego elementu członkowskiego `collection` jako zapytanie iteruje `collection`. Musi być typem wyliczenia.|  
|`type`|Opcjonalna. Typ `element`. Jeśli nie `type` jest określony typ `element` jest wywnioskowany na podstawie `collection`.|  
|`collection`|Wymagana. Odnosi się do kolekcji można wykonać zapytania. Musi być typem wyliczenia.|  
  
## <a name="remarks"></a>Uwagi  
 `From` Klauzuli służy do identyfikowania źródło danych pod kątem zapytania i zmienne, które są używane do odwoływania się do elementu z kolekcji źródłowej. Te zmienne są nazywane *zmienne zakresu*. `From` Klauzuli jest wymagany dla zapytania, chyba że `Aggregate` klauzuli służy do identyfikowania czy zwraca tylko zagregowane wyników zapytania. Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Można określić wiele `From` klauzule zapytań do identyfikowania wielu kolekcji ma zostać umieszczony. Jeśli określono wiele kolekcji, są one niezależnie iterowane za pośrednictwem lub można je dołączenia, jeśli są one powiązane. Dołącz kolekcje niejawnie za pomocą `Select` klauzuli, lub jawnie za pomocą `Join` lub `Group Join` klauzul. Alternatywnie, można określić wiele zmiennych zakresu i kolekcji w jednej `From` klauzuli z każdej zmiennej zakresu pokrewne i pobierania od siebie oddzielone przecinkami. Poniższy przykład kodu pokazuje obie opcje składni `From` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 `From` Klauzuli określa zakres kwerendę, która jest podobna do zakresu `For` pętli. W związku z tym każdy `element` zmiennej zakresu w zakresie zapytania musi mieć unikatową nazwę. Ponieważ można określić wiele `From` klauzule dla zapytania, kolejne `From` klauzule mogą odwoływać się do zmiennych zakresu w `From` klauzuli lub może dotyczyć zmiennych zakresu w poprzednim `From` klauzuli. Na przykład w poniższym przykładzie przedstawiono zagnieżdżoną `From` klauzuli gdzie kolekcji w klauzuli drugi opiera się na właściwość zmienną zakresu, w pierwszej klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 Każdy `From` klauzula może występować przez dowolną kombinację klauzule zapytań dodatkowe kwerendzie. Zapytania można dostosować w następujący sposób:  
  
-   Łączenie wielu kolekcji niejawnie za pomocą `From` i `Select` klauzule, lub jawnie za pomocą `Join` lub `Group Join` klauzul.  
  
-   Użyj `Where` klauzuli filtrowanie wyników zapytania.  
  
-   Sortowanie wyników za pomocą `Order By` klauzuli.  
  
-   Grupowania podobnych wyników przy użyciu `Group By` klauzuli.  
  
-   Użyj `Aggregate` klauzuli do identyfikowania funkcji agregujących można obliczyć wyniku zapytania całego.  
  
-   Użyj `Let` klauzuli wprowadzenie zmiennej iteracji, którego wartość jest określona przez wyrażenie zamiast kolekcji.  
  
-   Użyj `Distinct` klauzuli zignorowanie wyniki zduplikowane zapytanie.  
  
-   Identyfikowanie części wyników do zwrócenia przy użyciu `Skip`, `Take`, `Skip While`, i `Take While` klauzul.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie używa wyrażenia `From` klauzuli, aby zadeklarować zmienną zakresu `cust` dla każdego `Customer` obiektu w `customers` kolekcji. `Where` Klauzuli używa zmiennej zakresu, aby ograniczyć dane wyjściowe do klientów z określonego regionu. `For Each` Pętli Wyświetla nazwę firmy dla każdego klienta w wyniku zapytania.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Aggregate, klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Distinct, klauzula](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [Join, klauzula](../../../visual-basic/language-reference/queries/join-clause.md)  
 [Group Join, klauzula](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Order By, klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Let, klauzula](../../../visual-basic/language-reference/queries/let-clause.md)  
 [Skip, klauzula](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Take, klauzula](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Skip While, klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take While, klauzula](../../../visual-basic/language-reference/queries/take-while-clause.md)
