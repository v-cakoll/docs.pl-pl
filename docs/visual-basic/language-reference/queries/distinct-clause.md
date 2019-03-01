---
title: Distinct — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 00a2e52bd6669869bb2e25bc2857f1598da5763f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971250"
---
# <a name="distinct-clause-visual-basic"></a>Distinct — Klauzula (Visual Basic)
Ogranicza wartości bieżącej zmiennej zakresu w celu wyeliminowania zduplikowanych wartości w klauzulach kolejnych zapytań.  
  
## <a name="syntax"></a>Składnia  
  
```  
Distinct  
```  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `Distinct` klauzulę, aby powrócić do listy unikatowych elementów. `Distinct` Klauzuli powoduje, że zapytanie, aby zignorować wyników zapytania zduplikowane. `Distinct` Klauzuli dotyczy zduplikowane wartości dla wszystkich zwraca pola określone przez `Select` klauzuli. Jeśli nie `Select` określono klauzulę `Distinct` klauzula jest stosowany do zmiennej zakresu zapytania w `From` klauzuli. Jeśli zmienna zakresu nie jest typem niezmienne, zapytanie tylko zignorować wynik zapytania, jeśli wszystkie elementy członkowskie tego typu odpowiada istniejącej wyniku zapytania.  
  
## <a name="example"></a>Przykład  
 Poniższe wyrażenie zapytania łączy listę klientów i listę zamówień klienta. `Distinct` Klauzula jest aby zwrócić listę klientów unikatowe nazwy i kolejność daty.  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
