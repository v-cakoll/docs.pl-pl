---
title: "Take While — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c8add6c55bb9353bac3489e68f497cb32785aad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="take-while-clause-visual-basic"></a>Take While — Klauzula (Visual Basic)
Zawiera elementy w kolekcji, tak długo, jak jest określony warunek `true` i pomija pozostałe elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
Take While expression  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`expression`|Wymagany. Wyrażenie reprezentuje warunek do sprawdzenia elementów. Wyrażenie musi zwracać `Boolean` wartość lub jej odpowiedniku funkcjonalne, takie jak `Integer` ma zostać obliczone jako `Boolean`.|  
  
## <a name="remarks"></a>Uwagi  
 `Take While` Klauzuli zawiera elementy od początku w wyniku zapytania do podane `expression` zwraca `false`. Po `expression` zwraca `false`, zapytanie będzie pominąć wszystkie pozostałe elementy. `expression` Jest ignorowany w przypadku pozostałych wyników.  
  
 `Take While` Klauzuli różni się od `Where` klauzuli w tym `Where` można użyć klauzuli uwzględnienie wszystkich elementów w wyniku zapytania, które spełniają określony warunek. `Take While` Klauzuli zawiera elementy tylko dopiero po raz pierwszy warunek nie jest spełniony. `Take While` Klauzula jest najbardziej przydatne podczas pracy z wynikiem uporządkowane zapytanie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Take While` klauzuli można pobrać wyników, aż do znalezienia pierwszego klienta bez żadnych zleceń.  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [SELECT — klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzula FROM](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Take — klauzula](../../../visual-basic/language-reference/queries/take-clause.md)  
 [SKIP While — klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Gdy klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
