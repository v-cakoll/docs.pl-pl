---
title: ?? Operator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 153accdc4995065563b00da0fd62992341c06cf1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241882"
---
# <a name="-operator-c-reference"></a>?? Operator (odwołanie w C#)
`??` Operator jest nazywany operatorem łączenia wartości null.  Zwraca argument operacji z lewej strony, jeśli ma on wartość inną niż null; w przeciwnym razie zwraca argument operacji po prawej stronie.  
  
## <a name="remarks"></a>Uwagi  
 Typ dopuszczający wartość null może reprezentować wartość z domeny typu albo wartość może być niezdefiniowana (w tym przypadku wartość jest równa null). Możesz użyć `??` wyrazistość składni operatora zwracać odpowiednią wartość (argument operacji po prawej stronie) kiedy Lewy argument operacji ma typ dopuszczający wartość null, którego wartość jest równa null. Jeśli użytkownik próbuje przypisać typem wartościowym z typem wartości niedopuszczającym wartości bez korzystania z `??` operatora, spowoduje wygenerowanie błędu kompilacji. Jeśli używane rzutowanie, a typem wartościowym jest obecnie zdefiniowany `InvalidOperationException` zostanie zgłoszony wyjątek.  
  
 Aby uzyskać więcej informacji, zobacz [typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Wynik? operator nie uznaje się za stałą, nawet jeśli oba argumenty są stałymi.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [null operatora łączącego](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)  
- [Typy dopuszczające wartości null](../../../csharp/programming-guide/nullable-types/index.md)  
- [Jakie dokładnie jest oznacza "Podniesiony"?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
