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
ms.openlocfilehash: e8d3e38261a04c4d29faab351d24d6710413b09a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004788"
---
# <a name="distinct-clause-visual-basic"></a>Distinct — Klauzula (Visual Basic)
Ogranicza wartości bieżącej zmiennej zakresu w celu wyeliminowania zduplikowanych wartości w kolejnych klauzulach zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a>Uwagi  
 Można użyć klauzuli `Distinct`, aby zwrócić listę unikatowych elementów. Klauzula `Distinct` powoduje, że zapytanie ignoruje zduplikowane wyniki zapytania. Klauzula `Distinct` ma zastosowanie do zduplikowanych wartości dla wszystkich zwracanych pól określonych przez klauzulę `Select`. Jeśli nie jest określona klauzula `Select`, klauzula `Distinct` zostanie zastosowana do zmiennej zakresu dla zapytania zidentyfikowanego w klauzuli `From`. Jeśli zmienna zakresu nie jest niezmiennym typem, zapytanie zignoruje tylko wynik zapytania, jeśli wszystkie elementy członkowskie tego typu pasują do istniejącego wyniku zapytania.  
  
## <a name="example"></a>Przykład  
 Poniższe wyrażenie zapytania dołącza listę klientów i listę zamówień klientów. Klauzula `Distinct` jest uwzględniona w celu zwrócenia listy unikatowych nazw klientów i dat kolejności.  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
