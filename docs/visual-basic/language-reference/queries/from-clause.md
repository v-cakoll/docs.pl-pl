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
ms.openlocfilehash: 781902f1bf28bd029c8d9825aee155a6691cbae9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004781"
---
# <a name="from-clause-visual-basic"></a>From — Klauzula (Visual Basic)
Określa co najmniej jedną zmienną zakresu i kolekcję do zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`element`|Wymagany. *Zmienna zakresu* używana do iteracji elementów kolekcji. Zmienna zakresu służy do odwoływania się do każdego elementu członkowskiego `collection`, ponieważ zapytanie wykonuje iterację przez `collection`. Musi być typem wyliczalnym.|  
|`type`|Opcjonalny. Typ `element`. Jeśli nie określono `type`, typ `element` jest wnioskowany z `collection`.|  
|`collection`|Wymagany. Odwołuje się do kolekcji, do której mają być wysyłane zapytania. Musi być typem wyliczalnym.|  
  
## <a name="remarks"></a>Uwagi  
 Klauzula `From` służy do identyfikowania danych źródłowych zapytania i zmiennych, które są używane do odwoływania się do elementu z kolekcji źródłowej. Te zmienne są nazywane *zmiennymi zakresu*. Klauzula `From` jest wymagana dla zapytania, z wyjątkiem sytuacji, gdy klauzula `Aggregate` służy do identyfikowania zapytania, które zwraca tylko zagregowane wyniki. Aby uzyskać więcej informacji, zobacz [klauzula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Można określić wiele klauzul `From` w zapytaniu, aby zidentyfikować wiele kolekcji do przyłączenia. Jeśli określono wiele kolekcji, są one powtarzane niezależnie lub można je przyłączać, jeśli są powiązane. Kolekcje można sprzęgać niejawnie za pomocą klauzuli `Select` lub jawnie za pomocą klauzul `Join` lub `Group Join`. Alternatywnie można określić wiele zmiennych zakresów i kolekcji w pojedynczej klauzuli `From`, z każdą pokrewną zmienną zakresu i kolekcją oddzieloną od innych, przecinkiem. Poniższy przykład kodu pokazuje obie opcje składni dla klauzuli `From`.  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 Klauzula `From` definiuje zakres zapytania, który jest podobny do zakresu pętli `For`. W związku z tym Każda zmienna zakresu `element` w zakresie zapytania musi mieć unikatową nazwę. Ponieważ można określić wiele klauzul `From` dla zapytania, kolejne klauzule `From` mogą odwoływać się do zmiennych zakresu w klauzuli `From` lub mogą odwoływać się do zmiennych zakresu w poprzedniej klauzuli `From`. Na przykład poniższy przykład pokazuje zagnieżdżoną klauzulę `From`, gdzie kolekcja w drugiej klauzuli jest oparta na właściwości zmiennej zakresu w pierwszej klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 Każda klauzula `From` może następować dowolną kombinacją dodatkowych klauzul zapytania, aby uściślić zapytanie. Zapytanie można uściślić w następujący sposób:  
  
- Połącz wiele kolekcji niejawnie za pomocą klauzul `From` i `Select` lub jawnie za pomocą klauzul `Join` lub `Group Join`.  
  
- Użyj klauzuli `Where`, aby odfiltrować wynik zapytania.  
  
- Posortuj wynik przy użyciu klauzuli `Order By`.  
  
- Grupuj podobne wyniki przy użyciu klauzuli `Group By`.  
  
- Użyj klauzuli `Aggregate`, aby zidentyfikować funkcje agregujące do obliczenia dla całego wyniku zapytania.  
  
- Użyj klauzuli `Let`, aby wprowadzić zmienną iteracji, której wartość jest określana przez wyrażenie zamiast kolekcji.  
  
- Użyj klauzuli `Distinct` do ignorowania zduplikowanych wyników zapytania.  
  
- Zidentyfikuj części wyniku do zwrócenia przy użyciu klauzul `Skip`, `Take`, `Skip While` i `Take While`.  
  
## <a name="example"></a>Przykład  
 Następujące wyrażenie zapytania używa klauzuli `From`, aby zadeklarować zmienną zakresu `cust` dla każdego obiektu `Customer` w kolekcji `customers`. Klauzula `Where` używa zmiennej zakresu w celu ograniczenia danych wyjściowych do klientów z określonego regionu. Pętla `For Each` Wyświetla nazwę firmy dla każdego klienta w wyniku zapytania.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
- [Aggregate, klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Distinct, klauzula](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [Join, klauzula](../../../visual-basic/language-reference/queries/join-clause.md)
- [Group Join, klauzula](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Order By, klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Let, klauzula](../../../visual-basic/language-reference/queries/let-clause.md)
- [Skip, klauzula](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Take, klauzula](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While, klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take While, klauzula](../../../visual-basic/language-reference/queries/take-while-clause.md)
