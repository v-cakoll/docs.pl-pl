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
ms.openlocfilehash: f8ee46b12e84f99629c3a92057fc3a7bb8a3c2e8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004956"
---
# <a name="order-by-clause-visual-basic"></a>Order By — Klauzula (Visual Basic)
Określa kolejność sortowania wyników zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Części  
 `orderExp1`  
 Wymagany. Co najmniej jedno pole z wyniku bieżącego zapytania, które określa sposób uporządkowania zwracanych wartości. Nazwy pól muszą być oddzielone przecinkami (,). Każde pole można zidentyfikować jako posortowane w kolejności rosnącej lub malejącej przy użyciu słów kluczowych `Ascending` lub `Descending`. Jeśli nie określono słowa kluczowego `Ascending` lub `Descending`, domyślna kolejność sortowania to Ascending. Pola porządku sortowania mają pierwszeństwo od lewej do prawej.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć klauzuli `Order By` w celu sortowania wyników zapytania. Klauzula `Order By` może sortować wynik wyłącznie na podstawie zmiennej zakresu dla bieżącego zakresu. Na przykład klauzula `Select` wprowadza nowy zakres w wyrażeniu zapytania z nowymi zmiennymi iteracji dla tego zakresu. Zmienne zakresu zdefiniowane przed klauzulą `Select` w zapytaniu nie są dostępne po klauzuli `Select`. W związku z tym, jeśli chcesz zamówić wyniki według pola, które nie jest dostępne w klauzuli `Select`, należy umieścić klauzulę `Order By` przed klauzulą `Select`. Przykładem, gdy trzeba to zrobić, jest sortowanie zapytania według pól, które nie są zwracane jako część wyniku.  
  
 Porządek rosnący i malejący dla pola jest określany przez implementację interfejsu <xref:System.IComparable> dla typu danych pola. Jeśli typ danych nie implementuje interfejsu <xref:System.IComparable>, porządek sortowania jest ignorowany.  
  
## <a name="example"></a>Przykład  
 Następujące wyrażenie zapytania używa klauzuli `From`, aby zadeklarować zmienną zakresu `book` dla kolekcji `books`. Klauzula `Order By` sortuje wyniki zapytania według ceny w kolejności rosnącej (wartość domyślna). Książki o tej samej cenie są sortowane według tytułu w kolejności rosnącej. Klauzula `Select` wybiera właściwości `Title` i `Price` jako wartości zwracane przez zapytanie.  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>Przykład  
 Następujące wyrażenie zapytania używa klauzuli `Order By` w celu sortowania wyników zapytania według ceny w kolejności malejącej. Książki o tej samej cenie są sortowane według tytułu w kolejności rosnącej.  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>Przykład  
 Następujące wyrażenie zapytania używa klauzuli `Select` w celu wybrania tytułu książki, ceny, daty publikacji i autora. Następnie wypełni `Title`, `Price`, `PublishDate` i `Author` pól zmiennej zakresu dla nowego zakresu. Klauzula `Order By` porządkuje nową zmienną zakresu według nazwy autora, tytułu książki, a następnie ceny. Każda kolumna jest sortowana w kolejności domyślnej (rosnąco).  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
