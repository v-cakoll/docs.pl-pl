---
title: ++ — Operator (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6deb2f772fefc93020e7eaaed6be35e48b11df7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
