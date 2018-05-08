---
title: ?? Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 8fa751654acaf5939fb8f8068c7323e365f7bdab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>?? Operator (odwołanie w C#)
`??` Operator jest nazywany operatora łączenia wartości null.  Zwraca argument operacji z lewej strony, jeśli ma on wartość inną niż null; w przeciwnym razie zwraca argument operacji po prawej stronie.  
  
## <a name="remarks"></a>Uwagi  
 Typ dopuszczający wartość null może reprezentować wartość z domeny typu albo wartość może być niezdefiniowana (w tym przypadku wartość jest równa null). Można użyć `??` wyrazistość składni operatora do zwrócenia ją odpowiednią wartością (argument prawej) kiedy Lewy argument operacji ma typ dopuszczający wartość null, którego wartość jest równa null. Jeśli spróbujesz przypisać typu wartości null na typ wartości niedopuszczający wartości null bez użycia `??` operatora, zostanie wygenerowany błąd kompilacji. Jeśli używasz rzutowanie i typ wartości null jest obecnie Niezdefiniowany `InvalidOperationException` zostanie wygenerowany wyjątek.  
  
 Aby uzyskać więcej informacji, zobacz [typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Wynik? operator nie jest uważany za stałą, nawet, jeśli oba argumenty są stałe.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)  
 [Typy dopuszczające wartości null](../../../csharp/programming-guide/nullable-types/index.md)  
 [Jakie dokładnie jest "Unosiło" oznacza?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
