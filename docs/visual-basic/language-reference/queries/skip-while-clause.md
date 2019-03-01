---
title: Skip While — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 380372d6aaf8df3050e0ba8606b74eb3834dec67
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972602"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While — Klauzula (Visual Basic)
Pomija elementy w kolekcji, tak długo, jak długo określony warunek przyjmuje `true` , a następnie zwraca pozostałe elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`expression`|Wymagana. Wyrażenie, które reprezentuje stan, aby przetestować elementy. Wyrażenie musi zwracać `Boolean` wartość lub równoważnej funkcjonalności, takie jak `Integer` mogło zostać ocenione jako `Boolean`.|  
  
## <a name="remarks"></a>Uwagi  
 `Skip While` Klauzuli pomija elementy od początku wynik zapytania do momentu podane `expression` zwraca `false`. Po `expression` zwraca `false`, zapytanie zwraca wszystkie pozostałe elementy. `expression` Jest ignorowany dla pozostałych wyników.  
  
 `Skip While` Klauzuli różni się od `Where` klauzuli w tym `Where` klauzuli można wykluczyć wszystkie elementy z zapytania, które nie spełniają określony warunek. `Skip While` Klauzuli wyklucza elementy tylko do pierwszego, który nie jest spełniony warunek. `Skip While` Klauzula jest najbardziej przydatne podczas pracy z wynikiem zapytania uporządkowane.  
  
 Można pominąć określoną liczbę wyników od samego początku wyników zapytania za pomocą `Skip` klauzuli.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Skip While` klauzulę, aby pominąć wyników, aż do znalezienia pierwszego klienta ze Stanów Zjednoczonych.  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Skip, klauzula](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Take While, klauzula](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
