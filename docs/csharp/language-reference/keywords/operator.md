---
title: "operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords: operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1d035319318a710ccee62a0c64ce5981767a21ca
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/20/2018
---
# <a name="operator-c-reference"></a>operator (odwołanie w C#)
Użyj `operator` — słowo kluczowe przeciążenia operatora wbudowane lub udzielenia konwersji zdefiniowanej przez użytkownika w deklaracji klasy lub struktury.  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się bardzo uproszczonego klasę liczbami ułamkowymi. Przeciąża `+` i `*` operatory przeprowadzić ułamkowych Dodawanie i mnożenie i udostępnia również operatora konwersji tego konwertuje `Fraction` typ `double` typu.  
  
 [!code-csharp[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [implicit](../../../csharp/language-reference/keywords/implicit.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)  
 [Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
