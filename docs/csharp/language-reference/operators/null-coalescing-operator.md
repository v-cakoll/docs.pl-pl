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
ms.openlocfilehash: 03d81d4216dabce2ea75b9fdcf6ef0971cc32490
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388862"
---
# <a name="-operator-c-reference"></a>?? Operator (odwołanie w C#)
`??` Operator jest nazywany operatorem łączenia wartości null.  Zwraca argument operacji z lewej strony, jeśli ma on wartość inną niż null; w przeciwnym razie zwraca argument operacji po prawej stronie.  
  
## <a name="remarks"></a>Uwagi  
 Typ dopuszczający wartość null może reprezentować wartość z domeny typu albo wartość może być niezdefiniowana (w tym przypadku wartość jest równa null). Możesz użyć `??` wyrazistość składni operatora zwracać odpowiednią wartość (argument operacji po prawej stronie) kiedy Lewy argument operacji ma typ dopuszczający wartość null, którego wartość jest równa null. Jeśli użytkownik próbuje przypisać typem wartościowym z typem wartości niedopuszczającym wartości bez korzystania z `??` operatora, spowoduje wygenerowanie błędu kompilacji. Jeśli używane rzutowanie, a typem wartościowym jest obecnie zdefiniowany `InvalidOperationException` zostanie zgłoszony wyjątek.  
  
 Aby uzyskać więcej informacji, zobacz [typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Wynik? operator nie uznaje się za stałą, nawet jeśli oba argumenty są stałymi.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)  
- [Typy dopuszczające wartości null](../../../csharp/programming-guide/nullable-types/index.md)  
- [Jakie dokładnie jest oznacza "Podniesiony"?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
