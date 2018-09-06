---
title: Operator % (odwołanie w C#)
ms.date: 04/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: 477f2491e6d2efe6b5c327efb371843d0bf12c26
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723876"
---
# <a name="-operator-c-reference"></a>Operator % (odwołanie w C#)
Operator reszty (`%`) oblicza pozostałą po podzieleniu swojego pierwszego operandu przez drugi jej. Wszystkie typy liczbowe ma wstępnie zdefiniowane operatory resztę. 
  
## <a name="remarks"></a>Uwagi  
 Formuła `a % b` zawsze zwraca wartość w zakresie `(-b, b)`Ekskluzywna (nigdy nie może zwrócić `b` lub `-b`), utrzymywanie znak dzielna. Dzielenie liczby całkowitej, operator reszty spełnia reguły `a % b = a - (a / b) * b`.
  
 Nie należy mylić modulo canonical, które spełniają reguły podobne, ale floored dzielenia i zwraca wartości na zakresie `[0, b)`. C# ma operator modulo kanonicznej. Jednak to zachowanie jest taki sam dla dywidendy dodatnią.
  
 Typy definiowane przez użytkownika mogą przeciążać operator `%` — (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/remainder-operator_1.cs)]  
  
## <a name="comments"></a>Komentarze  
 Należy pamiętać, błędy zaokrąglania skojarzone z typem double.  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
