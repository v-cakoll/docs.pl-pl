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
ms.openlocfilehash: 28cf2633d74f047a751ffdad11f1e1db8328cd6f
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a>?. Operatory warunkowe null ?. oraz ? [] (C# i Visual Basic)
Testuje czy wartość lewego operandu jest `null` przed próbą dostępu do elementu (`?.`) lub indeksu (`?[]`); zwraca `null` jeśli wartość lewego operandu jest `null`. 

Operatory te pomagają w ograniczeniu ilości kodu potrzebnego do sprawdzenia wystąpień wartości `null`, zwłaszcza dla przypadków zagnieżdżania się w strukturach danych.
  
```csharp  
int? liczba_klientow = klienci?.Length; // null jeśli klienci są null   
Klient pierwszy = klienci?[0];  // null jeśli klienci są null  
int? liczba_zamowien = klienci?[0]?.Zamowienia?.Count();  // null jeśli klienci, pierwszy klient lub jego zamówienia są null  
```  
  
```vb  
Dim liczba_klientow = klienci?.Length  ' null jeśli klienci są null  
Dim pierwszy as Klient = klienci?(0)  ' null jeśli klienci są null  
Dim liczba_zamowien as Integer? = klienci?(0)?.Zamowienia?.Count()  ' null jeśli klienci, pierwszy klient lub jego zamówienia są null  
```  
  
Operatory warunkowe `null` skracają łańcuch wykonywania operacji. Jeśli jedna z operacji w łańcuchu zwraca wartość `null`, dalsze wykonanie łańcucha zostaje przerwane. W poniższym przykładzie `E` nie jest wykonywane, jeśli `A`, `B` lub `C` zwraca wartość `null`.
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
Inne użycie sprawdzania wartości `null` polega na utworzeniu delegatów w sposób bezpieczny dla wywołań wielowątkowych ze znacznie mniejszą ilość kodu. Stary sposób wymaga kodu podobnego do poniższego:  
  
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
  
Nowy sposób jest bezpieczny dla wywołań wielowątkowych, ponieważ kompilator generuje kod, aby sprawdzić stan `PropertyChanged` tylko jeden raz, przechowując wynik w zmiennej tymczasowej. Należy jawnie wywołać metodę `Invoke`, ponieważ nie istnieje możliwość wywołania delegata warunkowego w inny sposób, np. `PropertyChanged?(e)`.  
  
## <a name="language-specifications"></a>Specyfikacje języka  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 Aby uzyskać więcej informacji, zobacz [dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [?? (operator łączenie null)](null-coalescing-operator.md)  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Przewodnik programowania w języku Visual Basic](../../../visual-basic/programming-guide/index.md)
