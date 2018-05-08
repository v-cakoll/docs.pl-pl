---
title: ++ — Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: 0fe1150ca7267d02feeab33168eab7f79734c2a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>++ — Operator (odwołanie w C#)
Operator inkrementacji (`++`) zwiększa jej argument operacji o 1. Operator inkrementacji może występować przed lub po jej argument: `++variable` i `variable++`.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy formularz jest operacja zwiększenia prefiks. Wynikiem operacji jest wartość operandu po została zwiększona.  
  
 Drugi formularz jest operacją operatory przyrostka inkrementacji. Wynikiem operacji jest wartość operandu przed została zwiększona.  
  
 Typy numeryczne i wyliczenia mają wstępnie zdefiniowane operatory inkrementacji. Typy definiowane przez użytkownika można przeciążać `++` operatora. Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
