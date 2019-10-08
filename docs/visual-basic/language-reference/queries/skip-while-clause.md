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
ms.openlocfilehash: 7f37a6fa1c9ba7fdf7978ac6853e4c2985bf72e7
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004701"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While — Klauzula (Visual Basic)
Pomija elementy w kolekcji, tak długo, jak określony warunek jest `true`, a następnie zwraca pozostałe elementy.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`expression`|Wymagany. Wyrażenie reprezentujące warunek, dla którego mają zostać przetestowane elementy. Wyrażenie musi zwracać wartość `Boolean` lub odpowiedni odpowiednik funkcjonalny, taki jak `Integer` do obliczenia jako `Boolean`.|  
  
## <a name="remarks"></a>Uwagi  
 Klauzula `Skip While` pomija elementy od początku wyniku zapytania, dopóki podane `expression` nie zwróci `false`. Po `expression` zwraca `false`, zapytanie zwraca wszystkie pozostałe elementy. Wartość `expression` jest ignorowana dla pozostałych wyników.  
  
 Klauzula `Skip While` różni się od klauzuli `Where`, aby można było użyć klauzuli `Where` do wykluczenia wszystkich elementów z zapytania, które nie spełniają określonego warunku. Klauzula `Skip While` wyklucza elementy tylko do pierwszego niespełnienia warunku. Klauzula `Skip While` jest najbardziej przydatna podczas pracy z wynikiem kwerendy uporządkowanej.  
  
 Możesz pominąć określoną liczbę wyników od początku wyniku zapytania, używając klauzuli `Skip`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa klauzuli `Skip While`, aby pominąć wyniki do momentu, gdy zostanie znaleziony pierwszy klient z Stany Zjednoczone.  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Skip, klauzula](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Take While, klauzula](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
