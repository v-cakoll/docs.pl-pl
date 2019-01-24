---
title: Operatory warunkowe null (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: d30d452a7c140a0c56529386b14ef3a3512df490
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722156"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. i? Operatory warunkowe null () (Visual Basic)

Sprawdza wartość operandu po lewej stronie w przypadku wartości null (`Nothing`) przed wykonaniem dostęp do elementu członkowskiego (`?.`) lub indeksu (`?()`) operacja; zwraca `Nothing` Jeśli po lewej stronie operand ma wartość `Nothing`. Należy pamiętać, że w wyrażeniach, które zazwyczaj zwróci typów wartości, operatorów warunkowych działających z wartością null zwraca <xref:System.Nullable%601>.

Te operatory pomóc w pisaniu mniejszej ilości kodu do obsługi sprawdzanie wartości null, szczególnie w przypadku, gdy malejąco do struktur danych. Na przykład:

```vb
Dim length As Integer? = customers?.Length  ' Nothing if customers is Nothing  
Dim first As Customer = customers?(0)  ' Nothing if customers is Nothing  
Dim count As Integer? = customers?(0)?.Orders?.Count()  ' Nothing if customers, the first customer, or Orders is Nothing  
```

Dla porównania alternatywnych kod dla pierwszego dnia te wyrażenia bez operatorów warunkowych działających z wartością null jest:

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Operatory warunkowe `null` skracają łańcuch wykonywania operacji.  Jeśli jedna operacja w łańcuchu operacji dostępu i indeks warunkowa składowa zwraca nic, zatrzymuje pozostałą część wykonania łańcucha.  W poniższym przykładzie C(E) nie są oceniane, jeśli `A`, `B`, lub `C` ocenia na wartość Nothing.

```vb
A?.B?.C?(E);
```

Innym zastosowaniem uzyskać dostęp do elementu członkowskiego warunkowe null jest wywoływać delegatów w sposób wątkowo ze znacznie mniejszej ilości kodu.  Stary sposób wymaga kodu podobnego do poniższego:  

```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```

Nowy sposób jest znacznie prostszy:  

```vb
PropertyChanged?.Invoke(…)
```

Nowy sposób jest bezpieczny wątkowo, ponieważ kompilator generuje kod, aby sprawdzić stan `PropertyChanged` tylko jeden raz, a następnie zapisuje wynik w zmiennej tymczasowej. Metodę `Invoke`trzeba wywołać jawnie, ponieważ nie istnieje składnia `PropertyChanged?(e)` do wywołania delegata przy użyciu operatora warunkowego „null”.  

## <a name="see-also"></a>Zobacz także

- [Operatory (Visual Basic)](index.md)
- [Przewodnik programowania w języku Visual Basic](../../../visual-basic/programming-guide/index.md)
- [Dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md)
