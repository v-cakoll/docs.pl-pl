---
title: Tworzenie atrybutów niestandardowych
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 84b400c2fa1b2d4019eec32092f954d680e64978
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400697"
---
# <a name="creating-custom-attributes-visual-basic"></a>Tworzenie atrybutów niestandardowych (Visual Basic)

Można utworzyć własne atrybuty niestandardowe przez zdefiniowanie klasy atrybutów, klasy, która dziedziczy bezpośrednio lub pośrednio z <xref:System.Attribute> , co sprawia, że definicje atrybutów i są łatwe w użyciu w metadanych. Załóżmy, że chcesz oznakować typy nazwą programisty, który zapisał typ. Można zdefiniować `Author` klasę niestandardowego atrybutu:

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

Nazwa klasy jest nazwą atrybutu, `Author` . Jest ona pochodną `System.Attribute` , więc jest klasą atrybutów niestandardowych. Parametry konstruktora są parametrami pozycyjnymi atrybutu niestandardowego. W tym przykładzie `name` jest parametrem pozycyjnym. Wszystkie publiczne pola do odczytu i zapisu są nazwanymi parametrami. W tym przypadku `version` jest jedynym nazwanym parametrem. Zwróć uwagę na użycie `AttributeUsage` atrybutu, aby atrybut był `Author` prawidłowy tylko dla klasy i `Structure` deklaracji.

Tego nowego atrybutu można użyć w następujący sposób:

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

`AttributeUsage`ma nazwany parametr, `AllowMultiple` za pomocą którego można wykonać pojedyncze użycie lub Multiuse atrybutu niestandardowego. W poniższym przykładzie kodu tworzony jest atrybut Multiuse.

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

## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection>
- [Przewodnik programowania w Visual Basic](../../index.md)
- [Wpisywanie atrybutów niestandardowych](../../../../standard/attributes/writing-custom-attributes.md)
- [Odbicie (Visual Basic)](../reflection.md)
- [Atrybuty (Visual Basic)](../../../language-reference/attributes.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](accessing-attributes-by-using-reflection.md)
- [AttributeUsage (Visual Basic)](attributeusage.md)
