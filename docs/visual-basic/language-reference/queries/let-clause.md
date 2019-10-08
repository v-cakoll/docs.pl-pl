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
ms.openlocfilehash: 88166a040823cfefe623f672e556c364d652a7fc
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004731"
---
# <a name="let-clause-visual-basic"></a>Let — Klauzula (Visual Basic)
Oblicza wartość i przypisuje ją do nowej zmiennej w zapytaniu.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`variable`|Wymagany. Alias, który może służyć do odwoływania się do wyników podanego wyrażenia.|  
|`expression`|Wymagany. Wyrażenie, które zostanie obliczone i przypisane do określonej zmiennej.|  
  
## <a name="remarks"></a>Uwagi  
 Klauzula `Let` umożliwia obliczanie wartości dla każdego wyniku zapytania i odwoływanie się do nich za pomocą aliasu. Alias może być używany w innych klauzulach, takich jak klauzula `Where`. Klauzula `Let` umożliwia utworzenie instrukcji zapytania, która jest łatwiejsza do odczytania, ponieważ można określić alias dla klauzuli Expression zawartej w zapytaniu i zastąpić alias za każdym razem, gdy zostanie użyta klauzula wyrażenia.  
  
 W klauzuli `Let` można uwzględnić dowolną liczbę przypisań `variable` i `expression`. Każde przypisanie należy oddzielić przecinkami (,).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa klauzuli `Let` w celu obliczenia rabatu w wysokości 10% na produkty.  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
