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
Operator inkrementacji (`++`) zwieksza wartosc argumentu operacji o 1. Operator inkrementacji moze wystepowac przed argumentem operacji lub po nim: `++variable` i `variable++`.
  
## <a name="remarks"></a>Uwagi  
 Pierwsza forma to inkrementacja prefiksowa. Wynikiem tej operacji jest wartosc argumentu po zwiekszeniu.
  
Druga forma to inkrementacja odwrotna. Wynikiem tej operacji jest wartosc argumentu przed zwiekszeniem. 
  
 Typy numeryczne i wyliczenia maja wstepnie zdefiniowane operatory inkrementacji. W typach definiowanych przez uzytkownika mozna przeciazac operator `++`. Operacje na typach calkowitych w wyliczeniach sa zazwyczaj dozwolone.
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
