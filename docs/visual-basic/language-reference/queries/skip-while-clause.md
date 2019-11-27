---
title: Skip While, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 47703e445865435f5bf5312c3fe41833ac21aa3f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333143"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While — Klauzula (Visual Basic)
Pomija elementy w kolekcji tak długo, jak określony warunek jest `true` a następnie zwraca pozostałe elementy.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`expression`|Wymagana. Wyrażenie reprezentujące warunek, dla którego mają zostać przetestowane elementy. Wyrażenie musi zwracać wartość `Boolean` lub odpowiedni odpowiednik funkcjonalny, na przykład `Integer` do oceny jako `Boolean`.|  
  
## <a name="remarks"></a>Uwagi  
 Klauzula `Skip While` pomija elementy od początku wyniku zapytania, dopóki podane `expression` nie zwróci `false`. Po `expression` zwraca `false`, zapytanie zwraca wszystkie pozostałe elementy. `expression` jest ignorowana dla pozostałych wyników.  
  
 Klauzula `Skip While` różni się od klauzuli `Where`, w której klauzula `Where` może służyć do wykluczania wszystkich elementów z zapytania, które nie spełniają określonego warunku. Klauzula `Skip While` wyklucza elementy tylko do pierwszego niespełnienia warunku. Klauzula `Skip While` jest najbardziej przydatna podczas pracy z wynikiem kwerendy uporządkowanej.  
  
 Można pominąć określoną liczbę wyników od początku wyniku zapytania przy użyciu klauzuli `Skip`.  
  
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
