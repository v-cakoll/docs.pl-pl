---
title: unchecked (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: daccd7916a9f81f26f468ab0f64833d9537cff8e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43415779"
---
# <a name="unchecked-c-reference"></a>unchecked (odwołanie w C#)
`unchecked` Słowo kluczowe jest używane, aby pominąć sprawdzanie przepełnienia dla typu całkowitego operacje arytmetyczne i konwersje.  
  
 W kontekście niesprawdzanym Jeśli wyrażenie generuje wartość, która znajduje się poza zakresem typu docelowego przeciążenia nie jest oznaczony. Na przykład ponieważ obliczenie w poniższym przykładzie jest wykonywane w `unchecked` bloku lub wyrażenie, fakt, że wynik jest za duży dla liczby całkowitej jest ignorowana, a `int1` jest przypisywana wartość-2,147,483,639.  
  
 [!code-csharp[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 Jeśli `unchecked` środowiska zostanie usunięty, pojawia się błąd kompilacji. Ponieważ wszystkie warunki wyrażenia są stałe, można wykryć przepełnienie w czasie kompilacji.  
  
 Wyrażenia, które zawierają wartość niebędącą stałą warunki nie domyślnie są zaznaczone w czasie kompilacji i czasu wykonywania. Zobacz [zaznaczone](../../../csharp/language-reference/keywords/checked.md) informacji na temat włączania środowiska zaznaczone.  
  
 Ponieważ sprawdzania dla przepełnienia zajmuje trochę czasu, użycie unchecked kodu w sytuacjach, gdy ma zagrożenia przepełnienia może zwiększyć wydajność. Jednak jeśli przepełnienia jest możliwość, należy użyć środowiska zaznaczone.  
  
## <a name="example"></a>Przykład  
 Ten przykład ilustruje sposób używania `unchecked` — słowo kluczowe.  
  
 [!code-csharp[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Checked i Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
- [checked](../../../csharp/language-reference/keywords/checked.md)
