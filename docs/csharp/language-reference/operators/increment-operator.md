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
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
