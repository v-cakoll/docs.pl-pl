---
title: Atrybut „Extension” można stosować tylko w deklaracjach „Module”, „Sub” lub „Function”
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 9b8f49c498699a8f7d1c4b329e82258501aa0c47
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363101"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>Atrybut „Extension” można stosować tylko w deklaracjach „Module”, „Sub” lub „Function”

Jedynym sposobem rozszerzania typu danych w Visual Basic jest zdefiniowanie metody rozszerzającej wewnątrz modułu standardowego. Metoda rozszerzenia może być `Sub` procedurą lub `Function` procedurą. Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia, `<Extension()>` z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw. Opcjonalnie moduł, który zawiera metodę rozszerzenia, może być oznaczony w taki sam sposób. Żadne inne użycie atrybutu Extension nie jest prawidłowe.

**Identyfikator błędu:** BC36550

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń atrybut rozszerzenia.

- Przeprojektowanie rozszerzenia jako metody zdefiniowanej w otaczającym module.

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano `Print` metodę dla `String` typu danych.

```vb
Imports StringUtility
Imports System.Runtime.CompilerServices
Namespace StringUtility
    <Extension()>
    Module StringExtensions
        <Extension()>
        Public Sub Print (ByVal str As String)
            Console.WriteLine(str)
        End Sub
    End Module
End Namespace
```

## <a name="see-also"></a>Zobacz też

- [Przegląd atrybutów](../../programming-guide/concepts/attributes/index.md)
- [Metody rozszerzające](../../programming-guide/language-features/procedures/extension-methods.md)
- [Module — Instrukcja](../statements/module-statement.md)
