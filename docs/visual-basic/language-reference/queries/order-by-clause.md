---
title: Order By — Klauzula
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
ms.openlocfilehash: a7104e3dd82ff2dde2911861ce98a7367faf3b25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350418"
---
# <a name="order-by-clause-visual-basic"></a>Order By — Klauzula (Visual Basic)
Określa kolejność sortowania wyników zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Części  
 `orderExp1`  
 Wymagana. Co najmniej jedno pole z wyniku bieżącego zapytania, które określa sposób uporządkowania zwracanych wartości. Nazwy pól muszą być oddzielone przecinkami (,). Każde pole można zidentyfikować jako posortowane w kolejności rosnącej lub malejącej przy użyciu słów kluczowych `Ascending` lub `Descending`. Jeśli nie określono `Ascending` ani `Descending` słowa kluczowego, domyślną kolejnością sortowania jest rosnąco. Pola porządku sortowania mają pierwszeństwo od lewej do prawej.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć klauzuli `Order By`, aby posortować wyniki zapytania. Klauzula `Order By` może sortować wynik tylko na podstawie zmiennej zakresu dla bieżącego zakresu. Na przykład klauzula `Select` wprowadza nowy zakres w wyrażeniu zapytania z nowymi zmiennymi iteracji dla tego zakresu. Zmienne zakresu zdefiniowane przed klauzulą `Select` w zapytaniu nie są dostępne po klauzuli `Select`. W związku z tym, jeśli chcesz zamówić wyniki według pola, które nie jest dostępne w klauzuli `Select`, należy umieścić klauzulę `Order By` przed klauzulą `Select`. Przykładem, gdy trzeba to zrobić, jest sortowanie zapytania według pól, które nie są zwracane jako część wyniku.  
  
 Porządek rosnący i malejący dla pola jest określany przez implementację interfejsu <xref:System.IComparable> dla typu danych pola. Jeśli typ danych nie implementuje interfejsu <xref:System.IComparable>, porządek sortowania jest ignorowany.  
  
## <a name="example"></a>Przykład  
 Następujące wyrażenie zapytania używa klauzuli `From`, aby zadeklarować zmienną zakresu `book` dla kolekcji `books`. Klauzula `Order By` sortuje wyniki zapytania według ceny w kolejności rosnącej (wartość domyślna). Książki o tej samej cenie są sortowane według tytułu w kolejności rosnącej. Klauzula `Select` wybiera właściwości `Title` i `Price` jako wartości zwracane przez zapytanie.  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>Przykład  
 Następujące wyrażenie zapytania używa klauzuli `Order By`, aby posortować wyniki zapytania według ceny w kolejności malejącej. Książki o tej samej cenie są sortowane według tytułu w kolejności rosnącej.  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>Przykład  
 Poniższe wyrażenie zapytania używa klauzuli `Select`, aby wybrać tytuł książki, cenę, datę publikacji i autora. Następnie wypełnia pola `Title`, `Price`, `PublishDate`i `Author` zmiennej zakresu dla nowego zakresu. Klauzula `Order By` porządkuje nową zmienną zakresu według nazwy autora, tytułu książki, a następnie ceny. Każda kolumna jest sortowana w kolejności domyślnej (rosnąco).  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
