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
ms.openlocfilehash: 6484da5329c8240735b7c35f506637dd01cbeda4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604474"
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
|`variable`|Wymagana. Alias, który może służyć do odwołania wyniki podane wyrażenie.|  
|`expression`|Wymagana. Wyrażenie, które zostanie obliczone i przypisane do określonej zmiennej.|  
  
## <a name="remarks"></a>Uwagi  
 `Let` Klauzuli pozwala obliczyć wartości dla każdego wynik kwerendy i odwoływać je za pomocą aliasu. Alias mogą być używane w innych klauzul, takich jak `Where` klauzuli. `Let` Klauzuli umożliwia tworzenie instrukcji kwerendy, która jest łatwiej odczytywać, ponieważ można określić alias dla klauzuli wyrażenie uwzględnione w zapytaniu i Zastąp alias zawsze jest używana klauzula wyrażenia.  
  
 Może zawierać dowolną liczbę `variable` i `expression` przydziały w `Let` klauzuli. Każde przypisanie należy oddzielić przecinkami (,).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Let` klauzuli można obliczyć rabat 10 procent produktów.  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
