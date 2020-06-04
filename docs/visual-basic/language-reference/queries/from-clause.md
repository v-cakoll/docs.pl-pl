---
title: From, klauzula
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
ms.openlocfilehash: 33680f49247b3b2a6082b3a6b27ca64f8401e42d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396184"
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
|`element`|Wymagany. *Zmienna zakresu* używana do iteracji elementów kolekcji. Zmienna zakresu jest używana do odwoływania się do każdego elementu członkowskiego, `collection` ponieważ zapytanie wykonuje iterację przez `collection` . Musi być typem wyliczalnym.|  
|`type`|Opcjonalny. Typ `element` . Jeśli nie `type` jest określony, typ `element` jest wnioskowany z `collection` .|  
|`collection`|Wymagany. Odwołuje się do kolekcji, do której mają być wysyłane zapytania. Musi być typem wyliczalnym.|  
  
## <a name="remarks"></a>Uwagi  
 `From`Klauzula służy do identyfikowania danych źródłowych zapytania i zmiennych, które są używane do odwoływania się do elementu z kolekcji źródłowej. Te zmienne są nazywane *zmiennymi zakresu*. `From`Klauzula jest wymagana dla zapytania, z wyjątkiem sytuacji, gdy `Aggregate` klauzula służy do identyfikowania zapytania, które zwraca tylko zagregowane wyniki. Aby uzyskać więcej informacji, zobacz [klauzula Aggregate](aggregate-clause.md).  
  
 Można określić wiele `From` klauzul w zapytaniu, aby zidentyfikować wiele kolekcji do przyłączenia. Jeśli określono wiele kolekcji, są one powtarzane niezależnie lub można je przyłączać, jeśli są powiązane. Kolekcje można sprzęgać niejawnie przy użyciu `Select` klauzuli lub jawnie za pomocą `Join` `Group Join` klauzul or. Alternatywnie można określić wiele zmiennych zakresów i kolekcji w pojedynczej `From` klauzuli, z każdą pokrewną zmienną zakresu i kolekcją oddzieloną od innych, przecinkiem. Poniższy przykład kodu pokazuje obie opcje składni dla tej `From` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 `From`Klauzula definiuje zakres zapytania, który jest podobny do zakresu `For` pętli. W związku z tym każda `element` zmienna zakresu w zakresie zapytania musi mieć unikatową nazwę. Ponieważ można określić wiele `From` klauzul dla zapytania, kolejne `From` klauzule mogą odwoływać się do zmiennych zakresu w `From` klauzuli lub mogą odwoływać się do zmiennych zakresu w poprzedniej `From` klauzuli. Na przykład poniższy przykład pokazuje klauzulę zagnieżdżoną `From` , gdzie kolekcja w drugiej klauzuli opiera się na właściwości zmiennej zakresu w pierwszej klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 `From`Po każdej klauzuli można wykonać dowolną kombinację dodatkowych klauzul zapytania, aby uściślić zapytanie. Zapytanie można uściślić w następujący sposób:  
  
- Połącz wiele kolekcji niejawnie za pomocą `From` `Select` klauzul i lub jawnie za pomocą `Join` `Group Join` klauzul or.  
  
- Użyj `Where` klauzuli, aby odfiltrować wynik zapytania.  
  
- Posortuj wynik przy użyciu `Order By` klauzuli.  
  
- Grupuj podobne wyniki przy użyciu `Group By` klauzuli.  
  
- Użyj `Aggregate` klauzuli, aby zidentyfikować funkcje agregujące do obliczenia dla całego wyniku zapytania.  
  
- Użyj `Let` klauzuli, aby wprowadzić zmienną iteracji, której wartość jest określana przez wyrażenie zamiast kolekcji.  
  
- Użyj `Distinct` klauzuli do ignorowania zduplikowanych wyników zapytania.  
  
- Zidentyfikuj części wyniku do zwrócenia przy użyciu `Skip` `Take` klauzul,, `Skip While` , i `Take While` .  
  
## <a name="example"></a>Przykład  
 Następujące wyrażenie zapytania używa klauzuli, `From` Aby zadeklarować zmienną zakresu `cust` dla każdego `Customer` obiektu w `customers` kolekcji. `Where`Klauzula używa zmiennej zakresu w celu ograniczenia danych wyjściowych do klientów z określonego regionu. `For Each`Pętla wyświetla nazwę firmy dla każdego klienta w wyniku zapytania.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a>Zobacz też

- [Zapytania](index.md)
- [Wprowadzenie do LINQ w Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [For Each...Next, instrukcja](../statements/for-each-next-statement.md)
- [For...Next, instrukcja](../statements/for-next-statement.md)
- [SELECT — klauzula](select-clause.md)
- [Klauzula WHERE](where-clause.md)
- [Aggregate, klauzula](aggregate-clause.md)
- [Distinct, klauzula](distinct-clause.md)
- [Klauzula join](join-clause.md)
- [Group Join. klauzula](group-join-clause.md)
- [Order By, klauzula](order-by-clause.md)
- [Klauzula Let](let-clause.md)
- [Skip, klauzula](skip-clause.md)
- [Take, klauzula](take-clause.md)
- [Skip While, klauzula](skip-while-clause.md)
- [Take While, klauzula](take-while-clause.md)
