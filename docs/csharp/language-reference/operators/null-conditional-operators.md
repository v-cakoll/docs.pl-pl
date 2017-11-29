---
title: Operatory warunkowe null (C# i Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c95b4079cf4e71c0ef9cd436ec230337f512229a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="null-conditional-operators-c-and-visual-basic"></a>Operatory warunkowe null (C# i Visual Basic)
Wykorzystywane do testowania dla wartości null przed wykonaniem dostępu elementu członkowskiego (`?.`) lub indeks (`?[`) operacji.  Tych operatorów pomóc zapisu sprawdza mniej kod obsługujący wartości null, szczególnie w przypadku malejącej do struktur danych.  
  
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
  
 W ostatnim przykładzie pokazano, czy short-circuiting operatory warunku wartości null.  Jeśli jedna operacja w łańcuchu operacji dostępu i indeksu warunkowy element członkowski zwraca wartość null, pozostałe wykonywania łańcucha zatrzymuje.  Nadal innych operacji o niższym priorytecie w wyrażeniu.  Na przykład `E` poniżej wykonuje w drugim wierszu i `??` i `==` wykonania operacji.  W pierwszym wierszu `??` krótkiej obwody i `E` nie wykonuj po lewej ocenia się na inną niż null.
  
```csharp
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
```

```vb
A?.B?.C?(0) ?? E  
A?.B?.C?(0) == E  
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
  
 Należy jawnie wywołać `Invoke` metody ponieważ nie istnieje żadna Składnia wywołania delegata warunkowe null `PropertyChanged?(e)`.  Znaleziono zbyt wiele niejednoznaczne analizy sytuacji, aby umożliwić jego.  
  
## <a name="language-specifications"></a>Specyfikacje języka  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 Aby uzyskać więcej informacji, zobacz [dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [?? (operator łączenie null)](null-conditional-operator.md)  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md)  
 [Przewodnik programowania w języku Visual Basic](../../../visual-basic/programming-guide/index.md)
