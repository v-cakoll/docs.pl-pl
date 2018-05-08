---
title: Operator % (odwołanie w C#)
ms.date: 04/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: b906feb22aaec97e58da562b615baae01f3e0719
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>Operator % (odwołanie w C#)
Operator reszty (`%`) oblicza resztę po podzieleniu jego pierwszym argumentem przez jego sekundy. Wszystkie typy liczbowe ma wstępnie zdefiniowane operatory resztę. 
  
## <a name="remarks"></a>Uwagi  
 Formuła `a % b` zawsze zwróci wartość z zakresu `(-b, b)`, wyłącznego (nigdy nie może zwrócić `b` lub `-b`), przechowywania znak dzielna. Dla dzielenie liczby całkowitej operator reszty spełnia reguły `a % b = a - (a / b) * b`.
  
 Pozwala to nie należy mylić z canonical modulo, które spełniają reguły podobne, lecz z floored dzielenia i zwraca wartości zakresu `[0, b)`. C# nie ma operator modulo kanonicznej. Jednak zachowanie jest takie same dla dywidendy dodatnią.
  
 Typy definiowane przez użytkownika można przeciążać `%` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/remainder-operator_1.cs)]  
  
## <a name="comments"></a>Komentarze  
 Należy pamiętać, błędów zaokrąglania skojarzonych z typu double.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
