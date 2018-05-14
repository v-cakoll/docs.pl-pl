---
title: Operatory warunkowe null (C# i Visual Basic)
ms.date: 04/03/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- null-conditional operators [C#]
- null-conditional operators [Visual Basic]
- ?. operator [C#]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: da771fa4a2a89dca308508ea81ef8e0060efa7f0
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2018
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a>?. Operatory warunkowe null ?. oraz ? [] (C# i Visual Basic)
Testy wartość lewego operandu na wartość null przed wykonaniem dostępu elementu członkowskiego (`?.`) lub indeks (`?[]`) operację; zwraca `null` Jeśli lewego operandu daje w wyniku `null`. 

Pomagają one w ograniczeniu ilości kodu potrzebnego do sprawdzenia wystąpień wartości null, zwłaszcza dla przypadków zstępujących do struktur danych.  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
```vb  
Dim length = customers?.Length  ' null if customers is null  
Dim first as Customer = customers?(0)  ' null if customers is null  
Dim count as Integer? = customers?(0)?.Orders?.Count()  ' null if customers, the first customer, or Orders is null  
```  
  
 Operatory warunkowe null są short-circuiting.  Jeśli jedna z operacji w łańcuchu dostępu zwraca wartość null, dalsze wykonanie łańcucha zostaje przerwane.  W poniższym przykładzie `E` nie jest wykonywane, jeśli `A`, `B` lub `C` zwraca wartość null.
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 Użyj innego dostępu warunkowego wartości null elementu członkowskiego jest powoływanie delegatów w sposób obsługującej wielowątkowość ze znacznie mniejsza ilość kodu.  Stary sposób wymaga kodu podobnego do poniższego:  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```  
  
 Nowy sposób jest znacznie prostszy:  
  
```csharp
PropertyChanged?.Invoke(…)  
```  

```vb
PropertyChanged?.Invoke(…)
```  
  
 Nowy sposób jest bezpieczny wątkowo, ponieważ kompilator generuje kod, aby ocenić `PropertyChanged` tylko jeden raz, przechowując wynik w zmiennej tymczasowej. Należy jawnie wywołać metodę `Invoke`, ponieważ nie istnieje możliwość wywołania delegata warunkowego null za pomocą żadnej z dostępnych składni `PropertyChanged?(e)`.  
  
## <a name="language-specifications"></a>Specyfikacje języka  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 Aby uzyskać więcej informacji, zobacz [dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [?? (operator łączenie null)](null-conditional-operator.md)  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Przewodnik programowania w języku Visual Basic](../../../visual-basic/programming-guide/index.md)
