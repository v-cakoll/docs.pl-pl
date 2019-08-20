---
title: Tworzenie atrybutów niestandardowych (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: c0f25adf0d562b659edaa8f36e72332fd0c1ee7e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595406"
---
# <a name="creating-custom-attributes-c"></a>Tworzenie atrybutów niestandardowych (C#)
Można utworzyć własne atrybuty niestandardowe przez zdefiniowanie klasy atrybutów, klasy, która dziedziczy bezpośrednio lub pośrednio z, co <xref:System.Attribute>sprawia, że definicje atrybutów i są łatwe w użyciu w metadanych. Załóżmy, że chcesz oznakować typy nazwą programisty, który zapisał typ. Można zdefiniować klasę niestandardowego `Author` atrybutu:  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class Author : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 Nazwa klasy jest nazwą atrybutu, `Author`. Jest ona pochodną `System.Attribute`, więc jest klasą atrybutów niestandardowych. Parametry konstruktora są parametrami pozycyjnymi atrybutu niestandardowego. W tym przykładzie `name` jest parametrem pozycyjnym. Wszystkie publiczne pola do odczytu i zapisu są nazwanymi parametrami. W tym przypadku `version` jest jedynym nazwanym parametrem. Zwróć uwagę na użycie `AttributeUsage` atrybutu, aby `Author` atrybut był prawidłowy tylko dla klasy i `struct` deklaracji.  
  
 Tego nowego atrybutu można użyć w następujący sposób:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage`ma nazwany parametr `AllowMultiple`, za pomocą którego można wykonać pojedyncze użycie lub Multiuse atrybutu niestandardowego. W poniższym przykładzie kodu tworzony jest atrybut Multiuse.  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 W poniższym przykładzie kodu do klasy są stosowane wiele atrybutów tego samego typu.  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection>
- [Przewodnik programowania w języku C#](../../index.md)
- [Wpisywanie atrybutów niestandardowych](../../../../standard/attributes/writing-custom-attributes.md)
- [OdbicieC#()](../reflection.md)
- [Atrybuty (C#)](./index.md)
- [Uzyskiwanie dostępu do atrybutów przyC#użyciu odbicia ()](./accessing-attributes-by-using-reflection.md)
- [AttributeUsage (C#)](./attributeusage.md)
