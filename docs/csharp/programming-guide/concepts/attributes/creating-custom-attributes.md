---
title: Tworzenie atrybutów niestandardowych (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: ec959723c339a13a40fd62388421ceacb736dfca
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389557"
---
# <a name="creating-custom-attributes-c"></a>Tworzenie atrybutów niestandardowych (C#)
Można utworzyć własne atrybuty niestandardowe przez zdefiniowanie klasy atrybutów, klasy, która dziedziczy bezpośrednio lub pośrednio z <xref:System.Attribute> , co sprawia, że definicje atrybutów i są łatwe w użyciu w metadanych. Załóżmy, że chcesz oznakować typy nazwą programisty, który zapisał typ. Można zdefiniować `Author` klasę niestandardowego atrybutu:  
  
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
  
 Nazwa klasy jest nazwą atrybutu, `Author` . Jest ona pochodną `System.Attribute` , więc jest klasą atrybutów niestandardowych. Parametry konstruktora są parametrami pozycyjnymi atrybutu niestandardowego. W tym przykładzie `name` jest parametrem pozycyjnym. Wszystkie publiczne pola do odczytu i zapisu są nazwanymi parametrami. W tym przypadku `version` jest jedynym nazwanym parametrem. Zwróć uwagę na użycie `AttributeUsage` atrybutu, aby atrybut był `Author` prawidłowy tylko dla klasy i `struct` deklaracji.  
  
 Tego nowego atrybutu można użyć w następujący sposób:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage`ma nazwany parametr, `AllowMultiple` za pomocą którego można wykonać pojedyncze użycie lub Multiuse atrybutu niestandardowego. W poniższym przykładzie kodu tworzony jest atrybut Multiuse.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection>
- [Przewodnik programowania w języku C#](../../index.md)
- [Wpisywanie atrybutów niestandardowych](../../../../standard/attributes/writing-custom-attributes.md)
- [Odbicie (C#)](../reflection.md)
- [Atrybuty (C#)](./index.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](./accessing-attributes-by-using-reflection.md)
- [AttributeUsage (C#)](../../../language-reference/attributes/general.md)
