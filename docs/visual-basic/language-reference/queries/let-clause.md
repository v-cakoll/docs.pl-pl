---
title: Let — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 34c0fd239d9e08dab4a107cb8447941e7ab3ecbe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516766"
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
|`variable`|Wymagane. Alias, który może służyć do odwołania wyniki podane wyrażenie.|  
|`expression`|Wymagane. Wyrażenie, które będą oceniane i przypisane do określonej zmiennej.|  
  
## <a name="remarks"></a>Uwagi  
 `Let` Klauzuli pozwala do obliczenia wartości dla każdej wynik zapytania i odwoływać się do nich za pomocą aliasu. Alias mogą być używane w innych klauzul takich jak `Where` klauzuli. `Let` Klauzuli pozwala na tworzenie instrukcji zapytań, która jest łatwiejsza do odczytania, ponieważ możesz określić alias dla klauzuli wyrażenie uwzględnione w zapytaniu i Zastąp alias zawsze jest używana klauzula wyrażenia.  
  
 Może zawierać dowolną liczbę `variable` i `expression` przydziały w `Let` klauzuli. Każdego przypisania należy oddzielić przecinkami (,).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Let` klauzuli do obliczenia 10 procent rabatu na produkty.  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/index.md)  
 [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
