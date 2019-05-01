---
title: Atrybut „Extension” można stosować tylko w deklaracjach „Module”, „Sub” lub „Function”
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: a4561359e4d7cb0f6ebe44a5deb09b3374556ed8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801650"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>Atrybut „Extension” można stosować tylko w deklaracjach „Module”, „Sub” lub „Function”
Jedynym sposobem, aby rozszerzyć typu danych w języku Visual Basic jest zdefiniować metodę rozszerzenia w ramach standardowego modułu. Metoda rozszerzenia może być `Sub` procedury lub `Function` procedury. Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia, `<Extension()>`, z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw. Opcjonalnie moduł, który zawiera metodę rozszerzającą może być oznaczony w taki sam sposób. Zakaz używania atrybutu rozszerzenia jest nieprawidłowy.  
  
 **Identyfikator błędu:** BC36550  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Usuń atrybut rozszerzenia.  
  
- Zmodyfikowanie Twojego rozszerzenia jako metoda, zdefiniowana w module otaczającej.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano `Print` metodę `String` typu danych.  
  
```  
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
  
## <a name="see-also"></a>Zobacz także

- [Omówienie atrybuty](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Metody rozszerzeń](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Instrukcja Module](../../../visual-basic/language-reference/statements/module-statement.md)
