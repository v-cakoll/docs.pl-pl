---
title: Order By — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: 7c60156ee81618530b42d5f61dbcac6f59c4f675
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604123"
---
# <a name="order-by-clause-visual-basic"></a>Order By — Klauzula (Visual Basic)
Określa porządek sortowania dla wyniku zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Części  
 `orderExp1`  
 Wymagana. Co najmniej jednego pola z bieżącego wyniku zapytania określających kolejność zwracanych wartości. Nazwy pól muszą być oddzielone przecinkami (,). Każde pole można określić jako sortowane w kolejności rosnącej lub malejącej przy użyciu `Ascending` lub `Descending` słów kluczowych. Jeśli nie `Ascending` lub `Descending` zostanie określone słowo kluczowe, domyślna kolejność sortowania jest rosnąca. Pola kolejność sortowania podano pierwszeństwo od lewej do prawej.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `Order By` klauzuli sortowania wyników zapytania. `Order By` Klauzuli można sortować tylko wynik oparte na zmienną zakresu dla bieżącego zakresu. Na przykład `Select` klauzuli wprowadzono nowy zakres w wyrażeniu zapytania z nowe zmienne iteracji dla tego zakresu. Zakres zmienne zdefiniowane przed `Select` podklauzul nie są dostępne po `Select` klauzuli. W związku z tym aby uporządkować wyniki według pola, który nie jest dostępny w `Select` klauzuli, możesz umieścić `Order By` klauzuli przed `Select` klauzuli. Jeden przykład kiedy należy to zrobić to można sortować według pól, które nie są zwracane w ramach wyniku zapytania.  
  
 Rosnąca i malejącej dla pola zależy od implementacji <xref:System.IComparable> interfejs dla typu danych pola. Jeśli typ danych nie implementuje <xref:System.IComparable> interfejsu, kolejność sortowania jest ignorowana.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie używa wyrażenia `From` klauzuli, aby zadeklarować zmienną zakresu `book` dla `books` kolekcji. `Order By` Klauzuli sortowania wyników zapytania cen Rosnąco (ustawienie domyślne). Książek z tej samej cenie są sortowane według tytułu w kolejności rosnącej. `Select` Wybiera klauzuli `Title` i `Price` właściwości jako wartości zwracane przez zapytanie.  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie używa wyrażenia `Order By` klauzuli sortowania wyników zapytania przez cen w kolejności malejącej. Książek z tej samej cenie są sortowane według tytułu w kolejności rosnącej.  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie używa wyrażenia `Select` klauzuli wybierz tytułu ceny, Opublikuj datę i autora. Następnie wypełnia `Title`, `Price`, `PublishDate`, i `Author` pola zmienna zakresu dla nowego zakresu. `Order By` Klauzuli porządkuje zmienną zakresu imię i nazwisko autora, tytuł książki i cenę. Każda kolumna jest sortowane w kolejności domyślnej (rosnąco).  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
