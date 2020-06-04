---
title: Take While, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 4b6133efdbd9c46ab85201ad454671e5538b6a81
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359583"
---
# <a name="take-while-clause-visual-basic"></a>Take While — Klauzula (Visual Basic)
Zawiera elementy w kolekcji, tak długo, jak określony warunek jest `true` i pomija pozostałe elementy.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`expression`|Wymagany. Wyrażenie reprezentujące warunek, dla którego mają zostać przetestowane elementy. Wyrażenie musi zwracać `Boolean` wartość lub odpowiedni odpowiednik funkcjonalny, na przykład, `Integer` Aby można było je oszacować jako `Boolean` .|  
  
## <a name="remarks"></a>Uwagi  
 `Take While`Klauzula zawiera elementy od początku wyniku zapytania do podanej wartości `expression` zwracanej `false` . Po `expression` powrocie `false` zapytanie spowoduje obejście wszystkich pozostałych elementów. Wartość `expression` jest ignorowana dla pozostałych wyników.  
  
 `Take While`Klauzula różni się od `Where` klauzuli, w której `Where` klauzula może być używana do dołączania wszystkich elementów z zapytania, które spełniają określony warunek. `Take While`Klauzula zawiera elementy tylko do pierwszego niespełnienia warunku. `Take While`Klauzula jest najbardziej przydatna podczas pracy z wynikiem kwerendy uporządkowanej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa klauzuli, `Take While` Aby pobrać wyniki do momentu, w którym nie zostanie znaleziony pierwszy klient bez zamówień.  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do LINQ w Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](index.md)
- [SELECT — klauzula](select-clause.md)
- [Klauzula from](from-clause.md)
- [Take, klauzula](take-clause.md)
- [Skip While, klauzula](skip-while-clause.md)
- [Klauzula WHERE](where-clause.md)
