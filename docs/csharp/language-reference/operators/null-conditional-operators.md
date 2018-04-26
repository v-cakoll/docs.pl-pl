---
title: Operatory warunkowe null (C# i Visual Basic)
ms.date: 04/03/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3ffeaa3c2088d0bb2c000704cfe312b0f9453b68
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a>Operatory warunkowe null ?. oraz ? []  (C# i Visual Basic)
Wykorzystywane do testowania wystąpienia wartości null przed wykonaniem dostępu elementu członkowskiego (`?.`) lub odwołaniem do indeksu (`?[]`).  Pomagają one w ograniczeniu ilości kodu potrzebnego do sprawdzenia wystapień wartości null, zwłaszcza dla przypadków zstępujących do struktur danych.  
  
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
  
 Operatory warunkowe wartości null są krótko obiegowe.  Jeśli jedna z operacji w łańcuchu dostępu zwraca wartość null, dalsze wykonanie łańcucha zostaje przerwane.  W poniższym przykładzie `E` nie jest wykonywane Jeśli `A`, `B`, lub `C` zwraca wartość null.
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 Inne użycie operatorów warunkowych null, polega na "wątkowo bezpiecznym" wywołaniu delegatów z mniejszą ilością kodu. Stary sposób wymaga kodu podobnego do poniższego:  
  
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
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 Nowy sposób jest bezpieczny wątkowo, ponieważ kompilator generuje kod, aby ocenić `PropertyChanged` tylko jeden raz, przechowując wynik w zmiennej tymczasowej.  
  
 Należy jawnie wywołać metodę `Invoke` ponieważ nie istnieje możliwość wywołania delegata warunkowego null za pomocą żadnej z dostępnych składni `PropertyChanged?(e)`.  
  
## <a name="language-specifications"></a>Specyfikacje języka  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 Aby uzyskać więcej informacji, zobacz [dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [?? (operator łączenie null)](null-conditional-operator.md)  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md)  
 [Przewodnik programowania w języku Visual Basic](../../../visual-basic/programming-guide/index.md)
