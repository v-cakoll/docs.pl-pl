---
title: Take While — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 080a106fc1deeb54165511ed03d7c7c5d2060f21
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818752"
---
# <a name="take-while-clause-visual-basic"></a>Take While — Klauzula (Visual Basic)
Zawiera elementy w kolekcji, tak długo, jak długo określony warunek przyjmuje `true` i pomija pozostałe elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
Take While expression  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`expression`|Wymagana. Wyrażenie, które reprezentuje stan, aby przetestować elementy. Wyrażenie musi zwracać `Boolean` wartość lub równoważnej funkcjonalności, takie jak `Integer` mogło zostać ocenione jako `Boolean`.|  
  
## <a name="remarks"></a>Uwagi  
 `Take While` Klauzula zawiera elementy od początku wyników zapytania do momentu podane `expression` zwraca `false`. Po `expression` zwraca `false`, zapytanie będzie pominąć wszystkie pozostałe elementy. `expression` Jest ignorowany dla pozostałych wyników.  
  
 `Take While` Klauzuli różni się od `Where` klauzuli w tym `Where` można użyć klauzuli, aby uwzględnić wszystkie elementy z zapytania, które spełniają określony warunek. `Take While` Klauzuli zawiera elementy tylko do pierwszego, który nie jest spełniony warunek. `Take While` Klauzula jest najbardziej przydatne podczas pracy z wynikiem zapytania uporządkowane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Take While` klauzuli, aby pobrać wyniki, aż do znalezienia pierwszego klienta bez żadnych zamówienia.  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Take, klauzula](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While, klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
