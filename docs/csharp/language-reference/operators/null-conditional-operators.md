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
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a>?. i? warunkowe null [] operatory (C# i Visual Basic)
Wykorzystywane do testowania dla wartości null przed wykonaniem dostępu elementu członkowskiego (`?.`) lub indeks (`?[]`) operacji.  Tych operatorów pomóc zapisu sprawdza mniej kod obsługujący wartości null, szczególnie w przypadku malejącej do struktur danych.  
  
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
  
 Operatory warunku wartości null są short-circuiting.  Jeśli jedna operacja w łańcuchu operacji dostępu i indeksu warunkowy element członkowski zwraca wartość null, pozostałe wykonywania łańcucha zatrzymuje.  W poniższym przykładzie `E` nie jest wykonywana Jeśli `A`, `B`, lub `C` obliczane do wartości null.
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 Użyj innego dostępu element członkowski warunku wartości null jest powoływanie delegatów w sposób obsługującej wielowątkowość ze znacznie mniejsza ilość kodu.  Stary sposób wymaga kodu podobne do poniższych:  
  
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
  
 Nowy sposób jest znacznie prostsza:  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 Nowy sposób jest bezpieczne wątkowo, ponieważ kompilator generuje kod, aby ocenić `PropertyChanged` tylko jeden raz, zachowania wynik w zmiennej tymczasowej.  
  
 Należy jawnie wywołać `Invoke` metody ponieważ nie istnieje żadna Składnia wywołania delegata warunkowe null `PropertyChanged?(e)`.  
  
## <a name="language-specifications"></a>Specyfikacje języka  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 Aby uzyskać więcej informacji, zobacz [dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [?? (operator łączenie null)](null-conditional-operator.md)  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md)  
 [Przewodnik programowania w języku Visual Basic](../../../visual-basic/programming-guide/index.md)
