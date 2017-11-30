---
title: "Skip While — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f447a6d9b2eb58fa546ced6c96b987caf68fb3e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="skip-while-clause-visual-basic"></a>Skip While — Klauzula (Visual Basic)
Pomija elementy w kolekcji, tak długo, jak jest określony warunek `true` , a następnie zwraca wszystkie pozostałe elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`expression`|Wymagany. Wyrażenie reprezentuje warunek do sprawdzenia elementów. Wyrażenie musi zwracać `Boolean` wartość lub jej odpowiedniku funkcjonalne, takie jak `Integer` ma zostać obliczone jako `Boolean`.|  
  
## <a name="remarks"></a>Uwagi  
 `Skip While` Klauzuli pomija elementy od początku w wyniku zapytania do podane `expression` zwraca `false`. Po `expression` zwraca `false`, gdy kwerenda zwraca wszystkie pozostałe elementy. `expression` Jest ignorowany w przypadku pozostałych wyników.  
  
 `Skip While` Klauzuli różni się od `Where` klauzuli w tym `Where` klauzuli można wykluczyć wszystkie elementy z zapytania, które nie spełniają określony warunek. `Skip While` Klauzuli wyklucza elementy tylko dopiero po raz pierwszy warunek nie jest spełniony. `Skip While` Klauzula jest najbardziej przydatne podczas pracy z wynikiem uporządkowane zapytanie.  
  
 Można pominąć określoną liczbę wyników od początku w wyniku zapytania za pomocą `Skip` klauzuli.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Skip While` klauzuli obejść wyników, aż do znalezienia pierwszego klienta ze Stanów Zjednoczonych.  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [SELECT — klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzula FROM](../../../visual-basic/language-reference/queries/from-clause.md)  
 [SKIP — klauzula](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Take While — klauzula](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Gdy klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
