---
title: Tworzenie atrybutów niestandardowych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 3b1b03f69229bd4d824d6fff734b83400c2aab44
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524299"
---
# <a name="creating-custom-attributes-visual-basic"></a>Tworzenie atrybutów niestandardowych (Visual Basic)

Można utworzyć własne atrybuty niestandardowe przez zdefiniowanie klasy atrybutów, klasy, która dziedziczy bezpośrednio lub pośrednio z <xref:System.Attribute>, co umożliwia szybkie i łatwe identyfikowanie definicji atrybutów w metadanych. Załóżmy, że chcesz oznakować typy nazwą programisty, który zapisał typ. Można zdefiniować niestandardową klasę atrybutów `Author`:

```vb
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName
        version = 1.0
    End Sub
End Class
```

Nazwa klasy jest nazwą atrybutu, `Author`. Jest ona pochodną `System.Attribute`, więc jest klasą atrybutów niestandardowych. Parametry konstruktora są parametrami pozycyjnymi atrybutu niestandardowego. W tym przykładzie `name` jest parametrem pozycyjnym. Wszystkie publiczne pola do odczytu i zapisu są nazwanymi parametrami. W tym przypadku `version` jest jedynym parametrem nazwanym. Zwróć uwagę na użycie atrybutu `AttributeUsage`, aby atrybut `Author` był prawidłowy tylko w deklaracjach klasy i `Structure`.

Tego nowego atrybutu można użyć w następujący sposób:

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

`AttributeUsage` ma nazwany parametr `AllowMultiple`, za pomocą którego można utworzyć atrybut niestandardowy pojedynczy lub Multiuse. W poniższym przykładzie kodu tworzony jest atrybut Multiuse.

```vb
' multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
```

W poniższym przykładzie kodu do klasy są stosowane wiele atrybutów tego samego typu.

```vb
<Author("P. Ackerman", Version:=1.1),
Author("R. Koch", Version:=1.2)>
Class SampleClass
    ' P. Ackerman's code goes here...
    ' R. Koch's code goes here...
End Class
```

> [!NOTE]
> Jeśli Klasa atrybutu zawiera właściwość, ta właściwość musi mieć wartość Read-Write.

## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection>
- [Przewodnik programowania Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Wpisywanie atrybutów niestandardowych](../../../../standard/attributes/writing-custom-attributes.md)
- [Odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Atrybuty (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
