---
title: Operatory warunkowe null — C# odwołania
ms.custom: seodec18
ms.date: 04/03/2015
helpviewer_keywords:
- null-conditional operators [C#]
- ?. operator [C#]
- ?[] operator [C#]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: 38298cded904cbfedeaf3c6b66c74d610d714902
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333242"
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a>?. i? Operatory warunkowe null [] (C# i Visual Basic)

Testuje, czy wartość lewego argumentu operacji to „null”, zanim przeprowadzi operację dostępu do elementu (`?.`) lub indeksowania (`?[]`). Zwraca `null`, jeśli wartość lewego argumentu operacji to `null`.

Operatory te pomagają ograniczyć ilość kodu potrzebnego do sprawdzenia wystąpień wartości „null”, zwłaszcza w przypadku wchodzenia głębiej w struktury danych.

```csharp
int? length = customers?.Length; // null if customers is null
Customer first = customers?[0];  // null if customers is null
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null
```

Operatory warunkowe `null` skracają łańcuch wykonywania operacji.  Jeśli jedna operacja w łańcuchu operacji dostępu i indeks warunkowa składowa zwraca wartość null, nie będzie możliwy pozostałą część wykonania łańcucha.  W poniższym przykładzie `E` nie jest wykonywane, jeśli `A`, `B` lub `C` zwraca wartość `null`.

```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

Inne zastosowanie dostępu do elementu członkowskiego przy użyciu operatora warunkowego `null` polega na wywołaniu delegatów w sposób bezpieczny wątkowo i ze znacznie mniejszą ilością kodu.  Stary sposób wymaga kodu podobnego do poniższego:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
    handler(…);
```

Nowy sposób jest znacznie prostszy:

```csharp
PropertyChanged?.Invoke(…)
```

Nowy sposób jest bezpieczny wątkowo, ponieważ kompilator generuje kod, aby sprawdzić stan `PropertyChanged` tylko jeden raz, a następnie zapisuje wynik w zmiennej tymczasowej. Metodę `Invoke`trzeba wywołać jawnie, ponieważ nie istnieje składnia `PropertyChanged?(e)` do wywołania delegata przy użyciu operatora warunkowego „null”.

## <a name="language-specifications"></a>Specyfikacje języka

Aby uzyskać więcej informacji, zobacz [operatorów warunkowych działających z wartością Null](~/_csharplang/spec/expressions.md#null-conditional-operator) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [?? (z operatorem łączenia wartości null)](null-coalescing-operator.md)
- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)