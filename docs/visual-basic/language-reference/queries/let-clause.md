---
title: "Let — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70e47517a62f58dcababd31c26277417b62eab66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="let-clause-visual-basic"></a>Let — Klauzula (Visual Basic)
Oblicza wartość i przypisuje go do nowej zmiennej w ramach zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`variable`|Wymagany. Alias, który może służyć do odwołania wyniki podane wyrażenie.|  
|`expression`|Wymagany. Wyrażenie, które zostanie obliczone i przypisane do określonej zmiennej.|  
  
## <a name="remarks"></a>Uwagi  
 `Let` Klauzuli pozwala obliczyć wartości dla każdego wynik kwerendy i odwoływać je za pomocą aliasu. Alias mogą być używane w innych klauzul, takich jak `Where` klauzuli. `Let` Klauzuli umożliwia tworzenie instrukcji kwerendy, która jest łatwiej odczytywać, ponieważ można określić alias dla klauzuli wyrażenie uwzględnione w zapytaniu i Zastąp alias zawsze jest używana klauzula wyrażenia.  
  
 Może zawierać dowolną liczbę `variable` i `expression` przydziały w `Let` klauzuli. Każde przypisanie należy oddzielić przecinkami (,).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Let` klauzuli można obliczyć rabat 10 procent produktów.  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [SELECT — klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzula FROM](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Gdy klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
