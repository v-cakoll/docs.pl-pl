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
ms.openlocfilehash: a3c0749560d8cea1e46d96298347ce54f0bf9185
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393733"
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
|`expression`|Wymagane. Wyrażenie, które reprezentuje stan, aby przetestować elementy. Wyrażenie musi zwracać `Boolean` wartość lub równoważnej funkcjonalności, takie jak `Integer` mogło zostać ocenione jako `Boolean`.|  
  
## <a name="remarks"></a>Uwagi  
 `Skip While` Klauzuli pomija elementy od początku wynik zapytania do momentu podane `expression` zwraca `false`. Po `expression` zwraca `false`, zapytanie zwraca wszystkie pozostałe elementy. `expression` Jest ignorowany dla pozostałych wyników.  
  
 `Skip While` Klauzuli różni się od `Where` klauzuli w tym `Where` klauzuli można wykluczyć wszystkie elementy z zapytania, które nie spełniają określony warunek. `Skip While` Klauzuli wyklucza elementy tylko do pierwszego, który nie jest spełniony warunek. `Skip While` Klauzula jest najbardziej przydatne podczas pracy z wynikiem zapytania uporządkowane.  
  
 Można pominąć określoną liczbę wyników od samego początku wyników zapytania za pomocą `Skip` klauzuli.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Skip While` klauzulę, aby pominąć wyników, aż do znalezienia pierwszego klienta ze Stanów Zjednoczonych.  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/index.md)  
 [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Skip, klauzula](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Take While, klauzula](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
