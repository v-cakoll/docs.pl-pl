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
ms.openlocfilehash: b357320a92ace1b7a261991737ed653d54d0eeab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359648"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While — Klauzula (Visual Basic)
Pomija elementy w kolekcji, tak długo, jak określony warunek jest `true` , a następnie zwraca pozostałe elementy.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`expression`|Wymagany. Wyrażenie reprezentujące warunek, dla którego mają zostać przetestowane elementy. Wyrażenie musi zwracać `Boolean` wartość lub odpowiedni odpowiednik funkcjonalny, na przykład, `Integer` Aby można było je oszacować jako `Boolean` .|  
  
## <a name="remarks"></a>Uwagi  
 `Skip While`Klauzula pomija elementy od początku wyniku zapytania do momentu podania podanej `expression` wartości `false` . Po `expression` zwracaniu `false` zapytanie zwraca wszystkie pozostałe elementy. Wartość `expression` jest ignorowana dla pozostałych wyników.  
  
 `Skip While`Klauzula różni się od `Where` klauzuli, w której `Where` klauzula może służyć do wykluczenia wszystkich elementów z zapytania, które nie spełniają określonego warunku. `Skip While`Klauzula wyklucza elementy tylko do pierwszego niespełnienia warunku. `Skip While`Klauzula jest najbardziej przydatna podczas pracy z wynikiem kwerendy uporządkowanej.  
  
 Można pominąć określoną liczbę wyników od początku wyniku zapytania przy użyciu `Skip` klauzuli.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa klauzuli, `Skip While` Aby pominąć wyniki do momentu, gdy zostanie znaleziony pierwszy klient z Stany Zjednoczone.  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do LINQ w Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](index.md)
- [SELECT — klauzula](select-clause.md)
- [Klauzula from](from-clause.md)
- [Skip, klauzula](skip-clause.md)
- [Take While, klauzula](take-while-clause.md)
- [Klauzula WHERE](where-clause.md)
