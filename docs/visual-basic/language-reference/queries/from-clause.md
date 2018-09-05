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
ms.openlocfilehash: 71573de48cc51c48291fc4b82a0628d2d0f96caa
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556812"
---
# <a name="from-clause-visual-basic"></a>From — Klauzula (Visual Basic)
Określa co najmniej jednej zmiennej zakresu i kolekcji do wykonywania zapytań.  
  
## <a name="syntax"></a>Składnia  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`element`|Wymagane. A *zmiennej zakresu* używany do iterowania po elementach kolekcji. Zmienna zakresu jest używana do odwoływania się do każdego elementu członkowskiego `collection` jako zapytanie wykonuje iterację przez `collection`. Musi być typem wyliczenia.|  
|`type`|Opcjonalna. Typ `element`. Jeśli nie `type` jest określona, typ `element` wynika z `collection`.|  
|`collection`|Wymagane. Odnosi się do kolekcji być badana. Musi być typem wyliczenia.|  
  
## <a name="remarks"></a>Uwagi  
 `From` Klauzuli służy do identyfikowania źródło danych pod kątem zapytania i zmienne, które służą do odwoływania się do elementu z kolekcji źródłowej. Te zmienne są nazywane *należeć do zakresu zmiennych*. `From` Klauzula jest wymagana dla zapytania, chyba że `Aggregate` klauzuli służy do identyfikowania, zwraca tylko zagregowane wyniki zapytania. Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Można określić wiele `From` klauzule w zapytaniu, aby zidentyfikować wielu kolekcji, które mają zostać połączone. Jeśli określono wiele kolekcji one jest powtarzana niezależnie lub można je dołączyć, jeśli są ze sobą powiązane. Dołącz kolekcje niejawnie przy użyciu `Select` klauzuli lub jawnie przy użyciu `Join` lub `Group Join` klauzul. Alternatywnie, można określić wiele zmiennych zakresu i kolekcji w jednym `From` klauzuli z każdej zmiennej zakresu powiązanych i kolekcji od siebie oddzielone przecinkami. Poniższy przykład kodu pokazuje obie opcje składni `From` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 `From` Klauzuli definiuje zakres kwerendy, co jest podobne do zakresu `For` pętli. W związku z tym, każdy `element` zmiennej zakresu w zakresie zapytania musi mieć unikatową nazwę. Ponieważ można określić wiele `From` klauzul zapytania, kolejne `From` klauzule mogą odwoływać się do zakresu zmiennych w `From` klauzuli lub może dotyczyć zmiennych zakresu w ramach poprzedniego `From` klauzuli. Na przykład, poniższy kod przedstawia zagnieżdżoną `From` klauzuli gdzie kolekcji w drugiej klauzuli opiera się na właściwość zmiennej zakresu w pierwszej klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 Każdy `From` klauzula może występować w dowolnej kombinacji klauzule dodatkowe kwerendy w celu doprecyzowania zapytania. Zapytania można dostosować w następujący sposób:  
  
-   Łączenie wielu kolekcji niejawnie za pomocą `From` i `Select` zdań, lub jawnie przy użyciu `Join` lub `Group Join` klauzul.  
  
-   Użyj `Where` klauzulę filtrującą dane wyniku zapytania.  
  
-   Sortowanie wyników za pomocą `Order By` klauzuli.  
  
-   Zgrupować podobne wyniki za pomocą `Group By` klauzuli.  
  
-   Użyj `Aggregate` klauzuli w celu identyfikacji funkcji agregujących do oceny, czy wynik całego zapytania.  
  
-   Użyj `Let` klauzulę, aby wprowadzić zmienną iteracji, którego wartość jest określona przez wyrażenie zamiast kolekcji.  
  
-   Użyj `Distinct` klauzuli ignorowanie wyników zapytania duplikatów.  
  
-   Identyfikowanie części wyników do zwrócenia przy użyciu `Skip`, `Take`, `Skip While`, i `Take While` klauzul.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie używa wyrażenia `From` klauzulę, aby zadeklarować zmienną zakresu `cust` dla każdego `Customer` obiektu `customers` kolekcji. `Where` Klauzuli używa zmiennej zakresu, aby uniemożliwić klientom określonego regionu danych wyjściowych. `For Each` Pętli Wyświetla nazwę firmy, dla każdego klienta, w wyniku zapytania.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytania](../../../visual-basic/language-reference/queries/index.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Klauzula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Distinct, klauzula](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [Join, klauzula](../../../visual-basic/language-reference/queries/join-clause.md)  
 [Klauzula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Order By, klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Let, klauzula](../../../visual-basic/language-reference/queries/let-clause.md)  
 [Skip, klauzula](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Take, klauzula](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Skip While, klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take While, klauzula](../../../visual-basic/language-reference/queries/take-while-clause.md)
