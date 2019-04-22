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
ms.openlocfilehash: 1c84a4cdb4a149154d459ca4d9c290ed360d1772
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835014"
---
# <a name="order-by-clause-visual-basic"></a>Order By — Klauzula (Visual Basic)
Określa porządek sortowania dla wyniku kwerendy.  
  
## <a name="syntax"></a>Składnia  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Części  
 `orderExp1`  
 Wymagana. Co najmniej jednego pola z bieżącego wyniku zapytania określających sposób sortowania wartości zwracane. Nazwy pól muszą być oddzielone przecinkami (,). Można zidentyfikować każde pole, jak posortowane w kolejności rosnącej lub malejącej, używając `Ascending` lub `Descending` słów kluczowych. Jeśli nie `Ascending` lub `Descending` — słowo kluczowe jest określony, domyślna kolejność sortowania jest rosnąca. Pola kolejności sortowania są podane pierwszeństwa od lewej do prawej.  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `Order By` klauzuli sortowania wyników zapytania. `Order By` Klauzuli można sortować tylko wynik, w oparciu o zmiennej zakresu w bieżącym zakresie. Na przykład `Select` klauzuli wprowadza nowy zakres w wyrażeniu zapytania przy użyciu nowych zmiennych iteracji dla tego zakresu. Zakres zmiennych zdefiniowanych przed `Select` podklauzul nie są dostępne po `Select` klauzuli. W związku z tym jeśli chcesz uporządkować wyniki według pola, która nie jest dostępna w `Select` klauzuli, należy umieścić `Order By` klauzuli przed `Select` klauzuli. Jeden przykład przypadku w tym celu jest posortować według pól, które nie są zwracane jako część wyniku zapytania.  
  
 Kolejności rosnącej i malejącej dla pola jest określane przez implementację <xref:System.IComparable> interfejsu dla typu danych pola. Jeśli typ danych nie zawiera implementacji <xref:System.IComparable> interfejsu, kolejność sortowania jest ignorowana.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie używa wyrażenia `From` klauzulę, aby zadeklarować zmienną zakresu `book` dla `books` kolekcji. `Order By` Klauzuli sortowania wyników zapytania cena Rosnąco (ustawienie domyślne). Sklepu iBook książek z tej samej cenie są sortowane według tytułu w kolejności rosnącej. `Select` Wybiera klauzuli `Title` i `Price` właściwości jako wartości zwracane przez zapytanie.  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie używa wyrażenia `Order By` klauzuli sortowania wyników zapytania według ceny w kolejności malejącej. Sklepu iBook książek z tej samej cenie są sortowane według tytułu w kolejności rosnącej.  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie używa wyrażenia `Select` klauzuli wybierz tytuł książki, cen, Data opublikowania i autora. Następnie wypełnia `Title`, `Price`, `PublishDate`, i `Author` pola zmienna zakresu dla nowego zakresu. `Order By` Klauzuli porządkuje nowej zmiennej zakresu nazwisko autora, tytuł książki i ceny. Każda kolumna jest sortowana w kolejności domyślnej (rosnąco).  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
