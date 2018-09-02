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
ms.openlocfilehash: f00d5e489931d9c1172a21ee5f0d3e3d0a6f4a4e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43409001"
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a>?. Operatory warunkowe null ?. oraz ? [] (C# i Visual Basic)
Testuje, czy wartość lewego argumentu operacji to „null”, zanim przeprowadzi operację dostępu do elementu (`?.`) lub indeksowania (`?[]`). Zwraca `null`, jeśli wartość lewego argumentu operacji to `null`. 

Operatory te pomagają ograniczyć ilość kodu potrzebnego do sprawdzenia wystąpień wartości „null”, zwłaszcza w przypadku wchodzenia głębiej w struktury danych.  
  
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
  
 Operatory warunkowe `null` skracają łańcuch wykonywania operacji.  Jeśli jedna z operacji w łańcuchu zwraca wartość `null`, dalsze wykonanie łańcucha zostaje przerwane.  W poniższym przykładzie `E` nie jest wykonywane, jeśli `A`, `B` lub `C` zwraca wartość `null`.
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 Inne zastosowanie dostępu do elementu członkowskiego przy użyciu operatora warunkowego `null` polega na wywołaniu delegatów w sposób bezpieczny wątkowo i ze znacznie mniejszą ilością kodu.  Stary sposób wymaga kodu podobnego do poniższego:  
  
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
  
 Nowy sposób jest bezpieczny wątkowo, ponieważ kompilator generuje kod, aby sprawdzić stan `PropertyChanged` tylko jeden raz, a następnie zapisuje wynik w zmiennej tymczasowej. Metodę `Invoke`trzeba wywołać jawnie, ponieważ nie istnieje składnia `PropertyChanged?(e)` do wywołania delegata przy użyciu operatora warunkowego „null”.  
  
## <a name="language-specifications"></a>Specyfikacje języka  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 Aby uzyskać więcej informacji, zobacz [odwołanie językowe Visual Basic](../../../visual-basic/language-reference/index.md).  
  
## <a name="see-also"></a>Zobacz też

- [?? (z operatorem łączenia wartości null)](null-coalescing-operator.md)  
- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Przewodnik programowania w języku Visual Basic](../../../visual-basic/programming-guide/index.md)
