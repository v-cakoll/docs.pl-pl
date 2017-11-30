---
title: "Distinct — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ed92d5d601c1ec329728346ac881c4fa2bad8aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="distinct-clause-visual-basic"></a>Distinct — Klauzula (Visual Basic)
Ogranicza wartości bieżącą zmienną zakresu w celu wyeliminowania zduplikowanych wartości w klauzulach kolejne zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```  
Distinct  
```  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `Distinct` klauzuli, aby powrócić do listy unikatowych elementów. `Distinct` Klauzuli powoduje, że kwerenda Ignoruj wyników zduplikowane zapytanie. `Distinct` Klauzuli dotyczy zduplikowane wartości dla wszystkich zwraca pola określone przez `Select` klauzuli. Jeśli nie `Select` określono klauzuli `Distinct` klauzuli jest stosowany do zmiennej zakresu dla zapytania, zostały zidentyfikowane w `From` klauzuli. Jeśli zmienna zakresu nie jest typem niezmienne, zapytanie tylko zignoruje w wyniku zapytania, jeśli wszystkie elementy członkowskie tego typu są zgodne istniejącego wyniku zapytania.  
  
## <a name="example"></a>Przykład  
 Poniższe wyrażenie kwerendy łączy listę klientów i listę zamówień klienta. `Distinct` Klauzula jest aby zwrócić listę nazw unikatowych klientów i kolejność daty.  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [Klauzula FROM](../../../visual-basic/language-reference/queries/from-clause.md)  
 [SELECT — klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Gdy klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
