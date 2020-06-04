---
title: Order By, klauzula
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
ms.openlocfilehash: 63f454064e88bc18f252940f3abd8e59b8900e5b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359751"
---
# <a name="order-by-clause-visual-basic"></a>Order By — Klauzula (Visual Basic)
Określa kolejność sortowania wyników zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Części  
 `orderExp1`  
 Wymagany. Co najmniej jedno pole z wyniku bieżącego zapytania, które określa sposób uporządkowania zwracanych wartości. Nazwy pól muszą być oddzielone przecinkami (,). Można zidentyfikować każde pole jako posortowane w kolejności rosnącej lub malejącej za `Ascending` pomocą `Descending` słowa kluczowego or. Jeśli nie `Ascending` `Descending` określono słowa kluczowego or, domyślna kolejność sortowania to Ascending. Pola porządku sortowania mają pierwszeństwo od lewej do prawej.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć klauzuli, `Order By` Aby posortować wyniki zapytania. `Order By`Klauzula może sortować wynik tylko na podstawie zmiennej zakresu dla bieżącego zakresu. Na przykład `Select` klauzula wprowadza nowy zakres w wyrażeniu zapytania z nowymi zmiennymi iteracji dla tego zakresu. Zmienne zakresu zdefiniowane przed `Select` klauzulą w zapytaniu nie są dostępne po `Select` klauzuli. W związku z tym, jeśli chcesz zamówić wyniki według pola, które nie jest dostępne w `Select` klauzuli, należy umieścić `Order By` klauzulę przed `Select` klauzulą. Przykładem, gdy trzeba to zrobić, jest sortowanie zapytania według pól, które nie są zwracane jako część wyniku.  
  
 Porządek rosnący i malejący dla pola jest określany przez implementację <xref:System.IComparable> interfejsu dla typu danych pola. Jeśli typ danych nie implementuje <xref:System.IComparable> interfejsu, porządek sortowania jest ignorowany.  
  
## <a name="example"></a>Przykład  
 Następujące wyrażenie zapytania używa klauzuli, `From` Aby zadeklarować zmienną zakresu `book` dla `books` kolekcji. `Order By`Klauzula sortuje wyniki zapytania według ceny w kolejności rosnącej (wartość domyślna). Książki o tej samej cenie są sortowane według tytułu w kolejności rosnącej. `Select`Klauzula służy do wybierania `Title` `Price` właściwości i jako wartości zwracanych przez zapytanie.  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>Przykład  
 Poniższe wyrażenie zapytania używa `Order By` klauzuli do sortowania wyników zapytania według ceny w kolejności malejącej. Książki o tej samej cenie są sortowane według tytułu w kolejności rosnącej.  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>Przykład  
 Poniższe wyrażenie zapytania używa `Select` klauzuli, aby wybrać tytuł książki, cenę, datę publikacji i autora. Następnie wypełnia `Title` `Price` pola,, `PublishDate` , i `Author` zmiennej zakresu dla nowego zakresu. `Order By`Klauzula porządkuje nową zmienną zakresu według nazwy autora, tytułu książki, a następnie ceny. Każda kolumna jest sortowana w kolejności domyślnej (rosnąco).  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do LINQ w Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](index.md)
- [SELECT — klauzula](select-clause.md)
- [Klauzula from](from-clause.md)
